---
layout: page
subheadline: "Programming Projects"
title: "Tellas: The Conclusion"
teaser: "The final report on Tellas and the features added and considered since the initial post."
header:
    image_fullwidth: "tellas.png"
    caption: Image by Joseph
image:
    thumb:  tellas.png
    homepage: tellas.png
categories:
    - programming
tags:
    - OpenGL
    - games
    - scala
    - c++
comments: true
---

It has been a good, and slightly shorter than expected, journey, but I’m probably going to leave Tellas here for now. It’s taught me how to make a working OpenGL application and use Scala, but it’s at the point it’s not got much left to teach me. So alas it must be let go.

<!--more-->

![alt text](https://black-photon.github.io/images/tellas-sharp.png "A view of Tellas in the last version")

Since the last post, I’ve added many features visible in the image.

The game now allows multiple block faces. This was tricky as I either had to give the shader 6 textures, or draw each face separately. However, by doing the latter, I could cull faces that are covered by other blocks, thus that was the option I chose. Overall it worked out, but lag became a problem with 4 chunks render distance. This was mostly a result of the number of dirt blocks below being rendered.

In addition, I finished the Day-Night cycle. I wanted to have shadows. After some research, I found shadow mapping as a useful technique and proceeded to implement it. It had an issue where it only worked for the first 180 degrees, and some analysis showed that it was actually optimizing too much. I had added an optimization to not render chunks behind the player. But this worked against it here. Disabling this fixed the problem.

It also had a problem that at steep angles, blocks got incorrect shadows as a result of only a few pixels being available for large areas. The image was at the resolution limit, so I found the solution was to use different bias values for different angles (bias values being how ‘off’ the pixel can be from where it’s meant to be and still be considered light)

With that done, I moved to the sky and sun. The sky was relatively simple to change the clear colour for. However, the sun seemed to never get to the right orientation. In the end I had to use a manual matrix in place of the helper function to make it work.

I also added an option to change the block placed, indicated by the block in the corner without too much effort.

Finally, I added in some basic terrain. I looked up and completed a basic implementation of the perlin noise algorithm to generate slopes. The algorithm was quite complex and took time to make sense of. I ended up with spikes quite a bit, and thus a smaller grid was necessary. However, after tweaking it eventually it came out realistic.

Unfortunately there’s only so far you can go to make cubes look good, but it was useful for what it was used for. I plan to move onto another game soon.

I’ll be trying to compile what I’ve got for Linux and Windows, but the Windows one seems to be more difficult so I’m unsure how long till or if I will be able to get that one working. But either way, this is likely it for Tellas.