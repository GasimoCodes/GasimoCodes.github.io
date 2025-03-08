---
author: "Gasimo"
title: "CineBlend Alpha Release: Virtual Camera System for FlaxEngine"
date: 2025-03-08
tags: ["FlaxEngine", "CineBlend", "Featured"]
thumbnail: /media/img/CineblendWide.png
---
{{< youtube bhDjrhjGJCI >}}


I'm excited to announce the alpha release of [CineBlend](https://gasimo.dev/CineBlend/), an advanced virtual camera system for [FlaxEngine](https://flaxengine.com/)! After months of development and using it in our own game production, we're making it available to the Flax community.

## What are Virtual Cameras?

If you've ever struggled with camera controls in your games or interactive applications, virtual camera systems offer an elegant solution. 

Virtual cameras exist in your scene but don't directly render anything. Instead, they act as proxies that define their own properties and behaviour. Cineblend then blends and applies these behaviours onto the physical scene camera.

This separation creates a powerful workflow: you can place multiple camera setups driven by separate gameplay systems throughout your scene and smoothly transition between them without complex animation or code. Switching driving camera to first person view, adding a cinematic sequence forcing the player to look at something, adding camera shakes...

## Introducing CineBlend

CineBlend brings this powerful workflow to FlaxEngine, inspired by successful systems like Unity's [Cinemachine](https://unity.com/features/cinemachine). It's designed to give developers and artists fine-grained control over camera movements while maintaining an intuitive workflow. It comes packed with simple to use but powerful modules and tools for artists and developers and programmers alike.


#### Virtual Cameras
CineBlend introduces a priority-based virtual camera system that seamlessly integrates with FlaxEngine. Cameras with higher priority automatically become active, while the soloing function lets you temporarily override this for testing specific shots. The system works directly in the editor, allowing you to preview camera blends without entering Play Mode.

#### Modules
Enhance your cameras with non-destructive, stackable effects through our module system. Add natural camera shake, automatic target tracking with Look At, intelligent Auto-Framing to keep subjects on screen, and collision prevention with the Collider module... Effects can be stacked to create complex camera behaviors with ease.

#### Transitions
Create cinematic camera movements with smooth transitions between every camera property. CineBlend handles position, rotation, field of view, and even near/far planes with customizable easing and duration settings. Transitions can be triggered automatically or through our extensive API.

#### Developer Friendly
CineBlend is built with extensibility in mind, using a clean interface-driven architecture that makes it easy to add your own camera modules or even whole virtual cameras. Cineblend also comes with Large World Support, meaning it can support FlaxEngine's 64bit mode.


## Early Development - Your Feedback Matters

CineBlend is currently in alpha, which means we're actively developing and refining the system. While it's primarily shaped for our internal production needs, we welcome suggestions, feedback or PRs! 

If you'd like to see CineBlend become an official part of the Flax ecosystem, please share the [repository](https://github.com/GasimoCodes/CineBlend) and show your support.

Check out CineBlend on [GitHub](https://github.com/GasimoCodes/CineBlend) and explore our [documentation](https://gasimo.dev/CineBlend/) to get started!

---

*CineBlend is in early alpha - API may be subject to change.*