---
title: "Ackermann Maths"
date: 2024-01-01T16:53:06+01:00
draft: false
---

# The maths behind independent four wheel drive with "virtual" ackermann steering

Whether controlling OSoD in skid or "Ackermann" steering modes, we use the desired forward and angular velocities as the inputs to the "inverse kinematics" of calculating the wheel speeds and steering angles. This isn't that different from how the joystick inputs are usually interpreted for a skid steer robot, where stick up/down movement is considered the requested forward velocity, and stick left/right is the rate of turn. The only difference is we pre-scale them a somewhat arbitrary amount[^1] and give them the units metres per second (m/s) for linear velocity, and radians per second (rad/s) for the rate of turn. You'll see in a moment why we use the slightly weird and academic "radians" over the much more common units of degrees, revolutions or rpm. From that input, to get the robot to move in the desired fashion, we need to calculate the speed of each of the wheels, and the turn angle for each of the front wheels, as shown in the diagram below:

![General Ackermann steering arrangement](ackermann1.PNG "General Ackermann steering arrangement")

With a forward velocity (\\(v\\)) in m/s and the turn rate (\\(w\\)) in rad/s, the centreline radius (\\(R_{CL}\\)) of the resulting turn in metres can be calculated from the simple formula:
$$R_{CL} = v/w \tag{1}$$

Note that this specific formula only works without any extra scaling or conversion factors if the chosen units are used. Once we know the radius of the turn, all the speeds and angles can be calculated fairly quickly by forming a right angle triangle around the wheel of interest:
![Geometry of Ackermann steering](ackermann2.PNG "Geometry of Ackermann steering")

We can then use Pythagoras to go from the chassis radius of turn, the wheel base and the wheel track to the radius of turn of an individual wheel. Taking the front right (FR) wheel as an example:

![Radius of turn for front right wheel](ackermann3.PNG "Radius of turn for front right wheel")

The specific radius that wheel is travelling around is:
$$R_{FR} = \sqrt{\left( \left(R_{CL}+\frac{wheelTrack}{2} \right)^2+wheelBase^2 \right)} \tag{2}$$

Since the whole chassis, including the wheels, has the same angular velocity around the centre of the turn, the linear speed of that wheel can be calculated by rearranging the original formula in (1):
$$v_{FR} = w\times R_{FR} \tag{3}$$

The turn angle \\(\theta_{FR}\\) can be calculated by the corresponding angles principle[^2]:
$$\theta_{FR} = \tan^{-1}\left(\frac{wheelBase}{R_{CL}+\frac{wheelTrack}{2})}\right) \tag{4}$$

The above calculations work for all combinations of forward velocity and turn rate, except for when the turn rate is zero. When either the forward velocity or turn rate are zero, the formulas can be made simpler. With a turn rate of zero, the "radius of turn" becomes infinite, so the formulas break down from the beginning at (1), but then in that case, it's fairly obvious that all the wheel speeds must be equal and match the chassis's forward velocity, and the front wheels point straight ahead. When the forward velocity is zero, the chassis's turn radius also becomes zero, so the formula for the front right wheel's radius of turn can be simplified to:
$$R_{FR} = \sqrt{\left( \left( \frac{wheelTrack}{2} \right)^2+wheelBase^2 \right)} \tag{2b}$$

With a turn angle of:
$$\theta_{FR} = \tan^{-1}\left(\frac{2\times wheelBase}{wheelTrack)}\right) \tag{4b}$$

As shown in the diagram below:
![Steering arrangement when forward velocity is zero](ackermann4.PNG "Steering arrangement when forward velocity is zero")

Our code for calculating the wheel speeds and angles from the inputs can be found here: https://github.com/thingswebuilt/osod24_firmware/blob/main/libs/mixer/src/ackermann_strategy.cpp


[^1]: scaling was chosen so that joystick full forward made all motors go full speed forward, and full left made the right-hand motors go full forward, and the left-hand motors full reverse.

[^2]: https://thirdspacelearning.com/gcse-maths/geometry-and-measure/corresponding-angles/