---
title: "About"
permalink: /about

layout: single
align: center
hideTitle: True
---

<script>
var description = [
  "loving <a href = 'https://youtu.be/paqr3kdmcZg?list=PLwic3h1bAlblkSJ-U9YxEpTclFoUS_Otq&t=41' target=_blank>Woodkid's music</a>",
  "quoting The Simpsons",
  "procrastinating at <a href = 'https://www.reddit.com/r/aww' target=_blank>r/aww</a>",
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

## Professional stuff

I've been studying CSE since August 2016. I've developed some things that you can check on my [../portfolio](../portfolio) or at [Daque's](https://github.com/daque-dev).

I develop mainly in `D`, `Python`, and `Javascript`, but learning a new language isn't a trouble.

I always comment my code and I always focus on readability. For some code examples, you can check out [`daque/traces`](https://github.com/daque-dev/traces){:target="_blank"} or [`davidomarf/zipf`](https://github.com/davidomarf/zipf){:target="_blank"}.

I have some experience in web publishing, using WordPress and Jekyll. This website, [my blog](https://blog.davidomar.me) and [Daque](https://daque.me) are built with Jekyll.

I've also done some data visualization work that you can see at my [Kaggle Profile](https://www.kaggle.com/davidomarfch/){:target="_blank"}.

I'm fluent working with git. That means knowing how to work on forks and branches, writing modular commits, pulling and pushing changes, merging, and solving merge issues. 

You can find all my code at [my github profile](https://github.com/davidomarf){:target="_blank"}.

I'm looking forward to do more work in data visualization, computer simulation, development, and machine learning.

## Personal Stuff

After I got into college, an avalanche of mindset changes started. I became more avid for knowledge and wisdom. I became a lot more curious. Those were the main reasons I started to pick up reading as a habit.

And I really think now that by reading, your mind gets into a broader, more dynamic, and more connected configuration. It makes you easier to think between different disciplines and discern some similarities (of course, this depends on what you read).

And that's one of my favorite things. Learning something new and feel that I *intuitively* knew it. And then figure out why I felt it.

---

I love music. And I'm pretty versatile at it. You can befriend me at [last.fm](https://www.last.fm/user/davidomarf) or follow me in [Spotify](https://open.spotify.com/user/davidomarfch).

---

One thing I'm recently obsessed about is sleeping. I commited myself to sleep and wake up at the same time everyday, always giving me 8:30 hours of sleep opportunity.

---

I write some of my beliefs and ideas at my [blog](https://blog.davidomar.me){:target="_blank"}. It's a very personal and honest thing.

I write impartially. Both "positive" and "negative" things. For example, when I feel bad, dobious, insecure, or angry about myself —thing that I believe, happens to all of us every once in a while. 

I also write book reviews and summaries. It would make me authentically happy if you go there and read something.

---

There's some (alive) people I like for what they do. A short non-exhaustive list in alphabetical order includes 
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

## Get in touch

If you'd like to get in touch, connect with me via [LinkedIn](https://www.linkedin.com/in/davidomarfch/), or write me at [davidomarfch@gmail.com](mailto:davidomarfch@gmail.com).

I check them constantly, so you won't have to wait too much to get a response.

# About the site

This webiste was built with [Jekyll](https://jekyllrb.com). The theme I use is a modification of [Minimal Mistakes](https://mademistakes.com/work/minimal-mistakes-jekyll-theme/).

The `.me` domain extension was a gift from [Namecheap](https://www.namecheap.com). It was included in the [GitHub Student Pack](https://education.github.com/pack). The hosting is provided for free by [GitHub Pages](https://pages.github.com).

To handle other things like SSL certificate, cache, and DNS, I use [CloudFlare](https://www.cloudflare.com).