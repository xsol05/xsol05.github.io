---
title: "💀 My First Postmortem"
date: 2022-08-19T14:09:59+12:00
draft: false
summary: "I 'broke' production 😅 Here's what happened and what I learnt"
tags: ["Career"]
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
---

![Img](https://miro.medium.com/max/900/1*yAHNy48W06zLymKwBxClWA.jpeg#center)

## What is a postmortem

A [postmortem](https://kwa29.medium.com/it-post-mortem-guidelines-77214c6e7e34) in tech is basically a process where teams dissect and reflect on an incident that usually happened in Production. They document what happened, learnings, and how to avoid it in the future. There's no naming and shaming the perpetrator of the incident.

> Postmortems are not about figuring out who to blame for an incident that happened. They are about figuring out, through data and analysis, what happened, why it happened, and how it can be stopped from happening again. - [Arni Birgisson](https://twitter.com/arnibirgisson)

## My first incident

As luck would have it, I had my first incident last week 😅

Let me explain: I was the feature lead for a feature. The feature involved replacing some old components with new ones. One of the components replaced also had a validation check added to it. This check was run through Product, and the whole feature underwent extensive QA testing in various environments. Everything was going smoothly so when I received the green light, I shipped the feature aka I realeased it into our production code base, meaning our users would be able to access the feature.

I posted an annoncement in the release channel then gave myself a pat on the back. Woohoo! 🥳 This feature took several sprints and I was so glad it was finally shipped.

About half an hour later, my colleague alerts me of a tech support ticket created regarding my feature. Not too long after, I get pulled into another Slack thread regarding the same issue reported about the feature. Before I know it, an incident management process is kickstarted and my feature gets reverted from production 🤡

A wave of emotions overcome me. Embarrassment, humiliation, sadness, disappointment, perplexion, indignation.

I knew that it wasn't my fault, or anyone's fault for that matter, and no one was blaming me either. But, since I made the change and shipped the feature, I couldn't help but feel a sense of responsibility. And you know, your first one just hits differently ok? 🥲

So first things first. I'm human and it's natural to feel all these emotions, so I allowed myself to acknowledge them instead of just brushing them away.

Then I reflected on the whole process and wrote some notes in preparation for our postmortem meeting. I documented what happened, why it happened, the incident timeline, mitigations, and various discussion points.

The meeting went smoothly and we had some great discussions, even discovering another unrelated issue through this incident.

All was well.

## What I learnt

This incident sparked a bunch of thoughts:

### 1. What constitutes a discussion

As I was working on the feature, I came across a bug in the same area that was present in production. I posted a message in the feature channel about the bug and whether a certain field was required. Product replied that it was. Because of that, I added the validation check. This validation check ended up being the cause of the incident.

In retrospect, that was hardly a discussion 😅

It was simply a question and answer on Slack.

Had I messaged more and clarified if it would be alright to add the validation check, perhaps we might have done a bit more thinking about the user flow of the form. And just maybe, this issue could have been picked up on.

### 2. User testing is so important

Everything seemed to be going fine with my feature. It passed all the code reviews, it passed all the QA testing.

So why did this validation check issue not get picked up on?

It's because we did not test it with the end users themselves.

Sure, we as engineers and testers can write and test our feature, but how we use it might be very different to how our end users use it.

Here's a meme of how differently engineers and users think 🤣

![Img](https://res.cloudinary.com/practicaldev/image/fetch/s--l-SwdXF5--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/i/rv0scugndbxl66lldkuo.png#center)

Side note: Usually before we release a feature, we will have a Bug Bash, an event where various people, both from the Product and Engineering Team and the wider business, will test out the feature. It's where these sorts of issues get picked up on. But because of the small scale and low risk of this feature, we didn't have one 🥲

### 3. Writing tests for your code is key

Tests are a great way to spot an issue before it occurring.

You bet that after we fixed the issue, we wrote tests for various scenarios to prevent this issue from happening again 🤡

### 4. After releasing a feature, monitor the bugs channel

It goes without saying, but one should always monitor the bugs channel after a feature is released.

I never did this in the past because of how low risk my releases were, but this incident taught me a lesson.

Always monitor the bugs channel after a release so that you can be on standby to put out any fires! 🔥

### 5. How to manage incidents in the future

Since this was my first time getting involved in an incident, I was pretty clueless about the incident management process, so shout out to my colleagues for carrying me through. To put it bluntly, I felt like I was a bystander observing the firefighters put out a fire I had caused lmao 🤣

On the bright side, this was a fantastic opportunity for me to get acquainted with the process!

## Afterthoughts

Thankfully, this incident was fairly small, low risk, and was resolved relatively quickly. There was no impact on the customers either.

Everyone congratulated me for my first incident / postmortem because it's something we all experience at some point and graduate from 😅

My manager also told me that experiencing your first incident is a sign that you're growing fast and should be celebrated.

My VP of Engineering even said he's over the moon about us having more incidents as there is no cheaper time than right now in a fast-growing business to have incidents and practise handling them so we can build robust and resilient processes.

I really appreciate the blameless culture we have here as it makes making and learning from mistakes a lot easier.
