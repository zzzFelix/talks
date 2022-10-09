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

My name is Felix Hoffmann

Software engineer @iteratec

---
layout: image-right
image: '/bendy-straw.webp'
---

# Joseph Friedman and the bendy-straw

---
layout: center
---

# Web Content Accessibility Guidelines

<vue-video src="/wcag.mp4" stillSrc="/wcag-still.webp" :clicks="$slidev.nav.clicks"></vue-video>

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

# Captions

- Eating chips
- Learning a language
---
layout: center
---
<vue-video src="/youtube.webm" stillSrc="/youtube-still.webp" :clicks="$slidev.nav.clicks"></vue-video>
---

# Many users use a11y features

- Android users love to customize EVERYTHING
- 20% of teenage users have activated zoom mode

---

# Legal

- Austria has a law
- EU will have a law in 2025
- Corporations in 2025: surprised pikachu face
---
layout: center
---

<img src="/surprised-pikachu.png"
     alt="Surprised Pikachu face meme"
     style="height: 15rem;" />

---
layout: two-cols
---

::default::

# Thank you
<br>
<small>@felixmhoffmann</small>

::right::

<img src="/qrcode.png" alt="QR code with a link to the slides" style="height: 15rem;">
<br>
Slides

