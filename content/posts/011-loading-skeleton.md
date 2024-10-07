---
title: '🛼 How to Create a Loading Skeleton Animation'
date: 2023-07-31T22:08:36+12:00
draft: false
summary: "But let's start with what even is a loading skeleton and why we need it" #displays underneath title in blog title card on homepage
description: "But let's start with what even is a loading skeleton and why we need it" #displays underneath title in actual blog page
tags: ["CSS", "Animations"]
author: "Magdeline Huang"
showToc: true
TocOpen: false
hidemeta: false
comments: true
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Frsamorim.azurewebsites.net%2Fwp-content%2Fuploads%2F2020%2F05%2F68747470733a2f2f63646e2d696d616765732d312e6d656469756d2e636f6d2f6d61782f3830302f312a5471364375495f494a306b5838443274546f556554512e676966.gif&f=1&nofb=1&ipt=59bf4543dafe81689dc3b3930b9940153b75c33092b30207cfa81b02475dcce8&ipo=images#center" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/xsol05/xsol05.github.io/blob/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

![Img](https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Frsamorim.azurewebsites.net%2Fwp-content%2Fuploads%2F2020%2F05%2F68747470733a2f2f63646e2d696d616765732d312e6d656469756d2e636f6d2f6d61782f3830302f312a5471364375495f494a306b5838443274546f556554512e676966.gif&f=1&nofb=1&ipt=59bf4543dafe81689dc3b3930b9940153b75c33092b30207cfa81b02475dcce8&ipo=images#center)

## What is a loading skeleton screen?

A loading skeleton screen is essentially a low-fidelity version of the final page UI. The skeleton blocks are usually animated and display the UI gradually as opposed to all at once upon complete load like loading spinners.

There are several advantages of using a skeleton loading screen:

1. **Clear indication of progress**

   Because the UI gradually loads over time, there is a clear indication of the loading progress. Gradual progression examples include first displaying text or displaying the dominant colour of an image.

2. **Shifts attention from the wait time to the progress**

   Gradually displaying the UI over time as opposed to just displaying a loading spinner helps to shift the user’s attention from the wait time to the actual loading progress.

3. **Perceived to be faster than actual**

   Being able to see loading progress causes the user to perceive that the loading speed is faster than what it actually is.

4. **Final UI is not a surprise**

   Since the skeleton loading screen is a barebones mockup of the final UI, users know what to expect.

## Examples of loading skeleton screens

![Img](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.freecodecamp.org%2Fnews%2Fcontent%2Fimages%2F2022%2F04%2F1-2.png&f=1&nofb=1&ipt=fb2b67f89118dc83f6bddeabc39de109b461060e098c2f5206b709447adc63a0&ipo=images#center)

![Img](https://www.freecodecamp.org/news/content/images/2022/04/2-2.png#center)

![Img](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fmiro.medium.com%2Fmax%2F1400%2F0*Z47w4-DkaWPY92HO.png&f=1&nofb=1&ipt=412c5faf0fa1757aafe818b4e76415e7d90a7d03e37279fc967f845f69b736cd&ipo=images#center)

## Let's build a loading skeleton screen!

According to [research](https://uxdesign.cc/what-you-should-know-about-skeleton-screens-a820c45a571a#:~:text=transition%20was%20faster%3F%E2%80%9D-,The%20tests,-I%20sequentially%20layered), here are the preferred characteristics of the loading skeleton block:

- Animation: Wave
- Direction: Left to right
- Speed: Slow and steady
- Colour: Light grey or a neutral colour for the skeleton blocks. For images, use the dominant colour of the image.

Ok, let's start building it! If you don't have a development environment set up, you could simply code in something like [replit.com](https://replit.com/) or [codepen.io](https://codepen.io) ✨

We will use this HTML structure:

```html
<div class="container">
  <div class="avatar skeleton"></div>
  <div class="info">
    <div class="text skeleton"></div>
    <div class="text skeleton"></div>
  </div>
</div>
```

And apply these CSS styles (note the skeleton class):

```css
.container {
  display: flex;
  align-items: center;
}

.skeleton {
  background: linear-gradient(90deg, #eee, #f9f9f9, #eee);
  animation: leftToRight 1.5s infinite reverse;
  background-size: 200%;
}

.avatar {
  width: 50px;
  height: 50px;
  border-radius: 50%;
}

.info {
  margin-left: 10px;
}

.text {
  width: 100px;
  height: 16px;
  border-radius: 4px;
  margin-bottom: 3px;
}

@keyframes leftToRight {
  0% {
    background-position: -100% 0;
  }

  100% {
    background-position: 100% 0;
  }
}
```

Note, it is very important to pair `background-position` with `background-size`! Without `background-size`, the gradient would not move.

Using a linear gradient background with a larger `background-size` eg 200% creates an illusion of a moving gradient or background color. The gradient is initially positioned outside the element's visible area, and as you animate the `background-position`, it appears as if the gradient is moving inside the element, creating the left to right animation effect. Cool right?! 😄
