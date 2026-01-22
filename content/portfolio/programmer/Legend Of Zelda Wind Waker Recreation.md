---
title: "Legend of Zelda: Wind Waker Recreation"
description: "A (loose) recreation of the Legend of Zelda: Wind Waker castle scene"
date: 2026-01-22
image: 
math: 
toc: false
license: false
hidden: false
comments: false
keywords: []
draft: false
params.sidebar: 
---

# Legend of Zelda: Wind Waker Recreation

{{< youtube qm9qiq35P5A >}}

This project was actually for a game asset creation course, though I still took the role of lead programmer. We were tasked with recreating a scene from a game. From creating an environment and making little assets to be used in the game, to recreating the interactivity for the gameplay. It's not meant to be a fully playable game, but enough to showcase the environment and models in an interactive and game-like environment.

As I often do, I created the character's main controls and locomotion. We also wanted link (or the player) to switch between different weapons, so I made the ability to pickup and store weapons in inventory, swap them out, and use them. I also added some animations and sound effects to the various weapons like:
- The bow streatches back as you draw it
- The player swigs their sword to melee attack all in its path
- (Not showcased) the player can also bring their hand back and chuck bombs away from them before they eventually explode.

What I realized was expecially challenging about this project was trying to have multiple people work on this project in a short span of time using Git. We often had someone who needed to modify changes on one git branch as someone makes changes on same objects, which lead to merge conflicts. Merge conflicts wouldn't normally be an issue, though with Unreal keeping each asset a binary file, code reviews and conflict resolution became a little more challenging (but still doable). Over time, I got into a rhythm of reviewing the code and resolving these conflicts much easier!