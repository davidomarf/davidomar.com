---
title: Branch is both ahead and behind master
---

For a long time, I've said that I'm «proefficient» using git, feeling
comfortable with [gitflow](https://nvie.com/posts/a-successful-git-branching-model/)
and capable of solving merge-conflicts. 

But all that is always assuming I'm working under ideal conditions. And that's
because so far, I've only worked either alone, or in <5 members teams. And all
the conflicts I've solved are pretty standard ones, solvable by either following
GitHub suggestions, or doing a quick search.

But today I had a different one that can be described like this:
- Submit PR from `dev` to `master`
- Merge `dev` into `master`
- Revert changes from merge
- Push a new commit to `dev`
- Merge `dev` into `master`, again

This isn't performed automatically since `dev` is both behind and ahead of `master`.

So far, being lazy and avoiding git docs has served me well, but this time, neither
GitHub's de facto solution nor first google results don't work. This time, **actual**
conflict solving is required.