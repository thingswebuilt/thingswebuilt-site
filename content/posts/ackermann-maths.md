---
title: "Ackermann Maths"
date: 2024-01-01T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- Modelling
---

# Unveiling the Mathematics Behind Independent Four-Wheel Drive with "Virtual" Ackermann Steering

In our journey to harness the full potential of Overwhelming Surplus of Diggity (OSoD), we delve into the intricate world of mathematics that underpins our innovative approach. Whether we're commanding OSoD in skid steering mode or leveraging its unique "virtual" Ackermann steering, the foundation lies in calculating the wheel speeds and steering angles using a concept known as "inverse kinematics."

This concept might seem reminiscent of interpreting joystick inputs for a skid-steer robot, where forward velocity corresponds to stick up/down movement, and rate of turn aligns with stick left/right motion. However, there's a crucial difference—we apply a somewhat arbitrary scaling factor[^1] and adopt units like meters per second (m/s) for linear velocity and radians per second (rad/s) for the rate of turn. In a moment, we'll uncover why we embrace the slightly unconventional "radians" over more common units like degrees, revolutions, or rpm. These inputs serve as the foundation for our quest to guide OSoD in the desired manner, necessitating the calculation of wheel speeds and steering angles.

![General Ackermann steering arrangement](ackermann1.PNG "General Ackermann steering arrangement")

Starting with a forward velocity (\\(v\\)) in m/s and a turn rate (\\(w\\)) in rad/s, we can determine the centreline radius (\\(R_{CL}\\)) of the resulting turn in meters using a straightforward formula:
$$R_{CL} = v/w \tag{1}$$

It's crucial to note that this formula maintains its integrity without additional scaling or conversion factors only when the chosen units are employed. Armed with the turn radius, we can swiftly calculate all the required speeds and angles by constructing a right-angle triangle around the wheel of interest:
![Geometry of Ackermann steering](ackermann2.PNG "Geometry of Ackermann steering")

Pythagoras' theorem comes into play, helping us transition from the chassis's turn radius, wheelbase, and wheel track to the individual wheel's turn radius. Taking the front right (FR) wheel as an example:

![Radius of turn for front right wheel](ackermann3.PNG "Radius of turn for front right wheel")

The specific radius that this wheel traverses is given by::
$$R_{FR} = \sqrt{\left( \left(R_{CL}+\frac{wheelTrack}{2} \right)^2+wheelBase^2 \right)} \tag{2}$$

Since the entire chassis, including the wheels, maintains the same angular velocity around the center of the turn, we can calculate the linear speed of the wheel by rearranging the initial formula in (1):
$$v_{FR} = w\times R_{FR} \tag{3}$$

The turn angle \\(\theta_{FR}\\) can be determined using the corresponding angles principle[^2]:
$$\theta_{FR} = \tan^{-1}\left(\frac{wheelBase}{R_{CL}+\frac{wheelTrack}{2})}\right) \tag{4}$$

The above calculations are applicable for all combinations of forward velocity and turn rate, except when the turn rate is zero. In cases where either the forward velocity or turn rate equals zero, the formulas can be simplified. With a turn rate of zero, the "radius of turn" becomes infinite, rendering the formulas unusable from the outset at (1). However, in this scenario, it's evident that all wheel speeds must be identical and match the chassis's forward velocity, while the front wheels align straight ahead.

When the forward velocity equals zero, the chassis's turn radius reduces to zero. Consequently, the formula for the front right wheel's turn radius can be simplified to:
$$R_{FR} = \sqrt{\left( \left( \frac{wheelTrack}{2} \right)^2+wheelBase^2 \right)} \tag{2b}$$

This yields a turn angle \\(\theta_{FR}\\) of:
$$\theta_{FR} = \tan^{-1}\left(\frac{2\times wheelBase}{wheelTrack)}\right) \tag{4b}$$

As depicted in the diagram below:
![Steering arrangement when forward velocity is zero](ackermann4.PNG "Steering arrangement when forward velocity is zero")

For a deeper dive into our code that calculates wheel speeds and angles from these inputs, you can explore the following link:  [OSoD Firmware Ackermann Strategy](https://github.com/thingswebuilt/osod24_firmware/blob/main/libs/mixer/src/ackermann_strategy.cpp) .

In this detailed exploration, we've uncovered the intricate mathematics that drive OSoD's exceptional control, making it an exciting contender for Pi Wars 2024 and beyond. Stay tuned for more insights and updates as we continue our journey of innovation and robotics mastery.


[^1]: The scaling factor was chosen so that full joystick forward input corresponds to all motors operating at maximum forward speed, and full left input makes the right-hand motors run at maximum forward speed, while the left-hand motors operate in full reverse..

[^2]: [corresponding angles principle](https://thirdspacelearning.com/gcse-maths/geometry-and-measure/corresponding-angles/)