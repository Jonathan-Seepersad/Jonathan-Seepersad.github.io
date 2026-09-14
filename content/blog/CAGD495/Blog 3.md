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
draft: false
---

# Background

In the last blog, I had setup the basis of the game. Including controls for the cars, the charge ability, and deciding the winner fo each battle. In this sprint, the game can now track winners in a best 2 of 3 game while also navigating between to and from a main menu (other menu screens yet to come). I've also begun working on a system for power ups, starting off with a battery that boost the player's speed and allows them to attack.

# GameMode

In the previous sprint, I created a `LevelManager` which was a simple script attached to a gameobject, specifying how to run a round of Rumble Rally.

This time, I've created a base abstract called `GameMode`, which not only specifies the behaviour of a round of gameplay, but allows for players to play a match and win a best 2 of 3 rounds.

These two objects behaved a little differently. `LevelManager` is a script attached to a regular game object. When the scene enters, Unity calls its `Start` method, and when a player spawned or died, it'd call a function on the current `LevelManager` (if present). 

`GameMode` however needs to store information that persists across scene loads. So the `GameMode` is set as a field value on our [singleton](https://en.wikipedia.org/wiki/Singleton_pattern) `GameManager` class. It also exposes event methods for when we load into different scenes (so a result screen has different behavior then a game arena or menu scene). So instead of using Unity's `Start`, our GameManager will track when we enter a scene and call the cooresponding `GameMode` event method.

When a player dies, kills another player, wins, etc. we store this data in the GameMode singleton, accessed by our `GameMode`. So when a player wins a certain number of rounds, we can can determine the winner of the match.

{{< video
    src="/blog/CAGD495/StateNavigation.webm" >}}

And as the video above should suggest, there will be other game modes to switch between. Because our `GameMode`s operate off of events, we can simply just swap which `GameMode` is attached to our `GameManager`.

# Power Ups and the Battery

Also showcased in that video above are the battery power ups, the other major feature worked on this sprint. 

Power ups use a base class of `BaseItem`, to make creating new power ups easier. It exposes an event one function called when a player collides with it, but then has an `Activate` and `Deactivate` function that can be overridden to start the power ups effect, and then reverse its effect when depleted.

The battery is the first item I am working on and it simply activates the charge ability regardless of how much charge the player had beforehand. It also has the option of filling the chage meter and increasing the max car's torque by a scalar.

# New Charge System

The charge system was also reworked a bit. Previously, it filled over time and the player can hold the charge button to deplete some charge to get a boost and to attack players. However, the charge was intended to be filled as the player keeps moving.

Here, we can see the charge bar fills slowly but only when the player is holding the throttle. When they switch to reverse, brake, or just stop driving, the charge meter rapidly empties.

Like last time, players deal damage during charge attacks. But they weren't supposed to get a large boost. Here we reuse that same throttle scalar from the battery power up to just give a little boost.

The other difference is after the player uses charge, it fully depletes the bar, so players need to strategize and time their attacks to avoid missing.