---
id: 1724904721508507261
title: "Setting up DireWolf TNC I-Gate and Digipeater on RaspBerry Pi"
date: 2024-08-29T09:42:01+05:30
author: "Kunal Gautam"
type: post

categories:
  - "HAM Radio"
  - "Radio Communicaion"

tags:
  - "HAM Radio"
  - "Amateur Radio"
  - "Raspberri Pi"
  - "Linux"

---

Last few days, with help of my Friend Prateek(Callsign VU3YEK), I was quite busy in testing APRS for communication over the radio. We setup APRS I-Gate at our home and extensively tested it over a period of time. Now that everything is in proper place, I had a thought to share my APRS I-Gate and Digipeater setup with everyone(and to show some activity on my almost dormant blog). I'm using a Raspberry Pi 3 along with USB sound card and PTT interface with Baofeng 888s radio. Before moving forward to installation of DireWolf TNC lets see overview of APRS and DireWolf TNC. 

##### Note: This post assumes, you have knowledge about proper wiring the connection and running linux.

## About APRS
APRS (Automatic Packet Reporting System)APRS is a fascinating system used by amateur radio operators to exchange real-time data over radio frequencies. Here are its pros and cons:
### Pros:
- Real-Time Position Tracking: APRS allows users to track the location of vehicles, weather stations, and other assets in real time. It's commonly used for vehicle tracking during events or emergency situations.
- Emergency Communication: In emergencies, APRS can transmit critical information such as distress signals, weather updates, and evacuation routes.
- Low-Cost Implementation: Unlike traditional TNCs (Terminal Node Controllers), APRS can be set up using inexpensive hardware and software.
- Integration with Maps and Software: APRS data can be visualized on maps, making it easy to see the position of stations and objects.
- Wide Coverage: APRS operates globally, making it useful for long-distance communication.

### Cons:
- Limited Data Rate: APRS uses low data rates, which restricts the amount of information that can be transmitted.
- Single Frequency: APRS typically operates on a single frequency, which can lead to congestion during high-traffic periods.
- Dependency on Radio Infrastructure: APRS relies on radio infrastructure, so coverage may be limited in certain areas.
- Privacy Concerns: Since APRS data is publicly accessible, privacy can be a concern for some users.

## About DireWolf TNC
DireWolf TNC SoftwareDireWolf is a versatile software "soundcard" TNC (Terminal Node Controller) and APRS encoder/decoder. Here's what you need to know:
### Functionality:
  - DireWolf can be used as a standalone APRS tracker, digipeater, APRStt gateway, or Internet Gateway (IGate).
  - It replaces the need for specialized hardware TNCs by utilizing a computer's soundcard interface.
  - It decodes APRS messages and supports over 1000 error-free frames from Track 2 of the WA8LMF TNC Test CD.
  - DireWolf includes Forward Error Correction (FEC) through FX.25, which is compatible with existing systems.

### Other Applications:
  - DireWolf can also act as a virtual TNC for applications like APRSIS32, UI-View32, Xastir, and more.
In summary, APRS offers real-time tracking and emergency communication, while DireWolf provides a flexible software solution for APRS decoding and encoding. Feel free to explore both further! 📡🌐

---

## Installation of DireWolf TNC


##### Note: This post is tested on freshly installed Raspbian OS on Raspberry Pi 3. It is assumed that it will work on All Raspberry Pi Models and Raspbian OS. Everything is being running as root, although it can be done with General user account too (With access to USB soundcard and ptt interface). In case PTT interface is not available, you can try VOX method of your radio, but that I'd not recommend. It is assumed that the Raspberry Pi is constantly connected via Internet also.


#### Installation of Prequisites

Install the required packages by running following command in the terminal window.

`
apt install nano tmux git gcc g++ make cmake libasound2-dev libudev-dev libgps-dev libhamlib-dev libavahi-client-dev libavahi-core-dev espeak -y
`
#### Download and Compile DireWolf

Download the latest DireWolf code from GitHub in the home directory and compile it using following commands.

`cd~`
`sudo git clone https://www.github.com/wb2osz/direwolf`
`cd direwolf`
`mkdir build && cd build`
`cmake ..`
`make -j4`
`make install`
`make install-conf`
`cp direwolf.conf ~`


#### Configure Raspberry Pi to disable HDMI and Inbuilt Sound card

One of the problem I faced was change in device number of soundcard after each reboot, to fix this I've disabled all HDMI Sound and onboard audio jack. To do this open `/boot/firmware/config.txt` in your preffered editor and add/modify the following lines accordingly

```
# Enable audio (loads snd_bcm2835)
dtparam=audio=off
# Enable DRM VC4 V3D driver
dtoverlay=vc4-kms-v3d,noaudio
```

After modifying/adding, reboot your Raspberry Pi and plug your USB Soundcard and PTT Interface.

#### Identifying Soundcard playback and Recording Device

To Identify Playback device run following command
`aplay -l`
It will list all playback devices. It will show something like this
```
**** List of PLAYBACK Hardware Devices ****
card 0: Device [USB PnP Sound Device], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```
Here the Device number is 0.

