---
title: "Application Accepted"
date: 2023-10-06T16:53:06+01:00
draft: false
---

# Preparing for Pi Wars 2024: Challenges and Innovations #
Great news, everyone! We're thrilled to announce that we've successfully secured a spot in the Pi Wars 2024 competition. Our journey to Pi Wars continues, and we're eager to share more insights into our robot's development and our strategies for conquering the challenges ahead.

## Eco Disaster: Sorting Sustainability ##
Our approach to the Eco Disaster challenge involves collecting all barrels into two sorted barrel storage cartridges, using a specially designed collection mechanism. To bring this concept to life, we've created a test rig to fine-tune the attachment.

**The Catapillar Track Barrel Mover**: This mechanism shows promise, but we're working on enhancing its grip to ensure it can efficiently push all six barrels back into the cartridge.


[Insert Video of the Mechanism in Action]

[![top view of the barrel collecting mechanism](resized_top.jpg "top view of the barrel collecting mechanism")](top.jpg)[![bottom view of the barrel collecting mechanism](resized_bottom.jpg "bottom view of the barrel collecting mechanism")](bottom.jpg)

We've also printed a full set of barrels so we can get a better idea of how to handle and store them, and to allow us to test the handling mechansim. Since we ran out of filament, some are ABS, some PLA, so they're two different shades of green. Hopefully testing with these will help us ensure that the colour detection method is robust.

[![12 printed barrels)](resized_barrels.jpg "barrels")](barrels.jpg)[![barrels of different shades of green)](resized_different-greens.jpg "shades of green")](different-greens.jpg)


**Barrel Storage Cartridge Design**: For optimal efficiency, we envision the barrel storage system as two interconnected U-shaped structures—one on top and one below. The barrels will be completely encased within a cartridge that can be ejected as a single unit, hopefully a faster and more reliable approach than collecting and ejecting individual barrels.


[![An empty barrel storage cartridge](resized_emptyCartridge.PNG "empty barrel storage cartridge")](emptyCartridge.PNG)
[![An expanded barrel storage cartridge full with 6 barrels](resized_fullCartridge.PNG "expanded barrel storage cartridge full of barrels")](fullCartridge.PNG)

**Sensor Integration**: We plan to equip the main chassis with three distance sensors and an IMU. This sensor array will enable us to establish an absolute position within most of the arenas, ensuring precise navigation for challenges like Minesweeper, Eco Disaster, and Pi Noon. In other challenges, like Escape Route, Lava Palava, and Obstacle Course, we'll rely on relative positioning, possibly supported by Monte Carlo localisation methods.

**Sensor Fusion with Kalman Filtering**: Our strategy involves using a Kalman filter to combine odometry-based position estimates with absolute sensor-based positioning. However, there's a concern about the TF-Luna sensor's speed. We need to verify whether its readings, while described as outputting at 250Hz, truly represent unique values or if they are repeated due to lower update rates.

**Navigating the Barrel Challenge**: One potential challenge we've identified is that barrels may catch on the edge of the forks, getting pushed close to the wall. To address this, we're planning a multi-step approach. First, a broad sweep of the arena to cover most of the area. Then, we'll perform a spin on the spot sweep to catch any stragglers. Finally, we'll use additional sensors to detect and approach missed barrels. We're considering adding another Time-of-Flight (ToF) sensor or a camera for this purpose. Our goal is to make the missed barrels stand out clearly.

[!["Two routes considered for a broad sweep of the arena to collect barrels"](ecodisaster_routes.PNG "Two routes considered for a broad sweep of the arena to collect barrels")](ecodisaster_routes.PNG)

**Barrel Collection Forks**: To ensure maximum efficiency, the barrel collecting forks will be designed to retract and conform closely to the wall. This design will enable us to pick up straggler barrels from various angles. The arms may need to be curved, telescopic, or multi-segmented to fit within the allowed space envelope.

**Obstacle Course**: Navigating the Unknown
The Obstacle Course challenge presents unique hurdles that are difficult to plan for in advance. Full autonomy might be challenging, given the unpredictable nature of the obstacles. To address this, we're considering a hybrid approach. We'll aim to attempt most of the challenges autonomously, but switch to manual control where autonomous is unlikely to work.

**UWB Sensors for Absolute Position**: We plan to leverage UWB sensors to establish an absolute position within the obstacle course. With the course layout and allowed areas prefined, our code will hopefully calculate the route based on the layout.

**Improved PID Tuning**: We recognize the need to enhance our PID tuning and approach to handle slopes (compared to how Tauradigm performed), ensuring smooth navigation on uneven terrain. This may involve incorporating feedback from the IMU's inclination or refining the integral (I) term of the PID controller.

## Exploring New Possibilities ##
In our quest for innovation, we're also exploring new hardware possibilities. Rob has introduced an ESP32 setup with an interactive serial console, a separate logger, and task scheduling. This versatile board offers built-in hardware peripherals and could serve as a valuable addition to our Pi Wars platform.

[Insert Image of the ESP32 Test Setup]

Additionally, as we progress, we're mindful of the benefits of a compact robot design for certain challenges like Escape Route, Lava Palava, and Obstacle Course. We've made our chassis as small as practical while ensuring space for essential electronics. Collaboration is key, and we're considering the transition from Solidworks to  Fusion for seamless teamwork.

[![Old, wide CAD, for comparison](resized_CADAugust.PNG "Old, wide CAD, for comparison")](CADAugust.PNG)
[![New smaller CAD with new steering linkage](resized_CADoctober.PNG "New smaller CAD with new steering linkage")](CADoctober.PNG)

As we continue our preparations, the excitement builds. Stay tuned for more updates on our Pi Wars journey, where challenges are met with innovation, and every obstacle is an opportunity for growth. Together, we're navigating the path to Pi Wars 2024, and the adventure has only just begun.