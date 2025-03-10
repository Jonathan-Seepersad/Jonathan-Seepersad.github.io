---
title: 'EPortfolio Post 1: Starting a team-based project'
date: 2025-03-08T18:47:39-08:00
draft: false
description: ""
author: "Jonathan Seepersad"
keywords: []
---

# Background

For this project, we were tasked with creating game prototypes as small groups, except this time we are trying to utilize Agile and Scrum methodologies. Our group is made of three people with the roles of Producer, Game Designer, and Developer. I chose to be the developer of the group as I wanted to showcase my programming prowess and manage the creation of the software for our game (however, all of our team members might contribute code to the repository as needed).

# Our project

Our team wanted to create a game based on the "rocket jump" ability, where players shoot a weapon, and the recoil/shockwave of the weapon propels the player. We intend for this to be a 3D platformer and want to encourage players to utilize this ability over traditional forms of locomotion in platforming games (i.e. WASD). We decided on using the Unity game engine our team was more familiar with it. 

# My tasks

As the developer, the first task I had was to set up the project and git repository. After creating these and ensuring each team member had access to the repository, I began implementing a custom 3rd person player controller to use for the player.

### Camera controller

The first component of the 3rd person controller is the camera controller. I've created simple camera controllers in the past where the camera is transformed offset from the player. However, as the player needs to aim to shoot, I realized that the player could not be in the center of the screen. So I designed this camera controller to track a point that is offset from the player rather than the player itself.

![alt text](</blog/CAGD370/CameraController.gif>)

Another part of the camera controller we thought was important was to prevent it from clipping through walls and obstacles. I tried a simple solution to address this problem by raycasting from the player to the target point. Then, from the hit point, we do another raycast going out in the direction of the cameras azimuth. This does prevent the camera from clipping but may need improvements in the future as the camera moves too quickly when near a wall.

### Player controller

After the camera controller I started working on a player controller so we can start moving the player. In previous classes, we'd normally use a rigid to control the player with physics. However, trying to program a 3rd person movement controller with it just didn't feel right. Rigidbodies move players by applying forces on itself, or by setting velocity. Trying to work with forces can be cumbersome when you want the player to predictably start and stop moving. Trying to work with velocity also faces other challenges as you want to still maintain some of the previous velocity.

Unity has another component called `CharacterController` which, appears like a stripped down collider object in Unity that we can move without it phasing through objects. It is sort of like translating a rigid body but feels a little bit more stable (plus it doesn't rotate).

Using this character controller, I can keep track of horizontal and lateral (parallel to the ground plane) velocities separately. This allows me to control jumping and gravity, while separately controlling the players directional movement.

Character controllers don't really have physics applied to them (aside from colliding with objects) so one issue I had to address is controlling vertical velocity when player hits the floor or hits a ceiling. In my implementation, I check whether the player is grounded, and cap the vertical velocity to not be less than zero (the the player isn't constantly accelerating downwards). 

Ceilings is only slightly trickier though. The way I handled this was to check when the character controller collides with an object when moving upwards, get the collision normal, and check if it is facing downwards. If so, set the vertical velocity to 0 so it can begin falling down. This method ensures players bounce downwards rather than float when hitting a ceiling, but it also allows players to jump and be pushed by slanted ceilings.

![alt text](</blog/CAGD370/PlayerMovement.gif>)

Again, similar to the camera controller, I still think the player controller can be improved. However it is a start that works and allows us to move forward with our prototype, allowing us to make a build that playtesters can give us feedback on. In the future, we'd like the player to roll when blasted away, so we may end up needing to add a rigidbody with out character controller in the end.