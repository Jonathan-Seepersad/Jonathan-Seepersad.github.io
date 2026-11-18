---
title: "EPortfolio Post 5: Tryall - Advanced Status Effects"
description: ""
date: 2026-11-08T20:41:14-08:00
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

In the previous sprint, I started creating status effects for the player to inflict onto enemies. Starting with the slow status effect. 

I attempted to create a more advanced wave system that could allow the game to get progressively harder as players reach higher wave levels. The logic worked, but some corruption prevented the project from opening when trying to include those features, so we kept that branch out, but the logic is developed and works.

In this sprint, I worked on a few more statuses. These were more advanced than the slow status that they necessitated a new system using actor components to attach long-running statuses to enemies (with complicated or repeating logic).

As we near the end of the project, I've also been scrambling to merge more and more features into the main branch, resolve conflicts, troubleshoot other issues, and overall maintenance of the project.

# New Status Component

The first created "slow" status really just applies a one-time, permanent de-buff on afflicted enemies. So the logic really boiled down to: "on hit, set the current movement and attack speed to the base speed multiplied by some scale". As such, it could be simplified to a function call. These other statuses we wanted to include however had more advanced behavior. Enemies may get the effect applied to them, but if they have the effect already, then it'd be increases up to a maximum. Some would also deal damage to the enemy at fixed intervals, needing the use of timers or latent actions. Some needed to perform actions when key events happen, like a time out or the afflicted enemy dies.

To make things easier, I thought about "equipping" a new class based on ActorComponent to the enemy. So if the enemy has a status component equipped already, they can re-apply the effect rather than attaching it as new. The component also allows us to keep track of latent actions and timers so we can create our damage intervals, store stacked status effects when inflicted with a status multiple times, Store values for later results, etc. (and may come in handy when creating visual effects for each of the statuses later on).

# Burn Status

The first of these advanced status implemented was the burn status. When inflicted, enemies take damage equal to a percentage of player damage every second.