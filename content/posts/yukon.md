---
title: "Looping You In: Timing and Task Management in Robotic Choreography"
date: 2023-11-17T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- Electronics
---

The Robotics Revolution: Pimoroni's Yukon vs. Our Custom PCB
In the evolving world of robotics, the choice between modular platforms and custom-built solutions is a pivotal decision for teams. Pimoroni's recent release of the Yukon, a RP2040 based board, has sparked interest among robotics enthusiasts, including our team. Here's a closer look at how Yukon stacks up against our custom PCB designed for the Pi Wars robot.

The Core of Innovation: Pimoroni's Yukon
Pimoroni's Yukon emerges as a high-power modular robotics platform, built around the versatile RP2040 chip. Its standout feature is the ability to host up to six interchangeable modules, enabling a wide range of functionalities from motor control to sensory inputs—all without the need for soldering. With its XT30 connector, the Yukon can deliver up to 15A of continuous power across a 5V to 17V range, ensuring your projects are powered for any challenge. Its built-in e-Fuse and internal sensors add a layer of protection and monitoring, vital for the robust demands of robotics.

Our Custom PCB: Tailored Precision
In contrast, our custom PCB is a testament to the bespoke engineering that Pi Wars demands. Designed for a 3S battery configuration, it incorporates XT30PB power connectors and offers comprehensive protection mechanisms, including over-voltage, under-voltage, and over-current conditions. Our board supports four DC motors with encoders and integrates Electronic Speed Controllers (ESCs) capable of handling up to 4.5A peak current, ensuring precise control and power for maneuvering through Pi Wars' challenges. 

Comparison and Considerations
Size and Cost: The Yukon boasts a compact form (67 x 84 x 18mm), albeit taller than our custom PCB (63 x 100 x 10mm). This size difference offers a nuanced choice between footprint and functionality. Cost-wise, the Yukon, with necessary add-ons, comes to £87, whereas our custom PCB runs at £100 for two boards, with potential redesign costs pushing this to £200.

Voltage and Current Capacities: Both solutions offer robust power delivery systems, but our custom PCB is specifically tailored to our robot's requirements, with a focus on drive and motor control that can handle specific current capacities up to 4.5A peak per motor at 12V. Yukon edges ahead ehre with a maximum capacity of 8A at 17V

Flexibility and Future Upgrades: The Yukon's modular design affords significant flexibility, allowing for easy swaps and upgrades. Our custom PCB, while less modular, is designed for optimal integration and performance within our specific Pi Wars context, prioritizing efficiency and reliability over modularity.

Conclusion: The Path Forward
Pimoroni's Yukon is undoubtedly a formidable tool for many Pi Wars teams, offering an excellent blend of power, versatility, and ease of use. However, for our team, the custom PCB remains our champion. It represents a tailored solution that meets our exact specifications and requirements, offering a level of control and integration that off-the-shelf solutions cannot match. As we venture into Pi Wars 2024, we do so with a board that embodies our commitment to innovation and precision.

For those interested, we've made a 3D model of the Yukon available on GrabCAD, providing a valuable resource for other teams considering this powerful platform. As we embrace the challenges ahead, we're reminded of the importance of community, sharing, and pushing the boundaries of what's possible in robotics.


![Isometric render of Yukon with modules](iso-render-with-modules.png "Isometric render of Yukon with modules")
![Isometric render of Yukon bare board](yukon-iso-render-bare-board.png "Isometric render of Yukon bare board")
![Yukon in chassis under Pi](yukon-in-chassis-under-pi.png "Yukon in chassis under Pi")
![Yukon nestled under Pi](yukon-nestled-under-pi.png "Yukon nestled under Pi")
![Yukon nestled under Pi - side view](yukon-nestled-under-pi-side-view.png "Yukon nestled under Pi - side view")

[![PCB Top with Labeled Connectors](resized_pcb-top-labeled-connectors.png "Top view of the PCB with labeled connectors")](pcb-top-labeled-connectors.png)
[![PCB Top View](resized_pcb-top.png "Top view of the PCB")](pcb-top.png)
[![PCB Bottom View](resized_pcb-bottom.png "Bottom view of the PCB")](pcb-bottom.png)
[![PCB 3D Isometric View](resized_pcb-3d-isometric.png "3D isometric view of the PCB")](pcb-3d-isometric.png)
[![Wiring Around PCB](resized_just-the-wiring-around-pcb.png "Focused view on the wiring around the robot's PCB")](just-the-wiring-around-pcb.png)
[![Isometric View of Chassis and Wiring](resized_chassis-hidden-to-show-wiring-isometric.png "Isometric view revealing the robot's wiring scheme")](chassis-hidden-to-show-wiring-isometric.png)


![Feature image for a blog post comparing a custom PCB for a Pi Wars robot to Pimoroni's Yukon modular board](Create_a_feature_image_for_a_blog_post_comparing_a.png "Create a feature image for a blog post comparing a custom PCB for a Pi Wars robot to Pimoroni's Yukon modular board. The image visually represents the theme of innovation and competition in robotics, incorporating elements such as circuit boards, robot parts, and the Pi Wars and Pimoroni logos in a dynamic and engaging environment that suggests a technological showdown.")