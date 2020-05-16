---
title: "Spicing tests with generative methods"
date: 2019-09-20T07:44:49-05:00
toc: true
draft: true
---

Clojure has a library called `spec` that _"specifies the structure of data,
validates or conforms it, and can generate data based on the spec."_

A few days ago I started specing my Clojure functions.

It has many advantages, the main one being generating docs automatically.
However, the main reason I tried to learn spec'ing was the possibility of
using property-based (or generative) testing.

It's not a Clojure exclusive. You can try property-based testing in
many other languages. In fact, QuickCheck, the very first tool for
property-based testing was written in Haskell in 1999, by Koen Claessen
and John Hughes.

QuickCheck has been implemented in many languages.

Testing for properties has proven to offer an [incredible ratio of lines
of test vs. lines of production][propertesting]

It's also more robust than unit tests. Unit tests are as good as you
can think of different cases. Property tests will exhaustively test
the properties you've set to be always true.

In a way, I think of this approach as a super-powered typing system.

A while ago I read
[_Is unit testing the biggest duplication of effort in human history?_][unittesting]
The main argument of the article was that in dinamically typed languages
you usually end up writing tests for things that a statically typed language
already handles flawlessly. 

You don't need to test what a function does when:

- it receives the wrong number of arguments, because it won't even compile. 
- it receives the wrong a wrong type, because it won't even compile.
- it returns a wrong type, because it won't even compile.

Now let's imagine you get another dimension of constraints. One that lets you
say not only the type of the argument and the return value, but some of its
properties.

They can be as simple as restricting its value to a certain range, or as
complex as you can compose it.

Some languages include such things as part of the standard library.

Dlang, for example, uses [Contract Programming][dcontracts], which allows you
to run assertions over the inputs and outputs of a function.
    
> By definition, if a pre contract fails, then the function received bad
  parameters. If a post contract fails, then there is a bug in the function.
  In either case, an assert statement within the corresponding in or out
  block will throw an AssertError.

Using a framework that allows for property based testing will allow yo

What is a property?



[dcontracts]: https://dlang.org/spec/contracts.html
[unittesting]: https://medium.com/@djsmith42/is-unit-testing-the-biggest-duplication-of-effort-in-human-history-ca78c39d6f02
[propertesting]: https://propertesting.com/book_foundations_of_property_based_testing.html#_promises_of_property_based_testing
