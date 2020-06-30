---
title: "Functional thinking and seemingly non-efficent code"
excerpt:
  Or why I needed to forget what I knew about efficency in programming to let
  myself rely on language optimizations.
date: 2019-09-13T19:59:51-05:00
toc: true
draft: false
---

Ever since I started to learn coding, I've been using imperative programming
languages, in which your focus as programmer is commonly described as _"writing
code that exactly defines how to perform a certain task"_.

These languages rely on loops, conditionals, and state changes or mutations.

But I guess every programmer who has spent some time learning new things, has
found some interest in functional languages, such as Haskell, Clojure, Elm,
Scala, etc...

I first tried to learn Haskell, and solved some programming problems with it. I
got somewhat familiar with pattern matching, tail recursion, pure functions, and
immutability. But I got back to what I was used to, namely JavaScript, Python,
and C.

After almost two years, I got the hots for functional programming again. The
tipping point to give it a try, was finding out that one of the companies I'd
like to work in was using **Clojure**.

## Migrating to Clojure

To start exploring it, I decided to migrate a personal project originally
written in JavaScript. I read [Brave Clojure](https://www.braveclojure.com/)
along the way to ease the process.

The two main Clojure features that made the migration interesting were:

- LISP syntax, and
- immutability.

The LISP syntax is something that just slows you down a little bit for the first
few hours. It feels weird to get a bunch of parentheses thrown at your face, but
you quickly get used to it, and may even start to like it.

The real struggle is the immutability thing.

Originally, I didn't think it would matter enough.

> Oh, yeah, just make this function return a new object with the updated values
> instead of mutating them, pff.

But oh boy if I was wrong.

I mean, yeah, at the end you can describe it like that. But to actually write
code in that way was harder than expected.

Functional programming enforces immutability, which left me without so many of
the things I just assumed were shared among all languages.

For-loops, for example, are now extinct, since you need a "flag variable" that
mutates every loop. Now you need to rely entirely in recursion.

Reassigning values to variables is **discouraged**. (Yes, discouraged, since
it's not forbidden. And in fact, it's one of the things that allows Clojure to
[have such a powerful **REPL**][doc-repldd])

## Functional thinking

For you to easily write functional code, you need to develop what is referred as
_functional thinking_ --- I read [Neal Ford's Functional
Thinking][functional-thinking] with the expectation that it'd make it easier for
me to do it, but I later realised that it was better to just practise it,
allowing myself to slow down every once in a while and reflect on how dumb and
non-idiomatic my code was.

I'm not suggesting it's a useless read. In fact, if I'd have no prior experience
with functional programming, I think it'd be a nice primer.

## Core concepts

The first part of developing this mindset consists of getting familiar with the
core concepts of functional programming.

- **Referential transparency** is the idea that you'll always get the same
  result when calling a function with the same arguments.

- **Pure functions** are those that don't have side-effects. This means that we
  no longer have mutability.

- **Composition** is a way to "chain" many functions that will take as argument
  the return value of another function.

You also need to know how to get stuff done with `map`, `filter`, and `reduce`.
If you're new to these, I'd recommend the second chapter of [Functional
Thinking][functional-thinking]: _Shift_.

Then you practise and check your own code to find flaws in your approach.

I don't feel like I could give any more advice than that. What follows is what I
felt was my biggest issue trying to write idiomatic Clojure.

## Apparent non-efficiency

One of the most important aspects of adopting the mindset was un-learning some
things about efficiency.

Every other function I wrote made me felt like I was doing such an inefficient,
inelegant, dumb thing, when actually was the idiomatic way to do it.

### Recursion

When I was first learning about recursion, it looked like a panacea that could
(and should) be used instead of every loop I needed to do.

Then I learned that it wasn't.

Most of the times you'll be better off by using loops instead of recursion.
Adding a new stack frame to the call stack for every call is just too costly.

In Clojure (and most functional languages) you are encouraged to use recursion,
which made me feel I was in some way writing poor code.

But the thing is, these languages should be optimized for recursive calls. At
least for [tail calls][tco] (those at the end of the function), avoiding a new
stack frame for every call.

Ideally, tail recursion should be as efficient as an equivalent loop.

### Data structures

Another thing was data structures. Specifically, "modifications".

Since they're not modifications, but "a modified copy of the original data
structure", they require you to **copy** the structure.

And deep copying entire data structures in most languages is costly. You'll need
to keep both the original and the copied structure in memory. And you'll need to
copy `n` values, thus it'd have `O(n)` time complexity.

However, [Clojure implements persistent vectors][clj-persistent-vectors], which
makes copying to have a time complexity of `O(log32 n)` [^cljperformance].

Is it faster to modify a persistent vector than mutating a raw array? No.

Is it faster to modify a persistent vector than copying and modifying a raw
array, trying to mimick immutability? Yes.

## Conclusion (?

I'm certainly used to imperative languages. And the things I know about memory
management and complexity, were explained using C code.

That makes some common patterns in the functional paradigm seem inefficient.

And sometimes they are, but most of those times, it's **part of the paradigm**.

Enforcing mutability needs different data structures, which have their own time
and space complexities associated with them.

**At the end, you're accepting a trade-off.**

Using the Clojure data structures is comfortable. One of the core ideas of
functional programming is that having few data structures with many operations
available to them is better than having many structures with few operations for
each one.

> It is better to have 100 functions operate on one data structure than 10
> functions on 10 data structures. —Alan Perlis

You may not reach the benchmark scores of strongly typed languages with raw data
structures in Clojure, but you won't have Clojure's data structures flexibility
and convenience in those languages, either.

To me, it's good enough to know that my code is:

- idiomatic,
- **as performant as the language/paradigm allows**, without sacrificing
  readability or maintainability.

If I ever forget what I've learned in the last week, I'll just re-read this:

Don't worry for the performance issues you feel you're causing by having to deal
with immutability or recursion depth.

[^cljperformance]:
  There has been
  [some discussion in Hacker News](https://news.ycombinator.com/item?id=6445628)
  around Jean Pierre's article on Clojure Persistent Vectors.

[subway-networks]: /projects/subway-networks/
[clj-persistent-vectors]:
  https://hypirion.com/musings/understanding-persistent-vector-pt-1
[top-down-bottom-up]: https://www.youtube.com/watch?v=Tb823aqgX_0
[doc-repldd]: /writings/repl-driven-development
[functional-thinking]:
  https://www.goodreads.com/book/show/18492332-functional-thinking
[tco]: https://en.wikipedia.org/wiki/Tail_call
