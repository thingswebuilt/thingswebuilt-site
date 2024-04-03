---
title: "Zombie Slayer: Engineering Precision for the Apocalypse"
date: 2024-03-24T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- testing
- Zombies
---

# Engineering Precision: The Odyssey of the Ball Flinger
In the world of robotics where theory meets practice, the journey from conception to completion is seldom a straight line. As we ventured into the realm of the undead for the Zombie Apocalypse challenge at Pi Wars 2024, our quest to develop the ultimate ball flinger attachment epitomized the iterative process of engineering innovation. This post delves into the trials, tribulations, and triumphs of bringing the ball flinger to life, underscoring the relentless pursuit of precision and performance.

## A Rocky Start
Our adventure began with high hopes and a clear vision, but we soon encountered the formidable challenges that accompany ambitious engineering projects. The initial tests of the ball flinger revealed a critical vulnerability — the motor's intolerance to being stalled, even momentarily. A piece of residual support material, a seemingly innocuous oversight, led to the motor burning out. This incident underscored the importance of meticulous testing conditions; a lesson learned the hard way about the necessity of using current-limited power supplies, which could have prevented the motor from drawing excessive current and overheating.

## The Quest for Reliability
Undeterred, we sought solace in the resilience of Ranglebox motors, known for their fortitude in the face of stalling. Yet, as one challenge was surmounted, another emerged. A loose flywheel heralded the demise of a speed controller, a casualty not of overcurrent, but perhaps of a voltage drop-induced failure. This unfortunate event highlighted the critical role of current-limited power supplies not just in motor protection, but that they can also in be responsible for electronic failure by causing the brownout conditions that can lead to failure. These setbacks, while frustrating, were invaluable lessons in the nuances of component selection, system design, and the pivotal role of regulated power delivery.

## Navigating the Software Maze
The software that breathed life into the ball flinger was a saga in its own right. The initial plan to harness the Pi Pico was abandoned in favor of an Arduino Nano, only to be thwarted by the limitations of serial communication. The switch to a Teensy, and finally, the full-circle return to the Pi Pico, exemplified the iterative nature of problem-solving in robotics. Each pivot was a step towards an optimal solution, driven by the constraints of Pi Wars-rule-requirements and the practicalities of remote control.

[![Microcontroller Selection Journey - A visual journey through the hardware selection process, showcasing the various microcontrollers evaluated.](sm_microcontrollers.jpg)](microcontrollers.jpg "Microcontroller Selection Journey")


## The Breakthrough
With the hardware and software hurdles gradually overcome, the ball flinger began to show promise. The integration of a laser guide and fine-tuning of the servo mechanisms marked the transition from concept to reality. Yet, it was the innovative use of aluminium foil to capture the imprints of the flinger's shots that provided the critical insight needed for refinement. This simple, yet effective method revealed a discrepancy in vertical accuracy, leading to an adjustment in the ball feeding mechanism — a lesson borrowed from past challenges.

[![Laser Targeting System - Demonstrating the laser guide mechanism for enhanced aiming accuracy.](sm_laser-targetting.jpg)](laser-targetting.jpg "Laser Targeting System ")
[![Innovative Testing with Aluminium Foil - Utilizing aluminium foil to capture the precision of our ball flinger's shots.](sm_foil-imprints.jpg)](foil-imprints.jpg "Innovative Testing with Aluminium Foil - Utilizing aluminium foil to capture the precision of our ball flinger's shots. the ball imprints are visible in the foil")


## Towards Autonomy
The realization that our autonomous performance didn't need to be flawless, but merely effective, to compete successfully was liberating. This strategic insight, coupled with the confirmation of a calibration period, offered a glimmer of hope. Our "3D scan" technique, while not perfect, became a key asset in our arsenal, promising the potential to discern targets amidst the chaos.
"Experience the power of our ball flinger in action as it decimates targets, demonstrating not just brute force but a finely tuned strategic weapon against the undead. Following the video, observe our '3D scan' results, presented as an Excel bubble plot, which played a pivotal role in our strategic planning for autonomous targeting."

{{< youtube EudxijrshXE >}}
{{< youtube ZblxMeU8SJk >}}
[![Front View of the Ball Flinger - Showcasing the ball flinger's design and the integration of its components.](sm_front-view.jpg)](front-view.jpg "Front View of the Ball Flinger - Showcasing the ball flinger's design and the integration of its components.")
[![Rear View of the Ball Flinger - Highlighting the engineering and design intricacies from a different perspective.](sm_rear-view.jpg)](rear-view.jpg "Rear View of the Ball Flinger - Highlighting the engineering and design intricacies from a different perspective.")

## Looking Forward
As we prepare to face the horde at Pi Wars, our journey with the ball flinger stands as a testament to the iterative process of engineering. From the ashes of burnt-out motors and speed controllers rose a device capable of challenging the undead. The path was fraught with setbacks, but each was a stepping stone towards a solution that balanced precision, performance, and strategic prowess.

The saga of the ball flinger is far from over, but as we stand on the brink of competition, we're reminded of the power of perseverance, the value of innovation, and the strategic depth of robotics competition.

