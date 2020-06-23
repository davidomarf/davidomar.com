---
title: David Omar's resume
layout: resume
position: Software Developer
excerpt: >

  I'm an engineer with a **strong interest in Open-source Software**. I invested
  my time to OSS development and self-learning way before I pursued my first
  job.


  I have 6+ years of experience with `HTML` and `CSS`; 4+ years with `C`,
  `Python` and `JavaScript` (more recently, and joyfully, `TypeScript`), and ~2
  years using frameworks such as `React` and `Angular`.


  I'm proud of having designed, developed, and documented
  [**Ginpar**](https://ginpar.rtfd.io), a framework meant to optimize the
  workflow of generative artists.


  I recently started [**Racegex.io**](https://racegex.io), a game to learn,
  practice, and compete in races using regular expressions. It's still a work in
  progress.
experience:
  - company: "[Jaque](https://jaque.me)"
    position: Front-end Developer
    period: Feb 2020 - Present
    location: Mexico City (Remote)
    stack:
      - Angular
      - NestJS
      - TypeScript
      - Socket.IO
      - RxJS
    achievements:
      - I'm one of the two core developers of [an open source front-end
        library](https://grupojaque.gitlab.io/jaqueoss/front-commons/docs/index).
      - Developed a one-to-many real-time chat to send messages, files; and
        images, and with permissions for some users to create chat groups.
      - Wrote scripts to seed mock content, users, and interactions with
        different information and progress in the database, making testing and
        development faster.
projects:
  - name: "[Racegex.io](https://racegex.io)"
    wip: true
    repo: daque-dev/racegex
    stack:
      - React
      - TypeScript
      - WebSockets
      - Go
    description:
      Web-based game to learn, practice, and compete using regular expressions
    achievements:
      - Connect two users in a room, and when the two are ready, load the same
        problem for both.
      - Write a regular expression and get instant visual feedback as-you-type
        to see how well it solves the problem tests.
      - See how well your opponent is doing, just by watching how many tests
        they have solved.
  - name: "[Ginpar](https://ginpar.readthedocs.io/en/stable/)"
    repo: davidomarf/ginpar
    stack:
      - Python
      - Jinja2
      - Click
      - (Some) Vanilla JS
    achievements:
      - Convert P5.js scripts into interactive pages that let you control the
        script parameters in a GUI.
      - Templating engine to generate the interactive GUI using YAML files to
        specify the controls.
      - Generate buttons for value randomization, sketch regeneration, and image
        download with seeding information.
      - CLI commands to initialize projects and sketches; build projects, and
        start a live reloading server.
  - name: "[Attractor seeder](https://davidomarf.github.io/attractor-seeder)"
    repo: davidomarf/attractor-seeder
    description:
      Web tool to assist generative artists interested in rendering attractors
    stack:
      - HTML5
      - CSS3
      - Vanilla JS
      - P5.js
    achievements:
      - An attractor is a mathematical function that sometimes, when graphed,
        results in attractive and complex patterns.
      - Mass-produce attractors to efficiently choose attractor building values.
      - Create multiple canvas elements that depend on the size of the screen
        and the URL parameters.
      - Each canvas can be regenerated without affecting the others.
      - You can select one of the attractor samples, and render it in higher
        quality.
extra: >
  - **I've given a public tech talk!**


  I've been interested in generative art for more than two years, which
  eventually inspired me to give my first (and so far only) tech talk:
  [Introduction to generative art](/talks/eventloop-2019-09/).

  - **I enjoy writing**


  I don't do it pretty often, and when I do, most of the times I don't publish
  it, but I enjoy it anyways. You can check [my blog](/#writings).


  My favorite entries are: [On Ignorance](/writings/ignorance/),
  and  [Functional thinking and seemingly non-efficent
  code](/writings/functional-thinking/).
---
