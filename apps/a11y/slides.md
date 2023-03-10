---
# try also 'default' to start simple
theme: spezi
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
# page transition
transition: slide-left
# use UnoCSS
css: unocss
---

# Accessibility for All

## The Benefits of Inclusive Design
<br><br>
<small>@felixmhoffmann</small>
---
layout: fact
---

# Hello 👋

<v-clicks>
My name is Felix Hoffmann

I'm a software engineer @iteratec

and I like trains 🚂
</v-clicks>

---
layout: center
---

<div grid="~ cols-3 gap-8">

<div>

### Elevators
<img src="/elevator.webp" alt="Elevator">
</div>

<div v-click>

### Step-free access
<img src="/level-access.webp" alt="Step-free access onto a train">
</div>

<div v-click>

### Automatic doors
<img src="/train-doors.webp" alt="A train with heavy, manual doors.">
</div>

</div>

---
layout: fact
---

# 1.6 billion
## 1 in 6 people experience significant disability

---
layout: quote
quote: "The design of mainstream products and/or services that are accessible to, and usable by, as many people as reasonably possible … without the need for special adaptation or specialised design."
author: "The British Standards Institute (2005)"
cite: "https://knowledge.bsigroup.com/products/design-management-systems-managing-inclusive-design-guide/standard"
---

::header::
# Inclusive design

---
layout: center
---

# Web Content Accessibility Guidelines

<vue-video src="wcag.mp4" stillSrc="wcag-still.webp" :clicks="$slidev.nav.clicks" alt="Screencast of Web Content Accessiblity Guidelines"></vue-video>
---

# Design for accessibility

- Users of screen readers
- Users with low vision
- Users with dyslexia
- Users with limited motor skills

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
layout: fact
---

# Structure

---
layout: fact
---

# Contrast

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

# Keyboard navigation

---
layout: fact
---

# Enough time

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
layout: fact
---

# Search engine optimization
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
layout: center
---

<img src="/nytimes.webp"
     alt="A New York Times article. Title: M.T.A. Vows to Make Subways 95% Accessible. It Will Take 33 Years."
     style="height: 28rem;" />

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

