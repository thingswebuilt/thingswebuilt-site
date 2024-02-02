---
title: "Flashy!"
date: 2023-11-10T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- Design
- Sensors
---

# Blog Post: Revolutionizing Pi Noon with OSoD's Autonomous Strategy
The Pi Noon challenge at Pi Wars has always been a thrilling test of precision and strategy, where robots face off in a duel of balloon-popping prowess. This year, Team Cyberwar is taking an unprecedented approach with their robot, Overwhelming Surplus of Diggity (OSoD), by entering the challenge autonomously—a pioneering move only previously attempted by Piradigm.

## The Autonomous Edge:
OSoD's strategy hinges on autonomy, leveraging advanced technology to outmaneuver opponents. Unlike traditional remote-controlled entries, OSoD will use a camera and computer vision for balloon detection. However, as Piradigm's attempt showed, relying solely on vision poses challenges, such as losing track of opponents not in the field of view (FOV) and mistaking audience faces for target balloons due to color similarity.

## Innovative Solutions:

* **ToF Arena Localization**: To overcome FOV limitations, OSoD employs Time-of-Flight (ToF) based localization, allowing it to reacquire targets by knowing its position and the last known location of the opponent. This method potentially enables predicting the opponent's movement direction.

* **Mecanum Wheels**: For enhanced maneuverability, OSoD may utilize Mecanum wheels. This choice trades off some acceleration and directional control for the ability to move laterally, keeping the robot always oriented towards its target—a crucial advantage for both offense and defense.

* **Depth Detection via Strobe Lighting**: Addressing the challenge of distinguishing balloons from the background, especially given uncertain balloon colors, OSoD introduces a novel technique using strobe or flash lighting. By capturing images with and without additional IR light, and analyzing the difference, the robot can highlight nearby objects more brightly. This method significantly enhances target discrimination, making balloons stand out as bright spots in processed images.  

## Technical Setup and Promising Results:
The team tested this approach using a NOIR Pi camera sensitive to IR light, an IR "floodlight," and a Raspberry Pi model 3B for control and image processing. Initial tests showed the target balloon becoming distinctly more visible in difference images, achieving near-perfect discrimination in some cases. This technological innovation simplifies target detection, allowing the computer vision system to focus on identifying the balloon's center with high reliability.

## Results  
### Raw images from a colour camera, white LED flash
[![flash off](LED_flash/resized_dark.jpg "image with LED flash off")](LED_flash/dark.jpg)
[![flash on](LED_flash/resized_light.jpg "image with LED flash on")](LED_flash/light.jpg)  


### Raw images from a NOIR camera, IR LED array flash
[![IR flash off](IR_flash/resized_dark.jpg "image with IR flash off")](IR_flash/dark.jpg)
[![IR flash on](IR_flash/resized_light.jpg "image with IR flash on")](IR_flash/light.jpg)  


### Processed difference images: colour camera, white LED flash
[![rgb difference image](LED_flash/resized_rgb_diff_image.jpg "rgb difference image")](LED_flash/rgb_diff_image.jpg)
[![grayscale difference image](LED_flash/resized_gray_diff_image.jpg "grayscale difference image")](LED_flash/gray_diff_image.jpg)  


### Processed difference images: NOIR camera, IR LED array flash
[![rgb difference image](IR_flash/resized_rgb_diff_image.jpg "rgb difference image")](IR_flash/rgb_diff_image.jpg)
[![grayscale difference image](IR_flash/resized_gray_diff_image.jpg "grayscale difference image")](IR_flash/gray_diff_image.jpg)


## Challenges and Next Steps:
The primary challenge now is to increase the frame rate to above 40fps for rapid target tracking, while maintaining flash synchronization with the camera. The team is exploring various solutions, including potentially using an older camera model with a flash output pin. Additionally, they aim to develop an image classifier to determine the opponent's orientation, enhancing strategic decision-making during the challenge.

## Assessment and Outlook:
Team Cyberwar's approach to the Pi Noon challenge with OSoD represents a significant leap forward in autonomous robot competition. While promising, this strategy introduces complex technical challenges, particularly in real-time image processing and target tracking. Success depends on overcoming these hurdles, but the potential benefits—improved accuracy, strategic positioning, and enhanced defense capabilities—could set a new standard for competition robotics.

The journey ahead is filled with both opportunity and obstacles. As Team Cyberwar continues to refine OSoD's capabilities, their innovative efforts not only aim for victory in the Pi Noon challenge but also contribute to the broader field of robotics, pushing the boundaries of what autonomous machines can achieve in competitive environments.
