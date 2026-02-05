---
title: "Blog 1"
description: ""
date: 2026-02-05T12:13:41-08:00
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

So begins another group games project. This time of a larger group of 9 teammates. Our team, called "Double AA Games", are working to create "Rumble Rally". A couch multiplayer RC car game, where players control cars and battle each other with weapon attachements.

I was tasked as the programmer, and also took charge of handling the Git repository.

## Car Controls and Acceleration

To start off, I started setting up a basic car using Unity's `WheelCollider`s. As it's the start of our project, I didn't have a model to use for testing, so I decided to use one of the assets from Kenney's [Racing Kit](https://kenney.nl/assets/racing-kit) (I've mentioned these in the past, but it's a really great place to get some nice clean assets for starting out!). After importing the model, I just add the wheel colliders to each of the car's wheels, adjust the parameters to fit the size of the wheel model, and modify the car's weight to work with the car's suspension system.

After that, I set up Unity to use the new input system and connected the right trigger to control the throttle so we can move our car.

{{< video
    src="/blog/CAGD495/CarAcceleration.webm" >}}

## Steering Controls

After that, I worked on getting steering to work using one of the joysticks. Initially, the controls for the car was supposed to be something like move the stick right to steer clockwise and move the stick left to steer counter clockwise, though I noted that this control scheme may be unintuitive if we use a top-down view of all the cars. Instead I suggested a control scheme where a target comes out of from the player in the direction of the joystick relative to the current camera view, and the car steers to the direction of that target.

It sounds a little confusing to explain but makes a lot more sense when visualized. See the following video, there is a little red target showing the direction that the gamepad's stick is pointed in. The wheels turn so that they steer the car into the direction of that target.

{{< video
    src="/blog/CAGD495/Steering.webm" >}}

These controls are a little more complicated, relying on some math to get the steering angle given a target. However, I created something similar in a previous project where I had AI cars steer to the direction of a player ([reference](https://github.com/Jonathan-Seepersad/CarGame/blob/3368477646e97617a09ebbf9a9b6285cde1aea12/Assets/Scripts/AICarControl.cs#L44-L47)), so I adapted it to point to this target instead of another player.

I've also created a `WheelController` script attached to each of the `GameObjects` for each of the wheels to rotate according to the orientation of the `WheelCollider`s. By default, the `WheelCollider` does not control the orientation of whatever `GameObject` it is attached to, so you have to retrieve its transformation each frame and apply that to the wheel's model objects.

## Stopping and Braking

You might've noticed that in the last video, the car was veeery slippery when trying to steer and turn. This was also becoming a problem with braking as the car would still continue to slide for quite a while when applying brakes. I'll need to become more familiar with the values in `WheelCollider` as a lot of these cryptic values influence how responsive the car feels when accelerating, how grippy the car feels when steering, and how stable the car feels overall.

For the purposes of braking, I've found [a nifty hack](https://discussions.unity.com/t/car-wheels-not-stopping-when-i-brake/673158/7) where you apply drag to the car's rigidbody. This makes the car rapidly come to a stop (depending on how much drag is applied) without worrying about any slip values (it sorta works like airplane "air brakes"). 

{{< video
    src="/blog/CAGD495/Braking.webm" >}}

As shown in the video, it is *incredibly* effective and responsive but has a few caveats:

1. Braking with drag also appears to brake the car when falling! This is a simple fix though, just check if any of the wheel colliders are grounded before applying the air brakes.
2. Drifting won't work with these types of brakes. We want our car to have drifting controls eventually. However, drifting works by losing traction (through braking) in certain wheels instead of simply braking. Drifting relies on a certain amount of slip.

Because of this, I'll need to research in more depth the values of the `WheelController` to figure out how to finely tune the grip and traction for greater drifting controls. Though this airbraking system may still be handy for immediately stopping a car. For example, when both the brake control and throttle controls are both held the car will switch to drift mode, but when only brake controls are held the car will switch to air braking.

## Problems and TODO

Currently I'm working on experimenting with the settings to make the car drift more naturally. Though it is cumbersome to individually change the settings of each wheel in code the way that is impelented right now. So I'm working on a new system that'd give us a little more flexibility with managing the settings of different types of wheels.

Currently, wheels are handled with individual fields allowing us to adjust it's settings directly using this reference.

```csharp
[Header("Wheels")]
[SerializeField] private WheelCollider frontLeft;
[SerializeField] private WheelCollider frontRight;
[SerializeField] private WheelCollider rearLeft;
[SerializeField] private WheelCollider rearRight;

public float FrontAcceleration
{
    get => (frontLeft.motorTorque + frontRight.motorTorque) / 2;
    set => frontLeft.motorTorque = frontRight.motorTorque = value;
}
```

Though when I want to apply settings to multiple wheels at once, I need set each wheel manually. Which, if I start to deal with slip values, gets pretty long and very messy.

So I'm switching to a system where I'll have an array of wheel controllers that I can add to the wheel model `GameObject`s. Each of these wheel controllers creates their own `WheelCollider` on new `GameObject`s so I'm able to apply settings either through the player or this new class.

```csharp
private ImprovedWheelController[] wheels;

private void Start() =>
    wheels = GetComponentsInChildren<ImprovedWheelController>();
```

These new wheel controllers also contain a few enums which indicate whether the wheel is part of the front or rear axel, and whether the wheel is on the left or right side. Which allows me to do something like this

```csharp
// Utility class to apply changes to wheels of a particular axis/side
public static class WheelControllerUtil
{
    public static bool Filter(
        this ImprovedWheelController wheel,
        WheelAxel? axel, WheelSide? side
    ) => (axel == null || wheel.axel == axel) &&
         (side == null || wheel.side == side);

    public static void Apply(
        this ImprovedWheelController[] wheels,
        Action<ImprovedWheelController> fn,
        WheelAxel? axel = null, WheelSide? side = null
    )
    {
        foreach (var wheel in wheels)
            if (wheel.Filter(axel, side))
                fn(wheel);
    }
}

// Allowing us to directly set all wheels accordingly like so:
private void Accelerate(float torque, WheelAxel? axel, WheelSide? side) =>
    wheels.Apply(
        wheel => wheel.wheelCollider.motorTorque = torque,
        WheelAxel.Front // Filter only on front axel wheels
    );
```

This new system would also give more flexibility for cars with an amount of wheels inequal to 4, and could also handle wheels breaking off of the car, but is still work-in-progress at the moment as I explore each of the parameters of `WheelCollider`s.