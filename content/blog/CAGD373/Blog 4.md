---
title: "Blog 4: Switching weapons and showing lives"
description: ""
date: 2025-12-03T17:34:51-08:00
image: 
math: 
toc: true
license: false
hidden: false
comments: true
keywords: []
draft: false
---

In this sprint I got to life display to work. Though while another teammate works on enemies damaging the player, I created a button to test damage on the player. The life display is similar to the other project I am working on in that it allows any maximum amount of lives so it'll just add more hearts as needed. I also created a basic heart graphics and an empty heart, inspired by how they look in Legend of Zelda: The Windwaker. No quirky references this time, unless we want to change it to be so.

{{< video
    src="/blog/CAGD373/Life Display.webm" >}}

In addition to that, I also added functions to swap the weapon the player is holding via mousewheel. I haven't really played Windwaker so I'm not sure of how it works in *that* game, but I made it so ou have to pick up the weapon first, and you swap through items in the order that you picked them up (and an extra empty slot to reveal your bare hand again).

{{< video
    src="/blog/CAGD373/Weapon Switching.webm" >}}