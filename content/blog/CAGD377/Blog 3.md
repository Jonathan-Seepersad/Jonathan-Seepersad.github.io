---
title: "Eportfolio Post 3: Play Store build and tile types"
description: ""
date: 2025-10-11T22:07:33-07:00
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

In the previous blog post, we were continuing to work on a new mobile game project for a class assignment but were trying to overcome certain issues with the Unreal to Android App pipeline. Basically certain types of builds from Unreal for Android tried to request filesystem permissions from Android, which just so happened to be deprecated and removed in the current versions of Android. We found a simple and cheap workaround to package all assets into a single APK (Android Package Kit) rather than separately into an APK and an OBB file (Android Opaque Binary Blob) as certain builds tried to load the OBB from the local filesystem. Even so, under certain unknown circumstances, Unreal would still perform the check for filesystem permissions, even though we might not have been using it for OBBs anymore. So we found that disabling the splash screen helped to disable the check and allow our game to run without issue!

It was a solution that was very inelegant, and doesn't solve other issues when trying to create release builds uploaded to the Google Play Store. So in this sprint I continued to investigated better solutions to get our project to work on Android, especially since we needed to prepare for some playtesting that happened during this spring.

# Attempting to upload to the Play Store 

We tried creating a new release build for the play store and attempted to upload it for the first time, just see how it goes. Then we were met with *yet another error* originating from Unreal Engine. The Google Play Console complains about how the billing library we are trying to use is too outdated to allow us to publish the app. We don't really use billing for any part of our project but since we are making everything purely in Blueprints, there isn't any easy way for us to just update the version of the library that Unreal decided to use.

## TDSHero

