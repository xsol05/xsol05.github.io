---
title: '♿️ Accessibility'
date: 2023-03-31T18:11:56+13:00
draft: false
summary: "My takeaways from a talk on accessibility" #displays underneath title in blog title card on homepage
description: "My takeaways from a talk on accessibility" #displays underneath title in actual blog page
tags: ["Accessibility"]
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
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/xsol05/xsol05.github.io/blob/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

<!-- {{< figure src="/images/fullstackdev.jpg#left" alt="Full stack dev meetup" caption="Full stack dev meetup" height="400px" width="300px">}} -->

<!-- {{< figure src="/images/accessibility.jpg#centre" alt="Accessibility Erosion by Ben Evans" caption="Accessibility Erosion by Ben Evans" height="400px" width="300px">}} -->

I recently attended my first ever [dev meet up](https://www.meetup.com/full-stack-dev-new-zealand/events/291941981/) hosted by [Full Stack Dev Group](https://www.meetup.com/full-stack-dev-new-zealand/)!

Here's my takeaways from the accessibility talk by [Ben Evans](https://benevans.buzz/). You can find the slides [here](https://docs.google.com/presentation/d/1tAjibS4JIEm7VwjFTmsU8Y3-yHDPeH-ZIN-lo1m52Gk/edit#slide=id.gd362d286f3_1_0).

1. What is more accessible is highly dependent on the user. Eg larger text would be more accessible for users with failing sight but smaller text would be more accessible for users with tunnel vision. So bottom line is to cater accessibility of your platform to your largest user group.
2. Might be a little controversial but web accessibility kinda got worse with the emergence of CSS and JS frameworks (cue random divs and spans 🥲)
3. Use semantic HTML! Eg instead of making a custom accordion, use the inbuilt HTML `<details>` and `<summary>` tag. I was actually working on building an accordion that time and had just learnt about those tags so super cool to have it mentioned in the talk!
4. You don’t need `alt` text for everything 👀 If it’s just a decorative image, just provide a blank `alt`. If it’s conveying info like a graph, explicitly specify the info.
5. How can we get businesses and not just FE devs and designers to care about accessibility? Just do it 🤡 Of course there might be certain times where you need to make a calculated decision and sacrifice accessibility, but the point is to not ask for permission and just always have accessibility at the core of what you do.
6. So how do we actually make our website more accessible? The speaker Ben Evans gives some great practical tips from slide 22 onwards. There’s also a bunch of resources on slide 37.

Overall, really great talk! Thanks Ben 😁
