---
title: "About me"
excerpt: "This is what I am, what I do, and what I believe in"
permalink: /about

layout: single
align: center
---

<script>
var description = [
  "procrastinating in <a href = 'https://www.reddit.com/r/aww' target=_blank>r/aww</a>",
  "<a href = 'https://youtu.be/paqr3kdmcZg?list=PLwic3h1bAlblkSJ-U9YxEpTclFoUS_Otq' target=_blank>Woodkid</a>",
  "quoting The Simpsons on a daily basis",
  "generative artwork",
  "dancing (even when I'm pretty bad at it)",
  "woodworking"
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

Hi, I'm David!

I'm a computer science and engineering student. I have a special interest on complexity, machine learning, quantum computing, and <script>document.write('—<a id="random-description-switcher" href="#">among other things</a>—, <span id="random-description"> ' + description[randomNumber] + '</span>');</script>.

<!-- ## ¿Quieres trabajar conmigo? ¡Conectemos!

Puedes enlazar conmigo vía [LinkedIn](https://www.linkedin.com/in/davidomarfch/), o escribirme a [davidomarfch@gmail.com](mailto:davidomarfch@gmail.com). Ambos los reviso constantemente.

-->

---

## About the site

This webiste was built with [Jekyll](https://jekyllrb.com). The theme I use is a modification of [Minimal Mistakes](https://mademistakes.com/work/minimal-mistakes-jekyll-theme/).

The `.me` domain extension was a gift from [Namecheap](https://www.namecheap.com). It was included in the [GitHub Student Pack](https://education.github.com/pack). The hosting is provided for free by [GitHub Pages](https://pages.github.com).

To handle other things like SSL certificate, cache, and DNS, I use [CloudFlare](https://www.cloudflare.com).
