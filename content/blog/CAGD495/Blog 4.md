---
title: "EPortfolio Post 4: Rumble Ralley - Sounds & even more powerups and menus"
description: ""
date: 2026-03-26T12:27:15-07:00
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

In the last blog, there were menu and scene navigations, modifications to the charge ability, and the start of some power up features in the game. Continuing on from there, this sprint I've added a few more items, begun adding in sound effects, and also link together more menu windows in preperation for a new build.

# Another Modification to Charge

As we often do, the Charge attack went through another change. During playtesting, we realized that necessitating the button input to initiate an attack didn't make sense as we are already trying to crash into the opponent. The button input meant that the player may click the button to initiate an attack, but then miss their opponent and need to wait to recharge. So the first change I did was to change the charge attack to not need a button, instead dealing damage while the player collides with opponents.

The charge attack is also based on forward velocity this time (So you don't have charge when reversing). Last time was similar, but technically was based on how long you held the throttle button rather than how fast you were moving.

{{< figure
    src="/blog/CAGD495/ButtonFreeCharge.gif"
    alt="Button Free Charge"
    caption="Car's charge is equivalent to car's velocity, and damages without button input."
>}}

Other notable changes, player's damage is impacted by the angle of attack as well. So hitting your opponent head-on deals less damage than if you hit them from behind. Damage is also defended by how much the opponent's charge meter is compared to the players. So hitting a running player from behind deals less damage than a stationary or reversing enemy.

# BGM and SFX

I've also begun to add sound effects and background music to the game. To start, our sound designer created some music for the menu screen and the gameplay scene. Divided into an intro part and a main looping part. So I created a component that takes in the into and the loop parts, plays the intro until completed, than switches the main loop and continuously loops it.

{{< video
    src="/blog/CAGD495/BGM.webm" >}}

I also added sound for when the player is driving. We used sound effects similar to that of an RC car, because the game is supposed to be based on driving RC cars in toy and play spaces. 

In order to sell the idea that the sound is from driving the car, I made it so it changes the pitch of the effect based on the wheel's RPM. I also made the volume be controlled by the RPM so it get's louder as you drive faster (though releasing the throttle makes the sound effects quiet as your not driving the wheels anymore).

{{< video
    src="/blog/CAGD495/WheelSFX.webm" >}}

Another programmer on the team made an options menu, allowing the player to adjust audio levels of BGM and SFX, so I also made sure that these values are preserved and updated per the user's settings.

# A Few More Items

There were also a few additional power ups added to the game. 

First is the "Floor Cleaner" powerup, which upon pickup causes all the vehicles to become slippery. I found the best way to get this to work, rather than fiddling with cars grip settings, is to modify the gravity of the environment. We already had the gravity set to a higher value so that the cars don't jump into the air as often, which lead to the side effect of cars being very responsive and grippy to the ground. So... reducing that gravity also has the side effect of making the cars less responsive and grippy, making the slippery effect we were looking for! (Oh, you can also hear it in the sound effects for the wheels, but the pitch of the wheels effect increases as the tires slip against the slippery road)

{{< figure
    src="/blog/CAGD495/FloorCleaner.gif"
    alt="Floor Cleaner Powerup"
    caption="Makes all cars slippery, as if driving on ice."
>}}

Afterwards, I also added the "Funny Mirror" powerup, which reverses the player's controls for a brief moment. This works for both the intuitive and manual steering modes. With the intuitive steering control, the player steers exactly behind where the player points their joystick. With manual mode, the left and right directions are flipped.

{{< figure
    src="/blog/CAGD495/FunnyMirror.gif"
    alt="Funny Mirror"
    caption="Reverses players controls for a brief moment."
>}}
