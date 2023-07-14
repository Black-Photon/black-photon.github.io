---
layout: page
subheadline: "Programming Projects"
title: "Cell Assault"
teaser: "A game about battling infection in the body"
header:
    image_fullwidth: "cells-header.png"
    caption: Image from Joseph
image:
    thumb:  cells-thumb.png
    homepage: cells.png
categories:
    - programming
tags:
    - games
    - unity
comments: true
---

Recently we had a 72 hour Warwick Game Design Game Jam for during the Coronavirus pandemic. I decided to make a game on the theme of disease.

<!--more-->

Most of my experience with Unity was doing basic UI additions to games others have made, whereas this time I wanted to program it myself. I started with the idea that it would be a strategy game where you had different types of infection come, and you had to control which white blood cells to send in to stop them.

I did some basic research, and decided a good start would be bacteria and Neutrophils, a type of WBC that can swallow bacteria. Then I got to making the game.

The first day was making textures. I was using a Tilemap to control collision and texturing, so it was just a matter of making all the textures. Then I made a basic map that used them.

The next day, I began on the movement of the particles. The bacteria were first, and needed to move around doing damage. Thus I chose to make a set of locations they would try to move towards. This mostly worked, but they often got stuck on a wall, the correct x or y coordinate, but unable to take a direct route from there. I could have written a pathfinding algorithm, but wanted something quicker to write given the limited time. Thus I instead made a check for being stuck, and if it is, move in another direction for a while before continuing. On this small map, it worked well and the bacteria avoided getting trapped.

Next I had to create a way of spawning them. This was as simple as making a spawn script creating instances of the prefab. This had a max spawn instances as well as a time between spawning.

Next was the red blood cells. These could use the same navigation as the bacteria, but instead of going to random locations on the map, instead going different routes to the end. Spawning them worked similarly, using the same script with different parameters.

Finally was the white blood cells. They needed to find the nearest bacteria and move towards them, and also could easily use the same algorithm as the bacteria and red blood cells with a different target.

At this point I had a pretty good simulation, spawning red blood cells moving to the exit, white blood cells moving to bacteria and bacteria moving randomly. Often bacteria and white blood cells were also dragged along by the flow of red blood cells, so had to respawn again at the start.

The main problem however was this wasn't actually a game. So for the final day of the jame, I decided to add some gameplay.

There wasn't a lot of time for anything complex, so my idea was to see how far I get with giving control over the spawn rate of what's already there. The idea was red blood cells gave you points, and these points could be spent on a higher red blood cell flow rate, or more white blood cells. At a higher flow rate, you get more points per second, but also likely bring along more bacteria and WBC's due to the physics of it. White blood cells would stop bacteria, so more of them would be able to handle more. In addition, the bacteria rate would increase indefinitely.

The bacteria would give -5 points if they reach the end, but also had a chance to infect RBC's. This would turn them from +1 point to -1 point. If you get to < 0 points, you lose. This means as long as the bacteria infect more than half the red blood cells, you quickly start losing all your points. You also need to be careful you don't instantly die from purchasing an upgrade. This balances as bacteria rarely reach the end, and adds a drawback to getting red blood cells - they can help and defeat you.

This created a final game I was pretty happy with:
![alt text](https://black-photon.github.io/images/cells-gameplay.png "Gameplay from the final release")

This had some final issues; You could have a white blood cell camp the entrance to stop the bacteria as they spawn. In addition, as you get too many cells, they can often form blood clots, where the WBC's are trying to get to the start, pushing back the RBC's, and the RBC's are on the wrong path, and trying to move backwards to their chosen goal. However, this also adds some fun to the game. It sometimes happens that the board gets completely filled, and some are even pushed out into the Tilemap.

Overall I thought it went well for my first solo Unity game, and gave me some understanding of the process, and the positive feeling finishing it and seeing others enjoy it.

I'm not sure if I will expand it, but if I did, I'd ideally want the bacteria to come in through an extra lungs section instead to avoid infecting the red blood cells immediately as a result of the same spawn. In addition, it'd be nice to allow the red blood cells to move forward in any direction, and maybe even add more disease types and other white blood cell types as originally conceived.

You can find and download the game over [here](https://itch.io/jam/wgd-2019-20-games/rate/604650)