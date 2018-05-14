---
layout:     post
title:      "The possibilities of a fledling engine"
date:       2018-05-14
category:   Computer graphics, demotools, renderer
tags:       [computer graphics, demotools, game engine, renderer ]
sitemap:
    priority: 0.7
    lastmod: 2018-05-14
    changefreq: weekly
excerpt: "Diverting from game engines, the resemblance to other tools and reusability"
image: "/images/pic05.png"
---

## Recap
I started writing my first game engine and got it to a decent stage, enough so that I can take a bit of a break. That is, I've made something I've never made before. After I've finished with a new asset system, I basically have a few extra choices on where to go with it, in addition to just working on a game engine. 

It will then have a way to load assets (3d models with PLY, some way to load scenes hopefully and a way to push those rather seamlessly into the renderer), a way to link shaders together and attach them to certain render groups, transformations, a camera and other basic rendering modules. Scenes, objects with child objects, and components associated with the objects. I will link a post with a more thorough recap once I finish writing it.

## The dreams
From this setup, I could keep on focusing on the game engine: maybe add physics (I would like to use PhysX in the future, but doing something on my own first will be helpful), improve controls and do some world interaction. This would involve working on the scripting engine and console. I could also focus even more heavily on graphics and divert to the offline rendering side. Third, I could go more of a world editor route, possibly integrated in the game engine. The fourth option is likewise divisible to two followup ones: create a demotool, and create a demotool inside a game.

## Demotool
Making a demo has long been a goal of mine, so I see this option as very intriguing. The key difference between a demotool inside a game and an actual demotool would revolve around time management and audio handling. In a demotool the sound controls the demo, on a game demo tool you would want to control the sound from the demo. The game tool would probably lack a synthesizer, unless I want to write one into the actual engine. Game engine tool would lose some of the graphics quality, and thus have to rely on simpler solutions, but would also be more lax in the hard technical requirements. This could be associated somehow with an offline rendering tool. All things considered, making an actual demotool does sound more fun.

I found an awesome [video][demotool_video] that goes into more detail in the workings of a demotool. Tons of stuff is translateable to game engines, which he remarks about in the video too. There's more of this stuff around, if you're interested and I highly recommend looking them up (you can start by checking his other Assembly presentations). I really liked the level of detail and abstraction he uses, and will be taking tips from these no matter if I will end up writing a demotool or not.

## Offline Rendering
Leaving the time constraint out lets you use a couple of more tricks that let you increase the image quality. I love raytracer projects, and making pretty pictures has always been fun to me. Physically based rendering is definitely something I'm keen on exploring. I'd imagine this part would also involve learning a bit more 3D modeling to get something uniqueish out of Blender into the actual engine.

This said, I feel this route would probably be premature. I've still tons of things to learn in real-time rendering, and those skills I can use in the offline world too. It wouldn't work the other way around. The way to link the real-time and offline renderer together, to avoid too much code duplication would require a lot of architecturing to make right, an area where I'm already hands full with OpenGL and the real-time renderer itself (this will get easier with a proper asset system).

#World/Game editor
Having an editor of some sorts will be a must at some point and I like the idea of building it in the engine itself. Another option I've been considering is to make the engine as compatible with Blender as possible. This would mean being able to create scenes and materials in Blender, load them in and then use the games scripting engine to manipulate the scene. This would be less coding for me, but then again I wouldn't have written an editor, and it could end up being an equal amount of work!

## Any Of The Choices
I will definitely be keeping an eye on features and design ideas that benefits as many of these as possible. It works as a good extra fitler, where there seems to be many design choices I don't really have a good grasp on, or know what's better and why. This might end up being premature considering I've never done a demo, a world editor or much at all offline rendering. I might be wrong in my assumptions, but the parts that I'm correct about will be all the more useful for it, I hope. I might aswell try and see if I can make it happen!

A good way to manage and create scenes is something that I will need sooner rather than later, and will be helpful in each of the cases. However, doing this right after finishing the asset system would leave me a long time without any visual improvement, and I might like to add some graphical flare first to give some some sense of improvement over time.

Starting with basic subsystems and rendering seems to have been a good option either way, as the code base will be usable either by forking or directly implementing the new stuff. Now all I need to make the asset flow be good enough to actually warrant reuse! 

[demotool_video]: https://www.youtube.com/watch?v=TbcZyAO6K7c    "Demotool video"
