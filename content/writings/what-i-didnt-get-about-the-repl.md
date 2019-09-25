---
title: "What I didn't get about the REPL"
date: 2019-09-23T19:25:59-05:00
draft: true
---

Over the last days I've been using Clojure to develop [sub-nets][sub-nets],
and I've found several things about it that made me want to keep using Clojure
as the main language for more projects.

The two main reasons don't have to do with Clojure syntax, the immutable typing
system, or the JVM (actually, why would that be the reason?).

They're the [generative testing][generative-testing], and the possibility to
use [REPL-driven development][repl-dd], the topic of this post.

## REPL-driven development

--- Or _RDD_, for short ---

I heard about _test driven development_, and _behaviour driven development_
before, but never about RDD.

And I smirked when I read about it.

I mean, REPLs are only used when trying a new language for the first time,
right? When you just want to get to know if `2.0 * 2` is a possible operation
or not, or if `1.0 + 1` and `1 + 1.0` are equal.

Then you get a little more familiar with the syntax rules, the typing, and
move on to use files that the language interpreter or compiler will read.

**How could you ever use the REPL in a non-tutorialish way?**

Well, it turns out that it is the default way to do things in Clojure.

### Editor-REPL link

This works because you can have the REPL always running while you write your
code, and interact with it without even leaving your text editor.

When you start the REPL, you can read the file (or directory) you're currently
in, so all the definitions you've done are loaded in it, and available for
interaction.

The beauty of this comes when you link the REPL and your editor.

This allows you to evaluate custom contents from the file, and to write the
return values in the file.

The most common environment is Emacs, but I'm using VSCode and the extension
[Calva][calva].

The shortcut to execute Calva commands is `Ctrl + Alt + C`.
Then you press whatever other key that triggers a command.

`E`, for example, will evaluate the current expression, and print the output
in a tooltip.
`C` will print it as a comment one line below.
`Enter` will evaluate your whole file and print the output in a tooltip.

With this you can check if a function definition contains syntax errors,
the value of a symbol, or the return value from a function.

### Writing new code

When I'm trying to write a new function that will receive a map and do
something with its keys, it's useful to know just how that map is structured.

I could go back to the function definition that builds that map. Or just force
my brain to remember it, which I imagine is what's hell like.

But with the REPL you can evaluate a value and append the return value as a
comment, so you can just check how a return value looks like.

```clojure
(def test-line (subway-line "ln-1" "st-19" "st-3"))
test-line

;; => {
;;    :id "ln-1"
;;    :start "st-19"
;;    :end "st-3"
;;    :stations ["st-19" "st-3"]
;;    :lentgh 2}
```

Even better, you can evaluate the definition of the new function (so the REPL
now knows about it), and start using it..

```clojure
(defn add-to-end
    [line station]
    (assoc
        ;; Set station as the line :end
        :end station
        ;; Add station at the end of line :stations
        :stations (-> line :stations conj station)
        ;; Increment the length of the line
        :length (-> line :length inc))

;; => #'user/add-to-end

(add-to-end test-line "st-new")

;; => {
;;    :id "ln-1"
;;    :start "st-19"
;;    :end "st-new"
;;    :stations ["st-19" "st-3" "st-new"]
;;    :lentgh 3}
```

And I didn't even **had to** save the file, let alone compile and execute.

### Debugging

Well, pretty much like before, comparing a function input and output is helpful
when debugging your code.

But the REPL can also help you track syntax errors.

Instead of crashing your REPL session, syntax errors get printed in a tooltip
and in the REPL, so you can easily see why a piece of code failed.

Either you didn't use parenthesis when you should've, did use them when you
shouldn't have, sent the wrong number of parameters, or whatever.

Of course, you still need to figure out what the error means and fix it.

### Testing

Clojure has [test.check][test-check], a property-based testing tool.

I've written about it [in here][generative-testing], but to put it briefly, you
can generate a whole lot of tests by specifying properties that hold true for
the inputs and the outputs.

And if that's not enough yet, mix it with the REPL.

When testing a function, it either suceeds, or fails.

The return value for successful tests is ok. You know it suceeded, the number
of tests that were generated, and some other info

```clojure
(t/check `add-to-end)
;; => {:sucess true
;;     :num-tests 1000
;;     ...
;;     :fn `add-to-end}
```

But the return value for failed tests is **great**. It will tell you how many
tests it suceeded in before failing, what was the input that made the function
fail, the received output, the property that didn't hold true, and even a
_shrunk_ input.

What is a _shrunk_? The tiny version of the failing input, that removed every
parameter, key, element, or character that didn't cause the failure.

```clojure
(t/check `add-to-end)
;; => {:sucess false
;;     :num-tests
;;     ...
;;     :shrunk {
;;       }
;;     :fn `add-to-end}
```

**JUST HOW AWESOME IS THAT!?**

**Seriously!** That is maybe the coolest feature I've known
in any language.

And all I needed to do was evaluating the function `spec`, and the `check`
(the single line of code).

### Good Ol' REPL

Remember when I said that I considered that REPL was only useful when you
were just getting to know the basics of a language?

Well, of course you can still use it like that.

Have an idea of how something might work (or don't work)?
Just write that idea and evaluate it. Is it what you expected?

I think that having such an interactive way to code makes it easier to learn.

---

Those are some of the useful capabilities I possess now that I
embraced the REPL.

But could I adopt this _RDD_ in other languages? Python has a REPL. Node,
Julia, Haskell, and so many more do as well.

Well yes, but actually no.

For _RDD_ to work, you need some constraints on the language.
And even when having them, you need to link your editor and the REPL.

For similar experiences, you could try:

- [Jupyter Notebook][jupyter-notebook] for Python.
- [ObservableHQ][observable-hq] for [something like JavaScript][obs-js].
- [IHaskell][ihaskell] for Haskell (which is built over Jupyter Notebook).

But, anyways, what are those constraints?

### Constraints

Or, why cannot---as easily--- this other language have this cool feature?

#### Immutability

If you're going to be evaluating functions calls over and over, you better hope
that they don't cause any side-effect, or you could get different results each
time you evaluate a piece of code.

For example, previously I called a function `add-to-end` that added a new
station at the end of a subway line. If I evaluate it again with the same line,
I'll get the same return value over and over.

But let's imagine that `(add-to-end)` actually mutates the received line,
updating the `:end ̣`, `:stations`, and `:length` keys of `test-line`.

If I evaluate `(add-to-end test-line "st-new")` again, I'd get this:

```clojure
(add-to-end test-line "st-new")
;; => {
;;    :id "ln-1"
;;    :start "st-19"
;;    :end "st-new"
;;    :stations ["st-19" "st-3" "st-new" "st-new"]
;;    :lentgh 4}
```

Which in practice would be equal to calling

```clojure
(add-to-end (add-to-end test-line "st-new") "st-new")
```



## Conclusion

RDD rocks.

[sub-nets]: /projects/sub-nets
[generative-testing]: /writings/generative-testing
[repl-dd]: hola
[calva]: https://github.com/BetterThanTomorrow/calva/
[spec]: https://clojure.org/guides/spec
[test-check]: https://github.com/clojure/test.check
[jupyter-notebook]: https://jupyter.org-hq/ 
[observable-hq]: https://observablehq.com/
[ihaskell]: https://github.com/gibiansky/IHaskell
[obs-js]: https://observablehq.com/@observablehq/observables-not-javascript