If only Unreal had a one-click solution that would just solve things immediately without so much hassle and hacky workarounds. but that would just be too easy right? Turns out there was a plugin on the Fab store called [TDSHero](https://www.fab.com/listings/34b3b891-9d65-4926-9e14-531e4689acbb) that claims to solve the billing issue, support current versions of Android, and fix the filesystem permissions (among other issues we have not experienced yet but no doubt may have ran into in the future). I'm still a little cautious about this plugin because I haven't had the chance to inspect its content to verify its safety, It appears to have very little ratings or comments, and it just felt too good to be true. Regardless, it seemed to have fixed several of our issues with minimal issues. So, for the time being, we'll continue to use it, but I still want to inspect it a little bit for security purposes and to give me peace of mind.

## Google Play Asset Delivery

The other black box for us was how we use Google Play Asset Delivery to properly distribute our OBB files. What happens is if we package OBBs with APKs instead of a single APK, our app will complain that it cannot fetch the OBB files or that it is missing a key. Packaging the assets into the APK is a kind of stopgap solution because the Play Store imposes a limit of 150MBs for APK size. I couldn't really figure out where I was supposed to put my OBB but then I realized that building an Android App Bundle (AAB) packs the APK and OBB files together as one to make uploading to the Play Store easy(-ish).

So after I eventually figured out the OBB is packaged inside of the bundle and that the Play Store already had the OBB stored in the console, I realized that Unreal itself was complaining that it couldn't fetch the OBB because we didn't tell it how to correctly. We need to supply a key to Unreal under `Project Settings > Android > Google Play Services > Google Play License Key` in order for Unreal to know where to fetch our assets from. This key however is not the same key used to sign the app, instead it's a smaller plain-text key we have to find in the Google Play console *...somewhere*. Fortunately there was documentation from Google and Unreal Engine on how to find the key to put into this field, so everything should be smooth sailings right? *...right?*

Turns out, the particular fields that the documentations said to look for inside the Play Store *...just simply didn't exist anymore!* Seeing how all answers we get lead to new dead ends, I had briefly went to ChatGPT just to see whether it can scour more sources and documentations to find out where the Google Play License Key is located. I learned the docs pointed to an old location that is currently outdated. The new location is not inside any tab related to uploading the app, but is tucked away somewhere under *Monetization*.

Now that I found the key, I was able to build, then upload the app to the Play Store, then download, install, and play the game. All without issue! Took out a large chunk of my time to learn how to solve this particular problem, but we finally made it.

# Getting back to game design

So, in this project I still am supposed to be the designer, and I should be playing a better role in guiding my team on what the vision of the game should be. Usually I tend to play the role of the programmer and have a lot of technical experience, so I try to lay out the foundation of features that may be more complicated and related to data structures and algorithms (*...and solving google and Epic Game's shenanigans when it comes to Android*). This led to me getting sidetracked and sharing ideas, but never really solidifying it into words.

So, finally I began working on creating a game design document (GDD) so we can solidify features into words with clear goals. I felt like different tile types are essential for our game as we are able to build levels and puzzles with basic tiles even if we don't implement a single enemy. Enemies also depended on another algorithmic heavy feature I need to implement: pathfinding (Due to the nature of our game being grid based, it doesn't seem feasible or possible to use Unreal's built-in Navmesh feature) so they are kind of being ignored until I finish the groundwork for enemies.

## Defining different concepts first; turns, steps, and signals

Before writing about any tiles, I decided to define a few behaviors of how our game should behave to make explaining the behaviors of tiles easier. First, our game is supposed to be turn based, but we want all characters to perform their action at the same time (i.e. player makes a move, then all enemies also make their move simultaneously). To allow this to work, I want to introduce the term: steps. When a player performs initiates their action, the turn starts with an initial step. Each enemy will also choose an action to initiate, then all characters will perform their actions moving into corresponding spots, attacking their targets, and pushing movable objects in their way. Then, certain actions may cause side effects or reactions within that turn, such as stepping on a button may trigger a door to open. These side effects should all take place within the same turn, but as a separate step, and any reactions triggered from those steps trigger other steps until all reactions have taken place and we can finally end the turn. Currently steps are not implemented yet, but may be important when we have plenty of enemies and interactive tiles.

Another concept I wanted to create was the idea of tiles sending signals to and from each other. In our tilemap configuration, I left a few settings for each tile, one of which is a list of coordinates where that tile will send a signal to. The idea is that a button could be activated and just emit a signal to each of the tiles at each of the coordinates listed. Signals are simply a string indicating an action, so if a tile can handle that action, it'd do so. For example a switch emits a signal called `activate` when it is turned on or `deactivate` when turned off. Then a door that received the signal could decide to open when activated, or close when deactivated. Also a button could emit a signal such as `toggle` and a door could handle that differently by switching between closed or opened instead. This makes it easier to set all the tilemap's interactions in a struct that we can save to a file or load at runtime (so we can load levels on the fly instead of manually linking tiles to each other in the Unreal Editor).

## Some tiles to create

So there are a certain number of basic tiles we would like to create to make a few puzzles. Pressure plates, allow us to activate and deactivate tiles whether a character or pushable object is above it. Then we can create spike tiles that damage characters that are on it when it is activated, but safe to walk on when deactivated. Wall torches might also be an interesting way to hide secrets unless players find a way to light them. We also want water tiles that, when frozen, turn into ice causing characters to slip on it. Characters should still walk through water but may drown if they don't exit soon enough. Toxic sludge damages most characters but may be cleansed to become water again. Bridges are another set of tiles that can be activated or deactivated and allow characters to cross over hazards when activated. Pipe tiles allow characters to traverse between different rooms in a level as players hunt for the goal tile to exit a level. And finally an object spawner and reset button can spawn or reset the position of pushable objects so players can push these onto pressure plates, or between gaps.

Our GDD explains a lot about these tile types, they're intended behavior, what kind of objects should it block (some tiles let characters and blocks to pass over, others only allow characters, and some block all movement through it as if it were a wall), as well as when it should send a signal and what to do when it receives a signal. We also have arbitrary parameters available in our tilemap configs so we are able to set the initial state of some tiles (like spike tiles being enabled or disabled at start).
