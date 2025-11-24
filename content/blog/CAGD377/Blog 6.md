---
title: "Blog 6"
description: ""
date: 2025-11-23T22:46:19-08:00
image: 
math: 
toc: true
license: false
hidden: false
comments: true
keywords: []
draft: false
---

# Ensuring fair turn cycle

We continue working on our turn-based game where players control their character on a grid using simple swiping gestures. Previously, after players swiped to move their character, enemies will make their move after a delay. However, this lead to cases where the player was able to move faster than the enemy if they timed their swipes correctly. It could be used as an interesting mechanic but was an unintended effect which did create certain problems. Notably, when enemies are moving into a space, the player could swipe fast enough to end up in the enemies spot so that they both overlap. Then our tilemap would lose the reference to the enemy as it doesn't support multiple entities on the same space.

So the main feature I added this sprint was to make it so players wait until all enemies complete their movement before they can take their turn again. The implementation is inspired by how [WaitGroups](https://pkg.go.dev/sync#WaitGroup) work in Go (though our code is not parallel or multithread, just the pattern is similar). We add a counter onto our tilemap (since it oversees everything). Then when any entity starts to make a move, we increment that counter by one. Finally when the move has been completed we decrement from that counter. Once the counter returns to zero, we know that all entities that were going to move have finished their move and the tilemap switches control to the next group of entities (player or enemies). 

As we had already done previously, players start their turn by swiping. When it becomes the enemies turn, the tilemap loops through all enemy entities on the tilemap and tells it to make a move. Then control returns to the player. A special case exists when there are no enemies, so we handle this by incrementing the counter before cycling through each enemies' move functions, then decrement after we called all of those functions. This ensure even if there is no enemy, the value would return to zero anyways.

-----

During playtest though, we observed that movement feels slower as player wait for their turn before moving. So we might consider some sort of "touchscreen joystick" control where players swipe in a direction but it repeats the input each turn as long as the player does not lift their finger.

# New UI

As I mentioned in the previous sprint blog, we planned to modify the in-game HUD in preparation for our final changes. 

{{< video
    src="/blog/CAGD377/New UI.webm" >}}

Here we can see when the player picks up items, they are equipped to the corresponding slot at the bottom of the screen (Each item has a particular class and each slot will hold only one item of that class). The player's health is also adjustable so we can increase the maximum number of lives as an upgrade (similar thing with breath, but we haven't used water yet so it stays hidden until then). We also display currency collected and whether the player has picked up a key in the top right corner. Some other changes that aren't immediately visible in the video, the UI elements are placed in horizontal and vertical boxes so that they properly adjust their size for the device's screen.