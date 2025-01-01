---
author: "Gasimo"
title: "Ether Devlog 9 - EMF, Camera & Vegetation"
date: 2025-01-01
tags: ["Ether", "Devlog", "Featured"]
thumbnail: /blog/dev9.png
---


{{< youtube IQErf2T90T8 >}}

Hello everyone and happy new year! Its been a while! There were some major changes to the backend (like a whole change of rendering engine, many shaders and a map streaming...). Those changes weren't visual so I didn't have enough to show to warrant its own backlog... until now!

## The Sea update

Anything sea related was completely reworked. The rendering backend was changed to allow for more dynamic waves and body-water interactions. Fog now also properly renders on top of the sea.

Ship received a much deserved upgrade with a new model and much better driving system (which now sways with waves dynamically and behaves like a ship). Player also now properly moves with the ship and waves while standing on it.

Player now has the ability to swim underwater. This allows for greater immersion and some sea-recovery mechanics down the line.

## World

There were huge changes to the map behind the scenes made in october but nothing which could be showcased in its own devlog. The terrain was made more diverse and few smaller islands were added. Thanks to a new system I migrated to, making terrains going onward will be considerably faster and easier.

A world-streaming system is now used to splice the world into chunks which can be streamed dynamically. This should help the game scale and to run on slower computers and HDDs.


## Signals:

6 more signals were added into the radio and 4 more are to be recorded. Added a mechanic where some events can only be triggered after you reach a certain amount of signals sent to IMC.

Also Ether is now integrated with Steam and has its own (private) steam page! Whoahoo! Patrons with the early access/testing perk can join the playtest and play the WIP version of the game from the devlog.

## The non-exhaustive list of other minor changes:

### Added:
- Patron names hidden in-game
- Discord Rich Presence integration
- Steamworks API for stat tracking
- Ambient sounds for vegetation and metal creaks
- Added Buoy names from last poll
- Map Streaming
- New boat model
- Sea system
- Swimming + Underwater rendering
- Added 6 new signals
- Added story progression system where events can be spawned depending on how far you progressed in your duties.

### Improvements:
- Sea render distance greatly improved
- Sun movement improved to be smoother and be more location-accurate (path).
- Fog now renders properly on top of the sea
- Boat UI was slightly polished
- Boat driving system was redone. Boat now interacts with sea more.
- Player moving on top of physics platforms now properly moves with them
- Subtitles are now more readable
- Tips added to loading screen
- Shaders were replaced with more optimized ones, this is especially noticeable with vegetation ovedraw.
- GI was fixed for many of the new shaders.
- Rendering backend was changed to a more recent one due to obsolete bugs which Unity refuses to fix. This will for now negate the performance improvements yielded by the shaders and partially map streaming but should be more future-proof.

### Bugfixes:
- While crouched and holding shift, the player would jitter between crouching and running. This is no longer the case and player transitions to running state as expected.
- Sleep status no longer gets reset to 0% after reaching 100%
- Opening and closing an app on the in-game PC sometimes prevents further clicks on the interface. This was fixed.
- Emails are now openable on the Steam version.
- Ship now displays the correct exit keybind prompt while driving.
- Lens flares now have correct position on screen on non-100% resolution scaling.
- Global Illumination should now properly affect more objects.
- Sea caustics now render as expected again
- Missing MainTex_ exception related to footsteps should be much less common.
- The game no longer crashes while sleeping. This was fixed by manually updating buoancy calculations on time separated from scaled sleeping time. 
- More vegetation should be shaded correctly and not dark. Partially related to the GI fixes.
- GI now works with world-streaming.