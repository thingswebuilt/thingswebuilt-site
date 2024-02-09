---
title: "Mega Loops"
date: 2023-11-17T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- Control
- Software
---

# Mastering Control Systems in Robotics: Lessons from Team Cyberwar's Journey
In the intricate world of robotics competition, such as Pi Wars, developing a control system that balances responsiveness, stability, and precision is paramount. Our journey with Overwhelming Surplus of Diggity (OSoD) has not only been about overcoming technical hurdles but also about extracting valuable lessons that can guide others in the robotics community. Here, we share insights into determining the optimal update rate for robotic control systems, drawing from our experiences and challenges.

## Understanding Update Rates:
The update rate of a control system, expressed in Hertz (Hz), is fundamental to a robot's ability to interact with its environment effectively. This rate influences how frequently the system processes sensor inputs, executes control algorithms, and updates actuators. 

## From Mega Loops to Pseudo Real-Time Systems:
Gone are the days of our robots running mega loops where every function is called in every loop without timeouts—an approach fraught with inefficiency. Instead, OSoD is evolving towards a more sophisticated system, employing a pseudo real-time operating system (RTOS). This system not only schedules tasks effectively but also incorporates timeouts to ensure that intermittent sensor or joystick connections don't derail our entire loop. Through our development of OSoD, we've identified several critical factors to consider:


## Task Initiation and Frequency Considerations:
### Fixed Loop vs. Interrupt-Driven Architectures:
In our exploration, we've encountered two primary software architectures for robotic control systems: fixed-loop and interrupt (or "push") based. Fixed-loop architectures operate on a consistent cycle, executing tasks at set intervals regardless of input changes. This approach offers predictability but can sometimes lag in responsiveness to sudden environmental changes. Its important with a fixed-loop approach to have timeouts on tasks, so that a glitch can't ruin the update rate of everything else.

Conversely, interrupt-based systems react to new inputs as they're received, prioritizing tasks based on the immediacy of the data. This method can significantly enhance responsiveness, particularly for autonomous operations where adaptability is key. For OSoD, balancing these approaches has been a cornerstone of our strategy, ensuring that it remains agile and responsive in the dynamic challenges of Pi Wars. It can make control system tuning challenging though, as the update time period may not be consistent.

Incorporating structures that initiate tasks based on new data inputs, such as a fresh camera frame or sensor reading, offers a streamlined workflow. An illustrative example is the Pi Wars openCV [sample code](https://www.piborg.org/blog/build/diddyborg-v2-examples-ball-following) for the "Over the Rainbow" challenge, which employs this method effectively.


## The Heart of Our Strategy: Loop Frequency Optimization:
For Pi Wars, where challenges like "Pi Noon" and "Lava Palava" demand both agility and precision, understanding and optimizing the frequency at which different tasks run is paramount. A swift robot, moving at 1m/s, can cover significant ground between updates—a fact that has pushed us to reconsider how we structure our code and task scheduling. A critical aspect of task scheduling is determining the desired frequency for each task. While higher frequencies are generally advantageous, they are often constrained by hardware capabilities. 

* Determining Update Rates: We've carefully considered how far OSoD might travel between updates, and how responsive the mechancial system might be. For critical functions like motor pulses, encoders and IMU readings, which influence OSoD's immediate reactions and navigation, we've aimed to exceed the 50Hz mark, pushing for faster and more responsive control.

* Managing Task Frequencies: While high-frequency updates are crucial for some elements of navigation and control, we've recognized that not all components require the same level of attention. While a human driver might barely perceive a 150ms delay in remote control operation, for an autonomous robot like OSoD traveling at 1m/s, this lag translates to a 150mm journey—an ample distance that could mean the difference between successfully navigating an obstacle or colliding with it.

## Real-World Timing and Hardware Considerations:
The variability of loop times on a Pi OS, influenced by the operating system's task prioritization, underscores the importance of regular monitoring to identify potential bottlenecks. To circumvent these challenges, we've transitioned high-frequency tasks to microcontrollers, ensuring faster and more consistent execution.


## Closing Thoughts:
The journey to Pi Wars with OSoD has been as much about technical optimization as it has been about strategic insights. By sharing our experiences, we aim to illuminate the path for others in the robotics community, highlighting the intricacies of control system design and the profound impact of seemingly minor factors like software architecture choice and lag management.

## Looking Forward:
The road ahead is filled with opportunities for further exploration and development. By continuing to refine our programming techniques and understanding of both mechanical and software systems, we pave the way for more sophisticated and capable robots.

As we navigate this intersection of disciplines, the potential for innovation is boundless. The challenges we face today inspire the solutions of tomorrow, driving us toward a future where robots are not only faster and more efficient but also more intelligent and adaptable.

!["A detailed illustration of a robotic workshop with a focus on a robot under development. The scene includes a laptop displaying code, a robot chassis on a workbench surrounded by various tools, and components like sensors and microcontrollers. The environment suggests a fusion of mechanical engineering and software development, highlighting the complexity and innovation in robot programming. Visual elements should emphasize the transition from traditional mechanical designs to incorporating advanced software solutions."](robot.jpg "A detailed illustration of a robotic workshop with a focus on a robot under development. The scene includes a laptop displaying code, a robot chassis on a workbench surrounded by various tools, and components like sensors and microcontrollers. The environment suggests a fusion of mechanical engineering and software development, highlighting the complexity and innovation in robot programming. Visual elements should emphasize the transition from traditional mechanical designs to incorporating advanced software solutions.")