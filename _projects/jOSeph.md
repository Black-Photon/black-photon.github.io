---
layout: post
header-style: text
title: jOSeph
subtitle: Multipurpose Learning Application
img: img/projects/jOSeph.png
hide-author: true
---

As my first project, jOSeph was really a way to explore what was possible via programming. I ended up working on it for 2 years or so, until eventually I understood how to make things properly.

It started as a console application which expanded to have more features as I learned more Java and JavaFX. The final application had a multitude of features including:
 - Login system with username + password saved. This involved basic file manipulation and security.
 - Loading screen with progress bar. It took a long time to find the parts of the API including this, and acts as a lesson not to reinvent the wheel. The older versions made use of threading.
 - Button with counter. This had achievements and eventually led to the creation of Aedmun.
 - Quiz, including Maths, Science and Computing.
 - Calculator with all basic operations
 - Achievements Tracker, which recorded achievements, mostly from the button clicker. A notification appeared when one was achieved.
 - Notes. Each note was in a folder dedicated to that user, and the files also had a basic 2-way encryption.
 - Messaging, made up of a single server and multiple clients supported. This allowed a group chat by way of the server as long as it was online. (Only 127.0.0.1 was supported)
 - Noughts and Crosses, including checks for if the move is valid as well as if it's a win.
 - Chess, with similar checks for checkmate.
 - Settings, allowing changing of username and/or password.
 - Changelog of what's new in each version.

<center>
   <img src="/img/in-post/jOSeph.png" title="A screenshot of the final version of Aedmun" width="400"/>
</center><br/>

In the end, the application made use of Java, JavaFX and CSS to finish, and marked the end of my learning period. While none of it was too impressive, it was useful to get used to programming, and gave me exposure to many elements in programming. You can find the source code and final product on my GitHub [here](https://github.com/Black-Photon/jOSeph)