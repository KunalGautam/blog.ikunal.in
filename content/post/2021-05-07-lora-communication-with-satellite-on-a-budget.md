---
id: 135
title: "LoRa communication with Satellite on a Budget"
date: "2021-05-07T09:26:43+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/05/07/lora-communication-with-satellite-on-a-budget/

categories:
  - "Electronics Laboratory"
  - "Radio Communicaion"
---

Radio and Wireless communication has always amazed me since I was a kid. We can not imagine our life without relying on wireless communication in current date. Be it WiFi or Cellular connectivity, almost everything rely a lot on Wireless Communication. The Wireless Technology has developed a lot since its inception. One of the interesting technology is LoRa, which stands for Long Range.

Although communication with satellite is nothing new. My friend Martin from U.K. (Call Sign G0PYB) is doing it since ages. The LoRa communication using satellite is something new and interesting. The LoRa communication requires much less power and have long range compared to other wireless protocols. With launch of many Cubesats (basically small satellites) in LEO (Low Earth Orbit), for educational and scientific purpose, anyone with access to basic hardware can access to LoRa communication using Satellite.

Interestingly, at the time of writing, there is one project named TinyGS, which will help you to get started with it. As per their website:

_"Initially TinyGS was born under the name ESP32 Fossa Groundstation, it was developed as a "weekend" project for the FossaSAT-1 LoRa satellite. We are passionate about space and created this project to be able to track and use the satellites and to learn and experiment about radio. Currently the network is open to any LoRa satellite and we also support other flying objects that have a compatible radio modulation with our hardware such as FSK, GFSK, MSK, GMSK, LoRa and OOK. And the project was renamed to TinyGS."_

There is very helpful community on Telegram (<https://t.me/joinchat/DmYSElZahiJGwHX6jCzB3Q>) where people are very helpful to get started with the TinyGS Project. The recommended hardware are listed at wiki page of TinyGS i.e. at <https://github.com/G4lile0/tinyGS/wiki#hardware>

This post is all about getting started with TinyGS project with very basic hardware in a budget friendly manner. Please note that connecting to OLED display is optional. To get started you would need the following Bill of Material (BOM):

1\) ESP32 Dev Kit

2\) RA02 LoRa Module (433MHz)

3\) Wires (for soldering)

4\) Coaxial Cable (For making antenna)

5\) u.fl Connector with Wire (To connect RA02 module with Antenna)

6\) OLED 128x64(Optional)

7\) RA02 plate board(Optional)

**Solder the wires in following manner**

RA02 Connection.

In case wiring RA02 seems hard, you can use plate board and solder RA02 to the board. It will give you better 2.54mm pitch for soldering. I didn't had that plate board hence used ESP8266 Plate Board after removing all resistors and capacitors from it.

| **SL. No.** | **RA02 LoRa Module** | **ESP32**     |
| ----------- | -------------------- | ------------- |
| 1.          | GND                  | GND           |
| 2.          | MISO                 | 19            |
| 3.          | MOSI                 | 27            |
| 4.          | SCK                  | 5             |
| 5.          | NSS                  | 18            |
| 6.          | DIO2                 | Not Connected |
| 7.          | DIO1                 | 33            |
| 8.          | DIO0                 | 26            |
| 9.          | 3.3v                 | 3.3v          |
| 10.         | DIO4                 | Not Connected |
| 11.         | RST                  | 14            |
| 12.         | DIO5                 | Not Connected |

OLED Connection

| **SL. No.** | **OLED Module** | **ESP32** |
| ----------- | --------------- | --------- |
| 1.          | GND             | GND       |
| 2.          | Vcc             | 3.3v      |
| 3.          | SCL             | 22        |
| 4.          | SDA             | 21        |

For antenna, we will make a Bazooka Dipole. To make a bazooka dipole, use following images as a guide on how to cut and strip. You can use any of these two design suggestion as both of them worked without any problem. Alternatively check out other Antenna suggestions at TinyGS Wiki (<https://github.com/G4lile0/tinyGS/wiki/Antenna>). Make sure to join the u.fl. wire end to bazooka dipole. If possible solder it for better connection and less losses. Use 34cm length, as we are going to track satellite around 433MHz.

![](/post/135/bazooka-dipole.jpg)
Bazooka Dipole design that I've used

![](/post/135/modified-bazooka-dipole.jpeg)Bazooka Dipole Design for better performance.

Once soldering is done, Follow Quick Started guide at TinyGS Wiki (<https://github.com/G4lile0/tinyGS/wiki/Quick-Start>)

After flashing successfully, configure the board as guided in quick started page, and select device as 433 Mhz TTGO LoRA 32 v2. Now that device is configured properly, you can now connect u.fl connector to RA02 Board. Place the antenna in open sky to receive the packets from Satellite using LoRa.

**Special Thanks :**

1\) @Kreatif for Antenna suggestion <https://github.com/G4lile0/tinyGS/wiki/Antenna> and time to time resolving my questions.

2\) G0PYB (Martin, U.K.) to help me out wiring for RA02 with ESP32 Dev Kit, time to time suggestion on improvements in antenna design and suggestion for this post.

**Deployment Pics**

![](/post/135/soldering-ra02.jpeg) Soldering RA02 Module on ESP8266 Plate

![](/post/135/after-soldering-ra02.jpeg) RA02 after soldering to ESP8266 Plate.

![](/post/135/esp32-connected-with-ra02.jpeg) ESP32 and RA02 connected.

![](/post/135/bird-side-view.jpeg)Side View of Bird Inspecting the Antenna

![](/post/135/bird-front-view.jpeg)Front View with Bird inspecting antenna
