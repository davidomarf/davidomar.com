---
title: "Building an Interactive Space for Generative Art"
date: 2019-10-01T15:31:01-05:00
draft: true
---

On Dec 1, 2017, I created my reddit acount, and started to join a crazy amount
of subs. In one of them, [r/GeometryIsNeat][geometryisneat], I found a video
under the name _Procedurally generated symbols_, and looking into the comments,
I found the credited author: Inconvergent.

That's what started it all. A rabbit hole that introduced me into what today
is one of my favorite hobbies: generative art.

After finding [r/generative][generative], I started reading several artists blog
posts about their environments. Most used Processing, some used Python, and
others even Haskell.

I tried different ones until I found one I was comfortable enough: [P5.js][p5].

I loved the fact that you didn't need to install anything. A simple text editor
and a browser were enough.

My process consisted of this:

1. Write code.
1. `Ctrl + S` to save.
1. `Alt + Tab` to focus on the browser.
1. `F5` to refresh.
1. Repeat.

Then months passed, then more than a year, and my process was the exact same as
when I started ---[Not that there's anything wrong with that][seinfeld].

It was ok-ish. But could be improved by tightening the feedback.

Specially since ost of my works have aquired their "final" version after
several iterations over the same idea. Final little "tweaks" that make me be
at peace with the piece.

Just like the popular 80-20 rule, I was spending 20% of my time developing the
core idea, and 80% just experimenting and making tiny adjustments that eventually
produced the final work.

I started wanting to create a space to interact with the code variables,
allowing you to modify each one separately and watching how it influences
the final result, **without you needing to modify the code everytime.**

I had saw things like that before.

When I read
[aesthetically pleasing triangle subdivision][tyler-subdivision], I saw a link
at the end to the live interactive implementation by Anthony DePasquale:
[triangle subdivision][depasquale-subdivision].

[GASP Gallery ][gasp-gallery] also features a set of UI controls for the
piece of art. 

<!-- ![alt](/img/writings/building-an-interactive-space-for-art/my-first-portfolio.png) -->

So that's the next project. Building an online platform for my
works, so each one can be run using this interactive controllers.

Originally meant to be an online platform for **my works**, this turned out to
be [Ginpar][ginpar]: Static content generator for interactive and
parametrisable p5 canvases.

[tyler-subdivision]: https://tylerxhobbs.com/essays/2017/aesthetically-pleasing-triangle-subdivision
[depasquale-subdivision]: https://depasquale.art/works/triangle-divider/
[ginpar]: https://github.com/davidomarf/ginpar
[inconvergent]: https://inconvergent.net/
[gen-algorithms]: https://inconvergent.net/generative/
[generative]: https://www.reddit.com/r/generative/
[p5]: https://p5js.org
[geometryisneat]: https://www.reddit.com/r/GeometryIsNeat/
[seinfeld]: https://www.youtube.com/watch?v=Oj3VphK9AMk
