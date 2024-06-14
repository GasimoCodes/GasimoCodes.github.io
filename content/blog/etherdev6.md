---
author: "Gasimo"
title: "Ether Devlog 6"
date: 2024-05-01
tags: ["Ether", "Devlog"]
thumbnail: https://img.itch.zone/aW1nLzE1OTgwMDYwLnBuZw==/x150/Z%2BmNM8.png
---

Hello everyone! Its the monthly Devlog time! This time focusing on gameplay, brought to you by our Patrons **Walpar**, **Pitti**, **Kyle** and **Vaipu**. ([Original Post with animated pictures available here](https://www.patreon.com/posts/ether-devlog-6-103412385))

{{< youtube nmg5ofF8D1o >}}


### Spawners
I have implemented a system which allows me to randomly spawn objects on the land or sea and align them automatically with the surface. This will be soon used to spawn **events** and **beacons**, some of which will be visible from the SatMap.


### SatMap
SatInsight now shows real-time and accurate **clouds** overlay, so you'll be able to see a rainstorm approach you.


Limited version of SatMap is now available on the go by using the PDA (Tab menu). As of now it shows only the SatMap preview and a compass. No device/beacon tracking or EMF info.


### Hiding
Player now has the ability to **hide inside lockers**. I am sure this won't cause any paranoia and the mechanic is not suspicious whatsoever.



### Food

You can now eat food. Yes, this is the **food update**. There is no benefit to eating food yet.

### Worldbuilding

We have managed to lay (write) down a solid foundation for worldbuilding. Thanks to **Seth** (and his impeccable writing), we now have a bunch of lore and ideas for the first few threats/anomalies we will put into the game. 


### Graphics
The previous versions appeared a little too dim so I have increased lighting intensity to compensate for it.

On top of that I have created a vegetation model for **cotton weed**, a plant commonly found in northern mountain regions. I think its whiteness breaks the monotone look of the grass. More vegetation models pending.


*I should also mention the new Radar model, yes we have that too!*


### Cave
Speaking of paranoia, the bunker now has a second enterance: **a cave which connects various points of interest across the island**.  A cave which is super-ultra safe to traverse and is totally not a possible enterance for threats.


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