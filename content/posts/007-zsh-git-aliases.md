---
title: "✨ Oh My Zsh Git Aliases"
date: 2023-03-17T14:36:08+13:00
draft: false
summary: "Supercharge your Git workflow in Oh My Zsh" #displays underneath title in blog title card on homepage
description: "Supercharge your Git workflow in Oh My Zsh" #displays underneath title in actual blog page
tags: ["Git"]
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

If you manage your Git workflow via the terminal and your terminal is [Oh My Zsh](https://ohmyz.sh/), then you're in for a treat.

Oh My Zsh has a bunch of built-in aliases for Git commands which are an absolute game-changer 🤯

```Bash
gst = git status # status of your repo and changes

gapa = git add --patch # choose which changes in a file to commit
gaa = git add --all # stage all your changes

gcmsg = git commit -m # commit with a message

gco = git checkout # change to a specific branch
gcb = git checkout -b # create a new branch off the current branch and change to it at the same time

gp = git push # add your changes to the remote repo
gpsup = git push --set-upstream origin $(current_branch) # push a local branch to remote

gl = git pull # obtain the latest changes from the remote repo

gm = git merge # combine various versions of a file or folder

grhh = git reset --hard # undo all your changes

gsta = git stash push # add to your stash
gstp = git stash pop #remove from your stash
```

See [here](https://kapeli.com/cheat_sheets/Oh-My-Zsh_Git.docset/Contents/Resources/Documents/index) for the complete list of aliases.

And if you forget what an alias does, just do this `which <alias>` eg

```Bash
> which gst
gst: aliased to git status
```
