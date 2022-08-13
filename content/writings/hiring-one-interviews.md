---
title: "Hiring Part One: Technical Interviews"
date: 2022-01-16T01:37:00-06:00
excerpt:
  How to make technical interviews fair, accurate, replicable, and smooth as
  butter.
toc: true
draft: true
---

I've been always interested on interviewing. In my firs job i wanted to be part
of the team that interviews new candidate

I didn't get to be the one who interviews, but I got to propose some ideas on
the process, propose some changes in the evaluations, and participate in the
reviewing of code challenges.

I support code challenges because it's a way of knowing how a candidate could
perform.

But anyway, what's the point of code challenges? and what's the ideal way of
designing one?

For example, I'm only talking about front-end interviewing.

I think a code challenge should help you (as a interviewer) check how the
candidate will perform in any, or all, of these:

- debugging,
- mantaining code,
- reusing code,
- adding new code,
- following UI,
- familiarity with the framework

So I'm all in for well-thought and designed challenge that can do this.

For me, it means:

- Providing a UI project they can follow.
- Working with an existing code base (the candidate can find some patterns, so
  their reviewers won't discard them just because they didn't know which pattern
  they liked), also, if they read the code they could reuse some of it, so it
  speaks about their capability to mantain a project.
- Solve bugs, so you could include an on-purposely broken feature, adding the
  expected behavior.

But anyway, back to interviewing.

---

In my current work, I got the opportunity a few months back to be part of the
recruitment team, and it got got me pretty energized.

First of all, we have to discuss the stages of interviewing.

In some of them, you won't be able to change a thing. Maybe the nature of the
company requires all candidate to follow a thorough background check you'd
rather not do, but you cannot do nothing about it.

Maybe there are one or two steps you'd think arent necessary, but you don't
dictate that, so the only option is:

Suck it up (well, of course you can talk with the hiring manager, make a case
about your ideas, and then go defend them), and making sure the stages you're
involved in smooth as butter, make the interviewing process one the candidates
will consider to reapply\*\*.

\*\* should we consider re-apply rate a metric?

So, I'm gonna tell you the steps I'm involved in, and how I try to make each of
those steps as smooth, humane, friendly, and fair to all our candidates:

One think I think about all the time is trying to maximize the number of
variables that you can control, and standardize them so you have less ifs to
consider.

The hiring stages I'm involved in are:

- Technical Interview (and HR feedback),
- Challenge Review (and HR feedback),
- Challenge Interview

They may sound like a lot. And personally, I cannot decide. I don't love the
number of interviews a candidate has to go through. But I've never disliked long
processes even as a candidate. I guess you can make some fast paths for some
people, but I don't think having these three interviews is excessive.

### Technical Interview

tldr; keep it friendly, don't shame the candidate, make the environment so that
the candidate can shine.

I think it's necessary to have a little bit of charm. You don't have to be a
funny, or smart guy who jokes around. But at least you should have the ability
to guide a conversation, ask questions, actively listen, and sensibly interrupt.

You want the environment to feel relaxed. And you can talk about some things to
break the ice at the start of the conversation. This is my go-to for
introductions:

> Hey, [candidate], how's your day going? {answer}
>
> Have you heard about [company]? (In my case, it's possible our candidate is
> also our user, so I always ask them if they're a user and kick a "I've found
> is pretty awesome to work in something you already use")
>
> well, [company] right now is focused on **\_**.

I've found is a non-awkward way of breaking the ice.

Then I "formally" talk about the interview schedule:

First, we're going to introduce ourselves, and talk for around 10 minutes about
your experience, your current (or last) work (if the candidate has worked, if
not, we can ask about what are they familiarized with or their favorite
projects).

Then, we're going to do some technical interviews. They are just to measure your
level of familiarity with the work tools, so don't worry, in most of them
there's not a right answer, so we can be pretty talkative and bounce back ideas.

Also, if you don't know an answer, it's better to state that upfront, and then
if you think you can provide an idea, do so.

Then, we're moving to a Live Programming Session. It's not a whiteboard
interview, it's more like we are both doing Pair/Mob programming to solve a
problem.

And at the end, we'll have some time (we usually don't limit this time unless
both of the interviewers have a meeting).

