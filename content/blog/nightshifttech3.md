---
author: "Gasimo"
title: "Tech behind Ječná Part 2: Environment"
date: 2023-11-11
tags: ["Nightshift", "Tech"]
thumbnail: https://img.itch.zone/aW1nLzEzODgzODIwLnBuZw==/original/FkaLuc.png
---
Heya everyone! It's time for a healthy dose of tech talk, where I rant about how I developed Nightshift. This time we are looking at the graphics, environment, and optimization efforts in Nightshift (This will not cover ray-tracing as that was more of an experiment than a feature, and is currently not even performant enough to be considered usable). 

## Lighting

![](https://img.itch.zone/aW1nLzEzODgzODIwLnBuZw==/original/FkaLuc.png)

Ječná Nightshift environment is lit by various artificial lights ranging from hallway lamps, monitors, and flashlight down to table lamps. However, having them all rendered at once would be a performance killer. I needed to create a system which is 
<br>
A: Performant (enough)
<br>
B: Dynamic (I can still do blackouts)

### Switching to APVs
In early development, I partially solved this issue by traditionally baking lights into textures and Light Probes. The blackouts were then accomplished using a custom shader with a GI contribution attribute. Later in development, I discovered this [Unity GDC talk](https://www.youtube.com/watch?v=iU7X5xICkc8) about **Adaptive Probe Volumes** and I tried them out ASAP. The performance was the same, the results were better and Nightshift was several hundred MBs lighter! It even gets rid of Lightmap UVs and overlap. I advise all future devs in 3D to look into this new approach.

### Blackouts 2nd try
I still really disliked the shader-based blackout approach. I later discovered that High Definition Render Pipeline (HDRP), the rendering pipeline powering Nightshift, offers a cleaner solution through API-managed render passes. This allowed my to skip all GI rendering altogether when blackout occurs. 
There however was one more code crime hidden in my blackout code: The dynamic lighting and electrical components in the game initially queried for blackout every frame (yuck!). Although this didn't have a noticeable performance impact at all, it made me feel bad as a programmer. I later redesigned it to subscribe to BlackoutManager's **OnBlackout()** and **OnRestore() C# events** instead.

### Volumetrics!
![](https://img.itch.zone/aW1nLzEzOTg5ODM3LmpwZw==/original/UIrG8%2B.jpg)
I am obsessed with volumetric effects. However, Volumetrics are costly, especially for dynamic lights which move or cast shadows! Nightshift initially did not have any proper volumetrics and faked the flashlight cone using geometry with the awesome Tech Salad's [fake volumetrics shader](https://assetstore.unity.com/packages/vfx/shaders/volumetric-light-beam-99888) Later in development it became apparent that Nightshift had rendering performance to spare, so I added in proper volumetrics for non-moving objects (like hallway lights) as part of a toggleable setting and kept the faked volumetrics for the flashlight.


## Room Occlusion

Nightshift employs three occlusion techniques to figure out what to render at any given time. The basic ones are Unity's **Frustrum Culling** (Don't render what isn't in the camera frustum) and **Occlusion Culling** (Don't render what's behind walls). The latter, however, proved to not be precise at all, and so I came up with a quick and simple custom solution: 

The map is divided into rooms and floors. Each room/floor is culled based on where the player currently is. This is tracked by setting 4 colliders for each room in the following configuration:

![](https://img.itch.zone/aW1nLzEzODgzODQwLnBuZw==/original/3WpBDH.png)
**Ply leave - Ply Enter - (Room/Floor) - Ply Enter - Ply Leave** 

When the player enters the room trigger, we need to know when they leave. The player leaves by walking past the room into the (second trigger leave), or by walking backward and triggering the (first trigger leave). This also prevents the player from spamming load/unload calls too fast by dancing around a single trigger and allows for very granular control of loading areas. There are probably better ways to do this, but this turned out to be enough.


## Making sound spookier
The ambiance loops soon became repetitive and boring. It was time to spice them up somehow. Horror games like Regalis's [SCP Containment Breach](https://www.scpcbgame.com/) accomplish this by playing randomized audio cues during gameplay, and to crank up the spook factor, they are played in 3D (When a player moves their head, they can tell the sound is coming from a direction). I do this by having an array of audio clips that I shuffle and then play one by one at random intervals. Every time I play a sound, I have it spawn somewhere in a **min-max proximity to the player** (using the [OnUnitSphere](https://docs.unity3d.com/ScriptReference/Random-onUnitSphere.html) method). This worked wonders on the play-testers, who were **200% more paranoid** during the playthrough (especially with the door open sound).

## Assets / Software
Operating on a constrained budget, Nightshift blends outsourced AssetStore assets with handmade ones. The asset creation process involves Blender for models, Substance Painter for textures, Krita/Illustrator for drawings/Illustrations, Presonus Studio One 5 for audio, and Hitfilm Pro 16 for video editing.
 
![](https://img.itch.zone/aW1nLzEzODgzNzk5LnBuZw==/original/A37WHg.png)

### Sacrifices
Some had to be made. For example, the Ječná map is not even remotely as authentic as I would have wanted it to be. The amount of classrooms has been reduced to allow for better gameplay and many models were outsourced to satisfy time and budget constraints. I was also worried that making things directly linked to a real-world location may bring legal issues, forcing me to redo the thing all over again. I however believe that I struck a fine middle ground of authenticity, vibe, and gameplay. Who knows, maybe this project will catch on and I will have time to polish some things out!


This should conclude some of the less boring curiosities of environment development. Thank you for reading and see in in the next rant!