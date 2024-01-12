---
author: "Gasimo"
title: "Tech behind Ječná Part 1: Interaction System"
date: 2023-11-04
tags: ["Nightshift", "Tech"]
thumbnail: https://img.itch.zone/aW1nLzEzOTI4NzYxLmdpZg==/original/MihOtF.gif
---

Greetings everyone! Its time for some Gasimo Tech Tips, where I rant about some of the systems I have developed for Nightshift (some are open-sourced over at my github!). This one focuses on the interaction framework.

## Interaction System
![](https://img.itch.zone/aW1nLzEzOTEzNzg5LmdpZg==/original/X%2BWiga.gif)
This is one of the first components I have developed for Nightshift back in the day where it was just a demonstration student project. I wanted to get rid of the commonly used raycast-based system, which plagues the majority of first person indie horror games. The raycast system relies on players looking pixel perfect at the item they want to interact with, which can be really difficult when it comes to small objects like keys and twice as difficult when using gamepads! My system instead only requires the player to look in the approximate direction of the object and it chooses the object automatically (like the big boy AAA games often do). But how does this work?


### Selection using Spherecasting

My system ditches raycasts for detection altogether and instead takes advantage of **spherecasts** (shooting a "sphere" shaped collider in the direction the player is looking at, registering every interactable which comes in its way). 

```csharp
    RaycastHit[] hits;  
    hits = Physics.SphereCastAll(mainCam.gameObject.transform.position, discoveryRadius, mainCam.transform.forward, interactRange, InteractMask);
```

Then follows a step by step process (each of the steps includes an early exit if no interactable remains):

 1. I check each of the objects for scripts which implement my **IInteractable** interface, based on that I filter out invalid objects (more on that later).
 2. Since Spherecasting can select items behind walls, I perform a **LineCast** pass from camera to each of the object's center (For greater precision, the newer iteration of this system does this for each corner of the mesh bounding box too) and I remove objects where the LineCast fails (= there is something between the player and the object).
 3. For each remaining object, I translate its world coordinates into screen space coordinates (the equations are available online) and I compare its value from screen center through Manthattan Distance. Then I just select the object which is closest to the screen center and display the interaction popup! Tadaa!

###  Quick note on Interfaces
 To make sure the system is modular and easy to scale, I took advantage of **Interfaces**. Defining common interaction types in Interfaces (IInteractable, IInventorySelector etc.) allows me to rapidly create new interactable objects in an object oriented way (just as our unnamed object-obsessed lord intended). If you ever create interaction system for any kind of game, definitely take advantage of this! 
  
```csharp
namespace Gasimo.Gameplay  
    {  
	    interface IInteractable  
	    {  
		    // When player interacts with object  
		    public  void OnInteract(FirstPersonController pc);  
	      
		    // Return empty if you want object to not show up as interactable for a certain condition  
		    public  string GetTitle(FirstPersonController pc);  
	      
	    }  
    }
```