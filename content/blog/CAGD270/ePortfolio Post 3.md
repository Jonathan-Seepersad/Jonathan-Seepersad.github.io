---
title: 'EPortfolio Post 3: Custom level in Unity'
date: 2024-12-09T16:36:13-08:00
draft: false
description: ""
author: "Jonathan Seepersad"
keywords: [ ]
---

# Background

For our last few projects, we created levels in Unity. We used Game Kit
Lite, which is an asset pack with pre-assembled prefabs and characters,
serving as a good starting point to create games easily. However, as we were
using Unity, a full-blown game engine, we had a lot more freedom and
flexibility compared to previous projects.

# First Iteration

As with the previous projects, our goal was to build a tutorial level that
teaches players the mechanics of the game. To fit this goal, I
initially designed with two parts. The first part contained no enemies but
some simple platforming for players to get used to.

![Level Start.png](/blog/CAGD270/LevelStart.png)

The player spawns in a secluded room safe from danger. They soon get
acquainted with the controls of movement as they explore. Then they get
familiar with jumping as they jump the stairs to get to the next section

![Blocked_Door.png](/blog/CAGD270/BlockedDoor.png)

After they climb the stairs, they come across a door. Approaching the door
hints to the player that they need to find a switch first before they can
progress through the level, so the player continues forward to find a switch.

![Second_Room.png](/blog/CAGD270/SecondRoom.png)

As the player makes their way to the next room, they see a pit with blocks
that they must jump on to get to the next area. Just basic platforming to
get familiar with.

Once they make their way to the next section, they find some breakable
blocks to encourage the player to try out their weapon. Breaking the blocks
reveals the switch that unlocks the door.

Finally, once the player has unlocked the door, they need to go back to the
pit to exit. However, the pit is higher than the last section, so the player
needs to higher platforms to make it back. It encourages the player to get
familiar with more precise platforming, jumping to multiple small platforms.

![TheRestOfTheLevel.png](/blog/CAGD270/TheRestOfTheLevel.png)

Once the door opens, the player is exposed to the rest of the level.
Starting off with one initial chomper enemy that the player can tackle without
being overwhelmed. They aren't very strong, only running up to player and
trying to bite them when near. There are a couple colonies the player can
fight as well.

The player also notices a pathway blocked by a door, meaning another switch
to search for. As seen from afar, the switch is placed on a tall platform
positioned on an acid lake. To get there, the player must jump up a series
of platforms, being careful not to fall in the acid.

At the top of the platform with the switch, the player is introduced to some
spitter enemies, which spit acid at players from afar. Spitters also aren't
very hard as they take a while to spit at the player, and the spit takes
a while to hit the player.

The switch opens the door that the player previously saw, but there wasn't
anything passed that door at the time.

# Level revision

Based on feedback received from play-testers, the layout of the level was
pretty okay. Most play-testers suggested increasing the difficulty as the
level was a little too easy and boring. But it does do a good job of
passively getting players used to the controls and mechanics. After
play-testing the other player's levels, I drew inspiration from a few
interesting tricks other classmates created. We also learned some other
areas that we can customize that weren't immediately apparent.

First, enemies can specify how much health they have. This allows us to
strengthen the enemies to make the game slightly more difficult. I also saw
how players were using moving platforms in unique and unorthodox ways, and I
played around to see what is possible and what I can use.

For the revision, the first sections of the level (before the first door)
had no changes as there were no complaints about it. However, after the door,
all chomper enemies have been bumped to 3 hit points.

![RevisedOpening.png](/blog/CAGD270/RevisedOpening.png)

Enemies were also placed in larger, more dense groups. This was balanced off
by placing some health regeneration blocks in some specific places where
enemies are denser. This makes it so that the level isn't too difficult as
players can replenish health, but not too easy as players still need to
fight to replenish health.

![FrogCouncilShallDecideYourFate.png](/blog/CAGD270/FrogCouncilShallDecideYourFate.png)

On top of where the switches were, the spitter enemies were moved towards
the edge, and their range is increased, so they spit at players as they try
to complete this platforming section.

![GuardingTheSwitch.png](/blog/CAGD270/GuardingTheSwitch.png)

On top of the platform with the switch, I've added chompers into the mix,
with some more spitters in the far corners. The chompers now have more
health, so they require more involvement from the player. This defends the
spitters in the corners, which spit at the player as they're distracted by
the chompers.

![FurtherProgressingThroughTheLevel.png](/blog/CAGD270/FurtherProgressingThroughTheLevel.png)

The area after the door has been expanded a bit. Players come across an
L-shaped bend with a spitter off to the side. When players kill the spitter,
it triggers a platform to rise up from the acid.

![RisingPlatforms.png](/blog/CAGD270/RisingPlatforms.png)

Each platform contains a pressure plate that, when pressed, brings up the
next platform. There is also another spitter placed just out of reach from
the player, just to keep their heads on swivel as they wait for the next
platform.

![EndOfLevel.png](/blog/CAGD270/EndOfLevel.png)

This all leads to one final platform with some enemies on it. Once the
player kills these enemies, a textbox appears, saying that the level is 
complete.

# Conclusion

In the design of my level, I wanted to create a layout that felt like it
could possibly be part of a 3D platforming game like Spyro, Ratchet & Clank,
or A Hat in Time. Based on feedback, it felt vary natural and was well
received. The revision improved the difficulty in a balanced way and fixed
previous issues.

There is still room for some more improvements. The theme is a bit lacking
as there are no materials. But certain structures could enhance the
setting of a jungle ruin better.

For the boss fight, I want to make it so that the player needs to jump
on pressure plates to injure the boss. But to make these pressure plates
appear, the player needs to fight standard enemies first.
