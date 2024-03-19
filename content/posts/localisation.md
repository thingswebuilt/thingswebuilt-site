---
title: "localisation"
date: 2024-03-03T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- software
- algorithms
- mavigation
---

# The Basics of Localization in Robotics: A Broader Perspective
Localization in robotics is a cornerstone of autonomous navigation, enabling robots to comprehend their position within an environment. This capability is crucial for tasks ranging from simple navigational exercises to complex exploration and mapping missions. While odometry, landmark navigation, and GPS-based localization serve as fundamental techniques, the field of robotics has developed several advanced methods to tackle more nuanced challenges. Here's a closer look at these sophisticated approaches:

### Odometry
Odometry calculates a robot's change in position over time using data from motion sensors, like wheel encoders or inertial measurement units (IMUs). While straightforward and directly reflective of the robot's movements, it's prone to cumulative errors from factors like slippage, making it less reliable over long distances without corrective measures.

### Landmark Navigation
Landmark navigation relies on recognizable features within the environment to determine a robot's location. These features, or landmarks, can be natural or artificial, including GPS coordinates, UWB signals, and visual markers like QR codes. This method triangulates the robot's position relative to known landmarks, offering a balance between simplicity and precision. It's effective in various settings but depends on the robot's ability to detect and identify landmarks accurately.

### GPS-based Localization
GPS-based localization uses satellite signals to provide outdoor robots with their geographical coordinates. This technique is highly accurate, especially with enhancements like differential GPS (DGPS) or Real-Time Kinematic (RTK) positioning. However, its effectiveness is limited indoors or in environments where satellite signals are obstructed.

### Particle Filters (Monte Carlo Localization)
This probabilistic method uses a set of particles (points in space) to represent the robot's potential locations. Each particle is assigned a weight based on how well the robot's sensor data matches the expected data for that location. Over time, particles converge around the most likely position of the robot, offering a robust solution to the localization problem.

### Iterative Closest Point (ICP)
ICP is an algorithm used to align two cloud points (sets of points in three dimensions) by minimizing the distance between them. It's particularly useful in robotics for aligning a robot's observed environment with a pre-existing map, aiding in precise localization and map updating.

### Simultaneous Localization and Mapping (SLAM)
SLAM techniques enable a robot to build a map of an unknown environment while simultaneously determining its location within that map. This dual capability is crucial for exploration tasks where pre-mapped landmarks are not available.

### Ultra-Wideband (UWB) Localization
UWB technology uses radio waves to determine the position of a robot with high accuracy. By measuring the time it takes for a signal to travel between the robot and fixed points (anchors), UWB systems can calculate precise distances, making them ideal for indoor localization where GPS signals are unavailable.

### QR Codes and ARuco Markers
These visual markers can be placed in the environment and easily detected by a robot's camera. Each marker encodes specific information, such as the robot's exact position within the environment, providing a simple yet effective means of localization.

### The "Kidnapped Robot" Problem
One particularly challenging scenario in robotics localization is the "kidnapped robot" problem. In this scenario, a robot is moved to an unknown location without its knowledge, requiring it to re-establish its position from scratch. This problem tests the robustness of a localization system's ability to recover from complete disorientation and accurately determine its new location. It highlights the need for sophisticated localization techniques capable of dealing with sudden, drastic changes in a robot's environment.


## Adapting Localization Techniques for Pi Wars Challenges
In the dynamic and varied landscape of Pi Wars challenges, our robot employs a blend of localization techniques tailored to the specific nature of each arena. Our approach is a testament to the adaptability required in robotics to navigate through different environments effectively.

### Localisation for Square Arenas
For challenges like EcoDisaster, Minesweeper, and Pi Noon, where the arena is a straightforward square, we leverage our Time-of-Flight (ToF) sensors for localization. This method is akin to a simplified version of the Iterative Closest Point (ICP) algorithm. By analyzing the distances to the nearest walls, we calculate the point within the arena that best matches our sensor measurements. This technique allows us to accurately pinpoint our location within these predictable, square environments, providing a solid foundation for our navigation strategy.

### Odometry and Wall Distances for Complex Arenas
In contrast, challenges such as Escape Route and Lava Palava feature arenas that deviate from the simple square layout. In these scenarios, our primary reliance shifts towards odometry to track our movement through the more intricate pathways. However, odometry alone isn't infallible, especially in environments where precise positioning is crucial. To mitigate potential inaccuracies and ensure smoother navigation, we slightly adjust our route based on real-time measurements of our distance to the arena walls. This hybrid approach enhances our odometry-based navigation, allowing for corrections that keep us on the optimal path.

### Waypoint Navigation Across All Challenges
A constant across all challenges is our utilization of waypoint navigation. This method involves calculating a heading error—the difference between our current heading and the direction towards our target waypoint. We then use this error as input for a Proportional-Integral-Derivative (PID) feedback loop to determine the necessary turn corrections. The beauty of waypoint navigation lies in its ability to dynamically adjust our trajectory based on the evolving understanding of our position within the arena.


## In Detail: How our localisation method works with square arenas

Our ToF-based localization within the StateEstimator component plays a pivotal role in accurately determining the robot's position within Pi Wars arenas. Here's a detailed overview of how this localization process works, in conjunction with odometry, to produce a reliable estimate of the robot's location.

### ToF Sensor Integration for Localization
The core of our localization method relies on Time-of-Flight (ToF) sensors that measure the distance to the walls. By using these distances and the known dimensions of the arena, we can infer the robot's position. This process starts with calculating potential positions for the robot based on each ToF sensor reading, considering the robot's current heading. These calculations assume a square arena, where each sensor's distance measurement can infer the robot's X or Y position relative to the nearest wall.

[![robot with sensors](robot_with_sensors_sm.png "robot in an arena with 4 distance sensors")](robot_with_sensors.png)[![robot with positions from front sensor](robot_with_positions_from_front_sensor_sm.png "robot in an arena with the potential X and Y positions that can be inferred from the front sensor and the robot's heading (and accounting for the robot's length with an appropriate offset to the sensor's reading)")](robot_with_positions_from_front_sensor.png)


### Calculating Potential Positions
For each direction (front, right, rear, left), we calculate potential X and Y positions using the distance measurements and the robot's heading. This involves trigonometric calculations that consider the orientation of the robot and the direction of each sensor. By doing so, we generate a set of possible positions (X, Y) that match the sensor readings.

[![robot with all potential positions.png](robot_with_all_potential_positions_sm.png "robot in an arena with all the potential X and Y positions that can be inferred from the 4 sensors and the robot's heading. only one location is consistent with all four sensor readings")](robot_with_all_potential_positions.png)

### Aggregating Sensor Data for Accurate Localization
Once we have the potential positions from each sensor, we face the challenge of combining these into a single, accurate estimate of the robot's location. This is where the process resembles a simplified version of the Iterative Closest Point (ICP) algorithm. We evaluate various permutations of the potential positions to find the one that offers the lowest variance, indicating the most consistent and likely accurate position estimate. This method allows us to derive a robust localization estimate even in the presence of measurement noise or partial obstructions.

### Combining with Odometry Data
Odometry provides a continuous estimate of the robot's movement based on wheel encoders. However, it's prone to drift over time due to slippage or uneven terrain. To counteract this, we blend the ToF-based localization data with odometry. This hybrid approach leverages the strengths of both methods: the relative movement accuracy of odometry and the absolute position correction offered by ToF localization.

### Filtering and Final Position Estimation
The final step in our localization process involves filtering the combined data to produce a smoothed, accurate estimate of the robot's position. This is achieved by weighting the contributions of the ToF-based position and the odometry estimate, with a bias towards the ToF data in square arenas where it's most reliable. The result is a comprehensive estimate of the robot's X, Y position, and heading within the arena, providing a solid foundation for navigation decisions.

Through this sophisticated integration of ToF-based localization with odometry, our system can accurately determine the robot's position, enabling precise navigation and strategic maneuvering across various Pi Wars challenges. This method showcases our commitment to leveraging advanced technologies and algorithms to enhance our robot's performance in competitive environments.