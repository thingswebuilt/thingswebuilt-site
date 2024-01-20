---
title: "Unraveling the Eco-Disaster Challenge"
date: 2023-10-20
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
---


## Unraveling the Eco-Disaster Challenge: Insights from Team OSoD
Welcome to our latest technical blog post, where we delve into the intricate strategies and technological advancements of our Pi Wars robot, the Overwhelming Surplus of Diggity (OSoD). Our team has been hard at work strategizing for the Eco-Disaster challenge, a task that involves sorting contaminated barrels within a specific time frame. Here, we'll explore our approaches, sensor integration, and estimated run times for the different options being evaluated.

### The Challenge at Hand
The Eco-Disaster challenge requires precision and speed. Robots must sort green (clean) and red (contaminated) barrels into respective zones. Our approach is to ensure OSoD can handle this task effectively, balancing thoroughness with efficiency.

### Approach Strategies
1.  **Full Coverage with Overlap (~20m Path):**
    * This strategy ensures no barrels are missed. However, its comprehensiveness results in a longer path and increased challenge time.
    * Estimated Run Time: Given the extensive coverage, this approach might take the longest, possibly close to the 5-minute limit.
2.  **Majority Coverage with Straggler Search (~15m + 0-5m):**
    * This approach aims to cover most areas efficiently, then specifically target missed barrels.
    * Estimated Run Time: Around 4 minutes for the initial sweep, plus additional time for straggler collection.
3.  **Point-to-Point Strategies:**
    * Random Order (~9m): Less predictable and potentially less efficient.
    * Next Nearest Barrel Approach (~4-5m): More efficient, with dynamic path planning.
    * TSP Minimum Route with Adaptation (4-6m): Optimizes for shortest path with real-time adjustments.
    * Estimated Run Time: These approaches vary, with the TSP method potentially being the most time-efficient, likely under 3 minutes, depending on real-time recalculations.
4.  **Route Patterns:**
    * Farming-type routes and spiral patterns offer structured approaches but may miss certain areas.
    * Estimated Run Time: These methods could take anywhere from 3 to 4 minutes, depending on the thoroughness of the coverage.

### Sensor Integration and Its Impact
As we gear up for the Eco-Disaster challenge in Pi Wars, the strategic integration of sensors into our Overwhelming Surplus of Diggity (OSoD) robot is critical. Our analysis focuses on three Time Of Flight (ToF) based contenders: the [TMF8801](https://thepihut.com/products/fermion-tmf8801-tof-distance-ranging-sensor-20-2500mm), [VL53L0X](https://thepihut.com/products/adafruit-vl53l0x-time-of-flight-distance-sensor-30-to-1000mm) and [TF-Luna](https://thepihut.com/products/tf-luna-lidar-ranging-sensor), each with unique characteristics that affect our robot's performance.

**Sensor Performance Comparison:**

The table below outlines the key specifications and calculated performance metrics for each sensor:
| Parameter | TMF8801 | VL53L0X | TF-Luna |
|-----------|---------|---------|---------|
| FOV (degrees) | 20 | 25 | 2 |
| Update Rate (Hz) | 60 | 50 | 250 |
| Min Distance (mm) | 20 | 30 | 200 |
| accuracy (mm) | 10 | 40 | 60 |
| Scan Time with 3 Readings per Barrel (s) | 0.9 | 0.864 | 2.16 |
| Effective Lateral Precision at 1m (mm) | 353 | 443 | 35 |
| Scan Time with 1 Degree Between Readings (s) | 6 | 7.2 | 1.44 |


**Time to Challenge Completion:**

Considering the necessity of precise navigation and barrel collection, the wider FOVs of the TMF8801 and VL53L0X present a challenge. Their effective lateral precision at 1m does not support a single-scan approach per barrel due to insufficient accuracy within the collection mechanism's width. This inaccuracy necessitates additional scans to refine the heading, increasing the time to complete the challenge.

**Path Planning Precision:**

The precision of a sensor directly influences path planning. With the barrels being 56mm wide and the robot's collection mechanism limited to 225mm, the lateral precision of our sensors at various distances determines how accurately we can approach each barrel. The TF-Luna's superior narrow FOV allows us to distinguish barrels that are close to each other and accurately navigate to them, a crucial advantage given the number of barrels and potential for occlusion. This will reducing the need for multiple scans and adjustments (required for the otehr two sensors), thereby optimizing our path planning.


**Sensor Choice Conclusion:**

Upon reviewing the capabilities of the three sensors, the TF-Luna stands out for its high precision, despite a potentially longer scan time. Its ability to accurately determine the location of each barrel with fewer scans could prove to be more time-efficient in a challenge where precision is paramount. The TMF8801 and VL53L0X, while faster in a coarse scanning, may require additional passes to confirm barrel positions, potentially offsetting their time advantage. 


### Wrapping Up
Our journey through the Eco-Disaster challenge reflects a fusion of strategic planning and technological ingenuity. Each approach and sensor integration choice brings OSoD closer to mastering this challenge, balancing the precision of barrel handling with the urgency of the ticking clock. Stay tuned as we continue refining our strategies and edge closer to the Pi Wars competition!

