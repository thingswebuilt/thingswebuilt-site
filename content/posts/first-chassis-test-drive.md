---
title: "Challenges with first test drive of new chassis and pcb"
date: 2024-02-04T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- Progress
- Setbacks

---

# Navigating the Challenges of Innovation – A Week with OSoD
This week has been a whirlwind of progress and challenges for Team Cyberwar as we forge ahead with our Pi Wars contender, Overwhelming Surplus of Diggity (OSoD). With a blend of breakthroughs and technical hiccups, our journey exemplifies the dynamic world of robotics.

## Progress Highlights:

* **Wiring and Assembly Completion**: Robert has meticulously finished the wiring for our new chassis and PCB, setting the stage for a pivotal moment in OSoD's development. Following this, I took the reins for assembly, culminating in a pivotal test drive that put our efforts to the test.  
[!["top view of 3D printed chassis complete with all sensors and custom PCB"](resized_chassis-top.jpg "top view of 3D printed chassis complete with all sensors and custom PCB")](chassis-top.jpg)
[!["bottom view of 3D printed chassis complete with all sensors and custom PCB"](resized_chassis-bottom.jpg "bottom view of 3D printed chassis complete with all sensors, custom PCB and extensive wiring loom")](chassis-bottom.jpg)
{{< youtube NUnWOVGWpas >}}

## Triumphs:

* **Enhanced Speed**: The new test bed is significantly faster than its predecessor, thanks to a higher voltage and more current. It's thrilling to see OSoD spring to life with such vigor.
* **Core Functionality**: The essentials are in place – the receiver, motors, and steering all respond as intended. Notably, the "Brain" and "Brawn" switches activate the logic and power components seamlessly.

## Challenges Faced:

* **Motor Direction Reversal**: An unexpected hiccup; the motor directions are the opposite of what they were previously.  
* **Steering Difficulties**: There's a mysterious hindrance affecting the steering. Whether it's the linkage stiffness, motor wire rigidity, or an obstructive element remains to be determined.  
* **Battery Accessibility**: The battery, now difficult to remove due to the crowded wiring, calls for a design revision of the battery mount.  
* **Power Management**: The current power on/off process is cumbersome, necessitating a PCB modification for easier battery management.  
* **Drive Tuning**: The transition to a higher voltage has disrupted the drive's smoothness, indicating a need for PID and feed-forward retuning.  
* **Servo Control**: Considering enabling the servos independently of the drive for easier setup, possibly utilizing an RC channel as a motor disable switch.  
* **PCB Temperature**: The PCBs are running warm, a condition we're monitoring closely.  

## Further Testing Insights:

* **Battery Overdischarge**: Initial tests may have overdischarged the batteries, a concern mitigated as they seemed to recover post-charge.  
* **Code Tuning**: Adjustments have been made to correct motor directions and refine speed control, though understeering persists.  
* **Battery Mount Redesign**: A redesigned battery mount improves accessibility, now undergoing further revisions.  
* **Indicator Light Issues**: The "Brains" indicator light flickers, suggesting a potential electrical issue.  
{{< youtube E3bU3fXOrHU >}}

## Troubleshooting Efforts:

After investigating the flickering and stuttering drive behavior, including resoldering wires and replacing components, the root cause remains elusive. Bench power supply tests show unusual current draws, indicating a deeper issue potentially unrelated to drive power.  
[!["broken wire on indicator switch"](resized_broken-wire.jpg "broken wire on indicator switch")](broken-wire.jpg)[!["new removable auxiliary input power port"](resized_new-removable-power-port.jpg "new removable auxiliary input power port, previous version was built in and required resoldering to change the bumper")](new-removable-power-port.jpg)[!["new rear bumper design"](resized_new-rear-bumper.jpg "new rear bumper design")](new-rear-bumper.jpg)

## Reflections and Next Steps:
The path of innovation is fraught with unexpected challenges, each presenting an opportunity for growth and learning. As we navigate these technical hurdles, our resolve is only strengthened. The coming week will focus on diagnosing the electrical issues, refining our control algorithms, and ensuring OSoD is battle-ready for Pi Wars.  

Stay tuned for more updates as we continue our journey of innovation, troubleshooting, and refinement. Team Cyberwar is committed to pushing the boundaries of what's possible, one challenge at a time.  

![A detailed image of a robotic workshop with a focus on a robot chassis on a workbench. The chassis is equipped with a complex PCB and wiring, highlighting the recent assembly and wiring completion. The scene includes tools, scattered components, and a partially disassembled robot, conveying a sense of ongoing development and troubleshooting. The atmosphere is busy yet organized, reflecting the challenges and progress of a robotics team working on an advanced project.](robot-maintenance.jpg "A detailed image of a robotic workshop with a focus on a robot chassis on a workbench. The chassis is equipped with a complex PCB and wiring, highlighting the recent assembly and wiring completion. The scene includes tools, scattered components, and a partially disassembled robot, conveying a sense of ongoing development and troubleshooting. The atmosphere is busy yet organized, reflecting the challenges and progress of a robotics team working on an advanced project.")

