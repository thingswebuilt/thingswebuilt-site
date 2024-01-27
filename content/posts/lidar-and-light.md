---
title: "Navigating the Spectrum"
date: 2023-10-27
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- Sensors
---
# Navigating the Spectrum: Sensor Selection for Pi Wars' Diverse Arenas #
As we gear up for the multifaceted challenges of Pi Wars, our focus shifts to the pivotal role of sensor selection for our robot, the Overwhelming Surplus of Diggity (OSoD). Let's delve into how we plan to harness these sensors to ensure our robot can ascertain its position within the varied arenas of the competition.  
  
## Sensor Requirements for Optimal Navigation ##  
The arenas present unique navigational challenges, from the tight 0.6m wide corridors of Lava Palava and Temple of Doom to the more spacious 2.4m square battlefield of Pi-Noon. Each arena, with its unique wall colours and sizes, demands a sensor suite capable of precise distance measurements and rapid adaptability. To adeptly manoeuvre through these spaces, we seek sensors that can accurately measure up to 3m distances, with a narrow FOV of less than 5 degrees to prevent misreading beyond the arena boundaries or hitting the ground. A minimum 10Hz measurement rate is desirable, although faster is preferable, to swiftly adjust to on-the-spot obstacles and arena walls.  
  

## The Sunlight Challenge in Optical Sensing # 
Sunlight has been the bane of optical sensors in past competitions. Indoors, lux levels are manageable (typically below 50klux), but in direct sunlight they can be blisteringly high, reaching up to 130klux. This intense light can overwhelm sensors rated for only 5klux, leading to miscalculations. However, sensors operating at IR wavelengths, like the 940nm VL53L0x and 850nm TF Luna, have varying degrees of sunlight resistance. The conundrum lies in the disparity between the figures espoused online, actual lux measurements, the specific spectrum transmissibility of the windows at the event and the IR wavelengths of the sensors. All this makes it hard to predict sensor performance based on their lux ratings alone.

## Exploring TOF Sensors: A Comprehensive Comparison ##

In our quest to select the ideal Time Of Flight (TOF) sensor for Pi Wars, we conducted an extensive search encompassing all available TOF sensors. Our focus was on popular models and those boasting high lux ratings or suitability for outdoor and sunlight-exposed environments. This table presents a comprehensive overview of TOF sensors, featuring key specifications relevant to Pi Wars challenges. It's worth noting that this compilation includes all the sensors we encountered during our search, offering a holistic view of the available options.

