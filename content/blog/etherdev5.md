---
author: "Gasimo"
title: "Ether Devlog 5"
date: 2024-03-14
tags: ["Ether", "Devlog"]
thumbnail: https://img.itch.zone/aW1nLzE1MzA1OTA4LnBuZw==/x150/4PxyZX.png
---

Greetings, everyone. It is that time. The time when I do the thing. The thing with the devlog!
Special thanks to my Patrons Walpar, Kyle, Pitti and Vaipu!

{{< youtube LfUehVpjm7Q >}}
# Random Signals
This was haunting the to-do list for at least 2 months now and I am happy I can finally cross it off. The game now spawns random signals (both sellable and not) so the player has means to earn credits outside of story-events.

![](https://img.itch.zone/aW1nLzE1MzA1OTAwLmpwZw==/original/mHBw3N.jpg)

# Audio Upgrade
Some sounds in the game are now taking advantage of FMOD, an audio middleware which allows me to create much more creative and realistic sounds. This allowed for following features:

     
- Advanced reverb (Especially nice in hallways and possibly caves)
- Dynamic sounds and variations (This for now involves footsteps, physics objects and random ambiance)
- Better Radio FX (Radio now has more radio-ish effects like pitch changing with tuning and different distortion profiles being applied based on modulation.)

![](https://img.itch.zone/aW1nLzE1MzA1OTAxLmpwZw==/original/nxTpHU.jpg)

# Graphics
## Volumetric Fog
Volumetric fog has now been added into Ether. We profiled in on an 1050Ti and the game performs fine above 60FPS so the fog is going to stay! This will be later integrated more tightly with the weather to create some nice spooky moods!

![](https://img.itch.zone/aW1nLzE1MzA1ODk2LmpwZw==/original/yoNIVz.jpg)

## Triplanar Mapping
Rocks and cliffs have evolved. Grass will now always render on top of them, no matter their size or rotation is, allowing for quick level development.

{{< youtube 0r2MnXv35c4 >}}

### Some smaller changes:

- Fog now renders in front of transparent objects correctly (The skybox blending with the sea is still an issue which will hopefully be resolved with next Unity update)   
- Table notification panel now has a proper model
- Email attachments are now cleared properly when changing emails   
- Downloaded email attachments are now properly treated as unique files.
- Fix lights not getting restored after blackout
- Fixed physics simulation during sleeping, objects are no longer acting silly after waking up.
- Radio volume is no longer compressed and is instead limited. This eliminates any peaking artifacts.

### Needs to be done:
- Polish ship, add better sea rendering.
- Some threats and more story events.
- Weather! Dangerous weathers!
- Hunger/sleep related debuffs.