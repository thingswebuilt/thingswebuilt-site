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
1. **Point-to-Point Strategies:**  
    1.1 **One-at-a-time** (~30m):  The quintessential strategy likely to be adopted by many. This methodical, one-barrel-at-a-time approach, despite its simplicity, may culminate in a significant cumulative distance.  
    [!["Plot showing the route taken for a typical one at a time approach"](resized_oneatatime.png "The typical one at a time approach")](oneatatime.png)  
    1.2 **Random Order, carrying all 12** (~9m):  A less conventional strategy that may not promise efficiency but certainly brings an element of unpredictability to the table. This approach, while better than one-at-a-time, is likely the least efficient in terms of overall route optimization.
    1.3 **Next Nearest Barrel** (4-6m): A testament to the virtues of carrying all 12 barrels in one go, this approach is remarkably more efficient, coming within a striking distance of 20% over the minimum possible distance. Coding this strategy should be straightforward, given that it doesn't require detecting all barrels in a single sweep. The route focuses on one barrel at a time, with a fresh scan after each collection. However, even with swift sensors, the cumulative time of twelve 360-degree scans might significantly impact the total duration..  
    [!["Plot showing the route taken for nearest-first when collecting all 12 barrels in one route"](resized_nearest.png "nearest-first")](nearest.png)  
    1.4  **"Travelling Salesman Problem" [(TSP)](https://en.wikipedia.org/wiki/Travelling_salesman_problem) Minimum Distance Route** (4-6m): The classic problem turned into a robotic reality, requiring a precise initial scan to map out the most efficient route amongst all barrels.  Achieving this level of detection reliability poses a challenge. Intriguingly, there's no definitive algorithm for determining the shortest route—only iterative methods that approximate the optimal path. Despite this, programming such algorithms is manageable, as evidenced by our successful modeling in Excel for this analysis.".  
    [!["Plot showing the route taken for the minimum-distance route when collecting all 12 barrels in one route"](resized_tsp.png "TSP minimum distance")](tsp.png)  
    1.5 **TSP with next nearest fall back** (4-6m): Given the inherent challenges with barrel sensors, it's improbable that a single scan will consistently reveal the location of every barrel. The likelihood of barrels being obscured or misidentified is high. Under these circumstances, a pragmatic approach is to default to retrieving the nearest barrel. Following each collection, a new scan should be conducted. If this scan successfully locates all remaining barrels, a TSP minimum distance route can be formulated and implemented. Should any barrels remain undetected, the strategy reverts to targeting the next nearest barrel, repeating this process until all are accounted for. This method could prove effective, especially if sensors occasionally overlook barrels. It's expected to closely resemble the 'Next Nearest' strategy but could outperform it by up to 30% in certain scenarios.  
    1.6 **Simplified TSP Route** (3-5m): Leveraging the width of our barrel collecting funnel allows us to streamline our navigation by cutting corners and softening the sharpness of turns. This strategy not only saves distance but, more importantly, simplifies maneuvering. However, its success hinges on accurately determining the position of each barrel and precise navigation. Additionally, the ability to track multiple barrels while in motion would be ideal, though this is a challenging feat for spot distance sensors.  
    [!["Plot showing the route taken for a simplified minimum-distance route when collecting all 12 barrels in one route"](resized_shortcuts.png "TSP with shortcuts")](shortcuts.png)  

2.  **Full Coverage with Overlap (~20m Path):**  
    This approach guarantees that no barrels are overlooked, as it doesn’t rely on identifying the location of each individual barrel. However, the trade-off for this thoroughness is a longer route, which could lead to an extended time to complete the challenge. An ingenious variation, particularly for remote-controlled and autonomous entries, involves utilizing a wide funnel to herd all the barrels towards the end zone. Once there, only the misplaced barrels would need repositioning. This method has the potential to be more efficient and quicker than a point-to-point strategy.  
    Potential Routes:  
    2.1 **Farm ploughing**-type routes that are mostly straight paths with fixed radius turns. The turns often have significant overlap on previously covered ground.  
    [!["Plot showing the route taken for a ploughing-style approach to cover almost the whole arena"](resized_ploughing.png "ploughing pattern")](ploughing.png)  
    2.2 **Spiral patterns** have less overlap but may be more complicated to program and consistently navigate. They become less efficient when including centre and corner coverage unless the barrels can be reliably collected whilst performing tight turns.  
    [!["Plot showing the route taken for a spiral-style approach to cover most of the arena"](resized_spiral.png "sprial with majority coverage")](spiral.png)
    [!["Plot showing the route taken for a spiral-style approach to cover the whole arena"](resized_spiralcorners.png "sprial pattern with complete coverage")](spiralcorners.png)  

3.  **Majority Coverage with Straggler Search (~15m + 0-5m):**
    * This strategy is designed to efficiently cover the majority of the area and then specifically address any barrels that were missed, possibly using a nearest-first or another path-planning method. Since no pre-set route can guarantee the collection of all barrels—some may inadvertently be nudged off course—it makes sense to have a contingency for stray barrels. With this in mind, it's practical to bypass the less efficient parts of the arena, like the corners, in our pre-planned route, and instead count on the straggler search method to recover any barrels in these outlying areas. 

In any point-to-point strategy, careful consideration of the robot’s approach angle and turning radius is crucial to avoid inadvertently displacing barrels not targeted for immediate collection. The [PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics) library offers valuable resources for path planning in Ackermann vehicles, which can be instrumental in such scenarios. Drawing inspiration, Phil and Lorrain from the Shetland Attack Pony Pi Wars team have effectively employed a 'visibility graph' method to devise paths that circumvent colliding with untargeted barrels. Their technical talks on this challenge are online [here](https://youtu.be/GgcCcJ3tKWM) and [here](https://youtu.be/IfEibRmXKJE).  

## Sensor Integration and Its Impact
As we gear up for the Eco-Disaster challenge in Pi Wars, the strategic integration of sensors into our Overwhelming Surplus of Diggity (OSoD) robot is critical. Our analysis here focuses on three Time Of Flight (ToF) based contenders: the [TMF8801](https://thepihut.com/products/fermion-tmf8801-tof-distance-ranging-sensor-20-2500mm), [VL53L0X](https://thepihut.com/products/adafruit-vl53l0x-time-of-flight-distance-sensor-30-to-1000mm) and [TF-Luna](https://thepihut.com/products/tf-luna-lidar-ranging-sensor), each with unique characteristics that affect our robot's performance.

### Sensor Performance Comparison: ###

We've meticulously charted the capabilities of our sensors:

| Parameter | TMF8801 | VL53L0X | TF-Luna |
| :- | :-: | :-: | :-: |
| Update Rate (Hz) | 60 | 50 | 250 |
| Min Distance (mm) | 20 | 30 | 200 |
| Accuracy (mm) | 10 | 40 | 60 |
| FOV (degrees) | 20° | 25° | 2° |
| FOV at 1m (mm) | 353 | 443 | 35 |
| Scan Time with 1 Degree Between Readings (s) | 6 | 7.2 | 1.44 |


### Sensor Choice ###

The dilemma we face is clear: the TMF8801 and VL53L0X, with their expansive fields of view, complicate the precise identification of barrels at a distance. Their utility might be confined to homing in on the nearest target, yet the risk of confusing adjacent barrels looms large. 

In the grand scheme, the TF-Luna's precision in delineating each barrel's location shines through, potentially streamlining our time in the arena. While the TMF8801 and VL53L0X could hasten initial detection, their broader scans may necessitate multiple confirmatory sweeps—a trade-off that could cost us precious seconds.

### Sensor Positioning ###
Mounting 2° FOV sensors on the elevated chassis of our robot means they won't detect barrels until they're within approximately 750mm range. While this setup is advantageous for establishing our position in the arena, it's less effective for barrel identification. Conversely, if we mount wide FOV sensors horizontally, they begin detecting the ground at a mere 600mm, rendering them ineffective for both position establishment and distant barrel detection. To optimize their utility, wide FOV sensors would require upward angling, potentially at the cost of long-distance sensitivity. Consequently, all sensors must be positioned relatively low (between 20-60mm off the ground) to ensure effective barrel detection.

#### Monocular sensing
Utilizing a single "spot" distance sensor introduces two challenges: occlusion and route correction. Our modeling shows that when scanning randomly spaced barrels from a single vantage point, occlusion frequently occurs, with one barrel obscuring another, complicating path planning. Even if all barrels are initially identified and a collection route is established, a single sensor provides limited feedback for final course adjustments. The sensor's binary nature – either seeing the barrel or not – offers no guidance for directional correction. It's improbable that the initial reading and subsequent navigation will be precise enough to collect the barrel without additional course corrections on the final approach.  
[!["Plot showing the visibility (or lack of visibility) for barrels when using a single spot sensor"](resized_monocular.png "visibility using a single spot sensor, showing some occluded barrels")](monocular.png)  

#### Binocular sensing
Employing two sensors spaced apart (around 60-100mm) can provide a form of binocular vision. When aligned approximately parallel, these sensors can discern if a barrel is directly ahead or slightly off to one side. Should "visibility" of the barrel be lost, the last known direction can guide course correction to intercept the barrel. Given our intent to channel barrels into a central sorting mechanism and then into two storage cartridges, the barrel-detecting sensors should be situated behind or below the funnel and outside the central mechanism. This necessitates a wider spacing than the width of a barrel to ensure effective detection. Positioning the sensors with a wider spacing not only avoids clashes with the sorting mechanism but also minimizes the likelihood of occlusion during scanning. However, this arrangement introduces a 'dead zone' directly in front of the robot, a region where neither sensor can detect a barrel. To mitigate this, angling the sensors slightly inward, creating an overlap in their fields of view, can effectively eliminate this dead zone for objects at a distance. This overlap must be carefully calibrated; too great an angle could lead to misleading detections, where the left sensor might pick up barrels on the robot's right side and vice versa, complicating or even rendering course correction infeasible. The precision in this sensor alignment is crucial – it's a delicate balance between ensuring comprehensive barrel detection and maintaining the accuracy needed for effective navigation and course correction. 
[!["Plot showing the visibility for barrels when using two spot sensors, separated by the length of the chassis"](resized_binocular.png "visibiltiy using a pair of spot sensor")](binocular.png)  


#### Camera and Computer Vision Integration
Incorporating a camera and computer vision system into our robot's design opens a new realm of possibilities for barrel detection and navigation precision. The primary merit of this approach lies in its ability to provide rich, multidimensional data, enabling not just the identification of barrel locations, but also the understanding of their orientation and spatial relationship to the robot. This can significantly enhance our path planning and course correction capabilities, especially in scenarios where barrels are closely spaced or partially occluded. However, the integration of computer vision also introduces complexities. The processing time for image analysis and the computational load could impact the robot's reaction speed and overall challenge time. Furthermore, ensuring robustness in varying lighting conditions within the arena presents another challenge. This approach would necessitate sophisticated programming and potentially more advanced hardware, but if executed well, it could provide a substantial edge in accurately and efficiently navigating the Eco-Disaster challenge.

### Wrapping Up
Our foray into the Eco-Disaster challenge is a testament to the marriage of tactical foresight and engineering prowess. As we inch closer to the competition, each decision we make—from the sensor we mount to the path we chart—edges OSoD ever closer to triumph. Keep an eye on this space as we continue to hone our strategies and prepare to take on the Pi Wars battleground.

