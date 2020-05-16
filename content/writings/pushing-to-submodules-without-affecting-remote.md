---
title: "Pushing to Git Submodules Without Affecting Original Remote"
date: 2019-09-06T20:15:13-05:00
toc: true
draft: false
---

Just today I started working with [Hugo][gohugo]. The default way to install themes in your
website is [adding the theme repository as a git submodule][hugo-theme-submodules].

Doing so, produces this structure:

```
-/mySite
├── .git            ## Contains the git info of mySite
├── .gitmodules     ## References the repositoriy added as submodule
├── themes/
    ├── niceTheme/
        ├── .git    ## Contains the git info of niceTheme
```

I originally assumed there would be no problem if I modified the files inside `niceTheme`
normally, like I did when using Jekyll themes, and then push all the changes to my repo.

The problem is that, upon reading about submodules, I found the same thing over and over:
**To make a change in the submodule, you need to push to the original repository you created
the submodule from**.

It may just be that I'm ignorant (which I am, but I cannot say it is **just that**) about
`git submodules`, but I'm confused about this ---[and several people are][gohugo-discourse].

## The Goal

Make changes to the content of `niceTheme` without pushing code to `owner/niceTheme`.

First, I need to understand why I'd use a submodule in the first place.

## Why submodules

If your software depends on other projects to work, —and you're not using a package manager—,
you're likely to  just copy the projects code into your repository, but that will
eventually generate a dirty git flow, mixing the development of your software, and the many
dependencies you're using.

Git submodules can help solve this. They are a reference to another repository, **always
pointed at a particular commit**.

It is simply a git repo inside another repo.[^1]

## Commiting without push

So, if I have a git repo that is embedded within my git repo, can I write commits to it so
my project will have the modified version of it?

Yes! But that will only work for the workspace you're making the commits in. If I were to clone
the repository from another workspace, the submodule would be cloned again from the origin we
specified at the moment of creation. Therefore, not having the code we commited in the other
workspace.

That will render the effort of commiting to the submodule as useless.

## Commiting and pushing

Now let's say we decided to push the changes we made to the original repository.

If the changes are useful for every project user; are consistent with the goals of the project;
and have good quality, they may be accepted, benefiting several people.

But if those changes are rejected, it won't matter we pushed code. The sobmodule would be pointing
to the same repository that didn't have that code.

## So what's the solution?

Forking the repository and adding the fork as the project submodule.

That way, now we own the repository. This allows us to confidently commit code to it.

It also keeps the possibility of updating our fork when future releases of the original project get
released, and we can customize the code so it fits our project better.


## Conclusion

Just fork that theme, and add your fork as the submodule.

## Further

When reading about submodules, I found `git subtree`, which supposedly is an alternative to 
`git submodule`. I may write about it later.

[gohugo]: https://gohugo.io/
[gohugo-discourse]: https://discourse.gohugo.io/search?q=submodule%20theme
[hugo-theme-submodules]: https://gohugo.io/getting-started/quick-start/#step-3-add-a-theme

[^1]: Attlasian. (2019, April 19). Git submodules.