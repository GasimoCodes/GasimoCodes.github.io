---
author: "Gasimo"
title: "Ether Devlog 1"
date: 2023-10-04
tags: ["Ether", "Devlog"]
thumbnail: https://img.itch.zone/aW1nLzE0NjM4MDE2LnBuZw==/original/AaIhU%2B.png
---

Heya everyone!

Its time to update you a bit on progress I made on Ether since last update. This is my first week at the university and the math is rather taxing so excuse the next devlog being shorter or delayed.

Ive managed to create a pretty fast and extendable event system for the game, which allows me to run various in-game events based on day, current time or even to schedule events randomly based on criteria for some replay value!

A basic day/night lighting has been added to make the currently plain exterior a bit prettier to look at! (Night lighting is not presentable yet because fog color does not get affected by night lighting yet. I will research this soon.

![](https://img.itch.zone/aW1nLzE0NjM4MDE1LnBuZw==/original/LAvA6G.png)
![](https://img.itch.zone/aW1nLzE0NjM4MDE3LnBuZw==/original/3X8804.png)

I have added the ability to download signals and upload them to the IMC, who will in return send you an email feedback about the signal (And possibly reward you with some credit points!) (Also note the notification popup, thats new!)

![](https://img.itch.zone/aW1nLzE0NjM4MDE4LnBuZw==/original/B5hbQJ.png)

To not make things easy, I have added a system which can mark the radio tower or uplink as NOT WORKING, which has an impact to info which gets presented to the player using the PC. (The status of Tower and Uplink are shown in SatInsight as of now)

![](https://img.itch.zone/aW1nLzE0NjM4MDE5LnBuZw==/original/etwq9x.png)

In the game, you need to take care of your energy (stamina) and food. With this devlog I have created a sleeping system prototype which seems to work just-fine(tm) so far. The implementation was a little tricky since while players sleep, I need to simulate the world going on 30x faster than real-time. I have managed to optimize some code but the biggest compute save was by severely limiting physics calculations during sleep. This is likely a temporary solution, as this approach would make any AI NPCs very unstable.

Also as a side note, the boat mechanics got a proof-of-concept prototype which isnt worth showing here at all at its current stage.


What am I going to work on soon:
- Ability to preview all downloaded media
- Shop system where you buy upgrades / items
- Misc polish on some pc/map stuffs

What needs to be done:
- General polish of everything
- All the graphical assets + more populated and nice-looking demo map.
- Hunger related mechanics + lack of sleep debuff
- Weather, Extreme weather events + Ability to see weather on Radar
- Shop system where you buy upgrades / items
- The actual events, signals and anomalies/threats which can be found/happen
- All the other stuff which I annually forget to list