---
title: "Blog 3"
description: ""
date: 2025-11-19T17:30:51-08:00
image: 
math: 
toc: true
license: false
hidden: false
comments: true
keywords: []
draft: false
---

In this sprint, I was originally tasked to create a bomb that players can pick up and throw. I realized I haven't create a way to unequip picked up items so I thought I should tackle that first.

I made some splines for the hands to make it look like the player is charging up for a throw when they press the mouse button, then makes the throw when they release. One issue I had to overcome was how to make the item look like it had been launched from the players hand. Enabling physics allows the bomb to roll a bit, but it doesn't keep the force of the throw. To fix that, I just added some force to the object and disabled collisions with the player so it actually moves forward.

Then I played around with the bombs explosion effect to make it more fun. See if you can recognize where the effect came from.

{{< video
    src="/blog/CAGD373/Bomb Throw.webm" >}}

You can see here a quick throw (though I might change it to affect the velocity of the throw later on)

{{< video
    src="/blog/CAGD373/Quick Bomb Throw.webm" >}}

