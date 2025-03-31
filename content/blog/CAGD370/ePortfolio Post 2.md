---
title: 'EPortfolio Post 2: Rocket Jumping'
date: 2025-03-30T15:03:12-07:00
draft: false
description: ""
author: "Jonathan Seepersad"
keywords: [ ]
---

# Background

In my last blog, I've started working on a 3D platforming project as the
developer for a small group. Our game idea uses the recoil of various
guns and weapons to propel the player. Some may be familiar with this
movement being referred to as [the rocket jump].

[the rocket jump]: https://en.wikipedia.org/wiki/Rocket_jumping

In the last blog post, I set up the foundation for the camera controller and
player movement. Since then, I've begun working on creating the weapon
systems including scripts for aiming a gun and firing bullets that "explode"
pushing the player away from the blast. My other team members also got to
work creating some environmental assets and a basic level to help with
visualizing gameplay during testing.

![GunRecoil.gif](/blog/CAGD370/GunRecoil.gif)

# Creating a Gun

Before the player can actually shoot, we needed to create a gun controller
that handles aiming of a gun model and firing of bullets. As this is a
prototype, we want to focus on the controls over the visual design of the
game. So the gun controller is simply rotating the gun model to point wherever
the player's cursor is aiming. In the future, we may want the player to actually
_hold_ the gun, but for now our player is still a simple, plain cube.

![GunController.png](/blog/CAGD370/GunController.png)

In the options above, you'll also notice an option to make the gun automatic.
This is for if we want to try controls more like Jetpack Joyride instead of
more familiar rocket jumping from Team Fortress 2.

# And Now the Bullets

Shooting bullets from a gun is pretty straightforward. Simply spawn a
projectile prefab from a specified location and orientation (I used an empty
game object that is a child of the gun model), then give it some force in
its forward direction. However, our game also needs bullets to propel or
launch the player away. So we also have behavior on our bullets when it collides
with the environment.

![BulletSettings.png](/blog/CAGD370/BulletSettings.png)

When our bullet collides with the environment, it checks whether the player is
within its blast radius then applies the blast force onto the player. The
amount of force is scaled based on how far the player is from the contact
point of the bullet, so that a blast closer to the player propels them more
than a blast from a distance.

You may have noticed that the gun controller also had a similar recoil force
property. I was thinking that the flexibility of specifying the force of  
firing the gun, and the force of the bullet exploding would be beneficial
when creating several different guns with various feels. For example, a
grenade launcher may have a little fire force but a lot of explosive force,
while a sniper rifle may have a lot of recoil force but may not explode much.

# Other Changes

Now that we have the main gimmick of our game available for testing, We can
begin to fix and fine tune some of the parameters of the camera and player
controller. While playtesting, I realized that the camera needs to be
_quite far_ from the player for a comfortable playing experience. The
explosion from bullets rapidly changes the trajectory of the player, which
is really hard to correct when the camera is really tight with the player.

Another aspect of the controls that changed was the player's influence of
movement while airborne. Originally, I wanted the player to rely on the
recoil from firing guns and the explosive force of bullets to change
their trajectory, so I drastically horizontal movement influence when the
player is airborne. However, I realized the player can easily be sent in
the wrong direction when you limit the rotation of the camera. It is also
harder to correct your trajectory when some bullets don't give a lot of
vertical movement. Increasing the player's horizontal movement influence
seems like a simple solution to this problem, although its values may need
even finer tweaking if we still want to discourage this type of movement.
