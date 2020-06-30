---
title: "Harder, better, faster building"
excerpt:
  Or how lazyness to write commands made me create a single command for every
  project, independently of the framework.
date: 2020-04-09T00:27:28-05:00
toc: true
code: true
draft: false
---

Over the last weeks I've been running a project that needed multiple servers to
run. Each one with its own set of commands to serve and build. Each one with its
own set of commands to test, lint, and format.

Although it wasn't difficult or slow, I was getting tired of making a tiny
effort to decide which command I should run in the current directory. Or wanting
to re-run one command by spamming my upwards arrow only to end up writing it up
myself.

Then I decided to spend a little time trying to optimise the way I ran those
commands. And I'm not talking about optimization of the actual process, **but of
the time I was taking to execute them.**

And that is pretty much reduced to aliasing each of my common "development
tasks" into unique and very short commands that I could alias in my shell.

But no command works for every project, so instead of aliasing the command, I
aliased the call to a file in the current directory that defined how to handle
such task.

For example, let's say I'm developing a node project, which has these commands
associated with it:

```sh
npm run start
npm run test
npm run build
```

So I created a script in the root directory of the project that ran those
commands when it received the corresponding "task name" as argument:

- `tasks.sh`

  ```sh
  #!/bin/sh

  case $1 in
    "serve") npm run start;;
    "test") npm run test;;
    "build") npm run build;;
  esac
  ```

so, running `./tasks.sh serve` would be equivalent to running `npm run start`.

And then I created global aliases to call the _tasks script_ with specific
arguments:

- `.bashrc`

  ```sh
  #...
  alias s="./tasks serve"
  alias t="./tasks test"
  alias b="./tasks build"
  ```

and voilá, now I was able to `serve`, `test`, and `build` my project just by
running `s`, `t`, or `b`.

---

But the best thing is that I could create a `./tasks` script anywhere, and add
aliases to whatever I wanted.

I could even create custom tasks to serve multiple projects simultaneously,
which in my specific case included one Nest project and two Angular projects.

```sh
#!/bin/sh

case $1 in
  "serve")
    ( cd backend && konsole -e s ) &
    ( cd front-1 && konsole -e s ) &
    ( cd front-2 && konsole -e s ) ;;
esac
```

And now, if I was in the directory that contained all the three projects, I
could simultaneously start all of them with a single command. A single `s`.

---

That solution pleased me enough, but anyways I got a jolt of electricity, and
talked a friend about my solution, which we decided to convert into a
distributable script to manage different taskfiles, tasks, and abbrs (what I
referred in here as aliases), and that resulted in us developing (or trying to)
[tasks].

It lets you handle the existance of multiple aliases (such as `s` and `b`),
tasks (such as `serve` and `build`), and their corresponding commands for each
directory indexed by tasks.

[tasks]: https://github.com/daque-dev/tasks.sh
