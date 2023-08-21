---
layout: post
header-style: invert
title: Tellas
subtitle: A Minecraft Clone
img: img/projects/tellas-sharp.png
hide-author: true
header-img: img/projects/tellas.png
---

I was interested in how games are made from scratch, as well as how 3D models can be rendered at all. So I started looking into OpenGL. After a while I thought I understood enough to try making a project in it, so I decided to make a Minecraft clone. I had been finding out about Scala for the first time then too, and thought it'd be a good chance to learn both at the same time, using C++ and OpenGL for the technical bits, and then working with an abstracted model in the Scala, interacting with the internals via JNI. Overall it turned out well, as you can see in this image:

![alt text](/img/in-post/tellas-sharp.png "A screenshot of the final version of Tellas")

Once done, the mechanics of the game included:
 - Multiple Blocks with different textures
 - The ability to place different blocks where you are looking
 - The ability to destroy blocks where you are looking
 - Jumping
 - Basic collision detection
 - Lighting
 - Shadows
 - Day/Night cycle (With sun and sky colour)
 - Chunk management (Via 16x16x16 block chunks)
 - Terrain Generation using basic perlin noise

While this could have gone further, I believed that this would result in less actual OpenGL being worked on in favour of better collision or more blocks, and being intended to learn OpenGL rather than create a final product to market, meaning it would be a better use of time to begin work on another project instead.

You can find the game on GitHub [here](https://github.com/Black-Photon/Tellas) including the downloads for Linux and some versions of Windows 10