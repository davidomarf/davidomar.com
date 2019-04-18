---
title: "About"
permalink: /about

layout: single
align: center
hideTitle: True
---

<script>
var description = [
  "loving <a href = 'https://youtu.be/paqr3kdmcZg?list=PLwic3h1bAlblkSJ-U9YxEpTclFoUS_Otq&t=41' target=_blank class = 'no-target-blank'>Woodkid's music <i class='fas fa-external-link-alt fa-xs'></i> </a>",
  "quoting The Simpsons",
  "procrastinating at <a href = 'https://www.reddit.com/r/wholesomememes/' target=_blank class = 'no-target-blank'>r/wholesomememes <i class='fas fa-external-link-alt fa-xs'></i></a>",
  "trying to succeed at plant caring",
  "dancing ridiculously",
  "fantasizing I'll decipher the stock market",
  "practicing my penmanship"
];
var randomNumber = Math.floor(Math.random() * description.length);
</script>
<script>
window.onload = function() {
  var a = document.getElementById("random-description-switcher");
  a.onclick = function() {
    if (randomNumber < description.length - 1) {
      randomNumber++;
      document.getElementById("random-description").innerHTML =
        description[randomNumber];
    } else {
      randomNumber = 0;
      document.getElementById("random-description").innerHTML =
        description[randomNumber];
    }
    return false;
  };
};
</script>

## About me

I'm a computer science and engineering student. I spend my time learning, writing, or <script>document.write('—<a id="random-description-switcher" href="#">among other things</a>—, <span id="random-description"> ' + description[randomNumber] + '</span>');</script>. 

### Professional stuff

Since I was ~11 (9 years ago), I started to get interested in the things that could be done with a computer. Ranging from game development with GameMaker, to installation and use of other Operating Systems (Ubuntu and Fedora, at that time).

By 15 (5 years ago), I had built several WordPress websites, and acquired some knowledge about web development: DNS Servers, Hosting servers, SEO, SQL data bases, HTML + CSS + JS, and PHP.

At 17 (3 years ago), I got to study *Computer Science and Engineering* in the *National Polytechnic Institue* in Mexico, and I'm still studying  there.

Since then, I've enrolled in several CS, Math, and Physics courses available online, like:
  - [*Machine Learning*](https://es.coursera.org/learn/machine-learning){:target="_blank"}, by Stanford University (at Coursera).
  - [*Algorithms*](https://es.coursera.org/learn/algorithms-part1){:target="_blank"}, by Princeton University (at Coursera).
  - [*Introduction to Complexity*](https://www.complexityexplorer.org/courses/89-introduction-to-complexity){:target="_blank"}, by Santa Fe Institute (at Complexity Explorer).

---

In terms of programming:

- I develop mainly in `C`, `D`, `Python`, and `Javascript`, but **learning a new language isn't any trouble** (for reference, I've written code *—beyond the hello world, I mean—* in `Haskell`, `Common Lisp`, `R`, and some more)

- I always comment my code, giving a **strong focus to readability**.

- I'm fluent working with git. That includes:
  - working with forks and branches,
  - writing modular and informative commits,
  - pulling and pushing changes,
  - merging, and solving merge issues. 

  I follow a working flow similar to [git flow](https://nvie.com/posts/a-successful-git-branching-model/){:target="_blank"}

- I read the docs. Yes. That.

For code examples, you can take a look at my pinned repos at [my github profile](https://github.com/davidomarf){:target="_blank"}.

### Personal Stuff

After I got into college, an avalanche of mindset changes started. I became more avid for knowledge and wisdom. I became a more curious person. Those were the main reasons I started to pick up reading as a habit.

And I really think now that by reading, your mind gets into a broader, more dynamic, and more connected configuration. It makes you easier to think between different disciplines and discern some similarities (of course, not anything you read will do).

And that's one of my favorite things. Learning something new and feel that I *intuitively* knew it. And then figure out why I felt it.

I write some of my beliefs and ideas at my [blog](https://blog.davidomar.com){:target="_blank"}. It's a very personal and honest thing.

I write impartially. Both "positive" and "negative" things. For example, when I feel bad, dobious, insecure, or angry about myself —thing that I believe, happens to all of us every once in a while. 

I also write book reviews and summaries. It would make me authentically happy if you go there and read something.

---

There's some people I admire for what they do. A short non-exhaustive list in alphabetical order includes 
[Adam Savage](https://www.youtube.com/channel/UCiDJtJKMICpb9B1qf7qjEOA){:target="_blank"},
[Bill Gates](https://www.gatesnotes.com/){:target="_blank"},
[Brady Haran](https://www.youtube.com/user/numberphile){:target="_blank"},
[Daniel Shifman](https://www.youtube.com/user/shiffman){:target="_blank"},
[Grant Sanderson](https://www.youtube.com/channel/UCYO_jab_esuFRV4b17AJtAw){:target="_blank"},
[Matt Parker](https://www.youtube.com/user/standupmaths){:target="_blank"},
[Michael Stevens](https://www.youtube.com/user/Vsauce){:target="_blank"},
[Nicholas Lloyd](https://www.youtube.com/watch?v=bY94eFCNv4g){:target="_blank"},
[Peter Diamandis](https://www.diamandis.com/){:target="_blank"},
[Simone Giertz](https://www.youtube.com/channel/UC3KEoMzNz8eYnwBC34RaKCQ){:target="_blank"}, 
and [Tom Scott](https://www.youtube.com/channel/UCBa659QWEk1AI4Tg--mrJ2A){:target="_blank"}.

Most of them are content creators. I'd really recommend you to watch what they do.

After reading some books recommended by Bill Gates (specifically:
[*Factfulness*, by Hans Rosling](https://www.goodreads.com/book/show/34890015-factfulness){:target="_blank"} and 
[*Enlightenment Now*, by Steven Pinker](https://www.goodreads.com/book/show/35696171-enlightenment-now){:target="_blank"},
I decided to become a volunteer at the *Mexican Red Cross*. I've been there since October 2018. That has also provided me with some basic knowledge in first aid, medicine, health, and world history.

## About the site

This webiste was built with [Jekyll](https://jekyllrb.com){:target="_blank"}. The theme I use is a modification of [Minimal Mistakes](https://mademistakes.com/work/minimal-mistakes-jekyll-theme/){:target="_blank"}.

The `.me` domain extension was a gift from [Namecheap](https://www.namecheap.com){:target="_blank"}. It was included in the [GitHub Student Pack](https://education.github.com/pack){:target="_blank"}. The hosting is provided for free by [GitHub Pages](https://pages.github.com){:target="_blank"}.

To handle other things like SSL certificate, cache, and DNS, I use [CloudFlare](https://www.cloudflare.com){:target="_blank"}.

## Get in touch

If you'd like to get in touch, connect with me via [LinkedIn](https://www.linkedin.com/in/davidomarfch/){:target="_blank"}, or write me at [david@davidomar.com](mailto:david@davidomar.com). I also use [Instagram](https://www.instagram.com/__dvorff/){:target="_blank"}, but mainly to post and like generative artwork.

I check them constantly, so you won't have to wait too much to get a response.