To Identify Recording device run following command
`arecord -l`
It will list all playback devices & the output of the command will be something like this
```
**** List of CAPTURE Hardware Devices ****
card 0: Device [USB PnP Sound Device], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```
Here the device number is 0.

#### Adjusting volume of the soundcard device

A proper volume level is needed for processing APRS signal. I've set up 50% level on both playback and recording devices. To adjust soundcard level run following command.
`alsamixer`
Once you quit `alsamixer`, save the sound settings by running following command.
`alsactl store`

#### Get device details for PTT Interface

Run the following command to get the devide information of PTT interface.
`ls /dev/serial/by-id/`
It will display something like this
```
ls /dev/serial/by-id/
usb-1a86_USB_Serial-if00-port0

```
Note down the file as '/dev/serial/by-id/usb-1a86_USB_Serial-if00-port0'. Otherwise the /dev/ttyUSB`x` or /dev/ttyAMA`x` device designation can also be used where x is your device number. I've not used this as it might also get changed if more peripherals are connected. 

#### Get your Passcode for Callsign

You can get passcode for your callsign at 
- https://apps.magicbug.co.uk/passcode/ 
- http://n5dux.com/ham/aprs-passcode/ 

There are many more websites which can generate passcodes for you. You can search them on search engines. Note down the passcode to be used later.

#### Make dwespeak.sh script for processing Text to Speech

Create a file named `dwespeak.sh` under `/usr/bin` with following content and make it executable.

```
#!/bin/bash
chan=$1
msg=$2
sleep 1
espeak -v en-sc "$msg"
```


#### Now that we have all the information available, let's dive into configuring the DireWolf TNC

Edit the direwolf.conf which we copied in user's home directory in earlier step and add/edit/uncomment following lines and save the file.

```
ADEVICE  plughw:0,0
ACHANNELS 1
CHANNEL 0
MYCALL VU3YEJ-10
MODEM 1200
PTT /dev/serial/by-id/usb-1a86_USB_Serial-if00-port0 DTR RTS
SPEECH dwespeak.sh
AGWPORT 8000
KISSPORT 8001
PBEACON delay=0 every=10 overlay=T symbol="igate" lat=18.603986824928814 long=73.93357992388026 comment="iGate of VU3YEJ>
CBEACON delay=0 every=5 dest="MORSE-7" info="VU3YEJ"
CBEACON delay=0 every=10 dest="SPEECH" info="Club meeting tonight at 7 pm."

DIGIPEAT 0 0 ^WIDE[3-7]-[1-7]$|^TEST$ ^WIDE[12]-[12]$
IGSERVER rotate.aprs2.net
IGLOGIN VU3YEJ 21412

IGFILTER r/18.603/73.933/50
FILTER IG 0 t/poimqcstuhnw/VU3YEJ-10/50

PBEACON sendto=IG delay=0:10 every=30:00 symbol="igate" overlay=T lat=18.60398 long=73.93357 power=4 height=001050 gain=2 comment="QRV on 434.500MHz"

IGTXVIA 0 WIDE1-1,WIDE2-1

```

So in above configuration:
- The `ADEVICE` is pointing to the device number of your Playback and Recording device.
- `ACHANNELS` is making audio channel to MONO.
- `CHANNEL` is for settings toward channel. You can make multiple channels and point your RF and I-Gate to them accordingly.
- `MYCALL` specify your call sign. I've added SSID of 10, although you can omit the SSID. But as per best practise I've used SSID 10.
- `MODEM` spevify bitrate, 1200 is commonly used for VHF/UHF, and 9600 is used for HF communication
- `PTT` settings for PTT interface
- `SPEECH` specify text to speech script.
- `AGWPORT` & `KISSPORT` specify port for KISS and AGW Communication over the network
- `PBEACON` Beacon setting. if 'sendto' option is not specified, the beacon is sent over RF, if the option is set to `ig` it will send beacon through Internet Gateway. `delay` option specify minutes of delay in transmitting beacon after direwolf is started/restart. `every` option specify the beacon transmittion delay after  number of minutes passed from last beacon. 
- `CBEACON` is automated beacon which you can configure to transmit MORSE or SPEECH beacon. MORSE-7 in above config specify the 7WPM speed. the `dest` option specify if the Beacon is morse or text to speech based. `info` option is the data you want to transmit.
- `DIGIPEAT` enable digipeating
- `IGSERVER` specify APRS IG (Internet Gateway) server
- `IGLOGIN` specify your call sign and passcode obtained earlier
- `IGFILTER` & `FILTER` filter the type of data to be retreived by APRS Internet Gateway
- `IGTXVIA` Relay Internet Gateway message via RF (0 in the above configuration specify the CHANNEL)


#### Note: SPEECH and CBEACON can be omitted, but I've added them as it was required for me for identification over RF.
---

Although this process may seems to be exaggerated for few people, but final result is a solid and reliable IG adn Digipeater solution. After setting up, one can also use it to track your APRS movement and share your track via different means (Like Telegram/WhatsApp/Email/SMS) to your friends and relatives, possiblities are endless!!