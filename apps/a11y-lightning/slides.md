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

---
layout: fact
---

# Hello 👋

My name is Felix Hoffmann

I'm a software engineer @iteratec

---
layout: fact
---

# 1.6 billion
## 1 in 6 people experience significant disability

---
layout: center
---

<div class="grid justify-center text-center">

# More people use accessibility features
<p class="justify-self-center">
  <img src="/tweet.webp"
     alt="Tweet by Nikita Bier: Startups usually ignore accessibility—since they're just trying to prove that a product works. But when testing Gas, we started seeing screenshots on Snapchat that looked off. We found that over 20% of teens have Zoom-mode enabled, so we prioritized it & saw our K-factor jump 0.1"
     style="height: 19rem;" />
</p>
</div>

---
layout: quote
quote: "The design of mainstream products and/or services that are accessible to, and usable by, as many people as reasonably possible … without the need for special adaptation or specialised design."
author: "The British Standards Institute (2005)"
cite: "https://knowledge.bsigroup.com/products/design-management-systems-managing-inclusive-design-guide/standard"
---

::header::
# Inclusive design

<!--
Inclusive Design = Instead of designing a product and then figuring out how it might work for people with disabilities, we design a product that works for everyone, including people with disabilities.
To do that, we have to follow certain rules. We find these rules in the Web Content Accessibility Guidelines. They look like this (CLICK).
-->

---
layout: center
---

# Web Content Accessibility Guidelines

<div class="grid justify-center">
  <img src="/wcag-still.webp" alt="Screenshot of Web Content Accessibility Guidelines" style="height: 20rem;">
</div>

<!--
For the purpose of this talk, I am not going into detail what's in there. I only have 7 minutes and they are quite long. (CLICK/SCROLL)
If you're not familiar with the Web Content Accessibility Guidelines, I highly recommend checking them out.
Let me give you a quick example of what you find in there.
-->

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

<!--
Let's assume we do this and everything else that's in WCAG
Leaves us with the Why? Why should we care? Because it's the right thing to do. It is. But that has never convinced anyone.
Let me tell you the story about Joseph Friedman and the bendy-straw. (CLICK)
-->

---
layout: image-right
image: '/bendy-straw.webp'
transition: fade
---

# Joseph Friedman and the bendy-straw

<!--
patent (CLICK)
ad (CLICK)
mood picture (CLICK)
When we design with accessibility in mind, we can create superior user experiences for everyone. Let's look at what YouTube has done with captions.
-->

---
layout: image-right
image: '/bendy-straw-2.webp'
transition: fade
---

# Joseph Friedman and the bendy-straw

---
layout: image-right
image: '/bendy-straw-3.webp'
---

# Joseph Friedman and the bendy-straw

---
layout: center
---

# Captions

<vue-video src="youtube.webm" stillSrc="youtube-still.webp" :clicks="$slidev.nav.clicks" alt="Screencast of YouTube displaying the use of captions for previews"></vue-video>

---

# Don't get sued

- European Accessibility Act (EAA), comes into force in 2025 🇪🇺
- Web-Zugänglichkeits-Gesetz 🇦🇹
- Other national and regional laws
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

<h1 style="font-size: 5rem;">Thank you</h1>

::left::

<div class="h-full grid items-end">
  <small style="line-height: 100%;">@felixmhoffmann</small>
</div>

::right::

<div class="h-full grid items-end justify-end">
  <div>
    <slides-arrow></slides-arrow>
    <img src="/qrcode.png" alt="QR code with a link to the slides" style="height: 11rem;">
  </div>
</div>
