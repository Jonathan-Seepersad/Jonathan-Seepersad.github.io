---
title: "EPortfolio Post 3: Tryall - Saves, Powers, & Controls"
description: ""
date: 2026-10-11T17:55:28-07:00
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

Last sprint, we prepared for creating our first testable gameplay loop so we can begin to get feedback from real players. That included aiming, player health and ending the game, basic upgrades to some spells, and a system to spawn waves of enemies to fight off. This time, we are continuing to iterate on the game, adding in some of the other proposed mechanics.

Starting off with gaining upgrades during gameplay after killing certain milestones of enemies. Moving onto a mechanism to save game data so we can track stats and begin to add in persistent upgrades later on. a few other control improvements and bug fixes. And lastly finishing on ensuring the barrier durability (the shield) can regenerate when not taking damage.

# Player Powers (Upgrades)

A value was added to the player to track the number of enemies killed. I then created a "milestone" system that awards the player a new "power" or non-persistent upgrade each time they kill the required amount of enemies, then moves the milestone progressively further away. At this moment, the upgrades are randomized, and three were implemented so far:

- **Minor Power of Health:** increases the maximum health and barrier amount by a small amount per each level of this power. It also replenishes the player's health and barrier instantly.
- **Minor Power of Speed:** increases the player's movement speed by a small amount each level, allowing for greater maneuverability.
- **Minor Power of Strength:** Increases the player's damage output a bit for each level of this power. However, this one isn't used at the moment as spells derive their damage values from themselves instead of the player.

To make these upgrades work, I've moved most of the players stats into a struct for their base stats. Then on each upgrade level, a decimal value is added to a bonus factor. This bonus factor is then added on top of the base stats where needed. 

The powers work similar to the [upgrade spells] in the previous sprint. A map is kept with each key being an enum, representing each possible power. The value of the map is an integer to track it's level. This'll become a very recurring pattern for a lot of level-up-able stats in this game.

[upgrade spells]: /blog/cagd470/blog-2#upgrading-spells

Lastly, in order to make it clear to the player that they've gained a power, I added some status text that fades into view indicating which upgrade they've earned.

Here, we can see the player gets a power when they kill enough enemies (depicted in the milestone tracker in the top corner):

{{<video
    src="/blog/CAGD470/PlayerPowerUpgrades.webm"
>}}

# Save Data

The player powers are supposed to reset each run, but the player is supposed to earn gold when killing enemies, and use that gold to gain permanent upgrades. So, we needed to create a method of saving and loading gameplay data so players don't lose their progress when they close the game. 

Turns out Unreal makes this very easy with their `SaveGame` object, specifying a name and an ID in order to save and retrieve game data. So for future planning, I've created a save game object that the player loads before gameplay, and updates at the end of gameplay.

This video demos the total number of kills the player has made over all play sessions. Starts at 167, and the next round ends at 200:

{{<video
    src="/blog/CAGD470/SaveData.webm"
>}}

# Dynamic Camera

Recalling from last sprint, the aiming allowed us to move the camera around the player for dramatic views, I decided to add that into the game. So with the mouse wheel, you can adjust the camera's azimuth, then using Q and E, you can rotate around the player. Also allowing the player to get a different view of the stage in the process. On gamepad, this also works using the D-pad to rotate vertically and around the player.

{{<video
    src="/blog/CAGD470/RepositionableCamera.webm"
>}}

# Barrier Regeneration

The idea of the barrier wasn't to simply be a second set of health, but it was meant to replenish if the player can avoid taking damage for a few seconds. I've added a feature where, after the player takes damage, if they can avoid more damage for a couple seconds, it'll start to replenish. Of course, as the player gets a brief moment of invincibility after their shield depletes, The cooldown to replenish the shield is longer if it empties.

{{<video
    src="/blog/CAGD470/BarrierRegen.webm"
>}}

# Subtle Progressions

One last thing, in order to increase difficulty as the game progresses, there are a few subtle adjustments to enemies as time progresses to increase their stats. At the current moment, as the wave becomes more complete, enemies grow faster. Also as the player enters new waves, the enemies become stronger and more durable. This should allow them to even out even when the player gets upgraded from all the powers they earn.

{{<video
    src="/blog/CAGD470/StrongerEnemiesInLaterWaves.webm"
>}}

It's subtle in this video, but you'll notice some enemies are faster than others as they have been spawned later in the wave.