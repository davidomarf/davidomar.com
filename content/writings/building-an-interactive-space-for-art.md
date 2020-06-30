---
title: "Building an Interactive Space for Generative Art"
excerpt:
  Or how I went from a plain simple unstyled web page into a static content
  generator focused on generative art.
date: 2019-10-01T15:31:01-05:00
toc: true
draft: false
---

On Dec 1, 2017, I created my reddit acount, and started to join a crazy amount
of subs. In one of them, [r/GeometryIsNeat][geometryisneat], I found a video
under the name [_Procedurally generated symbols_][pgs], and looking into the
comments, I found the credited author: [Inconvergent][inconvergent].

That's what started it all. A rabbit hole that introduced me into what today is
one of my favorite hobbies: generative art.

After finding [r/generative][generative], I started reading several artists blog
posts about their environments. Most used Processing, some used Python, and
others even Haskell.

I tried different ones until I found [P5.js][p5], which immediatle made me feel
comfortable.

I loved the fact that you didn't need to install anything. A simple text editor
and a browser were enough.

## My p5.js workflow

After creating the mandatory `index.html` and importing a `sketch.js` script,
I'd:

1. Modify some code in `sketch.js`.
1. `Ctrl + S` to save.
1. `Alt + Tab` to focus on the browser.
1. `F5` to refresh.
1. Repeat.

Then months passed, then more than a year, and my process was the exact same as
when I started ---[Not that there's anything wrong with that][seinfeld].

It was ok-ish. But could be improved by tightening the feedback between my
changes and the new results.

### Exploration bottleneck

Most of my artworks have aquired their "final" version after several revisions
of the same idea. Final little "tweaks" that make me be at peace with the piece.

Just like the popular 80-20 rule, I was spending 20% of my time developing the
core idea, and 80% just experimenting and making tiny adjustments that
eventually produced the final work.

**That's when my workflow started to get in the way of creativity.**

If I wanted to try different values to some constants, I'd have to modify them
in hard code, save, and refresh. Only to decide which constants to or not to
modify next.

This produced a bottleneck that limited me while exploring the whole range of
constant combinations.

## My "portfolio"

I'm reluctant to call the page I had at the time a "portfolio". It wasn't.

It was the simplest HTML page with hard coded links to the different artworks.

![alt](/img/writings/building-an-interactive-space-for-art/my-first-portfolio.png)

I definetely wanted to have something different. A nicer page that at least
showed some artwork information (such as the date of publication), and my social
links.

## A controllable, interactive portfolio

The bottleneck issue made me aim to create a space to interact visually with the
code constants, so **I wouldn't need to modify the code anymore.**

I had seen similar things before.

For example, Tyler Hobbs in his article [aesthetically pleasing triangle
subdivision][tyler-subdivision] links to Anthony DePasquale's [live interactive
implementation][depasquale-subdivision].

[GASP Gallery ][gasp-gallery] also features a set of UI controls for the
artworks.

But I also wanted to solve the portfolio problem.

At the end, I decided to create a framework that'd also serve as a static
content generator.

Its task would be to build an individual experimentation space for every work,
and concentrate all of them in a single home page.

The produced websites would be as easy to publish as it currently is to share a
Jekyll or Hugo website.

It'd also be useful to other artists using JavaScript to generate art.

It'd be easy to modify and extend, using a templating engine and custom themes.

**Well... all these ideas gave birth to [Ginpar][ginpar], and I'm pretty excited
about the current results, and future development of it.**

I've been using it experimentaly and it really sped up my process.

[tyler-subdivision]:
  https://tylerxhobbs.com/essays/2017/aesthetically-pleasing-triangle-subdivision
[depasquale-subdivision]: https://depasquale.art/works/triangle-divider/
[ginpar]: https://github.com/davidomarf/ginpar
[inconvergent]: https://inconvergent.net/
[gen-algorithms]: https://inconvergent.net/generative/
[generative]: https://www.reddit.com/r/generative/
[p5]: https://p5js.org
[geometryisneat]: https://www.reddit.com/r/GeometryIsNeat/
[seinfeld]: https://www.youtube.com/watch?v=Oj3VphK9AMk
[gasp-gallery]: https://gasp.gallery/
[pgs]:
  https://www.reddit.com/r/GeometryIsNeat/comments/7hgx55/procedurally_generated_symbols/
