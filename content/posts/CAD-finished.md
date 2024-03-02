---
title: "Layer-by-Layer"
date: 2024-01-16T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- Design
---


# Layer by Layer: Assembling Victory with Our 3D-Printed Pi Wars Gladiator #
## The Journey to the Final Design
In our quest to build a formidable contender for Pi Wars 2024, we've reached a significant milestone: the completion of the CAD design for our robot's "final" base. This design represents not just the culmination of our efforts thus far but also a blueprint for the exciting steps ahead.

Initially, we envisioned a chassis that doubled as a PCB. However, practical considerations led us to separate these elements, opting for a design that emphasizes cost-efficiency and flexibility. After much deliberation, we chose a 3D printed chassis, favoring its adaptability and the slight give it offers – a nod towards a primitive suspension system that keeps all wheels firmly on the ground.

Our design philosophy hinges on modularity, with separate mounts for each component, ensuring that future changes necessitate replacing only the parts directly affected. This approach allows for rapid prototyping and iteration, crucial for a project where design evolution is inevitable.

## Design Specifics and Revisions
The robot is built to accommodate:

* 4x 22mm gearmotors with encoders
* Two steerable wheels, powered by RS-3878MGT servos
* A choice between 49mm, 89mm, or Mecanum wheels
* Quad TF-Luna ToF sensors for all-directional navigation
* BNO08X IMU and R617XL CPPM receiver for precise movement and control
* A Raspberry Pi 3B heart, paired with a custom PCB featuring an RP2040 chip, overseeing motor control, power management, and communication

Our latest design review and subsequent adjustments reflect a meticulous approach to optimization. We've reconfigured motor placements for better wire management, enhanced the electronics mount to prevent SD card displacement, and added features like cable tie points and embossed labels for ease of use. Importantly, we've addressed potential clashes between components, ensuring everything from the OLED display to the USB sockets fits without issue.

## Next Steps and Expectations
With the CAD and PCB designs finalized, our focus shifts to assembly and testing. We're in the process of acquiring the remaining components, ensuring we have everything needed to bring our robot to life. This phase includes ordering specific parts like the GNB 930mAh battery and Adafruit BNO08X IMU, alongside general hardware like rocker switches and OLED displays.

As we proceed, we're mindful of the challenges ahead. The integration of cosmetic covers and the finalization of the robot's aesthetic appeal remain on our to-do list, promising to blend form with function in our quest for artistic points.

## Reflections
This blog post not only marks a pivotal point in our project but also serves as a testament to the power of iteration and flexibility in robotics. Our journey, filled with both challenges and triumphs, underscores the importance of adaptability and the relentless pursuit of improvement.

We're excited about the road ahead, eager to see how our robot will perform in the competitive arena of Pi Wars 2024. Stay tuned for more updates as we gear up for the challenges and opportunities that lie in wait.


[![Isometric Robot Render](resized_isometric-render.png "Isometric view of the robot highlighting the internal structure and wiring")](isometric-render.png)
[![Top View with Components](resized_top-view.png "Overview of the robot's top with all components in place")](top-view.png)
[![Top Isometric View](resized_top_iso.png "Isometric view from the top of the robot")](top_iso.png)
[![Bottom View](resized_bottom-view.png "Bottom perspective of the robot showing the wheel arrangement")](bottom-view.png)
[![Top View](resized_top.png "Top down view of the robot's internal components")](top.png)
[![Auxiliary XT30 Connector](resized_aux_xt30.png "Close-up view of the auxiliary XT30 connector integration")](aux_xt30.png)
[![Chassis with Hidden Wiring](resized_chassis-hidden-to-show-wiring.png "Internal wiring layout within the robot's chassis")](chassis-hidden-to-show-wiring.png)
[![Isometric View of Chassis and Wiring](resized_chassis-hidden-to-show-wiring-isometric.png "Isometric view revealing the robot's wiring scheme")](chassis-hidden-to-show-wiring-isometric.png)
[![SD Card Retainer Top](resized_sd-card-retainer-top.png "Top view of the SD card retainer in the robot")](sd-card-retainer-top.png)
[![SD Card Retainer Screw](resized_sd-card-retainer-screw.png "Close-up of the SD card retainer and its securing screw")](sd-card-retainer-screw.png)
[![Switch Labels](resized_switch-labels.png "Detail of the switch labels on the robot's chassis")](switch-labels.png)
[![Top View of Wire Routing](resized_top-view-of-wire-routing-around-motors.png "Top view showing the wire routing around the motors")](top-view-of-wire-routing-around-motors.png)
[![Pi PCB USB Cable Routing](resized_pi-pcb-usb-cable-routing.png "The Raspberry Pi PCB with USB cable routing")](pi-pcb-usb-cable-routing.png)
[![Wiring Around PCB](resized_just-the-wiring-around-pcb.png "Focused view on the wiring around the robot's PCB")](just-the-wiring-around-pcb.png)
[![Wire Routing Around Motors](resized_wire-routing-around-motors.png "Detailed routing of wires around the robot's motors")](wire-routing-around-motors.png)
[![Battery Caddy](resized_battery-caddy.png "Design of the battery caddy holding the power source")](battery-caddy.png)
