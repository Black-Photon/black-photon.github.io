---
layout: post
title: Hacker Hell
subtitle: A game about protecting your computer against a hacker
header-img: img/in-post/hacker-hell.png
header-img-credit: Joseph28
header-img-credit-href: "joseph28.itch.io/"
header-style: text
tags:
  - programming
  - games
  - unity
---

Last weekend, Warwick Game Design had another Game Jam, this one being 48 hours and with the theme of Connections. I teamed up with another Joseph to create a game about blocking off connections from Hackers.

Our general idea was that Hackers are attacking your computer, and you need to put up the firewalls to stop their connection. However, the hackers are making getting to the firewall very difficult, and you need to fight your way across the desktop to save your computer.

We started by simply making a desktop. I worked on the start menu while Joseph worked on making the enemies. We soon had a basic game, made up of a player, antiviruses to shoot at the viruses, and a firewall to stop the enemy. This is the game near the end of the Saturday:
![alt text](/img/in-post/hacker-hell-early.png "Gameplay from the halfway through")

Joseph has more experience than me in Unity, so he created the initial scripts, and suggested ideas for implementing the rest. We ended up by having triggers on all the buttons to send a signal to the master script to say what button the mouse is over. Then, that corresponding button's action is activated by assigning a function to which processes this to the OnClick of the player. This meant we were able to easily allow clicking on any button and correctly process it.

Later, I started on textures, creating some for the start icons, the fire in the barriers, black holes for the spawners and viruses for the viruses. This started to make it look much nicer. I had to wrestle with the animation API for a while to manage to get the fire to switch between two textures. In this time, Joseph creates the barrier blocks, inspired by the ones in Minecraft, to make reaching the end more challenging.

Finally, after Joseph created the window for viruses, I modified it to also work for the firewall, and added used a public list variable in the scripts to let us change the messages inside the Unity UI. I also finished by messing around with particles, to make the portals look better.

Then Joseph did a massive amount of polish, creating the last few textures, and adding a start screen, end screen, bottom right utility bar and a sensitivity option. You can see the result here:
![alt text](/img/in-post/hacker-hell-game.png "Gameplay from the final game")

Overall it was an enjoyable experience, and helped me learn a little more about how to use Unity. I also came across some issues during production, requiring me to restart Unity many times over to clear various bugs. But the final game both looked good, and is enjoyable, yet challenging, as well as fitting the theme of connections. While unsure about the idea at first, it's clear it worked out in the end.

An especially enjoyable part was simulating a desktop - seeing such a UI take shape was great to experience and I may yet consider doing again.

You can find and download the game over [here](https://itch.io/jam/wgd-2019-20-games/rate/677595)