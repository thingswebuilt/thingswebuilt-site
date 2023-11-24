---
title: "Solid progress"
date: 2023-11-24
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- Software
---


![A DALL-E generated image representing the SOLID software principles](solid.png "SOLID")

This week, we've been learning about the SOLID principles of software. When I say we, I mean I (Mark) have been learning, and Rob (the professional computerman on our team) has been suggesting videos and other resources, and helping clarify bits I've not understood. 
My take on the SOLID principles, in the context of a Pi Wars robot's software is:

S: Single Responsibility Principle (SRP)
Each component of the code (function, class or whatever) should have one job. If a piece of code does two things, it might be better to split it in two. The "single thing" could be PID, drive the motors, read a sensor or decide on a route to a goal. 

O: Open-Closed Principle (OCP)
I think this principle is technically about derived classes or subclasses (concepts that amateur coders may not be familiar with), but it can be applied to simpler code structures. The "open-closed" is referring to how extra features are added - "open" for features to be added on top, but closed for direct modification. I think one way to think about this is if you want some variants of a unit of code, it'd be better to wrap that code with the variations in the wrapper function, than to duplicate the code and then make the changes by editing one of the copies. Duplicating code can make it difficult to maintain. 

L: Liskov Substitution Principle (LSP)
This principle is technically also about derived classes, but I think the intent applies to other units of code too. Basically, components of the code should be substitutable. So if you making a line follower, it should be possible to swap out the steering "algorithm" (whether "bang-bang", PID or something else), with a different algorithm without making any other changes to the code. This makes it easy to try different behaviours and to make changes. This principle obviously goes well with the Single Responsibility Principle, as it's harder to just swap out the algorithm if the code responsible for that algorithm also does other tasks, like talk to the motors or read the sensors. 

I: Interface Segregation Principle (ISP)
Technically, this is about "clients" not being forced to depend on inappropriate interfaces, but I'm not sure that applies much to most Pi Wars robots. A possible example could be if you use a servo library to generate the 1-2msec pulses to control an RC ESC. In that case, it'd make more sense for the servo library to have a -1 to +1, or -100% to +100% input, than to use a less relevant angle input. A generic microseconds or milliseconds interface might be a reasonable compromise.
For us, it's about defining interfaces that contain only the information required for that unit to operate, with appropriate units. This is somewhat related to the security principle of the "Principle of Least Privilege (PoLP)", where code only has access to the information that's required for it to do its job. In practical terms, this means avoiding using global variables (where different parts of the code could inadvertently change their value), and instead passing only the required values, pointers or objects to the unit of code.

D: Dependency Inversion Principle (DIP)
This principle is related to abstraction. Which sounds complicated, but actually can make code much easier to write and understand. Basically, the "high level" code (e.g. how do we follow a line), shouldn't depend on the details of the how the motors are driven or the individual sensor values. I find it easiest to think in terms of units. If the code responsible for line following uses things like centimetres from the line or angle of deviation from the line as the input, and wheel speed in cm/s as the output, then that code can be used on any robot. The lower level code can convert the specific raw sensor values into the more universal (abstract) values with standard units. This also allows for different motors or sensors to be swapped in without changing the algorithm. 


We're going to be trying to appropriately apply these principles to the structure of our software, which is likely to be the subject of an upcoming post. 

Some links to further reading:
[article](https://www.freecodecamp.org/news/solid-design-principles-in-software-development/)
[video with examples in python](https://www.youtube.com/watch?v=pTB30aXS77U)