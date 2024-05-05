---
author: "Gasimo"
title: "Ether Devlog 6"
date: 2024-05-01
tags: ["Ether", "Devlog"]
thumbnail: https://img.itch.zone/aW1nLzE1OTgwMDYwLnBuZw==/x150/Z%2BmNM8.png
---

Hello everyone! Its the monthly Devlog time! This time focusing on gameplay, brought to you by our Patrons **Walpar**, **Pitti**, **Kyle** and **Vaipu**.

<iframe width="560" height="315" src="https://www.youtube.com/embed/nmg5ofF8D1o" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Spawners
I have implemented a system which allows me to randomly spawn objects on the land or sea and align them automatically with the surface. This will be soon used to spawn **events** and **beacons**, some of which will be visible from the SatMap.

![enter image description here](https://media.discordapp.net/attachments/789582276749033502/1235223742293217401/Editor34-ezgif.com-video-to-gif-converter.gif?ex=66339741&is=663245c1&hm=484d6d27c9e409aef75dde8a2332db31bb61e94cb0aae90c32740a408de6ffb0&=)

### SatMap
SatInsight now shows real-time and accurate **clouds** overlay, so you'll be able to see a rainstorm approach you.

![enter image description here](https://media.discordapp.net/attachments/789582276749033502/1235223742993399848/Editor35-ezgif.com-video-to-gif-converter.gif?ex=66339741&is=663245c1&hm=583abac9e820078b11ebbe3379cffc7ac7f2dc28aa61bc2e84e030e2dfdd5713&=)

Limited version of SatMap is now available on the go by using the PDA (Tab menu). As of now it shows only the SatMap preview and a compass. No device/beacon tracking or EMF info.


### Hiding
Player now has the ability to **hide inside lockers**. I am sure this won't cause any paranoia and the mechanic is not suspicious whatsoever.

![enter image description here](https://media.discordapp.net/attachments/789582276749033502/1235224541014265900/Image_Sequence_031_0005.jpg?ex=663397ff&is=6632467f&hm=516ee8d6c40e49d512c6e95a19c3861c23b46953df701ca558939a6b2cee1a6b&=&format=webp&width=1340&height=754)


### Food

You can now eat food. Yes, this is the **food update**. There is no benefit to eating food yet.

### Worldbuilding

We have managed to lay (write) down a solid foundation for worldbuilding. Thanks to **Seth** (and his impeccable writing), we now have a bunch of lore and ideas for the first few threats/anomalies we will put into the game. 


### Graphics
The previous versions appeared a little too dim so I have increased lighting intensity to compensate for it.

On top of that I have created a vegetation model for **cotton weed**, a plant commonly found in northern mountain regions. I think its whiteness breaks the monotone look of the grass. More vegetation models pending.

![enter image description here](https://media.discordapp.net/attachments/789582276749033502/1235224541849059389/Image_Sequence_029_0005.jpg?ex=66339800&is=66324680&hm=1d1a6727606ab28644785f640c5010469d17b2d5f6ed7a7edacc15965b76c5c3&=&format=webp&width=1340&height=754)

*I should also mention the new Radar model, yes we have that too!*


### Cave
Speaking of paranoia, the bunker now has a second enterance: **a cave which connects various points of interest across the island**.  A cave which is super-ultra safe to traverse and is totally not a possible enterance for threats.

![enter image description here](https://media.discordapp.net/attachments/789582276749033502/1235224541412855879/Image_Sequence_030_0005.jpg?ex=66339800&is=66324680&hm=5df94b3ebeff2a9f59f2badbd0fe790353c805738841b73a1513f7769eb1e9cc&=&format=webp&width=1340&height=754)

### Weather
To liven up the world further, I have added weather sounds for wind/rain which changes dynamically depending on whether you are indoors or outdoors.
Rain particles are WIP and will probably arrive in next devlog.

### Smaller changes:
- Exterior Global Illumination is now baked, resulting in non-black shadows anf AO which looks much nicer. Time of day related corrections will come much later.
- More details models, textures and decals added
- New footstep sounds for water
- Monitors are now affected by fog.
- Fixed invalid AABB bug for reflection probes
- Wind now has different sound variants for exterior and interior
- Items grabbing no longer causes the object to become a rocket and fly far away behind you. 
- Dynamic beacons now properly spawn on SatMap.
- Some terrain textures were refreshed.
- Improved sea rendering for day/night scenarios.

### Needs to be done:
- Implement some of the threats and story events
- Polish ship
- Make dynamic fog alongside weather events.
- Player lost in fog event.