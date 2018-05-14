---
layout:     post
title:      "Camera flights! (p1)"
date:       2018-05-15
category:   Game engine, opengl, computer graphics
tags:       [game engine, opengl, computer graphics]
sitemap:
    priority: 0.7
    lastmod: 2018-05-15
    changefreq: weekly
excerpt: "I've been making my first game engine and now that I have something to show for it, it's time for a writeup. I managed to enter closer to the previous century [...]"
image: "/images/Kalm/intro.png"
---

<!--[//]: # (COMMENT EXAMPLE)-->
<!--[//]: # (TODO(Kasper): Move gallery somewhere else, or hide and load with javascript)-->


## Preface
I've been making my first game engine and now that I have something to show for it, it's time for a writeup. I managed to enter closer to the previous century and I know there's going to be a lot of engine side coding in the near future, which won't really advance the graphical output at least in a direct way.

## The Dreams
I wanted to create a sort of playground game engine for Lua. Not a Lua library per se, but an engine for creating games with Lua so that Lua lives inside the engine, not the other way around. I was thinking about a 2D engine, because I hadn't really built either 2D or 3D engine, and knew alot of the code would be reusable.

I thought of Unity style object-component model. Basic audio playback with either DirectX or an audio library. The very high level abstraction I copied from idTech, Quake and Doom engines. You basically have a core engine and the system-interacting parts in the executable, eg. rendering, audio, file I/O, memory and timers. In a dll you put more of the scripting side, preferences, and assets in usable form and the actual game logic. First thing you do when you load the game you pass pointers from one to the other, so they can talk to freely through an API. Some parts might have "private lines", for example the front-end renderer and the back-end renderer, making relevant communication easier.

The compilation style I went for was to have these two objects compiled, other relevant code being *included* to the base object or some manager class. For example my **MemoryStack** class is included straight in the **Memory Manager**.

This was more or less what I had in mind before I started coding.

## But first
I personally like seeing tons of timeline pictures, so I'm just going to show you the ones I've gathered during the project.
You can refer back to it if you wish, but it's not necessary at all, and if you're not interested you can just scroll past them.
If you want to see them in bigger resolution, you should be able to either *right-click->show image* or hold your thumb on
the image to open similar options. The pictures should be in chronological order.

<hr />

<div class="box"><p>
<span class="image fit"><img src="{{ "/images/Kalm_logo_padded.png" | absolute_url }}" alt="" /></span>
<div class="box alt">
<div class="row 50% uniform">
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images1.png" | absolute_url }}" alt="" /></span></div>
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images2.png" | absolute_url }}" alt="" /></span></div>
<div class="4u$"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images3.png" | absolute_url }}" alt="" /></span></div>
<!-- Break -->
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images4.png" | absolute_url }}" alt="" /></span></div>
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images5.png" | absolute_url }}" alt="" /></span></div>
<div class="4u$"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images6.png" | absolute_url }}" alt="" /></span></div>
<!-- Break -->
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images7.png" | absolute_url }}" alt="" /></span></div>
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images8.png" | absolute_url }}" alt="" /></span></div>
<div class="4u$"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images9.png" | absolute_url }}" alt="" /></span></div>
<!-- Break -->
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images10.png" | absolute_url }}" alt="" /></span></div>
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images11.png" | absolute_url }}" alt="" /></span></div>
<div class="4u$"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images12.png" | absolute_url }}" alt="" /></span></div>
<!-- Break -->
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images13.png" | absolute_url }}" alt="" /></span></div>
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images14.png" | absolute_url }}" alt="" /></span></div>
<div class="4u$"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images15.png" | absolute_url }}" alt="" /></span></div>
<!-- Break -->
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images16.png" | absolute_url }}" alt="" /></span></div>
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images17.png" | absolute_url }}" alt="" /></span></div>
<div class="4u$"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images18.png" | absolute_url }}" alt="" /></span></div>
<!-- Break -->
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images19.png" | absolute_url }}" alt="" /></span></div>
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images20.png" | absolute_url }}" alt="" /></span></div>
<div class="4u$"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images21.png" | absolute_url }}" alt="" /></span></div>
<!-- Break -->
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images22.png" | absolute_url }}" alt="" /></span></div>
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images23.png" | absolute_url }}" alt="" /></span></div>
<div class="4u$"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images24.png" | absolute_url }}" alt="" /></span></div>
<!-- Break -->
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images25.png" | absolute_url }}" alt="" /></span></div>
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images26.png" | absolute_url }}" alt="" /></span></div>
<div class="4u$"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images27.png" | absolute_url }}" alt="" /></span></div>
<!-- Break -->
<div class="4u"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images28.png" | absolute_url }}" alt="" /></span></div>
<div class="4u$"><span class="image fit"><img src="{{ "/images/Kalm/gallery/images29.png" | absolute_url }}" alt="" /></span></div>
</div>
</div>
</p></div>

<hr />


## Beginning steps

I started working my way towards a window with an image on it. I wanted to use OpenGL, so I chose to use [glfw][glfw] in my platform-layer. I didn't want to use my old platform code and wanted to start working on the actual interesting bits as fast as possible.

At this stage I was already using the doom architecture, as I like having a good high level understanding of the code while I'm working on it. This meant some tedious editing in multiple places while starting up, but didn't slow things down too much. I think it also saved me at least one refactoring cycle. Any more pre-engineering would've been too much, as I only had a vague idea of what I was doing anyway.

I built some modules: Barebones versions of the renderer, file loading and timer. What I like to do for memory management at the start of projects, is to make a simple memory stack that you can't really even free memory with (it has to be done in order). At the start of the program you allocate X amount (eg. 16Mb). You keep an assert for when you end up allocating more than you currently have, and then you increase the size again. This helps keep track of the memory usage and the code I write is already using my own memory manager, so once I actually get around to making a proper one, it won't be that difficult to integrate. As long as I actually come back and implement a proper one, I've noticed this approach works best for me to actually get started on projects. The simple stack structure also lets you do temporary buffer allocations easily and those you can still free (you know you just did the latest allocation, having no threads).

## The other beginning steps

At start I wrote my own BPM loader, only to later store that away and use [stb_image.h][stb] instead. Image loading is takes time, but is rather straightforward and hunting a lot of edge cases (not taking away from any of the libraries. There is no way I could write anything even close to those), so using a library seemed like the best idea. That's what they're there for! Later I might consider rewriting some of these parts, but that'll be with a reason (maybe just for having done them).

Now I wanted some primitives on the screen. I effectively copied some cube vertices from tutorials, made them go through my pipeline and wrote new things as they came along. This lead to some shader code, a world scene of sorts, and a bunch of math. I had never really been too serious with matrices, so this was definitely a useful step. My math library is a patchwork of different implementations from different places so it was hard to keep track of row/column majoring, matrice orders and other possible pitfalls. I'm glad I spent the time though, it's an important tool and without, it's impossible to properly learn the topics that follow from it.

Added cubes and made them move. It's what you do.

I started wanting actual models. I could use some files I had around and Blender to fix others into a format I wanted. I picked up the [tinyply][tinyply] library. After getting over the heavy C++ style it was pretty easy to get up and running. The example provided proved to be very helpful. I loaded up some Stanford models to see how I did.

<div class="box">
<p>
At this time I introduced a very subtle bug that could've easily been avoided. I had just finished testing the shader loader. After making sure it worked I quickly moved a bit of openGL code around before starting to work on the mesh loader. It took long enough to finish it and start testing it before noticing nothing was working, and of course I blamed it on the new loader.
</p><br />

<p>
This led to an 8 hour debugging session, in the course of which I managed to find around 5 bugs, but the one that started it all eluded me until the end. I had copied the glUniform code badly when moving it from the renderer to the shader side. When I wanted to upload a matrice, I thought I said <em>"Here is one matrice you don't have to transpose"</em>, but ended up saying <em>"Here is <strong>no</strong> matrice, would you transpose it"</em>. It's important to actually leave from a clean slate before starting something new.
</p> <br />

<br />
<br />

<p>
Tests might work too.
</p>
</div>

## /part1

I didn't get very far, but it's been quite lengthy already. Time to continue in the next part!
Quite opposite to the title I didn't even get to the flying part. I'll try to put together a video,
an executable and the source is already in [github][kalm_barrel_gh]. It doesn't include the libraries I use,
but they are named in the readme-file. Everything is unchanged apart from some warning-compatibility things.
You can lower the warning level in build.bat to fix that. Read through it to get an idea how to build the 
program and how it's structured. Glad settings include just the OpenGL4.3 Core for now.

If you have questions or ideas, send me an email! :)


[glfw]: http://www.glfw.org/                                                        "glfw"
[stb]: https://github.com/nothings/stb                                              "stb"
[tinyply]: https://github.com/ddiakopoulos/tinyply                                  "tinyply"
[kalm_gh]: https://github.com/schme/KalmEngine                                      "kalmengine"
[kalm_barrel_gh]: https://github.com/schme/KalmEngine/releases/tag/v0.001_barrels   "kalm_barrel_gh"
