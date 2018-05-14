---
layout:     post
title:      "My first 3D flights"
date:       2018-05-14
category:   Game engine, opengl, computer graphics
tags:       [game engine, opengl, computer graphics]
sitemap:
    priority: 0.7
    lastmod: 2018-05-14
    changefreq: weekly
excerpt: "Building a game engine, thoughts and pictures!"
image: "/images/Kalm/intro.png"
---

## Preface
I've been making my first game engine and now that I have something to show for it, it's time for a writeup. I managed to enter closer to this century and I know there's going to be a lot of engine side coding ahead of me, which won't really advance the graphical output at least in a direct way, so I thought now would be a good time to write a small recap on what I thought about and have done so far. 

## The Dreams
I wanted to make create a sort of playtool for Lua. I didn't however want to write a Lua library per se, but an engine for creating games with Lua so that Lua lives inside the engine, not the other way around. I was thinking about a 2D engine, because I hadn't really built either and new some of the parts would be reusable and possibly integrateable. 

I thought of Unitys object-component model. Basic audioplayback with either Windows or an audio library. The very high level abstraction I copied from idTech, the Quake and Doom engines. You basically have a core engine and the system-interacting parts in the executable, eg. rendering, audio, file i/o, memory and timers. On a dll you put more of the scripting side, preferences, and assets in a usable form. First thing you do when you load the game you pass pointers from one to the other, so they can talk to each other freely through an abstracted API. Some parts might have one part living in the other side, making relevant communication easier. 

The compilation style I went for was to just have those two objects (unless it's convenient, for example tinyply and glad which won't change too often. I can just manually remake the objects if I nede to.) compiled, other relevant code being straight *included* to the base object or some logical manager class. For example my **MemoryStack** class is included straight in the **Memory Manager**.

This was more or less what I had in mind before I started coding.

## The first steps
I started working my way towards a window with a loaded image drawn on it. I wanted to use OpenGL, so I chose to integrate [glfw][glfw] in my platform-layer abstraction. I didn't want to use my old platform code and wanted to start working on the actual interesting bits as fast as possible.

At this stage I was already following the doom architecture, as I like to have a good high level understanding of the project I'm working on. This did mean some tedious editing in multiple places while starting up, but didn't slow things down too much. I think it also saved me at least one refactoring cycle. Any more pre-engineering would've been too much, as I did only have a vague idea of what I was doing.

I built some submodules: Fledling versions of the renderer, file loading and timer. What I like to do for memory management at the start of projects, is to make a simple memory stack that you can't really even free memory with (it has to be done in order, and I rarely keep track of it). At the start of the program you allocate X amount (like 16Mb). You keep an assert for if you end up allocating more than you currently have, and then you increase the size again. This helps me keep track of the memory usage and the code I write is already using my own memory manager, so once I actually get around to making a proper one, it won't be a big deal. The simple stack structure also lets you do temporary buffer allocations easily and those you can still free (because you know you were the latest allocation, having no threads).

## First pictures
![First texture load][img1]

At start I wrote my own BPM loader, only to later store that away and use [stb_image.h][stb]. Image loading is a part that takes time, but is rather straightforward, so using a library seemed like the best idea.


[img1]: /images/Kalm/texture_load1.png      "Kalm2D First Texture Load"

[glfw]: http://www.glfw.org/                "glfw"
[stb]: https://github.com/nothings/stb      "stb"
