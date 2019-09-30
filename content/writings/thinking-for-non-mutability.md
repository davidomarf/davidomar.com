---
title: "Living without the assignment operator"
date: 2019-09-13T19:59:51-05:00
draft: true
---
Today I started to migrate [subway-networks][subway-networks] from JavaScript
to Clojure.

It wasn't like migrating it from JavaScript to Go, Ruby, Java, or any other C-like
language.

It represented a higher challenge by two main reasons:

- Clojure is a LISP-family language, which meant that I had to learn
to write programs using Lisp syntax. 
- Clojure types are immutable.

And one extra reason that I didn't found out about until later in the game:

- The approach to system design, or [top-down vs bottom-up][top-down-bottom-up].

The LISP-syntax problem is something that just slows you down a little bit for
a few hours. If you write a piece of code that looks like this

```javascript
let doubleDistance = distance(a.x, a.y, b.x, b.y) * 2
```

You just (most of the times) need to go back, and change the order a little bit

```clojure
(def double-distance 
(* (distance (:x a) (:y a) (:x b) (:y b)) 2))
```

The real struggle is in the immutability thing.

Originally, I didn't think it would matter enough. **Oh, yeah, just make this
function return a new object with the updated properties instead of updating
the original object, pff.**

But oh boy if I was wrong.

If a language strongly enforces immutability, you'll be left without so many
things you just assumed were shared among all the languages. (And with this,
I assume that the "you" in that sentence has only programmed in imperative
languages that allow mutability)

For loops? Gone.

You need to start thinking in
a _functional_ way.

Referential transparency is the idea that you'll always obtain the same result
when calling a particular function if you call it with the same arguments every
time.

And pure functions are those that don't have side-effects. This means that we no
longer have mutability.

This has various implications. For-loops, for example, are now extinct, since
you need a "flag variable" that mutates every loop. Nowu need to rely completely
in recursion.

But being used to write programs using imperative languages for a long time (yes,
I'm daring to call 2-3 years a long time), makes it really hard to make the
mindset shift necessary to think in a functional way.

---

The topic that made me doubt if any of the things I was coding were any good was
efficiency.

Every function I wrote made me felt like I was doing such an inefficient,
inelegant, dumb thing.

And I think that's still one consequence of being used to languages with mutable
data types.

Let's take the case of the array, for example.

In C, an array is, underneath the hood, a memory location.

Accessing an element using `[i]` just retrieves the value inside the
memory location `m` + `i * sizeof(type)`.

That's why an array in C can be created using `malloc`, which takes the size
of the memory space you want to allocate, and returns the address of that
assigned memory space. That's also why you call malloc using the number of
items you want to include, and the size in bytes for the data type you're
going to contain.

`double *dArr = malloc (n * sizeof(double))`

Now, let's say we want to create a copy of an existing array.

To do that, we need to
allocate a new array (O(1)),
loop through the existing array (O(n))
and copy each element (O(1)) from `old[i]` to `new[i]`.

This means that the copy operation has O(n) complexity, making the time our
program will take to copy an array to grow linearly with the size of the array.

And not only that. We now have two copies of the array, each one taking the same
memory space.

That certainly adds a cost to preferring copying over mutating. Because mutating
the value of any index of the array is done in O(1): `arr[i] = newValue`.

[Clojure has persistent vectors][clj-persistent-vectors], which makes copying
an array, map, tuple, list, or whatever floats your boat, a function with O(1)
complexity.

[Watch this talk to understand how to decide the approach to keep track
of chanegs][top-down-bottom-up]

## TL;DR

If I ever forget what I've learned in the last week, I'd just re-read this:
don't worry for the performance issues you **feel** you're causing by having to
deal with non-mutability, the language knows how to handle it.

Same for recursion depth. the language knows how to handle that as well.


[subway-networks]: /projects/subway-networks/
[clj-persistent-vectors]: https://hypirion.com/musings/understanding-persistent-vector-pt-1
[top-down-bottom-up]: https://www.youtube.com/watch?v=Tb823aqgX_0
[pros-debugging]: 
[pros-succint]:
[pros-modularity]:
[pros-testing]: