---
title: "Echoes & Edges: Mapping Moves"
date: 2024-03-03T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- software
- algorithms
- navigation
---

# Pinpoint Precision: Choreographing Our Robot's Every Move
Localization is the linchpin of autonomous navigation, allowing robots to discern their location and navigate complex environments. Our journey in Pi Wars leverages advanced localization techniques to surmount various navigational hurdles.

### The Localization Landscape
**Odometry** serves as our primary gauge of movement, albeit with a caveat—accumulating errors. It's a straightforward reflection of motion but requires correction over distance.

**Landmark Navigation**  Landmark navigation relies on recognizable features within the environment to determine a robot's location. These features, or landmarks, can be natural or artificial, including GPS coordinates, UWB signals, and visual markers like QR codes. This method triangulates the robot's position relative to known landmarks. It's effective in various settings but depends on the robot's ability to detect and identify landmarks accurately.

**GPS-based Localization**, while precise outdoors, faces limitations indoors or where satellite signals wane, prompting the need for alternative methods in such scenarios.

**Particle Filters and Simultaneous Localization and Mapping (SLAM)** represent our venture into probabilistic localization, confronting the notorious "kidnapped robot" problem by deducing position from a constellation of possibilities, generally fusing distance measurements or landmarks identified on-the-fly, with odoemtry's incremental offsets.

## Adapting to Pi Wars Arenas
Our strategy adapts to the Pi Wars' diverse challenges by employing a mix of odometry for movement tracking and Time-of-Flight (ToF) sensors for spatial awareness. These sensors act as our digital eyes, measuring distances to walls and integrating this data with our movement history to refine our location estimates.

**Square Arenas**: Here, ToF sensors shine, allowing us to calculate precise positions by measuring the distances to the walls. This technique mirrors aspects of the Iterative Closest Point (ICP) algorithm, offering clarity in straightforward environments.

**Complex Arenas**: Challenges with intricate layouts see us blending odometry with wall distance measurements. This amalgamation corrects for odometry's drift, ensuring accuracy even in the winding paths of arenas like Escape Route and Lava Palava.

**Waypoint Navigation**: Across all terrains, our navigation hinges on calculating heading errors and adjusting our course via a PID feedback loop. This method ensures our bot remains aligned with its intended path, adjusting dynamically as it learns more about its surroundings.

## In Detail: How our localisation method works with square arenas
Our ToF-based localization within the StateEstimator component plays a pivotal role in accurately determining the robot's position within Pi Wars arenas. Here's a detailed overview of how this localization process works, in conjunction with odometry, to produce a reliable estimate of the robot's location.

### ToF Sensor Integration for Localization
At the heart of our method lies the ToF sensors, which gauge distances to the arena walls. These readings, coupled with the arena's dimensions, lay the groundwork for deducing the robot's precise location. By evaluating the distance from each sensor and factoring in the robot's orientation, we map out potential positions for our contender.

[![robot with sensors](robot_with_sensors_sm.png "robot in an arena with 4 distance sensors")](robot_with_sensors.png)[![robot with positions from front sensor](robot_with_positions_from_front_sensor_sm.png "robot in an arena with the potential X and Y positions that can be inferred from the front sensor and the robot's heading (and accounting for the robot's length with an appropriate offset to the sensor's reading)")](robot_with_positions_from_front_sensor.png)


### Pinpointing Potential Positions
For each direction (front, right, rear, left), we calculate potential X and Y positions using the distance measurements and the robot's heading. This involves trigonometric calculations that consider the orientation of the robot and the direction of each sensor. By doing so, we generate a set of possible positions (X, Y) that match the sensor readings.

[![robot with all potential positions.png](robot_with_all_potential_positions_sm.png "robot in an arena with all the potential X and Y positions that can be inferred from the 4 sensors and the robot's heading. only one location is consistent with all four sensor readings")](robot_with_all_potential_positions.png)

### Merging Sensor Insights
The leap from potential to actual positioning is a strategic assembly of sensor-derived coordinates. By evaluating these coordinates against each other, we apply a technique akin to the Iterative Closest Point (ICP) algorithm, zeroing in on the most consistent location estimate. We evaluate various permutations of the potential positions to find the one that offers the lowest variance, indicating the most consistent and likely accurate position estimate. This approach offers resilience against the inherent noise of measurement and minor obstructions. 

### Combining with Odometry Data
While ToF provides a snapshot of position, odometry tracks the journey. Recognizing odometry's susceptibility to cumulative error—like slippage or irregular terrain—we integrate these insights with our ToF data. This is achieved by weighting the contributions of the ToF-based position and the odometry estimate, with a bias towards the ackermann-accurate odoemtry data. This combination corrects odometry's drift, marrying the reliability of absolute positioning with the continuity of movement tracking.

Through this sophisticated integration of ToF-based localization with odometry, our system can accurately determine the robot's position, enabling precise navigation and strategic maneuvering across various Pi Wars challenges. This method showcases our commitment to leveraging advanced technologies and algorithms to enhance our robot's performance in competitive environments.