---
title: "Gearing Up"
date: 2023-09-23T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- Design
---

## Preparing for Pi Wars 2024: Building the Overwhelming Surplus of Diggity ##

Pi Wars 2024 has been announced, and we're gearing up for the challenges ahead. This time, the competition revisits the Disaster theme from 2020, and we're excited to take on the challenges with our latest creation, the Overwhelming Surplus of Diggity (OSoD). In this post, we'll dive into our journey so far, the design choices we've made, and how our past experiences have shaped our approach.

### A Trip Down Memory Lane ###

Our last in-person Pi Wars event was back in 2018 with Piradigm. Since then, we've been building and entering robots in subsequent Pi Wars, but fate had other plans. Whether it was overcommitting or event cancellations, we hadn't quite made it back to the competition floor.

In 2020 and 2021, we submitted videos, but Tauradigm, our robot, was never truly finished. Despite this, we made significant progress on attachments for the 2020 challenges, and those developments might prove invaluable this time around.

Since 2021, we've been working on a new platform called Overwhelming Surplus of Diggity (OSoD). While it hasn't yet reached the rolling testbed stage, we believe it has great potential for this year's Pi Wars. 

### OSoD: A Different Approach ##

![Overwhelming Surplus of Diggity (OSoD)](OSoD.PNG "Overwhelming Surplus of Diggity (OSoD)")

OSoD takes a unique approach that's somewhat uncommon at Pi Wars—a robot with car-like steering. Most competitors tend to avoid this due to its complexity and limited turning circle. However, we believe it offers distinct advantages, especially for autonomous challenges that require accurate and repeatable odometry and path following.

Our design, originally intended for the 2022 "Pi Wars At Home" challenges, features four 22mm gearmotors with encoders and 50mm Lego tires on a PCB chassis. Its low, flat, and wide design ensures stability, even when loaded with attachments.

## Revisiting Disaster Challenges ##

Now, let's examine how our attachment designs from the 2020 Disaster-themed challenges fare for Pi Wars 2024:

### 1. Zombie Apocalypse

{{< youtube u6rlgQtok3k >}}

In 2020, we crafted a formidable  Nerf ball flinger with impressive accuracy. Equipped with custom flywheels and a servo feed mechanism, it showed great promise. The attachment could tilt up and down, but we're contemplating adding pan control. While our hardware was robust, the software side needs a fresh start to handle different target heights. OSoD seems well-suited as it provides a low and stable base.


### 2. Minesweeper

{{< youtube 7Yx5ufqt2QU >}}

For Minesweeper, covering a large surface area is advantageous, as helps it cover a larger area (driving doesn't have to be so precise), it wouldn't have to travel as far and a simple circular route can cover all "mines". Our previous design featured light sensors on each corner, helping the robot detect and stop at mines. A large frame enabled efficient coverage. Our approach was to try to drive in a roughly circular path, ensuring we passed over all squares containing mines. OSoD's car-like steering should be an advante for precise and reproducible circular driving, and its large size will again be beneficial.

### 3. Escape Route

![Tauradigm navigating the centreline route that narrowly avoids all block combinations](Tauradigm_blind_maze.PNG "Tauradigm on the blind maze")

Although we didn't develop a specific attachment for the Escape Route challenge, we discovered that a narrow robot could potentially navigate the course effectively by following a consistent, single route, regardless of the block configuration. Identifying the course configuration ahead of time could provide an advantage, possibly by using a camera to peer over the walls. OSoD's design, whilst a bit on the wide side, should still tackle this challenge well, thanks to its car-like steering.

### 4. Eco Disaster

{{< youtube OzQbOpFJwvE >}}

Eco Disaster presented us with a complex attachment and an onboard state machine-based control system. While we didn't complete the barrel identification or route planning code, we learned valuable lessons. We're now considering a simpler approach — storing barrels under the robot and following a predefined path with a wide corral attachment. OSoD's wide body aligns with this challenge, but we'll need narrow wheels and a means to raise the chassis to accommodate barrel storage.

### 5. Lava Palava

Lava Palava Challenge

We hadn't developed an attachment for Lava Palava, but we had planned to use the time-of-flight sensors onboard Tauradigm. OSoD also features time-of-flight sensors, although we'll need to evaluate if they are sufficient for this challenge. The car-like steering provides a clear advantage, and we may not require additional sensors for accurate navigation. We'll need to address the speed bump and consider if suspension is necessary.

### Bringing It All Together

In summary, our previously developed attachments should serve as valuable starting points, and OSoD appears well-suited to the challenges. Our plan is to integrate these attachments with a slightly modified, shrunken version of the OSoD platform we've been developing. With these combined efforts, we're confident in our preparation for Pi Wars