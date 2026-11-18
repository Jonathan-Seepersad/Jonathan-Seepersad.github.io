---
title: "EPortfolio Post 3: RE4 Clone - Podium Puzzle and more interactive elements"
description: ""
date: 2026-11-18T03:22:35-08:00
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

In the last sprint, I created an inventory system and menu, allowing us to display and view what items we picked up. I also started creating the podium which would be used for our main puzzle. At the start of the sprint, it only allowed for the player to interact with it, locking their view in place, but there was little other interactions attached to it so they couldn't do any thing else with it.

This sprint continues building off the podium puzzle, and implementing more environmental and interactable elements.

# Podium Puzzle

{{<video
  src="/blog/CAGD373(II)/RotatingWindowPanels.webm"
>}}

In this video, once the player has begun focussing the podium puzzle, they are now able to select and switch between each of the 3 dials on the podium using "A" and "D". Then for each dial, they can it with "Q" and "E", which rotates the corresponding panel from the stained glass window.

In order to indicate the selected dial, I created a material last sprint that I can pulse a glowing color. Here I've made it so that only the selected one pulses, and when it becomes unselected, it stops.

# Cabinet

{{<video
  src="/blog/CAGD373(II)/CabinetModel.webm"
>}}

So we encourage the player to explore, and have a place to hide things, I added some interactions to the cabinet model made by another teammate. This takes a list of hinges for each doors, then interpolates their rotation along a curve when it receives an interact input from the player. I also added a subtle bounce to the door when opening and closing to give it a slight amount of personality.

# Cog Inventory Item

{{<video
  src="/blog/CAGD373(II)/BlueDial.webm"
>}}

As we have the inventory system working from last sprint, let's add some of these cogs as items for the player to pick up. So the cog can be placed into the level with it's model. It also has a rendered image to serve as an icon when viewed in the inventory menu.

What will happen next is that the podium will have slots missing dials, which the player can insert into the slot if they have picked up a dial. At the moment, the podium does ignore empty rotation input of empty slots, but I've prepopulated them for testing. I'd like to animate the dial being placed into the slot rather than have it poof into existence, but that will be what I start next sprint off with.