---
title: "Blueprints to Bytes"
date: 2023-11-30T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- progress
- art
---

# Navigating the Circuit: From Blueprint to Reality in Our Robot's Software Architecture
In the dynamic world of robotics, the journey from a meticulously crafted plan to its practical implementation is often as fascinating as the challenges the robot is designed to overcome. As Team Cyberwar gears up for Pi Wars 2024, our ambition to showcase the prowess of full autonomy in robotics has led us to chart out an intricate software architecture blueprint. However, as we delved into the nuances of making this vision a tangible reality, we've navigated through a maze of adaptations and innovations. This blog post explores the evolution of our robot's software architecture, highlighting the contrasts and similarities between our initial plan and the system we've built.

## The Blueprint: Our Planned Software Architecture
Our vision for a cutting-edge robot included a software architecture designed for robustness, modularity, and scalability. The planned architecture comprised several core components, each responsible for a distinct aspect of the robot's functionality:

**State Estimator**: To fuse sensor data into a coherent model of the robot's state, including position, orientation, and velocity.

**Navigator**: To generate high-level navigation commands based on waypoints or direct inputs, steering the robot through its environment with precision.

**State Manager**: To translate navigation commands into actionable changes, controlling actuators to achieve the desired state.

**Drive Train Config**: To encapsulate the physical attributes of the robot, informing the system of its capabilities and limitations.

Interfaces and datatypes were to be standardized across components, facilitating seamless data flow and component interchangeability. Timing mechanisms would ensure tasks were executed at precise intervals, crucial for maintaining real-time responsiveness. Data logging was envisioned as a comprehensive system for recording a wide range of metrics for debugging and optimization.

## The Reality: Implementing the Software Architecture
Transitioning from plan to practice, each component evolved, reflecting the complexities and demands of real-world functionality:

### State Estimator
The reality of implementing the State Estimator underscored the sophistication required in processing and integrating diverse sensor inputs. Utilizing data from the BNO080 IMU for orientation and the TF-Luna LiDAR for distance measurement, the estimator now serves as the robot's sensory hub, providing accurate, real-time updates on its physical state.

### Navigator
The Navigator, designed to transform high-level goals into actionable directives, became more than a simple path planner. Incorporating feedback from the State Estimator and inputs from a custom waypoint navigation system, it dynamically adjusts routes, optimizing for efficiency and obstacle avoidance. This component proves crucial in autonomously navigating the disaster-themed challenges of Pi Wars, from navigating mazes to avoiding zombies.

### State Manager
The State Manager's role expanded significantly beyond initial expectations. It now integrates closely with both the Navigator and the Drive Train Config, employing a sophisticated control loop to precisely manage the robot's movements. By leveraging a combination of PID controllers and a custom mixer strategy (including Ackermann steering logic), it ensures smooth, responsive control over the robot's actuators.

### Drive Train Config
Reflecting the need for adaptability, the Drive Train Config evolved to include a wider range of settings, allowing for adjustments based on the current challenge or environmental conditions. This configurability enhances the robot's performance across different terrains and tasks, from speed runs to precision maneuvers.

### Serial Monitoring
In lieu of a full-fledged data logging system, our firmware has initially adopted a pragmatic approach to monitoring and debugging. Utilizing serial prints, we managed to keep a close eye on the robot's state and behavior during development and testing. While this method lacks the sophistication of our envisioned data logging platform, it has been instrumental in our iterative tuning process, providing immediate insights into the system's performance.

## Bridging the Ideal and the Achievable
This journey from our planned architecture to the realized firmware underscored the importance of flexibility and pragmatism in robotics. The serial print-based monitoring, while a stopgap compared to our ambitions for a comprehensive data logging solution, exemplifies the iterative nature of development in which immediate insights can drive substantial improvements.

**Real-Time Insights over Sophisticated Logging**: The absence of a dedicated data logging system on the Pi led us to rely on serial prints for real-time monitoring. This approach, while rudimentary, enabled us to track the robot's performance closely and make necessary adjustments on the fly.

**Firmware-Centric Control**: With the Pi side of the system remaining undeveloped, our firmware took on the full breadth of control responsibilities. This consolidation highlighted the firmware's robustness and versatility, handling everything from sensor integration to actuator control, and even rudimentary monitoring.

## Looking Ahead
As we reflect on our journey, it's clear that the path from vision to implementation is as much about the adjustments we make as the milestones we achieve. The firmware stands as a testament to our adaptability and commitment to the project's core objectives. Looking forward, the development of a comprehensive data logging system and the integration of Pi-based controls remain on our horizon, promising to elevate our robot's sophistication in the competitions to come.

In this adventure of turning blueprints into bytes, we've not only crafted a robot capable of facing the challenges of Pi Wars but also laid the groundwork for future innovations and improvements. As we gear up for the challenges of Pi Wars 2024, our robot's software architecture stands as a beacon of what's possible when vision meets versatility.

![A sleek, futuristic robot navigating a complex maze, symbolizing the evolution from initial software architecture plans to a fully functional firmware. The robot, equipped with various sensors and actuators, is shown in the process of dynamically adapting its route based on real-time data analysis. The background is a stylized representation of software code and circuitry, blending into the maze to illustrate the integration of hardware and software. The overall atmosphere is one of innovation and precision, with a color palette that suggests technology and the digital world.](DALL·E_2024-03-19_00.02.50-A_sleek_futuristic_robot_navigating_a_complex_maze.png "A sleek, futuristic robot navigating a complex maze, symbolizing the evolution from initial software architecture plans to a fully functional firmware. The robot, equipped with various sensors and actuators, is shown in the process of dynamically adapting its route based on real-time data analysis. The background is a stylized representation of software code and circuitry, blending into the maze to illustrate the integration of hardware and software. The overall atmosphere is one of innovation and precision, with a color palette that suggests technology and the digital world.")
