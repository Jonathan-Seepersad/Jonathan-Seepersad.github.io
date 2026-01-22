---
title: "Sewer Swipers"
description: "Android Mobile game created with Unreal Engine"
date: 2026-01-22
image: /portfolio/sewer-swipers-icon.png
math: 
toc: false
license: false
hidden: false
comments: false
keywords: []
draft: false
params.sidebar: 
---

# Sewer Swipers

![Screenshot 1](/portfolio/sewer-swipers-1.jpg) ![Screenshot 2](/portfolio/sewer-swipers-2.jpg) ![Screenshot 3](/portfolio/sewer-swipers-3.jpg) ![Screenshot 4](/portfolio/sewer-swipers-4.jpg)

Sewer Swipers is a grid-based dungeon crawler game for Android, created in Unreal Engine.

Made from a small team of three, I played the role of the designer (who also contributed as a developer). I created the base components the game depends on including:
- The tilemap (which is used to generate levels from a set of data structures)
- The base tile object which other tiles use to add their own functionality
- Entities that traverse along the tiles of the grid
- Items the player can pick up off the floor and equip (or activate)

I also had to reimplement pathfinding for the enemies to chase the player. Even though Unreal has it's Navmesh tool, it wouldn't help us as entities between discrete grid cells, rather than walking along a mesh

What we are especially proud of in our game is the simplistic controls which work really well on mobile. The game was designed with a clean interface and simple swipe controls in order to make the player move or attack. The bottom three boxes house items that the player can pick up, which they can tap to activate their effect (although we only managed to finish getting a health item ready by the deadline).

The process of getting our app from Unreal to the Google Play store was also initially a challenge, but we are proud to say we've pulled through! If you're interested in trying it out for yourself, come check out game's page at the link below.

[![Get it on Google Play](/portfolio/google_play_badge.png)](https://play.google.com/store/apps/details?id=com.TeamBestFriends.SewerSwipers)