
---
title: "Odometry Matters"
date: 2023-12-27T16:53:06+01:00
draft: false
---

## Odometry Matters ##

In the journey towards Pi Wars 2024, we recently achieved a significant milestone that might sound deceptively simple but holds immense importance: we synchronized our wheel speeds with steering angles for the first time. While it happened relatively late in the build process (we embarked on this project back in 2021), grasping the significance of this achievement requires us to revisit the lessons learned from our past robot, Tauradigm

Tauradigm marked our first foray into the realm of encoders in 2018. Sporting six wheels, each equipped with an encoder, it allowed us to measure wheel movements with remarkable precision, down to the millimeter. By combining this data with heading information from the Inertial Measurement Unit (IMU), we ventured into the realm of odometry. Odometry, in simple terms, involves estimating a robot's position based on the movement of its wheels and sensors, and it's a crucial aspect of robotics.

## The Trade-offs of Odometry

While Tauradigm's odometry was highly repeatable, it wasn't notably accurate, suffering from approximately 10% drift over any distance traveled. This inaccuracy was most pronounced during sweeping turns, which made precise control challenging in certain scenarios.

For instance, Tauradigm excelled in moving straight or executing spot turns with relative ease. However, navigating wider turns was a tad erratic, necessitating quick feedback from external sensors to maintain smooth motion. These trade-offs were manageable for the at-home Pi Wars event in 2021, where we could fine-tune our control code to suit the specific arena.

## The Importance of Accurate Odometry

Accurate odometry is a game-changer in the world of robotics. It eliminates the reliance on error-prone external sensors such as time-of-flight, ultrasonics, or computer vision, making solving complex challenges significantly more manageable. This becomes especially critical in in-person events like Pi Wars, where fine-tuning control code on the fly isn't an option.

{{< youtube g7BF0To9cgk >}}

This video showcases the accuracy and repeatability of odometry during the Tidy the Toys challenge. The robot's movements rely solely on odometry, utilizing encoders and IMU feedback without external sensors. The initial runs highlight repeatability, while the final clip reveals accumulated errors over multiple runs.

## Inspired by Commercial Ventures: Accurate Odometry with RC Cars
Fast forward to 2020, and Rob and I embarked on a commercial project involving a robot platform built around an RC car. This unique platform featured encoders and an IMU for odometry. What surprised us was the astonishing accuracy of its odometry, with minimal drift of around 1%, even at relatively high speeds. This experience left a lasting impression on us and planted the seed for our innovative approach in the development of Overwhelming Surplus of Diggity (OSoD).
![example of a light painting created by our robot](https://pbs.twimg.com/media/Epix833XYAIaMw-?format=jpg&name=4096x4096 'light painting')
An image created by the RC car-based robot as part of the commercial project, demonstrating its capabilities though long-exposure light paintings. The robot's movement and path planning were predominantly based on odometry, which showcased impressive accuracy.

## The OSoD Concept: A Unique Blend
With this rich background of experiences, the concept of OSoD took shape. We recognized that traditional RC car setups—featuring undriven, steerable front wheels and a single motor driving a differential connected to the rear wheels—wouldn't meet the demands of many Pi Wars challenges. These challenges often call for the traction of four-wheel drive and the capability to execute spot turns with precision.

Our brainstorming sessions led us to an intriguing idea: What if we could retain the controllability of car-like steering while enjoying the benefits of independent four-wheel drive? This concept paved the way for OSoD. However, achieving this vision involved overcoming a significant hurdle—digitally mimicking the effect of a differential.

In essence, we needed to actively control the wheels when turning, driving the outer wheels faster and slowing down the inner ones in a manner perfectly synchronized with the steering angle. This would prevent slippage, maintain the accuracy of odometry, and allow for precise cornering. Additionally, OSoD could switch into an extreme "toe-in" configuration when executing spot turns, eliminating scrubbing and enhancing maneuverability.

Note: The term "Ackermann" steering, often associated with car-like steering, isn't entirely accurate here. OSoD achieves different wheel turn angles digitally rather than through mechanical linkages. We're brainstorming a more fitting name for this unique approach, such as "Half-Swerve" or "Virtual Ackermann."

## OSoD Testbeds: Proving the Concept
Our journey with OSoD kicked off with a scaled-down testbed, allowing us to experiment without committing to the full-scale build. This test platform employed n20 motors and existing electronics, driven manually via radio control. It was a valuable but challenging initial test, with motors lacking encoders, which made precise synchronization a persistent issue. Scrubbing and crab-like movements sometimes emerged, reminiscent of a go-kart with a fixed rear axle and no differential.

{{< youtube T5OmbwSUevo >}}
OSoD's initial testbed in late 2021, driven manually via radio control. The video illustrates challenges with wheel synchronization, highlighting the need for further refinement.

## Refinement and Progress: OSoD Testbed 2
In early 2022, we set the stage for a full-scale OSoD testbed, though it remained unassembled until the announcement of Pi Wars 2024 in late 2023. This testbed featured essential components, including four 22mm gearmotors with encoders, custom motor mount plates with integral steering bearings, and two RotorStar RS-3878MGT servos for steering.

{{< youtube 2O1fviydWTE >}}

We had figured out the mathematics governing the "mixing" of wheel speeds and steering angles—a concept known as Inverse Kinematics—in late September. However, the conversion into functional code awaited completion. In our current setup, encoder feedback and speed control aren't yet operational. Thus, different wheel speeds are achieved by adjusting motor duty cycles, with the assumption that these speeds will be proportionate to the duty cycle.

{{< youtube zi0BeEbqnBU >}}
A video demonstration of OSoD Testbed 2, showcasing the steering mechanism. The testbed features four 22mm gearmotors with encoders and two RotorStar RS-3878MGT servos for steering.

## A Promising Future
We're thrilled to report that the OSoD testbed is performing as anticipated. Wheel scrub and slip are nonexistent, and the robot responds precisely to our commands, displaying exceptional maneuverability. It excels in executing tight and wide turns with controllability—a feat we hope will translate into accurate and repeatable odometry. The final piece of the puzzle involves getting the IMU fully operational, which is our next endeavor.

With these advancements, we're laying a solid foundation for OSoD's success in Pi Wars 2024. Our commitment to achieving accurate odometry and precise control promises to make this year's competition an exciting journey. Stay tuned for more updates as we embark on the next phases of development.