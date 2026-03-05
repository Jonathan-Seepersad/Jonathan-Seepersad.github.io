---
title: "EPortfolio Post 3: Rumble Ralley - Power ups and menus"
description: ""
date: 2026-03-05T12:26:15-08:00
image: 
math: 
toc: true
license: false
hidden: false
comments: true
keywords: []
draft: true
---

# Background

In the last blog, I had setup the basis of the game. Including controls for the cars, the charge ability, and deciding the winner fo each battle. In this sprint, the game can now track winners in a best 2 of 3 game while also navigating between to and from a main menu (other menu screens yet to come). I've also begun working on a system for power ups, starting off with a battery that boost the player's speed and allows them to attack.

# GameMode

In the previous sprint, I created a `LevelManager` which was a simple script attached to a gameobject, specifying how to run a round of Rumble Rally.

This time, I've created a base abstract called `GameMode`, which not only specifies the behaviour of a round of gameplay, but allows for players to play a match and win a best 2 of 3 rounds.

These two objects behaved a little differently. `LevelManager` is a script attached to a regular game object. When the scene enters, Unity calls its `Start` method, and when a player spawned or died, it'd call a function on the current `LevelManager` (if present). 

`GameMode` however needs to store information that persists across scene loads. So the `GameMode` is set as a field value on our [singleton](https://en.wikipedia.org/wiki/Singleton_pattern) `GameManager` class. It also exposes event methods for when we load into different scenes (so a result screen has different behavior then a game arena or menu scene). So instead of using Unity's `Start`, our GameManager will track when we enter a scene and call the cooresponding `GameMode` event method.

![Rounds](/blog/CAGD495/Rounds.gif)