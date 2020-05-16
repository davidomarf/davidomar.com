---
title: "Automatically updating latex figures built with R"
date: 2017-10-18T00:00:00-00:00
toc: true
draft: true
---

Over the last couple of days, I've been trying to get my hands over LaTeX. After spending
around an hour installing MikTeX in Windows, and several packages that I don't remember
ever using again, I started to feel "in the zone".

Having grasped some of the syntax and the principles, I embedded R plots in my document,
but in an inefficient way. What I was doing consisted in:

- Exporting the graphics as _plot.png_,
- Moving (yeah, manually) _plot.png_ to the TeX project directory,
- Embedding the image in LaTeX.

If I had multiple plots that I wanted to includee