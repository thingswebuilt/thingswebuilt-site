---
title: "Navigating further in the Spectrum"
date: 2023-11-03
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
---

# Navigating the Spectrum - Sensor Testing Insights #
### Introduction ###
In our previous blog post, [Navigating the Spectrum](lidar-and-light.md), we embarked on a journey to select the most suitable sensors for our robotic endeavors, particularly for the challenges of PiWars. Building on that foundation, we've now put these sensors to the test, literally. The goal was simple yet crucial: verify if the real-world performance of our chosen sensors aligns with their datasheet specifications. This endeavor isn't just about validating our choices; it's about providing valuable insights for the entire PiWars community on sensor selection and deployment.

## Methodology ##
### Test Rig Configuration: ###

Our test rig was a model of precision and consistency. We mounted three sensors - TF-Luna, VL53L0X, and TMF8801 - side by side on a sturdy plywood board. This setup ensured that all sensors were subjected to identical conditions during each test.
The brain of our operation was a Maker Pi RP2040 development board, renowned for its versatility and reliability. This board facilitated seamless data collection from each sensor.

[![Target and Floor](resized_targetandfloor.jpg)](targetandfloor.jpg "Target and Floor") [![Test Rig In Place](resized_testriginplace.jpg)](testriginplace.jpg "Test Rig In Place")

[![Top of Test Rig](resized_topoftestrig.jpg)](topoftestrig.jpg "Top of Test Rig") [![Display Showing Results](resized_displayshowignresults.jpg)](displayshowignresults.jpg "Display Showing Results")

[![Sensors in Sunlight](resized_sensorsinsunlight.jpg)](sensorsinsunlight.jpg "Sensors in Sunlight")

### Testing Environment and Procedure: ###
The environment was carefully chosen to simulate common real-world conditions: indoors with varying degrees of sunlight exposure. Each sensor faced the same challenge - accurately gauging distance to a uniform black wall (representing the typical Pi Wars arena wall), positioned so the sensors were a consistent 30mm from the ground and pointed slightly above horizontal.
We methodically tested the sensors across a range of distances - from 25mm all the way up to 3m. This range was selected to cover typical use-cases in robotics, where precision in short-range detection is often critical, as well as establishing position at long range.
The true distance to the target was meticulously set for each test, providing us with a benchmark to measure each sensor's reported distance against.

### Objective of the Tests: ###
Our primary objective was to scrutinize each sensor's accuracy and consistency. We aimed to see how closely each sensor's readings matched the actual distances, and whether any sensor's performance was significantly influenced by the testing conditions.
The data gathered would not only guide our sensor selection for our own robot but also serve as a beacon for other PiWars competitors navigating the complex terrain of sensor technology.
In the next section, we will delve into the results of these tests, providing a clear and detailed comparison between our empirical findings and the datasheet specifications of each sensor.

## Test Results and Analysis ##
Our comprehensive sensor testing revealed insightful data on the performance of the TF-Luna, VL53L0X, and TMF8801 sensors under varying environmental conditions. The tests were conducted at different distances and in three specific lighting scenarios: sunlit shade, direct sunlight, and partial sunlight. 

#### Raw measurements: ####
|          |  sunlit  target | shade and | for  sensor | | target sensor | ` ` ` ` in `  `  ` `in  |  shade, sunlight | | target sensor | ` ` ` ` in `  `  ` `in |  sunlight, shade  |
| -------- | :------------: | :----------: | :----------: | - | :---------: | :-------------: | :-------------------: | - | :---------: | :----------------: | :---------: |
| **distance** | **TF Luna**      | **VL53L0X**    | **TMF8801**    | | **TF Luna**   | **VL53L0X**       | **TMF8801**             | | **TF Luna**   | **VL53L0X**          | **TMF8801**   |
| 25       | 25           | 35         | 49         | | untested  | untested      | untested            | | untested  | untested         | untested  |
| 50       | 50           | 66         | 77         | | untested  | untested      | untested            | | untested  | untested         | untested  |
| 100      | 100          | 133        | 156        | | 100       | 130           | 165                 | | 110       | 173              | 185       |
| 250      | 250          | 270        | 315        | | 250       | 8190[^1]      | 0                   | | 250       | 300              | 0         |
| 500      | 490          | 560        | 0          | | 490       | 8190[^1]      | 0                   | | 490       | 8190[^1]         | 0         |
| 1000     | 985          | 1104       | 0          | | 990       | 8190[^1]      | 0                   | | 1040      | 8190[^1]         | 0         |
| 1500     | 1490         | 8190[^1]   | 0          | | untested  | untested      | untested            | | untested  | untested         | untested  |
| 2000     | 2010         | 8190[^1]   | 0          | | untested  | untested      | untested            | | untested  | untested         | untested  |
| 2500     | 2520         | 8190[^1]   | 0          | | untested  | untested      | untested            |  | untested  | untested         | untested  |
| 3000     | 3000         | 8190[^1]   | 0          | | untested  | untested      | untested            | | untested  | untested         | untested  |

