---
layout:     post
title:      "A Monkey's Head"
date:       2018-04-04
category:   Computer graphics
tags:       [computer graphics, kodelife, handmade hero, handmade network, shadertoy]
sitemap:
    priority: 0.7
    lastmod: 2018-04-04
    changefreq: weekly
excerpt: "The discovery of Kodelife and a floating monkey's head. The head of a monkey. Suzanne. She has a name."
image: "/images/pic02.png"
---

## Tracing a ray
Way back I made an offline raytracer and absolutely loved it. Making pretty things with applied math was
extremely fun. As a base for it I reused my previous project's (Pong clone) windows platform code, where I had done everything from
scratch, starting from getting a window running in Windows. Handmade Hero style (the similarities are still
pretty [obvious](https://github.com/schme/KoomGL/blob/master/src/win_platform.cpp).

<figure class="image right">
    <img src="https://i.imgur.com/Wn2w2GA.png" alt="" />
    <figcaption>The final picture in a <a href="https://imgur.com/a/WPOrt/">series</a> I took while working on the Raytracer.</figcaption>
</figure>

Doing all that in the CPU by yourself gives a pretty good base understanding of the math going on in graphics programming.
It is no wonder that raytracers are often the first textbook project, it certainly felt very effective.
I did all the calculations and scene defining in C++, then output a PPM file. Pretty simple. But it worked, and I learned
a huge amount! You don't get to know much about shaders or the real-time aspects or how to exactly interact with the GPU
(although you could do a shader raytracer just as well), but you also don't **need** to know those, which lets you avoid quite a bit of
boilerplate and distraction from the actual graphics.

## Enter Kodelife

The project coupled with some research left me with a decent idea about what graphics programming was about. It was time to move on to
shaders and realtime graphics. In my [pong clone](https://www.youtube.com/watch?v=GmkdIcI93SM&t=4s) I had some clunky
shaders and I wrote the OpenGL in C++ with the [glm](https://glm.g-truc.net/0.9.8/index.html) library, giving me some idea about what
was happening. What I started yearning for was a way to play around with just shaders. A [shadertoy](https://www.shadertoy.com) if you will,
but native so it would run a bit smoother. I found [Kodelife](https://hexler.net/software/kodelife).

<figure class="image left">
    <img src="https://hexler.net/gfx/_software/kodelife-screens-06.png" alt="Kodelife" />
    <figcaption>Image from the Kodelife website</figcaption>
</figure>

Kodelife is a live coding platform and real-time shader editor, which was exactly what I wanted. And better! You have access to all the
shader types and the basic inputs you want on by default. You can import your music and whatever textures you have and they just work.
The audio input is coupled with low, mid and high gain sliders you can access through a vec3. It even has a template that changes all the variables
similar to Shadertoy, which allows you to copy-paste pretty much any shadertoy shader and it just works. I set off to try it out and create some
visuals. I setup my music input/output with Virtual Audio Cable so that I could play stuff from Spotify and have the output go to Kodelife,
not having to worry about importing stuff all the time. I could just listen to music while playing around with the code.

## The lack of Tai Chi and a Monkey

I had an idea about using a tai chi video and combine that with other effects. Tai chi has always been pleasing to me, so I figured it could work
in a music visual. Unfortunately Kodelife v0.5.3.1 doesn't support video importing yet (it's in the Mac version however and
should be implemented fairly quickly in Windows). That wrecked my plan, but I decided to go forward with the idea anyway and see where I land.

<span class="image right"><img src="{{ "/images/pic03.png" | absolute_url }}" alt="Edge detection" style="width: 320px;"/></span>

First thing I probably want some form of edge detection, which I hadn't done before. After some research I made a [test](https://www.shadertoy.com/view/XsVyWW)
in Shadertoy. It worked! Playing around with the edge color and how much of the original image you keep in the final result creates some fun effects.
In Kodelife I couldn't use a video, so I started playing with 3D perspective and the readily available Suzanne monkey. I gave her some shading, a lamp
and a bit of movement so she doesn't have to stare at one place all the time. I created a new shader pass and put my edge detection in. After some fiddling
I found a nice little effect. Doing a linear interpolation from the original color to the edge color created a transformation from the chill purple monkey
to a photo negative devil from another dimension. It was beautiful!

I set the linear interpolation to be proportional with music and added some ray marched fractal circles to the background for a spacey feel to finish up the end result.

<figure class="image">
    <a href="http://www.youtube.com/watch?feature=player_embedded&v=FNkV6vaQMEk" target="_blank">
    <img src="http://img.youtube.com/vi/FNkV6vaQMEk/0.jpg" alt="Video showcase" border="10" />
    </a>
</figure>


## From here

What there is left to do is explore some other edge detection methods and see how they compare in different situations. Then to actually use the
detection for something else than coloring edges e.g. cutting out the moving silhouette (I still don't know if this is a viable approach for it).
All in all I'm not sorry at all for not being able to explore that avenue yet, because this turned out a fun and educational journey in itself.
