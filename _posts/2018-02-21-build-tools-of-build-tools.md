---
layout:     post
title:      "Build tools of build tools for preparing your tool build"
date:       2018-02-21
category:   programming
tags:       [development, frameworks, workflow]
sitemap:
    priority: 0.7
    lastmod: 2018-04-05
    changefreq: weekly
excerpt: "Framework hell and finding things that work for you"
image: "/images/pic04.png"
---

## Piling them up
When I started programming, I did it with Vim and a console. I picked up Python and worked my way towards C. Html, CSS and
Javascript, all through my editor, command line and a browser. This was simple. I understood what was going on, and when I didn't it was easy to find out.
The workflow was almost identical no matter what I was doing.

Sometime after I learned about IDE's. I spent time looking for the best one and learning to use it. I learned about build tools. Make, CMake, Maven, Gradle, Travis..
Then came frameworks. Django, Spring, AngularJS, Bootstrap, Three.js. Things started to pile up. No longer had I any idea what was going on behind the scenes.
Getting a new project running became more tedious. There were multiple config files, some of which did the same thing. Some of them were in weird formats.
Things got worse when I needed to work in both Linux and Windows.

It's understandable that programmers are drawn to new technologies and new ways of doing stuff. Learning new things and finding new possibilities is
exciting and rewarding when they work and make life easier. Often they make life harder. There's a lot of new stuff out there and they aim to do different
things well. Learning about the options is valuable, but there is a drawback: It takes time. A lot of it.

## Tearing them down
What I've learned about myself is that keeping things simple between me and what I'm doing is the most effective way to get things done. I started going back
to what I used to do, keeping things as simple as possible. My builds are either makefiles (which is still relatively simple), bash scripts or batch
files. I still use Vim (Neovim to be precise). I know the compiler options and how to link stuff without turning to complicated build tools
and build tool building tools. I use git from the command line. I avoid having to use languages I can't comfortably use without an IDE. I started
getting things done again. Starting new projects was easy, I had done the same thing many times already. I started saving my own libraries
and layouts I knew I had needed before (Note: I didn't start saving things I *thought* I would need in the future. Just the ones I already had and needed again).
Cleaning your workflow and tools, especially for private projects, can be extremely beneficial. Knowing what works for you personally is empowering.

This will leave me with less experience in the new shiny things, but it doesn't matter. If I know I'll need something I can learn it *after* I know I need it.
If I can do the things I need to do without a new piece of shiny tech, I avoid it. Having a *"use a new thing"-weekend* every month or so would be a good idea. I'd have to
research the available options, it would give me cursory knowledge on interesting things and I could finally make the Trump-hair Firefox addon I've always dreamed of.
