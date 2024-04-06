---
title: "Return of the Carriage"
date: 2024-03-31T16:53:06+01:00
draft: false
tags:
- Robots
- RaspberryPi
- PiWars
- PiWars2024
- testing
- software
- debugging
---


# Serial Saga: Decoding the Mystery Byte
In the vast and intricate world of robotics, every byte matters, and a single misbehaving bit can lead to days of troubleshooting. Our recent odyssey with the  [SerialTransfer library](https://github.com/PowerBroker2/SerialTransfer), is a testament to the meticulous nature of debugging complex systems. This post recounts our journey through the frustrating, yet ultimately enlightening, process of identifying and resolving a bug that nearly stymied our project's progress.

### The Initial Success and Subsequent Stumble
Our mission was to adapt a serial transfer library for communication between our custom PCB, powered by a RP2040 (the same chip used by the Raspberry Pi Pico), and a Raspberry Pi. The library had served us well in the past, facilitating seamless message exchanges between a Teensy and a Pi. Armed with this confidence, we embarked on porting the library to bridge our PCB with the Pi, aiming to enable functionalities ranging from debug messages to autonomous control commands.

Rob had initially triumphed in sending a single message, comprised of three floats (1.0, 2.0, 3.0), a success that confirmed the basic viability of our approach. However, the landscape shifted dramatically when we introduced a new message type: a struct encapsulating our odometry data alongside time-of-flight (ToF) values - seven floats in total. Suddenly, the previously smooth transmission ground to a halt. Our messages were being dispatched but failed to arrive intact on the receiving end.

### Narrowing Down the Culprit
The bug manifested peculiarly; messages were sent and recognized by their intended type but arrived with an unwelcome addition - an extra byte. This intrusion rendered the CRC check unsuccessful, as the checksum no longer matched the data payload. Initial suspicions pointed towards the specific values being transmitted. Even hard-coded values, substituting live sensor readings, couldn't evade the bug. The extra byte, always 0x0D, hinted at something deeper, possibly related to encoding or data representation, yet its source remained elusive.

### The Breakthrough Insight
A eureka moment came when Rob noticed the extra byte consistently preceded a particular float value (0.159999996). This discovery led us down various hypotheses, from data padding concerns due to the RP2040's 32-bit system to potential issues with data types. Yet, it was the examination of the problematic float's hex representation (0ad7233e) that illuminated the path. The byte 0a stood out, not just for its position but for what it represented: a line feed character in ASCII.

Connecting 0a to its decimal form, 10, and recalling that ASCII code 10 signifies a line feed, we realized the nature of our adversary. Whenever the serial transfer encountered the byte for a line feed, it introduced a carriage return (0D or ASCII 13), altering the message integrity.

### The Simple Yet Elusive Solution
Our journey through forums and official documentation finally led us to the root of the issue: a "feature" within the Pico SDK that automatically added a carriage return upon encountering a line feed in serial output. The solution was disarmingly simple:

```
stdio_set_translate_crlf(&stdio_usb, false);
```
Inserted after `stdio_init_all();`, this one-liner disabled the default behavior, preserving the integrity of our serial communication.

## Reflections on a Debugging Odyssey
The resolution of this bug, while straightforward in hindsight, underscored several crucial facets of software development:

**Testing and Observation**: The importance of thorough testing and careful observation of anomalies cannot be overstated. Our iterative process of identifying the extra byte and its consistent association with specific data values was instrumental in narrowing down the problem.

**Deep Dive into Documentation**: Familiarity with the platform's documentation and features is invaluable. Our eventual solution came from understanding the nuances of the Pico SDK, facilitated by resources like the [official Pico SDK documentation](https://www.raspberrypi.com/documentation/pico-sdk/runtime.html#rpipa254b900af1131794ef5) and insights from [forum discussions on unexpected serial behavior](https://forums.raspberrypi.com/viewtopic.php?t=358887) and [SerialTransfer and Raspberry Pi Pico](https://forums.raspberrypi.com/viewtopic.php?t=305705).

**Persistence and Methodical Approach**: Debugging is often a test of perseverance. Our methodical approach, from scrutinizing code with a fine-toothed comb to leveraging an in-circuit debugger, exemplified the persistence required to unearth subtle bugs.

This debugging odyssey, while challenging, was a profound learning experience. It reinforced the value of meticulousness, collaboration, and resourcefulness in the face of perplexing software bugs. As we move forward, this episode remains a testament to the technical acumen and teamwork that drives our project's success.

![The magnifying glass hovers over a digital data stream, with '0ad7233e' clearly visible and highlighted, embodying the 'mystery byte'. The background blends circuit board patterns with binary code, highlighting technology and digital exploration. The scene is filled with intrigue and anticipation, showcasing a crucial discovery in the realm of computer science and electronic communication.](feature-image.png "The magnifying glass hovers over a digital data stream, with '0ad7233e' clearly visible and highlighted, embodying the 'mystery byte'. The background blends circuit board patterns with binary code, highlighting technology and digital exploration. The scene is filled with intrigue and anticipation, showcasing a crucial discovery in the realm of computer science and electronic communication.")
