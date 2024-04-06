---
title: "Firmware's Final Furlong: Racing to Refine Our Robotics Roster"
date: 2024-03-17T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- progress
- countdown
---

# Pi Wars 2024 Project Update: Navigating the Final Stretch
As we edge closer to Pi Wars 2024, with just five weeks remaining, the intensity and excitement within Team Cyberwar are palpable. The flurry of recent progress on our firmware, marked by a barrage of successful Pull Requests, beckons a pause to reflect on the journey thus far and map out the final leg towards our ultimate goal.

## Lava Palava: The Path to MVP and Beyond
Our journey through the molten challenges of Lava Palava has brought us to the cusp of a significant milestone: an almost-ready-to-merge branch teeming with sophisticated waypoints code. This development promises to mark the completion of our basic MVP. Yet, the journey is tempered by two notable challenges:

The sensitivity to initial heading—a dilemma that threatens the reliability of our navigational prowess.
The elusive distance between the start line and the first bend, a critical parameter for our waypoints algorithm.
The road to a robust solution lies in the realm of map-based localisation, demanding seamless pi<>rp2040 communications and a fresh codebase on the Pi. Yet, hope glimmers in the form of an alternative: an rp2040-based feedback loop utilizing wall following. This workaround could potentially circumvent the need for extensive code redevelopment, promising a solution within a few dedicated days or evenings.
{{< youtube LijrlQbrJvA >}}  

## Eco-Disaster: Towards a Greener Tomorrow
The Eco-Disaster challenge, with its massive scoop and dumb full-area-sweep, initially offers a straightforward path to half the points. However, the ambition to employ belt-driven "portal axles" for TOF-based localisation underscores our commitment to refinement. This approach, necessitating the extra height for sensor efficacy, aims to enhance precision beyond mere dead reckoning.

The integration of electric retract actuators and the testing of portal axles are steps towards a more nuanced barrel sorting mechanism—a task that presents its own set of complexities. The aspiration to process six barrels for additional points highlights the scale of work ahead, yet the team remains optimistic about achieving the MVP within a comparable timeframe to Lava Palava.
{{< youtube 1rno_h1L6No >}}  

## Escape Route: Autonomy as the New Frontier
The potential for an autonomous version of our robot to tackle the Escape Route is both a challenge and an opportunity. Mirroring the complexities of Lava Palava, the project's success hinges on nuanced navigation and avoidance strategies—ambitions that stretch our capabilities yet promise substantial rewards.

{{< youtube cOSk1KMeXyo >}}  

## Minesweeper and Beyond: A Spectrum of Challenges
From the autonomous ambitions in Minesweeper to the innovative designs for the Zombie Apocalypse, our journey through Pi Wars 2024's challenges is a testament to the team's resilience and ingenuity. Each challenge, from the tactical considerations in Pi Noon to the strategic deliberations for the Obstacle Course, represents a unique puzzle piece in our quest for robotic mastery.
{{< youtube b0zaCxePpPU >}}  

## In Conclusion: The Road Ahead
As Team Cyberwar gears up for the final stretch towards Pi Wars 2024, our spirits are buoyed by the progress made and the challenges overcome. The path ahead, while daunting, is paved with opportunities for learning, innovation, and ultimately, triumph. Stay tuned as we continue to navigate the exciting landscape of robotics, engineering, and teamwork, all in pursuit of Pi Wars glory.

Team Cyberwar's journey to Pi Wars 2024 is a blend of technical prowess, strategic planning, and collaborative spirit. Each challenge, from Lava Palava to the Eco-Disaster, not only tests our robot's capabilities but also strengthens our resolve. As we embark on the final leg of this thrilling adventure, our eyes are set on the horizon, eager to witness the culmination of our efforts. Join us as we push the boundaries of what's possible, one code commit, one test run, and one innovation at a time.