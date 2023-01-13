---
title: David Omar's resume
layout: resume
position: Software Engineer
excerpt: >

  I'm an engineer with a **strong interest in Open-source Software**.


  I have 6+ years of experience with `HTML` and `CSS`; 5+ years with `C`,
  `Python` and `JavaScript` (more recently, and joyfully, `TypeScript`), and 3+
  years using frameworks such as `React` and `Angular`.


  I'm proud of having designed, developed, and documented
  [**Ginpar**](https://ginpar.rtfd.io), a framework meant to optimize the
  workflow of generative artists.


  Strongly focused on **Development Experience**, **Web Performance**, and
  **Technical Writing**
experience:
  - company: "[Netflix](https://about.netflix.com/en)"
    position: UI Engineer
    period: Jan 2023 – Present
  - company: "[GBM Grupo Bursátil Mexicano](https://gbm.com)"
    position: Front-end Engineer
    period: Dec 2020 – Dec 2022
    location:
    stack:
      - Angular
      - NestJS
      - TypeScript
      - Socket.IO
      - RxJS
    # annotation:
    #   GBM is the largest stock broker in Mexico, with more than **3.8M
    #   investment accounts**, and over **$1T MXN operated in 2021**.
    achievements:
      - - Led the migration of an 8-year-old AngularJS project from Gulp to
          Webpack.
        - Upgraded our tech stack (Vanilla JS, and CSS ⟶ ES2020, Typescript, and
          Sass).
        - Reduced non-cold start re-compilation time for development builds
          **from 20s to <1s**.
        - Simplified the build process by reducing the number of commands that
          had to be ”manually” run.
      - - Led the continuous upgrade of a core application (>120k weekly active
          users) from Angular v4 to v9.
        - Reduced initial bundle size, loading times, and crash rate, which
          improved Apdex score from .6 to .85.
        - Documented the core architecture of the application using Sphinx.
        - Created a project-specific roadmap to keep up with the upgrades up to
          Angular 14
      - - Improved client-side performance on multiple front-end projects across
          the whole company by adding compression
        - Configured CachePolicies on AWS CloudFront to accept Brotli and Gzip
          encoding
        - Updated Webpack configurations to run compression on the generated
          bundles
        - Reduced the initial JS and CSS bundle size across all projects to 15%
          of the original size (avg.)
      - Participated in the candidate selection process, by directing technical
        interviews, reviewing take-home assignments, and mentoring new
        interviewers
  - company: "[Jaque](https://jaque.me)"
    position: Front-end Developer
    period: Feb 2020 – Dec 2020
    location:
    stack:
      - React
      - AngularJS
      - Angular 2+
      - TypeScript
      - RxJS
      - WebSockets
      - Unit Testing
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
  - name: "[Attractor seeder](https://attractors.davidomar.com)"
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


  I also maintain a generative art blog at
  [generativemistakes.art](https://generativemistakes.art)
---
