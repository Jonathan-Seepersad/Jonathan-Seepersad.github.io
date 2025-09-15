---
title: "EPortfolio Post 1: Starting a new mobile game "
description: ""
date: 2025-09-14T22:07:33-07:00
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

To start off our new class of CAGD377, or mobile game development, we've got into new teams as we attempt to build and publish a game for Android. Like previously in CAGD370, we are still trying to practice Agile and Scrum. This time though, someone else chose to be the developer so I played the role of the game designer and flex. However, as my skills are much more skewed towards programming, I'll also offer my support in that area to nudge the game closer in line to what I intend to design.

# Our project

Our only requirements for this project are that:
1. It needs to be 3D graphics
2. Needs to fit in both the roguelite and puzzle genres
3. Needs to be built with Android phones in mind.

Given these requirements, I wanted to design our game with simple and minimalist controls designed specifically to work on small touchscreen devices. The idea is that the player controls their character in a grid based dungeon (similar to that of Pokemon Mystery Dungeon) by swiping in the direction they want to perform actions. The character would either move into an empty tile, pick up/swap equipment on a tile, or attack an enemy on a tile. Players would also have access to three types of equipments: abilities/magic, weapon abilities, and consumable items. They can use by tapping its button on the bottom of the screen. Players however can only carry one of each type of equipment, so they need to strategize whether or not to pick up new items, keep and upgrade what they have, or use it out before swapping it with other equipment from the dungeon floor. One other feature about our game is that players and enemies perform their actions at the same time (a slight difference than Pokemon Mystery Dungeon, where players and enemies move one at a time). So if a player melee attacks an adjacent enemy, the enemy also has the opportunity to do its own action onto the player.

# My tasks

I still consider myself more comfortable with Git than my peers so I insisted on creating the project and repository so I can manage it and resolve issues and conflicts as needed. Though we'll want to be a little more careful here as we chose to create our game using Unreal Blueprints. Meaning all our files are binary, which git might not be able to create diffs of.

After that, I really wanted to tackle the scripts that would handle creating tilemap levels as well as scripts for any character that would traverse that tilemap as these components are very important for the base idea of our game.

![Tilemaps](/blog/CAGD377/Tilemap.gif)

### Tilemap

The tilemap simply accepts a map where keys are a structure representing the tiles coordinates, and the values are the type of tile to be placed at the corresponding coordinates. Then the tilemap iterates through the elements and spawns the corresponding tile. We can use the tilemap to then query what tiles are at a particular coordinate which is really useful for creatures that live and traverse the tilemap, leading to the next feature.

### Tilemap dwellers

Tilemap dwellers is intended to be a base class that any character can extend if they live on and move around a tilemap. It has some tools query what tile exists in the specific direction and move to a tile in a particular direction. It is very basic as it is meant to be extended by enemies or player characters. In the above example, our player checks whether a tile in a direction is a floor tile before moving in that direction. However, we could also make it so that enemies can autonomously move around the room in the future.

### Limitations and what to fix next

Currently our tilemap gives us the freedom and flexibility to create arbitrary levels by setting a map of tile types, however it currently must be done by hand. We'd probably want to create a map editor to make creating levels much easier or find a way to parse the format from other map editors such as Tiled or Ogmo. Our tilemap also only keeps track of the layout of tile types, however it doesn't yet have the ability to track what entities or items should spawn in the map. We'll want to modify the tilemap to also store items and entities at tiles coordinates.

I also really just created one type of tile, the floor tile, just to prototype the feature. But we'd also probably want to create other tiles such as water, hazards, traps, and interactive tiles. Though currently we don't have a way for tiles to specify settings and default states, like a portal or door that moves players to a specific location, or a button that triggers some event when pressed.

Another complication I suspect may arise is that since characters are moving on a tilemap rather than walking around a mesh, we probably cannot take advantage of navmeshes for pathfinding. I fear we may need to implement some form of A* or Dijkstra's algorithm just for entities to traverse the map intelligently, if Unreal doesn't provide generic pathfinding already.