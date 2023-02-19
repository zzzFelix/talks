---
theme: spezi
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
transition: slide-left
css: unocss
title: Accessibility for All
---

# Accessibility for All

## The Benefits of Inclusive Design
<br><br>
<small>@felixmhoffmann</small>

<!--
Inclusive Design = Not building for a small audience and then trying to slap accessibility on top but designing something so that it works for everyone
-->

---
layout: fact
---

# Hello 👋

<v-clicks>
My name is Felix Hoffmann

I'm a software engineer @iteratec
</v-clicks>

---
layout: center
---

# Web Content Accessibility Guidelines

<vue-video src="wcag.mp4" stillSrc="wcag-still.webp" :clicks="$slidev.nav.clicks" alt="Screencast of Web Content Accessiblity Guidelines"></vue-video>

---
layout: two-cols
---

# Semantic HTML

```html
<nav>
  <ul>
    <li><a href="/link">Menu item 1</a></li>
    <li><a href="/link">Menu item 2</a></li>
    <li><a href="/link">Menu item 3</a></li>
  </ul>
</nav>

<main>
  <h1>Accessibility</h1>

  <section>
    ...
  </section>
</main>
```
::right::

<v-click>
<h1> </h1>
```html
<div>
  <div>
    <div><span @click="jsAction()">Item 1</span></div>
    <div><span @click="jsAction()">Item 2</span></div>
    <div><span @click="jsAction()">Item 3</span></div>
  </div>
</div>

<div>
  <span>Accessibility</span>

  <div>
    ...
  </div>
</div>
```
</v-click>

---
layout: image-right
image: '/bendy-straw.webp'
---

# Joseph Friedman and the bendy-straw

---
layout: center
---

# Captions

<vue-video src="youtube.webm" stillSrc="youtube-still.webp" :clicks="$slidev.nav.clicks" alt="Screencast of YouTube displaying the use of captions for previews"></vue-video>

---
layout: fact
---

# 1.6 billion
## 1 in 6 people experience significant disability


---
layout: center
---

<div class="grid justify-center text-center">

# Resize text

<img src="/tweet.webp"
     alt="Tweet by Nikita Bier: Startups usually ignore accessibility—since they're just trying to prove that a product works. But when testing Gas, we started seeing screenshots on Snapchat that looked off. We found that over 20% of teens have Zoom-mode enabled, so we prioritized it & saw our K-factor jump 0.1"
     style="height: 15rem;" />
</div>

---

# Don't get sued

- Americans with Disabilities Act (ADA)
- European Accessibility Act (EAA)
- Other national laws
---
layout: center
---

# EU corporations in 2025

<div class="grid justify-center">
<img src="/surprised-pikachu.png"
     alt="Surprised Pikachu face meme"
     style="height: 15rem;" />
</div>

---
layout: two-cols-header
---

::header::

# Thank you

::left::

<div class="h-full grid items-end">
  <small>@felixmhoffmann</small>
</div>

::right::

<div class="h-full grid items-end justify-end">
  <div>
    <p>Slides</p>
    <img src="/qrcode.png" alt="QR code with a link to the slides" style="height: 11rem;">
  </div>
</div>
