---
title: 'Post Mortem'
date: 2025-05-10T23:15:16-07:00
draft: false
description: ""
author: "Jonathan Seepersad"
keywords: []
---

# Background

Over the last semester, I was part of a group project tasked with creating a 
game prototype to practice Agile methodology. I assumed the role of 
programmer while my teammates selected the role of producer and level 
designer. 

Our prototype, we called Static Bog (I believe that name was 
intended as a placeholder, but we never decided on a replacement). Its 
gimmick was that our player uses the recoil of a gun to launch them away and 
maneuver obstacles and enemies. Players were encouraged to explore levels to 
collect goals, allowing them to progress and complete the level. Players can 
move across various platforms, fight enemies, and avoid the water to survive.

# What went well?

One thing I felt worked well is that each of our roles made it so that we 
could focus on tasks in our skill set. In other game programming classes 
I've taken, we've been assigned tasks to plan features we intend to add to 
our game before writing any code. We are often tasked with using planning tools 
such as UML diagrams to create a sort of pseudocode before writing any real 
code. While I do acknowledge, it is beneficial for some to plan out a 
strategy beforehand; if I have a clear or strong idea of what behavior a 
feature should achieve, it is easier for me to jump straight into code. This 
is where the producer steps in.

Our producer handled creating most of the tasks on our backlog, creating a 
list of small features that combine into the full game. This removes my need 
to plan out the entire project before starting on code. It also simplifies each 
feature into small bite-sized tasks with clear goals, so I can easily 
implement them and scratch them off like a checklist.

Lastly, as the lead programmer (or I suppose sole programmer), I'm able to 
structure the code and behavior in ways I feel is best, allowing me to use 
more advanced patterns and creative solutions to solve tasks. In previous 
programming group projects, I tend to struggle with delegating tasks among 
teammates. This tends to lead me to work on projects, usually on my own, but 
giving smaller tasks to teammates to create scaffolds that I refine. Since I 
was the sole programmer, I can ensure that the code is clean and formatted 
in a way that works best for me.

# What didn't?

One area I found was an issue was that my teammates and I had differing 
expectations for the quality of our project. Although I believe I may have 
been the one making this issue worse. Our game was a 3D platformer and, as 
someone who is a big fan of this genre, I had high expectations of how I 
wanted our game to look and feel.

Our whole goal for this project is to create a game prototype, not a 
fully-fledged game. As such, most (if not all) attention should be directed 
towards fleshing out and refining the mechanics of the game. I got 
sidetracked when one of my teammates created simple assets for the game to 
look more appealing. However, I felt like I could have made the assets much 
better, and thus I stepped away from programming for a bit to improve the 
assets.

What is wrong with that is that the old assets were perfectly fine for a 
prototype, but my expectations for high quality distracted me from the  
programming. Even worth, some of the changes and optimizations I chose to 
make lead me to conclude it would be simpler to recreate most of the prefabs 
we already had. This took time that could have been used on other tasks and 
wasn't really needed for our prototype. Because I redid the prototypes, any 
older levels that our level designer made couldn't be used anymore.

# Future development

One of the reasons I had high expectations for the quality of our game was 
because I intended to continue developing it into a real game, even after our 
class. Unfortunately, I'm not sure if my teammates also want to continue 
this project, so I may have to decide to adopt it solo. To continue working 
on it, I'd like to add far more variations to our game to make it more fun.

I designed the behavior of the game to have the flexibility to support more 
guns for the player, with the hopes that different guns would have different 
movement/play styles coupled with varying strength and weaknesses. I managed 
to create a simple enemy behavior for our final prototype, so our player 
could have a reason to shoot things and to give them a bit more of a 
challenge. But different enemies with varying abilities might increase 
difficulty and how much fun players experience.

I'd also consider adding multiple ways a level should end. Currently, 
players collect all rings to spawn a key which, upon collecting the key, 
wins the level. However, we could have other clear conditions such as 
defeating a number of enemies, defeating a boss, reaching a goal post under 
a certain time, etc.

There are also a few tasks we didn't complete from the backboard as yet. We 
wanted to add an argument system to encourage players to explore unique 
and niche aspects of the game, but haven't gotten around to it as yet. We 
also wanted an upgrade system for guns to encourage players to use each 
weapon more and find all its niche quirks in the process.