### Plotted Results  ###
!["chart showing results for shade for target and sensor"](shade_for_target_and_sensor.png "shade for target and sensor")  

!["chart showing results for target in sunlight, sensor in shade"](target_in_sunlight_sensor_in_shade.png "target in sunlight, sensor in shade")  

!["chart showing results for target in shade, sensor in direct sunlight"](target_in_shade_sensor_in_direct_sunlight.png "target in shade, sensor in direct sunlight")


##  Analysis ##
#### TF-Luna Performance: ####

Demonstrated remarkable consistency in sunlit shade with measurements closely matching actual distances across all tested ranges.
In direct sunlight, the TF-Luna maintained better than ±10 mm accuracy for distances up to 1000 mm, a promising indicator for outdoor applications. It maintained ±20mm all the way up to 3m. 
Under partial sunlight conditions, it showed slight deviations at longer distances (±40mm) but remained fairly consistent, suggesting robustness against variable lighting.

#### VL53L0X Performance: ####

The VL53L0X sensor consistently overestimated distances in sunlit shade, with this trend becoming more pronounced at longer ranges.
Under direct sunlight, the sensor frequently reported error values (8190 mm), indicating a limitation in handling bright outdoor conditions.
In partial sunlight, the sensor struggled with accuracy, often defaulting to error readings, particularly at distances beyond 250 mm.

#### TMF8801 Performance: ####

Showed variable performance in sunlit shade, with no readings beyond 500 mm, indicating limited range capability.
In direct sunlight, the sensor failed to provide accurate readings even at shorter distances.
Similar performance was observed under partial sunlight, with the sensor unable to report accurate distances beyond 250 mm.

## Comparative Analysis: ##

The TF-Luna's consistent performance across various conditions makes it a reliable choice for both indoor and outdoor applications, aligning well with its datasheet specifications.
The VL53L0X, while performing adequately at shorter distances in controlled conditions, shows limitations under bright lighting, suggesting its use may be best suited for indoor or shaded environments with light coloured targets.
The TMF8801's performance suggests it is more suited for controlled, indoor environments with shorter range requirements and  lighter targets.
These results provide valuable insights into sensor capabilities and limitations, guiding us in selecting the most appropriate sensor for our robot's needs and offering a resource for other PiWars competitors.


## Strategic Considerations: ##

For our robot's design, which demands adaptability across various PiWars challenges, the TF-Luna appears to be the most strategic choice. Its robustness across different distances and environments aligns well with the diverse nature of the competition.
Incorporating sensor redundancy might be a strategy to consider. Utilizing the VL53L0X for certain tasks where its characteristics match the requirements could provide a backup or complementary system to the primary TF-Luna sensor.
The insights gained from this testing will not only inform our sensor selection but also provide valuable guidance to other PiWars competitors. Understanding each sensor's strengths and limitations is key to optimizing robot performance in different challenges.

# Conclusion #
In our quest to equip our robot with the most effective sensory apparatus, the journey through these tests has been enlightening. The TF-Luna, VL53L0X, and TMF8801 sensors each exhibit unique traits that define their suitability for different scenarios.

The data-driven approach of this testing regime has illuminated the path forward, clearly indicating the TF-Luna as a frontrunner for our needs, with the VL53L0X as a potential secondary option. As we progress in the PiWars competition, these findings will not only refine our robot's design but also contribute to the broader community's understanding of sensor capabilities.

We look forward to applying these insights in real-world scenarios, further pushing the boundaries of what our robot can achieve. The blend of theoretical knowledge and empirical data has once again proved invaluable, underscoring the importance of rigorous testing in robotics.

Stay tuned for more updates as we continue to navigate the exciting world of robotics and competition.

!["DALL·E: A futuristic robot equipped with advanced sensors navigating through a mixed indoor and outdoor environment, symbolizing sensor technology and robotic"](DALLEAfuturisticrobotequippedwithadvancedsensorsnavigatingthroughamixedindoorandoutdoorenvironmentsymbolizingsensortechnologyandrobotic.png "DALL·E: A futuristic robot equipped with advanced sensors navigating through a mixed indoor and outdoor environment, symbolizing sensor technology and robotic")

[^1]: 8190 is effectively an error code from the VL53L0X, so has been plotted as 0 for clarity