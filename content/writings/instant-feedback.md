---
title: "On (instant) feedback"
date: 2020-02-26T20:07:25-06:00
draft: true
---

Last week I got asked a pretty unexpected question in an interview:
_"do you like programming?"_. I quickly reflected (I didn't) my answer and
said "yes".

_"why?"_ 

Why? I laughed. Out of nervousness. Why did I just answer that I do like
programming? Why didn't I take a little bit more of time and thought about
the reasons prior to being asked such question?

Am I being perceived as a liar now? Do they think I just said yes so I could
"get more points"?

I tried to elaborate an answer using "I can tell the machine what I want",
"You can build whatever you want" and some other pre-made answers. 

When I left, I kept thinking about the question, and even googled it in an
attempt to get inspiration for the next time someone asked me that question.

Some of those answers will work when the person asking it isn't really into
programming, but if they do, I'll try to, having the "I like programming" as
a premise, elaborate on _what makes me **not to** enjoy programming_.

There are only two things so far that had made me to completely lose interest
in programming for a given period: handling ruby versions, and obsolete
hardware.

The first one can be atributed to many things. And it's of course very
subjective.

The second one can be measured differently, depending on what you're working
on. I don't have many problems writing code, saving, and running a compiler or
interpreter, and waiting. I don't have many problems running a Hugo server. 
I don't have many problems doing many things.

But recently I started working with AngularJS.
It wasn't just a simple stand-alone project, but one that used many home-made
libraries. 

If you were to work on those libraries, you had to recompile the libraries, and
then trigger a server reload.

Ideally, recompiling the libraries was to be done in no more than 2 seconds,
and the server reload in no more than 1 second.

Long story short: all this compilation after every change was hitting hard on
my 4 Gb RAM, rendering my laptop useless for an entire minute.