---
title: "Postmortem"
description: ""
date: 2025-12-14T21:10:50-08:00
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

In this class (Mobile Game Development, CAGD 377), we were tasked to work as a group to create a game for Android. We created Sewer Swipers, a grid-based, dungeon-crawler style game with some puzzle elements (and it was supposed to have some elements of roguelikes as well, but not so sure if we got to that point yet). Our focus for our game was to make the controls as simple as possible, so we got it down to swiping in the direction the player should move or attack. We intended for the player to pick up at most three items and have them get equipped into three slots at the bottom of the screen. Then Player's may tap on the item to activate its effect. We got to finish making the effect for one item, a pill bottle that fully heals the player, though the other weapons and items were scrapped for the initial release (who knows, maybe we will add them in a later update).

![Game Interface](/blog/CAGD377/GameplayScreenshot.png)

The game is actually live right now on the play store [right here](https://play.google.com/store/apps/details?id=com.TeamBestFriends.SewerSwipers&utm_source=na_Med)!

# Postmortem

## What went right?

Initially, when starting our project, we had to make a couple of decisions. One being which engine we were planning on using for our game. Knowing we were creating a mobile game, I suggested Unity as the rest of the class was using it, I had used it quite extensively last semester, and it is generally what the industry uses for mobile game development. However, my other teammates wanted to give Unreal a shot. As someone who likes to challenge themselves when it comes to programming, I decided to give it a shot. Although, we later realized what issues this decision would involve. We happened to be the only group to choose Unreal, and there was little resources our professors could give us about mobile game development in Unreal. So we had to research, fix, and solve a fair amount of problems on our own. But... *we actually managed to overcome most of them!*At least the one's that were important.

Unreal Engine actually has a few features to make the Android setup process pretty swift. Where other groups using unity needed to manually download a specific  version of Android Studios as well as the specific packages needed to work with that particular version of Android Studios and Unity, Unreal kind of has a one-click install solution.

Unreal has it's own tools to automatically fetch the right version of Android Studios. It then prompts you to manually install the latest version of the android command line tools, but afterwards it is able to install and setup all the other packages needed to build your app directly from Unreal.

There were also some other hiccups to get our app to the Play Store, but we learned and figured out most of these issues pretty early on. Actually I was very worried about using Unreal by ourselves that I spent a large portion of time figuring out the process as soon as we could, so we'd know whether we could use Unreal, or jump ship and use Unity like the rest of the class.

I've documented some of the issues in previous blogs, but some things we overcame:

- signing the build for the Play Store
- building both self-contained APKs that don't need to download extra OBBs, as well as AABs that we can upload to the Play Store that are able to fetch OBBs from Google Play Asset Delivery
- fixing the Play Store complaining about outdated libraries using a plugin we found called [TDSHero](https://www.fab.com/listings/34b3b891-9d65-4926-9e14-531e4689acbb).

Essentially, many of what we were worried might go wrong for our game managed to get fixed just in time, and just happened to work out!

## What went wrong?

There is one thing that I believe drastically hampered my attention and performance. I picked 4 classes this semester, just like last semester. However, this time I also started a job so I can cover the cost of living in Chico. I completely overlooked the fact that a job would eat up whatever leftover time I had for working on projects. So where most assignments were due on Sundays and most students are free to work over weekends, I wasn't available when most would have been free. 

In our project, I created a lot of the foundation. Because of that, I think my unavailability may have contributed to a few features being scrapped. I had to make sure that either other groupmates were able to use this foundation with as little friction as possible (meaning the function to interface with the foundation needed to be created for them), or I had to implement the feature myself.

-----

Another part that may have gone wrong: I was supposed to play the role as the game designer, but I acted more as another developer. Programming and scripting out the behavior is the area I excel at. But planning? not so much. Because of this, I didn't really create a real GDD.

I've also realized that I am very particular about the neatness and cleanliness of the code, I rewrote and refactored parts of our project. However, I didn't realize others saw that as erasing their efforts. I've also been told the code I write can be a bit confusing at some times.

## What would I do differently in the future?

First thing: I should make sure that I set up my schedule so I can budget enough time for work, as well as dedicate time to work on other projects. I'm already taking less courses this coming semester as I expect a few of them to be a similar style of group projects.

I also think I should push more to be a programmer in future projects. My background has largely been centered around programming. I wish I had better artistic and design skills outside of programming, but I know that many of my peers understand those fields a lot better than me. I also tend to take over many of the technical aspects of our projects such as managing the code repository as I have experience using Git.

That being said, I should do a better job of documenting features and functions I create. I've seen numerous times this project my groupmates would recreate the behavior of a function I've previously created because they were unaware or didn't know that an easier method exists. I should also create more rules centering around code styling and handling of the git repo. Consistent code styles should encourage other teammates to think alike, so the rest of the code seems easier to understand than having multiple competing philosophies. And enforcing good practices with Git, like creating branches per user or feature, makes it easier to manage and maintain. Lastly, I should consider the effort that other group members put in to tackling a problem. If possible, I should ask before I attempt to refactor other members contributed code.