---

So now, the interviewers start introducing themselves. It's pretty quick: I'm
David, I've been working here for X time, and I've been using X to maintain X
project.

---

And then, the interviewer gets to talk. Sometimes they've prepared a speech,
sometimes they haven't. So you can start guiding the conversation.

"Could you give us a quick tour of your experience?"

Then we ask to focus **more** on things that are relevant to the position. To
talk from the oldest to the most recent position.

You have to be able to interrupt the candidate. You're interviewing for the
position as a Frontend Engineer, and even if you value prior experience in other
areas, it can bias your final decision. So politely guide the conversation with
positive phrases: "Tell us more about \_\_\_".

You can gauge how to do this, and check on what to focus and what to let pass
with the time and with each interview. But you need to practice directing and
guiding conversations in a non-aggressive manner.

---

Then we have the technical questions.

I prefer them not to be _trivia_ questions, like "what gets logged if I put this
code into the console?", "what's the output of this expression?".

It pretty much encourages short, definitive, correct or incorrect answers. And
don't leave too much room for conversation.

Instead, I like to ask "do you know something about \_\_\_?", "tell me how you
work with \_\_\_\_".

For example, we consider there are some fundamental things we'd like our hires
to be competent at:

- Git,
- Web Accessibility and Usability,
- Web Layout,
- Javascript,
- Good Practices.

And depending on the position, we can ask questions about React or Angular.

Let's say we want to measure the knowledge about Git:

Instead of going all dry with "what does cherry-pick do?", I prefer to ask an
open question:

1. In your current job, how's the process from getting one task from
   requirement, to production?

Then it sprawls the question: "can you tell me a little bit about the git
workflow in your team?"

If they've used it, I usually continue with "is it common to find conflicts? how
do you solve them?"

"do you know what does the --force flag does? when do you find it useful?"

---

Across all categories, we like to start with very open questions, that can let
us gauge the level of the following questions.

If we ask about git workflow, and they tell use they've never used it, then why
would we ask any of the other git questions? Maybe we can ask them more
generally about version management, and ask them to explain what it consists of.

---

For Javascript questions, these are my go-to:

Do you know something about Functional Programming?

If yes, I ask them to ellaborate. If no, I do a quick description and some ways
JavaScript allows programmers to use some of the core concepts of the paradigm,
like array methods.

---

Then for the live-coding session, we ask them to present their screen. We give a
general set of tips and instructions:

- Don't worry about solving them, it's not the most important thing.
- Think of this process as a pair/mob programming session: we'll all work
  together to solve this. You can ask us anything, or if you prefer, you can
  Google things you don't remember.
- It'd be great to be relaxed, so we invite them to breath. Think slowly, try
  not to precipitate, and please, be as explicit as you can with your thought
  process.

Alog the problem, we answer their questions, ask them questions when they seem
to get stuck, and propose alternative solutions if the one they're taking seems
like a dead end.

---

You'll have to give feedback to the HR or People team, so I've found pretty
handy to have a fillable set of considerations, and I'm constantly taking notes
about the process.

If you can, and if the interview was done between more than one interviewer,
chat right after so you can discuss your veredict, and fast-track that feedback
so you can stop thinking about it.

In the feedback, it's nice to include tips if they didn't do it right on the
interview, so they know how to be better.

---

Provide them with resources to learn and invite them to re-apply in the near
future.

This of course should be discussed with the people team. Maybe it's the process
politics to not disclose your decision during the interview. Maybe any feedback
should go through them so they make sure it cannot be badly interpreted and
misread.

I like to provide the resources as the idea surges. It doesn't have to be at the
end, I'm sometimes sharing them as we're talking.

---

Some of my favorite resources that I visit every once in a while:

- [Sockpuppet's The Hiring Post](https://sockpuppet.org/blog/2015/03/06/the-hiring-post/)

---

About that "reducing variables to a minimum and control them", you can do so
with many parts of the interview:

- Make sure the purpose of asking each question isn't made on the spot.
- Make sure the interviews are consistent accross candidates.

---

One idea I like is having scorecards
