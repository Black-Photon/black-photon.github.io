---
layout: post
title: Metro Alpha-1.1
header-img: img/projects/metro.png
header-style: text
tags:
  - programming
  - c++
---

Metro started out as a way to replace Git in day-to-day use. To simplify the commands to a point where you can type what you want to do and let the program do its magic to accomplish your task. Since then, we've slowly but surely been changing Metro until the program is no longer for a simplified command set, but for the core problem we were originally working to solve - convenient work synchronisation.

It's been a long time since the last post back in the September of 2019, but in that time Metro has been progressing, both in its codebase, and our understanding of what Metro is trying to achieve. Recently we released the second alpha release of Metro since its conception. This brings a new set of commands as well as a much needed stability in the commands, fixing a truckload of issues in previous versions.

The alpha-1.1 release contains the most commands yet, including `create`, `clone`, `commit`, `patch`, `delete`, `branch`, `switch`, `info`, `absorb`, `resolve`, `sync`, `list`, `rename` and `wip`, each focusing on their own functionality, and most mirroring an equivalent command in Git.

Furthermore, the project has a wiki (albeit a severely outdated one), a continuous integration system setup, and a bats test suite, meaning that every pull request can be certain to have built and passed tests. In addition, the CMake build system has been simplified massively such on Linux nothing more than the standard `cmake .. && cmake --build .` is required.

However, there are big plans in the works for alpha-1.2. We began to discover over time how many commands were simply reimplementing the standard Git. From alpha-1.2, Metro is no longer a Git replacement, but rather supplements Git with new functionality, the core being the sync command. The ability to jump between workstations and workflows easily and quickly is the essence of Metro and all components beyond that are being retired. This means in alpha-1.2, the only remaining commands will be `sync`, `switch`, `wip`, `rename`, `clone` and `delete`, or in other words, any command that relies on the idea of WIPs.

A WIP is a branch which has the name of a base branch followed by `#wip`, containing a single additional commit from the base branch. The contents of this are automatically loaded into the working directory whenever the commit is checked out without actually committing. For example, you could be on branch A and want to move to branch B. `metro switch` would do so while saving your changes from branch A in `A#wip`. In addition, if you were to sync on branch A, the changes in the working directory would be saved to `A#wip` in the remote, while still being in the working directory locally.

We've still got a long way to go until the beta-1.0, but hopefully then we'll be able to get a real look at the impact of the design choices made, and discover if we made the right choices. For now Metro is at least useful as a full git replacement until the next version, so feel free to give it a try!

[Check out the project page for the latest updates!](/projects/metro/)