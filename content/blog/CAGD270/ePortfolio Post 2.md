---
title: 'EPortfolio Post 2: Custom Mega Man Levels'
date: 2024-10-30T21:34:46-07:00
draft: false
description: ""
author: "Jonathan Seepersad"
keywords: []
---

# Background

In our second project, we created levels the Mega Man Maker tool. It is a level editor similar to the Super Mario Maker game, but creates levels using Mega Man blocks and characters.

I've not really played Mega Man too much. I'm more familiar with Mario style of platforming games. So to understand Mega Man, I tried playing some example levels to see what I liked and disliked. That way I can think about ways that I can enhance the level design of my levels. There are subtle differences in the styles of the two franchises. Mario focuses on platforming more than combat and fighting, as Mario's primary form of beating enemies is to jump on them. However, in Mega Man, players always have a gun and also have much more health than in Mario games. This leads to Mega Man style of levels adding more combat focused ideas in addition to platforming.

# First Iteration

For the most part, my level was seen fairly favorably from playtesters. The start introduced many mechanics of Mega Man in a natural way without being too easy or too hard. The end also had some interesting platforming techniques that playtesters really liked. 

One idea that clicked with others was to have breakable blocks right after a set of falling blocks. 

![Favorable Concept](/blog/CAGD270/MegaManPlatformingConcepts.png "A favored concept used in my level where destructible blocks are placed after falling blocks")

I've seen this idea in a few other levels. It forces the player to think about which blocks they plan to shoot, but also requires them to think about it ahead of time as they cannot stand on the floating blocks for too long. If the players shoot willy-nilly, they will shoot the floor on which they are to stand on. So players realize they must shoot the top blocks and keep the bottom to allow themselves something to stand on.

On the flip side, there were a few rooms in the middle of the level which play-testers did not enjoy too much. One room features a small moving platform that players must stay on while dodging and fighting through waves of bullets and enemies. It was described as a bit too hard and really difficult to get through without taking damage. As Mega Man has health, and can take multiple hits, I did not intend the player to dodge everything, just enough to get through that section. However, I can understand that some players felt bad for being forced to take damage.

Another common complaint about my level was this following room in particular:

![Problematic room](/blog/CAGD270/MegaManIssue.png "An example of ambiguity leading to death and player confusion")

The problem with the above room is that players often thought the gaps at the bottom of the room were going to go to another room. This is a possible and natural thought players familiar with Mega Man can think, and players have often moved down to the next room in other areas of the levels. This ambiguity, leading to player's death, breaks the trust between the player and level designer.

It can be fixed by placing spikes there to enforce the idea that those gaps lead to death; however, I tried something different in the next revision of the level.

# Level Revision

In our revision, we were required to introduce keys and doors to the player. We were also given more flexibility in what enemies or components we were allowed to use in our level.   

To fix the ambiguity present in the second issue, I added spikes to the first gap but quicksand to the second gap.

![RevisionOfIssue.png](/blog/CAGD270/RevisionOfIssue.png)

The quicksand also leads to a whole other section of the level now.

When playtesting other classmates' levels, I've noticed a few of them have a lot of "Branching." In other words, there is not just one way to get to the end. However, did not like how others implemented branching as I've found myself getting lost when playtesting other levels. I decided to create a single branch which allows the players to choose it and do those challenges and separate mechanics rather than some of the mechanics on the main path. However, I made the branch linear, so players do not get lost if they happen to choose it.

The area under the quicksand introduced new concepts using these drillers that move across the screen. Drillers are special level objects that move straight in a single direction, but they demolish any blocks in their way. With this idea, I created a walkway with non-destructible blocks that players can only get through with the drillers. In the end, the players get awarded a key, and are placed right before the door to progress on the main section of the level.

I was excited to see if players will explore the secret area. Unfortunately, it seemed like playtesters didn't realize there was a second area to explore. Possibly they were untrusting of that gap as it previously led to death, or players weren't accustomed to the idea of being able to sink through quicksand to access hidden areas of the level. It's a fine and delicate balance between making things secret, but findable for the player. You don't want it to be too hidden, but at the same time, you don't want it to be too obvious.

To address the small platform issue that playtesters did not like, I placed two moving platforms to the left and right of the original platform, effectively widening players' standing space. However, this did little for playtesters as they felt it was too challenging to get through the section without taking damage.

Going back to our requirement that we introduce keys and doors, I've introduced some doors in the way of players' progression, but with separate challenges they will have to complete to get a key to continue. One of the keys that players could find was in this "fan room." A separate challenge room that players must do to be rewarded with the key (unless they took the secret route mentioned above, they'd also get the key, skipping the challenge).

![MegaManFanRoom.png](/blog/CAGD270/MegaManFanRoom.png)

These fan enemies pull the player in the direction that they face as long as they are on screen. Many playtesters mentioned that the concept was quite interesting, but also quite hard to get through. The small moving platform gave the player a very tight window to react to the fans' pull, leading to players falling off the platforms, hitting the fans, and getting damaged. This might be addressable by increasing the size of the platform though.

The next instance of using doors made players have to go through this separate room to find a key. My issue with using doors is that: if the path is linear, and that linear path gives you the key right before you reach the door, you can argue that the level can be refactored to play without the door. So to avoid that, I had players pick up the key, then backtrack completing the challenge room in reverse, before they can finally unlock the door again.

# Second Iteration

For the second iteration of the Mega Man level, I wanted to try something entirely different. I noticed that a few playtesters were creating levels in a way where level objects and enemies were exploited in a way that I wouldn't expect from a standard Mega Man Level. So I thought, I should do something similar and go crazy with my design.

![ManyChallengesForKeys.png](/blog/CAGD270/ManyChallengesForKeys.png)

This concept borrows inspiration from some Mario Maker levels I've seen where players must complete several challenges to get red coins to unlock a red door (which then leads to the goal). Similarly, I placed several keys which the player collects to be able to open a door to the goal. The main issue is to prevent the player from being able to access the other keys if they haven't completed the challenge, but also to save a player's progress after they collect a key.

Careful planning allows us to fix these issues and have this concept work. Using falling blocks, players can only exit, but cannot enter the reverse direction as the blocks don't fall. Blocks also respawn when out of view, so this also prevents player's backtracking through challenges in the reverse direction. To save player progress, you need the player to touch a checkpoint before they proceed to another challenge.

![CheckpointRoom.png](/blog/CAGD270/CheckpointRoom.png)

Using this room, the players enter from the top, touch the checkpoint, and are ready to pick any of the four challenge areas on the sides. Once they complete the challenge, they get lead back to the previous room where they collect a key and repeat the process.

We were also allowed to use other Mega Man abilities to enhance our levels. I chose the S.Arrow, and the Nado power up. These allow the player to jump high and maneuver platforms that they wouldn't be able to by just jumping. It gives us a little more freedom with how we design levels as we can place blocks at much higher and harder to reach areas. However, the one downside is that the player must be fed energy to get through these sections. So, in any challenge room where this mechanic is prevalent or required, there is block to spawn energy to complete the challenge. However, to not make things too easy, this only happens at the start of the challenge room.

Unfortunately, I was out of town and couldn't get feedback on this level in particular.