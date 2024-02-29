---
title: "Circuiting Success: The PCB That's Driving Us Forward"
date: 2024-01-23T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- PCB
- Electronics
- Design
---


# Powering Innovation - The PCB Behind Our Pi Wars Robot
## A Foundation for the Future
In our quest to dominate Pi Wars, the heart of our robot's prowess lies in a meticulously designed Printed Circuit Board (PCB), conceived and realized by our very own Robert K. This PCB is not just a circuit; it's the central nervous system of our entry, embodying innovation, resilience, and adaptability.

## Design Specification
* **Power**: 3S battery system with XT30 connectors and a barrel jack, featuring over-voltage, under-voltage, and over-current protection via eFuses. Onboard 3.3V and 5V regulation with high-efficiency switch-mode power supplies.
* **Drive**: Integrated 4.5A peak electronic speed controllers (ESCs) for four 22mm DC motors with encoders. Two servo channels are also included.
* **Sensors**: Support for four TF Luna I²C Time-of-Flight (ToF) range finders, a BNO080 IMU, and optional optical flow.
* **Communication**: RC receiver support via CPPM satellite or SBUS and an onboard SPI 2.23" OLED. USB or I2C attachment interface.
* **Processing**: A Raspberry Pi 3 B+ is permanently attached.
* **Board**: At least 1.6mm thick, two-layer or more, with silkscreen for debugging and fun features.

## Design Highlights
The PCB boasts an array of features tailored for the demanding arena of Pi Wars. It supports a 3S battery system enhanced with XT30 connectors, ensuring our robot is powered for performance while safeguarding against power anomalies through sophisticated eFuses. The inclusion of a barrel jack further diversifies our power options.

Efficiency is paramount, and our board doesn't disappoint. With onboard 3.3V and 5V regulation through high-efficiency switch mode power supplies, it ensures optimal power distribution to all components.

## Drive and Control
At its core, the PCB drives four 22mm DC motors, each with encoders, supported by built-in Electronic Speed Controllers (ESCs) capable of handling 4.5A peaks. This setup is complemented by two servo channels, highlighting the board's versatility in motion control.

## Sensory and Communication Prowess
Our robot's sensory array is powered by connections for four TF Luna I²C Time-of-Flight (ToF) range finders and a BNO080 IMU, providing unparalleled environmental awareness. Communication is facilitated through an onboard SPI 2.23" OLED and a versatile RC receiver, ensuring our robot remains in perfect harmony with its operators.

## Overcoming Design Challenges
The journey to the final PCB design was fraught with challenges, from navigating the volatile availability of motor drive chips to ensuring the board could accommodate the complex wiring and componentry required. Ultimately, the RZ7889 chip was selected for its robust performance, despite the heavy demands placed on it by our robot's weight and power needs.

## The Road Ahead
This PCB is more than just a component; it's a testament to our team's dedication to pushing the boundaries of what's possible in robotics. As we prepare for the trials of Pi Wars, we're confident that the foundation laid by this PCB will propel us to new heights of innovation and success.

Stay tuned for updates from the battlefield as we put our design to the ultimate test!

[![PCB Top with Labeled Connectors](resized_pcb-top-labeled-connectors.png "Top view of the PCB with labeled connectors")](pcb-top-labeled-connectors.png)
[![PCB Top View](resized_pcb-top.png "Top view of the PCB")](pcb-top.png)
[![PCB Bottom View](resized_pcb-bottom.png "Bottom view of the PCB")](pcb-bottom.png)
[![PCB 3D Isometric View](resized_pcb-3d-isometric.png "3D isometric view of the PCB")](pcb-3d-isometric.png)