| Manufacturer | Model | Price  | Range (m) | Points | FOV  | Update Rate | Max lux |            datasheet            |
|:------------:|:-----:|:------:|:---------:|:------:|:-----:|:----------------:|:---------:|:----------------------------------------|
| ST  | vl6180 | £14 | 0.1[^1]  | 1 | 42° | 150hz[^1] | 15k ("up to 100klux?!)  | [Datasheet](https://www.pololu.com/file/0J961/VL6180X.pdf) |
| ST   | vl53l0x | £7  | 2[^1]  | 1 | 25° | 50hz[^1] | 5k | [Datasheet](https://www.st.com/resource/en/datasheet/vl53l0x.pdf) |
| ST   | vl53l1x | £19 | 4[^1]  | 1 | 100° | 50hz[^1] | 1k| [Datasheet](https://www.st.com/resource/en/datasheet/vl53l1x.pdf) |
| ST   | vl53l3cx | £15 | 2[^1]  | 1 | 25° | 125hz[^1] | 5k | [Datasheet](https://www.st.com/resource/en/datasheet/vl53l3cx.pdf) |
| ST | vl53l5cx | £20 | 4[^1]  | 64 | 65° | 60hz[^1] | 5k | [Datasheet](https://www.mouser.co.uk/pdfDocs/vl53l5cx.pdf) |
| ST | VL53L7cx | £15 | 3.5[^1] | 64 | 90° | 60hz[^1]| 5k | [Datasheet](https://www.mouser.co.uk/ProductDetail/STMicroelectronics/SATEL-VL53L7CX?qs=sGAEpiMZZMu3sxpa5v1qrg00HnlQ5dqx9%2FGW28WAHjA%3D) |
| ST | VL53L8cx | £22 | 4[^1] | 64 | 65° | 60hz | ? | [Datasheet](https://www.mouser.co.uk/ProductDetail/STMicroelectronics/SATEL-VL53L8?qs=Jm2GQyTW%2FbjVYJXNfumfrw%3D%3D) |
| TI  | OPT3101  | £28 | 1 | 3 | 30° | 4khz | 130klux! | [Datasheet](https://shop.pimoroni.com/products/3-channel-wide-fov-time-of-flight-distance-sensor-using-opt3101) |
| arducam | TOF camera for raspberry pi | £49 | ? | 43200  | ?  | 120hz | ?  | [Pi_TOF Camera](https://thepihut.com/products/time-of-flight-camera-for-raspberry-pi) |
| Benewake | TF-Luna | £20 | 8 | 1 | 2° | 250hz | 70k | [TF-Luna](https://uk.robotshop.com/products/benewake-tf-luna-8m-lidar-distance-sensor) |
| Benewake | TF mini | £30 | 12 | 1 | 2.3° | 100hz | 70klux | [Datasheet](https://cdn.sparkfun.com/assets/5/a/b/1/d/TFmini-I__C-Datasheet_V1.1_EN.pdf) |
| Benewake | TF mini-S | £30 | 12 | 1 | 2° | 1000hz | 70klux | [Datasheet](https://www.unmannedtechshop.co.uk/wp-content/uploads/2020/01/SJ-GU-TFmini-S-01-A00-Datasheet.pdf) |
| Benewake | TF mini plus | £35 | 12 | 1 | 3.6° | 1000hz | 70klux | [Datasheet](https://www.mouser.co.uk/datasheet/2/1099/Benewake_10152020_TFmini_Plus-1954028.pdf) |
| Benewake | TF02 | £96 | 40 | 1 | 2° | 100hz | 100k | [Datasheet](https://cdn.robotshop.com/media/b/ben/rb-ben-23/pdf/benewake-tf02-pro-i-lidar-module-datasheet.pdf) |
| Benewake | TF02-pro | £88 | 22 | 1 | 3° | 100hz | 100k | [Datasheet](https://cdn.robotshop.com/media/b/ben/rb-ben-14/pdf/benewake-tf02-pro-lidar-led-rangefinder-ip65-40m-datasheet.pdf) |
| Benewake | TF03 | £234 | 100 | 1 | 0.5° | 1000hz | 100k | [Datasheet](https://cdn.robotshop.com/media/b/ben/rb-ben-08/pdf/benewake-tf03-lidar-led-rangefinder-ip65-100-m-datasheet1.pdf) |
| DFRobot | SEN0413 | £16 | 12 | 1 | 2° | 500hz | 15klux | [Product Page](https://wiki.dfrobot.com/TOF_IR_Distance_Sensor_0.2_12m_SKU_SEN0413) |
| DFRobot | SEN0430 | £10 | 2.5 | 1 | 24° | 30hz | 100k | [Product Page](https://www.dfrobot.com/product-2438.html) |
| DFRobot | SEN0492 | £22 | 4   | 1 | 36.5° | 20hz  | ? | [Datasheet](https://wiki.dfrobot.com/Laser_Ranging_Sensor_RS485_4m_SKU_SEN0492) |
| DFRobot | SEN0524 | £35 | 15 | 1 | 2° | 50hz | 100k   | [Datasheet](https://wiki.dfrobot.com/SKU_SEN0524_ToF_Outdoor_Laser_Ranging_Module_15m) |
| DFRobot | SEN0579 | £180 | 5 | 307200 | 60°  | ?  | ? | [Datasheet](https://wiki.dfrobot.com/SKU_SEN0579_Dual_Resolution_3D_TOF_Depth_Camera_Sensor_5m) |
| DFRobot | DFR0727 | £1,000| 4 | 7680 | 132°/9°| 20hz | 60k | [Datasheet](https://wiki.dfrobot.com/CE30_C_Area_Array_Laser_Radar_SKU_DFR0727) |
| DFRobot | DFR0727 | £1,000| 4 | 7680 | 132°/9° | 20hz | 60k | [Datasheet](https://wiki.dfrobot.com/CE30_C_Area_Array_Laser_Radar_SKU_DFR0727) |
| DFRobot | HPS-3D160-U | £264 | 12 | 9600 | 76°/32° | 35hz  | 80k | [Product Page](https://wiki.dfrobot.com/HPS_3D160_U_Area_Array_Laser_Radar_SKU_DFR0728) |
| TeraRanger | Evo Mini | £38 | 3.3 | 4 | 27° | 4hz | ? | [Spec Sheet](https://www.terabee.com/shop/lidar-tof-range-finders/teraranger-evo-mini/) |
| TeraRanger | TR-EVO-3M | £50   | 3  | 1 | 2° | ? | ? | [Product_Page](https://www.terabee.com/shop/lidar-tof-range-finders/teraranger-evo-3m/) |
| TeraRanger | Evo 64px | £113 | 5 | 64 | 15° | 130hz | ? | [Datasheet](https://cdn.robotshop.com/media/t/ter/rb-ter-28/pdf/teraranger-evo-64px-tof-rangefinder-datasheet1.pdf) |
| TeraRanger | TR-EVO-60M | £69 | 60 | 1 | 2° | 240hz | ? | [Product Page](https://www.terabee.com/shop/lidar-tof-range-finders/teraranger-evo-60m/) |
| TeraRanger | Evo medium-range | £64 | 15 | 1 | 2° | 240hz | ? | [Product Page](https://www.terabee.com/shop/lidar-tof-range-finders/teraranger-evo-medium-range/) |
| TeraRanger | Evo long-range | £83 | 40 | 1 | 2° | 240hz | ? | [Product Page](https://www.terabee.com/shop/lidar-tof-range-finders/teraranger-evo-long-range/) |
| LeddarTech | LeddarOne | £135 | 15 | 1 | 3° | 70hz | ? | [Product Page](https://www.leddartech.com/products/leddarone-sensor-module/) |
| Lidar-lite | v4 | £73 | 10 | 1 | 5° | 200hz | 50k | [Datasheet](https://cdn.robotshop.com/media/p/pli/rb-pli-26/pdf/lidar-lite-v4-led-rangefinder-10m--garmin-usb-ant-stick-combo-datasheet.pdf) |
| YDLIDAR   | GS2 | £46 | 0.3 | 160 | 100° | 28hz | 25k | [Datasheet](https://cdn.robotshop.com/media/y/ydl/rb-ydl-16/pdf/ydlidar-gs2-100-lidar-30cm-datasheet.pdf) |
| Waveshare | WAV-21221 | £29    | 15        | 1      | 1-2°     | 50hz        | 100k                        | [Product Page](https://www.waveshare.com/wiki/TOF_Laser_Range_Sensor_(B)) |
| Waveshare  | WAV-18301 | £23    | 5         | 1      | 15°-27°  | 10hz        | "affected by natural light" | [Product Page](https://www.waveshare.com/wiki/TOF_Laser_Range_Sensor) |


## Our Curated Sensor Selection ##  
After extensive research, we've charted a course through the available sensors, seeking those that promise to withstand the luminous challenge:
* **TI's OPT3101:** This sensor, priced at £28 on Pololu's 3-channel breakout board, stands out with its high 4kHz measurement rate and impressive resistance up to 130klux. The chip itself can measure up to 5m, but the board version limits the range to 1m. Its wide FOV makes it more suitable for obstacle avoidance rather than precise positional awareness. It represents an interesting option, although finding a version tailored for more focused measurements remains a challenge.
* **Benewake TF-Luna:** Priced around £25, this sensor offers an 8m range and a rapid 250Hz update rate. While its 70klux rating is robust, it might struggle in direct sunlight, which can exceed its lux capacity.  
* **AMS TMF8801:** Found on DFRobot's SEN0430 breakout board for £10, it strikes a balance with a 2.5m range, 30Hz update rate, and a formidable 100klux rating, making it a promising contender for accurate positioning even in brighter environments.
We'll compare them against the old favourite, the VL53L0X:
* **ST VL53L0X:** Offers an advertised 2m range for a cost-effective £7, with a wide 25° FOV, suitable for close-range detection but limited usefulness for pinpoint positioning due to the FOV and 5klux light level rating. 

## Testing Under the Sun ##  
We're not just stopping at theory. We'll be field-testing these new sensors against the community favourite VL53L0x, under varied lighting conditions to see which ones truly stand up to the challenge. Our aim is to strike a balance between range, accuracy, and resilience to light interference, ensuring OSoD's performance remains uncompromised, be it in the simulated shadows of a volcano or the glaring open arenas.

Stay tuned as we refine our choices and push the boundaries of robotic navigation in preparation for the upcoming Pi Wars competition.

!["A sophisticated robot navigating a maze with walls equipped with various sensors and a camera The robot is in an indoor setting with beams of sunlight"](DALLE_A_sophisticated_robot_navigating_a_maze_with_walls_equipped_with_various_sensors_and_a_camera_The_robot_is_in_an_indoor_setting_with_beams_ofsunlig.png "A sophisticated robot navigating a maze with walls equipped with various sensors and a camera The robot is in an indoor setting with beams of sunlight")

[^1]: Range and update rate depends strongly on one another, configuration, target reflectivity and lux levels, and are generally much lower than the max stated.