---
title: "EPortfolio Post 5: Rumble Ralley - Improving Gameplay"
description: ""
date: 2026-04-09T11:27:11-07:00
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

Continuing on, getting closer to the deadline, I added some qulity of life improvements in this sprint. Last time, I added some sound effects and background audio, while I continued adding sound effects when the player crashes into something. I also added some items last time while I added another item and made modifications to some of our older items. And, just like last time, the charge meter also went through another minor change again.

# Charge Meter Changes

The charge meter was originally supposed to deplete after a player deals damage. However, as the charge meter's value is tied to the velocity of the car, this didn't really make too much sense. Instead, I suggested that after a player makes an attack, the charge meter switches to a depleted state and charges back to normal. During this depleted state, the player wouldn't be able to attack until after the charge meter has replenished. To indicate this, I made the charge meter change color to indicate the state it is in.

{{< figure
    src="/blog/CAGD495/NewChargeMeter.gif"
    alt="New Charge Meter"
    caption="Charge meter switches between colors when it is depleted, recharging, and ready"
>}}

Shown in the GIF above, the charge meter is initially yellow when ready to deal damage. When the player hits their opponnent, it switches to grey, and slowly changes to red as it replenishes. Once ready again, it switches back to yellow. The entire time, the charge meter reflects the player's velocity, though they are unable to attack in a depleted state.

Lastly, there was a mistake I made where I divided the velocity by the `Time.deltaTime`, which lead to the charge meter filling up differently depending on the refresh rate of the user's monitor. Instead, the velocity is supposed to be a direct value, not influenced by deltatime.

# Item Changes and Additions

The reasoning for the changes to the charge meter is because of the new item needed to be added, the fuel tank. It functions similar to the battery, boosting it's speed. However, the battery was intended to keep charge enabled while the fuel tank kept it enabled and full. Previously, it really just boosted speed as the charge meter didn't get disabled.

Also, to indicate the player's charge meter is affected by one of these power ups, I changed the color depending on the effect enabled. The battery, which keeps the charge meter enabled for a duration, changes the color to cyan. Meanwhile, the fuel tank, which keeps the charge meter enabled and full, changes the color to purple.

# Crash SFX

I also added sound effects when the player crashes into the wall or another player, just to make the effect more satisfying. It plays different sound effects at varying intensities, based on the player's impact force. The values in between each sound effects control the volume and pitch, just to add a little bit of variation.

{{< video
    src="/blog/CAGD495/CrashSFX.webm" >}}

As with the other sound effects, they are controlled by the option menu's SFX volume level as well.

# Minor QOL imrpovements

We also noticed, especially when there's a few small areas to spawn items (particularly noticeable when using only spawn points over spawn zones), items would often spawn on top of each other. So I made a minor modification to the spawner to only spawn items if the spawn location is a certain distance away from other items, as well as the player.

Finally, it also became a little too easy to flip your car over, rendering you unable to control your car anymore. So a new script was added to unflip the player if they flipped over and are unable to flip back after a set period of time.
