---
layout: post
header-style: text
title: Metro
subtitle: A Git Commandline Repository Manager
img: img/projects/metro.png
hide-author: true
---

Git is an invaluable tool for managing any kind of programming project, as it both saves your progress, allows multi-tasking and working with other people. However, it seems to happen too often that something doesn't work. You need to reclone the repo. Your changes are completely out of sync as you forgot to push. You mess up one of the many things possible to mess up. While it is very powerful, most programmers have only learned some level of it, and these things get in the way of what you're trying to do. Git isn't bad, it just isn't simple, or convenient. So me and [SiliconSloth](https://www.siliconsloth.com/) decided to look into a way to improve it.

The idea of Metro is to cut out the unneccesary, ask the user and be convenient. Some examples are:
 - `metro commit "Message"`: Removes redundant add command and -m tag (Which are used in the vast majority of cases)
 - `metro absorb other`: Asks if you want to always take the changes from one
 - `metro autosync`: Automatically keeps the repo in sync with the remote via a WIP commit

When planning it, we initally decided on Go, but realised that the native support in C++ made it a better choice. Also it allowed us to use the current LibGit API rather than a wrapper. While initially we considered making it seperate to git, using LibGit would make it both simpler to write, and compatible with native git projects, allowing use of tools such as GitKraken and GitHub alongside it.

Working on this project taught me quite a bit about Git internals, but also experience in picking up a new API with limited documentation from scratch. In addition, there was a lot of C++ wrapping via classes that I used, improving my understanding of C++ and fixing its errors. In retrospect we should have done the project in python instead to speed up development.

We've decided to put the project on an indefinite hold now with alpha-1.1 as we've noticed that many of the main benefits of the tool exist in GitKraken. While it's useful to have a commandline tool, the use cases are few enough to not be worth working on. But we may continue one day if it turns out to be useful again.

You can find the current project [here](https://github.com/SiliconSloth/Metro)