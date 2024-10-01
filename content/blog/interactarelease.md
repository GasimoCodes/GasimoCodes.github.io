---
author: "Gasimo"
title: "Interacta Now Available On Asset Store"
date: 2024-10-01
tags: ["Asset Store", "Plugin", "Featured", "Unity"]
thumbnail: /media/img/Interacta Big.png
---

I am excited to share that **Interacta - A Screen-Center Proximity Interaction Kit** is now live on the [Asset Store](https://assetstore.unity.com/packages/tools/game-toolkits/interacta-a-screen-center-proximity-interaction-kit-273985). 


## What is Interacta?

Interacta is a game interaction framework designed to streamline object selection in your games. It automatically identifies items located at the center of the screen—specifically, interactables that players are looking at. This approach offers significant advantages over the traditional method of requiring precise alignment with a target.

The development of this system stemmed from my experiences with first-person indie games on mobile and console platforms, where pinpoint accuracy was often necessary to interact with small objects on the ground. Frustrated, I set out to create a more intuitive solution.


With screen-center proximity interaction, players can select objects simply by looking in their direction, eliminating the need to align items perfectly in the camera view. This makes gameplay more accessible and user-friendly, enhancing the overall experience. 


[Demo](https://github.com/GasimoCodes/Interacta-Public/releases) | [Documentation](https://gasimo.dev/Interacta/) | [Asset Store](https://assetstore.unity.com/packages/slug/273985)


## Backstory - Spherecast for the masses

The magic behind Interacta is made possible through SphereCasts. Unlike traditional Raycasts, which project a single ray in a specified direction and return just one collider upon hit, SphereCasts cast a sphere and can detect all objects it intersects. This capability opens up new possibilities for more intuitive interactions within games.

The idea for this system originated during my work on a school project titled *"Ječná Nightshift"*. I quickly realized the potential of SphereCasts when I saw how effectively they enabled player interactions. This initial success prompted me to integrate the system into a cross-platform multiplayer game called *"Classified Site"*, where it received overwhelmingly positive feedback from the community.

Since then, Interacta has undergone numerous iterations, evolving into a more modular and standalone package. This adaptability allows me to reuse the framework across a variety of genres, including first-person shooters (FPS), third-person shooters (TPS), and point-and-click adventures without any source code modifications.

#### Adding in interactables is as simple as implementing:
```csharp
/// <summary>
/// Called when player interacts with the object.
/// </summary>
/// <param name="player">Reference to your playerController object.</param>
public void OnInteract(T player);

/// <summary>
/// Returns the title shown when player looks at the object.
/// Run any custom logic here to determine the title. Returning null will exclude this object from showing up.
/// </summary>
/// <param name="player">Reference to the interacting playerComponent</param>
/// <returns>Title to show when looking at object</returns>
public string GetTitle(T player);
```

### Issues Inherent to SphereCasts
While SphereCasts are a powerful tool for detecting multiple objects within a defined area, they come with their own set of challenges. Since SphereCasts return all items they pass through, it’s possible that some of these items are obscured—either behind walls or other interactables. Fortunately, this issue has a straightforward solution: a simple **LineCast** can be used to check for obstructions and ensure that only visible objects are interactable.

However, the more complex issue arises when determining the point of reference for querying obstructions. The most straightforward approach would be to use the model’s pivot or bounding-box center, but this often falls short when dealing with specific objects. For example:

- Doors, where the pivot point matters for correct interaction.
- Drawers, where the center may be inside another object like a table, making interaction difficult.

These objects require a more manual approach to ensure that the right interaction point is used. To address this, I’ve included a system in Interacta that allows developers to easily override both the hint display position and occlusion check point. This system is non-destructive and simple to implement, ensuring accurate interactions without the need to alter your models or hiearchy.

You can read more about the features of Interacta over at the [Asset Store](https://assetstore.unity.com/packages/slug/273985) page and soon on Epic's FAB Store.


### Are SphereCasts here to stay?

I hope so! I believe that Interacta (and the SphereCast interaction methodology in general) will gradually phase out traditional Raycast-based systems often found in indie games. This shift will save developers and players alike from the frustration of struggling to interact with objects or manually setting up colliders.
