---
title: "Blog 2: Weapon Sound effects"
description: ""
date: 2025-11-12T16:50:29-08:00
image: 
math: 
toc: true
license: false
hidden: false
comments: true
keywords: []
draft: false
---

In this sprint, I added sound effects to a few weapons so they sound more natural and engaging when being used. I've been collecting a fair amount of soundpacks from [Ovani](https://ovanisound.com/) whenever they release a bundle to Humble Bundle, but haven't had a chance to use many of them yet. I find they're pretty high quality so thought might as well give some of them a spin in this project! 

Even though I used these premade sound effects, I still need to create the behavior of when to trigger the effect which is largely what this sprint has tackled.

## Sword Sound Behavior

Last sprint, I created a sword item the player can pick up and swing to attack some placeholder characters. This time, I added some whoosh sounds whenever the player swings the sword, and a clang sound when it makes content with a surface. However, I also added a `BP_ImpactSoundComponent` that I can use to change the sound when the sword slices through other objects. Using this, I can make the sword sound more like it's hacking through flesh when slicing other characters.

{{< video
    src="/blog/CAGD373/Sword Sounds.webm" >}}

## Bow Sound Behavior

I also added some sound to the bow weapon from last sprint. There are sounds when the player draws the bow, fires an arrow, and the arrow impacts other objects.

{{< video
    src="/blog/CAGD373/Bow Sounds.webm" >}}

## Fire Arrows

Adding to the previous feature, I created some fire arrows (as with everything at this current stage, it's still made up of placeholder models). These fire arrows have a slightly different sound to them when firing and hitting a target. 

They also can ignite targets that have a `BP_IgnitableComponets` attached allowing objects to create custom behavior when shot at. At the time of completing these features, I didn't have flame effects to use yet, however I tested this with a placeholder `BP_IgnitableCharacter` (depicted as the large brown cube in the below video). Shooting it with the fire arrows trigger's the object's ignitable component, which calls an event setting the character to yellow color. However, later on, we can have it attach a fire effect to the target object, or even trigger switches in certain puzzles (like lighting torches to reveal secret doors)

{{< video
    src="/blog/CAGD373/Fire bow Sounds.webm" >}}

