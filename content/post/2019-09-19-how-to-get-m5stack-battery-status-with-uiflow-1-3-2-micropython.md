---
id: 132
title: "How to Get M5Stack Battery Status with UIFlow 1.3.2 MicroPython"
date: "2019-09-19T13:53:59+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2019/09/19/how-to-get-m5stack-battery-status-with-uiflow-1-3-2-micropython/

categories:
  - "Coding Laboratory"
  - "Python Code"
---

Recently I’ve got my hands on the M5Stack Core device. This device, not only brought possibilities of awesome ideas, but also bring me close to the world of MicroPython. For those who are unaware, MicroPython is software implementation of Programming language largely compatible with Python 3. In short, MicroPython is Python Compiler which can run on Microcontroller.

In this post, we will use MicroPython’s “machine” library for accessing i2c bus of the M5Stack Core. The battery circuit of M5Stack core is composed of IC IP5306, which provides i2c interface at 0x75 address with Battery Percentage of 0%, 25%, 50%, 75% and 100%.

To get started, UIFlow 1.3.2 firmware need to be flashed to the M5Stack Core device.

#### Flashing UIFlow 1.3.2 and connecting the M5Stack device in USB Mode

You can watch video till (2 Minutes 5 Sec) <https://www.youtube.com/watch?v=Y9pOWgsNgKk> for Flashing and connecting the M5Stack device in USB Mode.

#### Running Program

While device is connected with your Computer/Laptop in USB Mode, run UI Flow Desktop IDE. It will prompt for Connecting the IDE with device. Set the correct com port and you should be good to go for running the program. Select Python Mode and use the following code to access i2c bus and get the device’s battery status

<script src="https://gist.github.com/KunalGautam/b6f8265889c3798556164d047525c0b3.js"></script>

Run the code and voila! you can now get battery statistics on the screen.
