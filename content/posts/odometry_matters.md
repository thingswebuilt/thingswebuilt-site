
---
title: "Odometry Matters"
date: 2023-12-27T16:53:06+01:00
draft: false
---

## Odometry Matters ##

We've passed a huge milestone for our Pi Wars entry this week - it was the first time we got the wheel speeds and steering angle to move in sync. At first, this might sound like quite a small thing, and that its come relatively late in the build, given we started on this design back in 2021! To explain the significance of this test drive, we need to go back to before we even had the idea for Overwhelming Surplus of Diggity, to our experience with our Pi Wars entry Tauradigm. 

### Learnings from Tauradigm
Tauradigm was our first robot with encoders, started in 2018. It had six wheels with an encoder per wheel, allowing us to measure the wheel movement of each wheel to within a millimetre. Combining that movement data with the heading data from the Inertial Measurement Unit, we could get a reasonable estimate of how the robot had moved around the arena. This approach is generally known as odometry. The odometry based position estimation on Tauradigm was very repeatable, but not particularly accurate (~10% drift over a distance travelled). The accuracy was particularly poor on sweeping turns. Similarly, Tauradigm was quite easy to control in a straight line, or turning on the spot, but wider turns were a little erratic and required fast feedback from external sensors to maintain a smooth turn. Luckily we could work around these trade-offs for the at-home Pi Wars event in 2021, but we knew they would be a handicap for an in-person event where we can't endlessly test and tune the control code to the specific arena. Accurate odometry makes solving robotics challenges so much easier, and avoids having to rely on error-prone external sensors like time-of-flight, ultrasonics or computer vision. 

{{< youtube g7BF0To9cgk >}}

This video shows us testing the accuracy and repeatability of odometry for the Tidy the Toys challenge. The movement of the robot is entirely based on odometry using the encoders and IMU for feedback, with no external sensors. The first few runs show the repeatability. The final clip shows us running the same course over and over without resetting the initial position, and so shows the accumulated error. 

### Playing with RC cars for work
Cut to 2020, and Rob and I worked on a (commercial) project where we developed a robot platform from on an RC car! That also had encoders and an IMU for odometry. The odometry was incredibly accurate (~1% drift!) and relatively easy to control, even at fairly high speeds. This is what made us decide to try car-like ("Ackermann"*) steering for OSoD. 
![example of a light painting created by our robot](https://pbs.twimg.com/media/Epix833XYAIaMw-?format=jpg&name=4096x4096 'light painting')
One of the tests of that robot platform was creating long-exposure light paintings. The movement and path planning was based on more than odometry, but in testing we found the odometry alone to be surprisingly good.

### The OSoD concept
So that's the background to the idea behind OSoD. We knew that a traditional RC car arrangement, with undriven, steerable front wheels and a single motor driving a differential connected to the rear wheels, wouldn't work for many Pi Wars challenges. We often need the traction of 4 wheel drive, and frequently need to be able to turn on the spot. We started brainstorming variations that might have the benefits of car-like steering without the trade-offs. We realised that independent 4 wheel drive would allow us to skid-steer turn on the spot like many entries, but if we turned the front wheels we could potentially retain the controllability of car-like steering. The complication would be that we'd have to digitally mimic the effect of a differential, actively driving the wheels faster on the outside of the turn and slowing those on the inside, at a rate consistent to the steering angle to avoid slip (and so lose accuracy with odometry, as well as limit the cornering speed or controllability). As we thought more about how the robot would perform in different situations, we realised that if the front wheels could be independently steered, then for situations where we want to turn on the spot, we could potentially go into an extreme "toe-in" arrangement and so also eliminate any scrub in that manoeuvre too.  

### OSoD testbed 1
To test the idea at small scale, without having to buy the motors, motor controllers etc planned for OSoD, we built a small test platform around n20 motors and electronics we already have. For this early test, the motors didn't have encoders, and we didn't have a microcontroller, it was all "manual" over radio control. 

{{< youtube T5OmbwSUevo >}}

This early test (in late 2021) was a little disheartening, as it was impossible to perfectly synchronise the wheel speeds with the steering angle.  There always seem to be some scrub, and sometimes it even seemed to crab sideways instead of turning. It looks like the wheels were fighting the turning, like when a go kart has a fixed rear axle with no differential. It certainly didn't show the idea was worthwhile. We weren't too put off by the test though, we hoped that the issues were all because of the manual control and the lack of encoders. 


### OSoD testbed 2
We cut the full-size test chassis in early 2022, but by that point it was clear we were too far behind to be ready in time for the event. The chassis wasn't actually assembled until Pi Wars 2024 was announced in late 2023. 

{{< youtube 2O1fviydWTE >}}

This video shows how the steering mechanism works on the test bed. There are 4 x 22mm gearmotors with encoders (two with custom motor mount plates with integral steering bearings), and 2 x RotorStar RS-3878MGT servos for the steering.
We figured out the maths for the "mixing" (wheel speeds and steering angles for a given movement, aka. Inverse Kinematics) in late September, but only recently got that converted into working code. We've actually still not got the encoder feedback and speed control working, so the different wheel speeds are just achieved by varying the duty cycle to the motors and its assumed/hoped that the wheel speeds will be proportional to the duty cycle. Anyway, without further ado, here's the video of the test:
{{< youtube zi0BeEbqnBU >}}
We're extremely pleased that it's performing as expected: there's no wheel scrub or slip, it goes where you ask it to, and it's extremely manoeuvrable. Tight and wide turns are controllable. We hope this all translates into accurate and repeatable odometry. All going well, we should find that out soon. We just need to get the IMU working.

* We need to come up with a better name, as its not using the linkages from an Ackermann geometry, the different wheel turn angles are achieved digitally. Half-Swerve? virtual Ackermann?