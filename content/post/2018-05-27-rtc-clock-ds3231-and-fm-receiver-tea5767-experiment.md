---
id: 126
title: "RTC Clock [ DS3231 ] and FM Receiver [ TEA5767 ] Experiment"
date: "2018-05-27T10:02:58+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2018/05/27/rtc-clock-ds3231-and-fm-receiver-tea5767-experiment/

categories:
  - "Arduino Code"
---

## Preface:

I've always fancy of using battery power devices, I run many of the my projects on Battery only, which are powered by Solar Panel(s). Music has very important place in my day to day life, and I didn't have any speaker which can run on battery. Hence I purchased Audio amp (PAM8403), and made a custom speaker powered by 5v DC. Although plugged to Raspberry Pi 1 B+ and using Internet Radio Stream, I found it very interrupting whenever there is a power cut. As my routers are not powered by Battery, there is Internet disconnection to Raspberry Pi and I can not play Internet Radio.

Hence to the call of the requirement, I purchased TEA5767 Module with Antenna and Audio Jack. Since I am planning to do some alarm clock type music system, which will turn on at required time and turn off in night, hence I added DS3231 RTC Module.

In future I might consider controlling it via wireless system (ESP8266 or NRF24l01). But let start this project with simple demo. Both of the module use I2C interface hence I used to share the wires between them.

## Libraries:

Default installed library : https://www.arduino.cc/en/Reference/Wire

I've used following Library, which were not installed by default.

Library for DS3231(Available for install via Library Manger in Arduino): https://github.com/adafruit/RTClib

Library for TEA5767 : <https://github.com/mroger/TEA5767>

## Pinouts:

| **Board**     | **I2C pins of DS3231 and TEA5767** |
| :------------ | ---------------------------------- |
| Uno, Ethernet | A4 (SDA), A5 (SCL)                 |
| Mega2560      | 20 (SDA), 21 (SCL)                 |
| Leonardo      | 2 (SDA), 3 (SCL)                   |
| Due           | 20 (SDA), 21 (SCL), SDA1, SCL1     |
| 5v            | Vcc                                |
| GND           | Gnd                                |

<script src="https://gist.github.com/KunalGautam/ec89304813fbee04ebd503ae5053fc89.js"></script>

## Project Description:

After pushing the code to microcontroller (Arduino Uno in my case), the default station set in the code is played. I open Serial Console, set baud rate at 115200 and send the desired frequency between 88MHz to 108MHz, and press send button. It play that FM station. Alternatively I can use to send "+" or "-" keys, to scan FM frequency and halt whenever a broadcasting frequency is found.

## Final Word:

There are other options like Mute sound, or put device to sleep in the GitHub code of TEA5767 which I have not included in this code.

Yes this is not consumer friendly project, as there is no option of controlling the device easily. The device can have option of using buttons or using wireless communication methods. I'll leave that part of exploration with my dear readers. Feel free to contact me via <https://ikunal.in/contact/>
