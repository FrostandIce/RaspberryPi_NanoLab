# RaspberryPi_NanoLab
###### A step by step guide on how to set up a Raspberry Pi Zero W to take pictures and tweet them online!
**Contains infomation for how to have plug and play fuctionality and how to run the Pi headlessly**\
This is meant to be followable for anyone with no coding and raspberry pi experience.\
This is the twitter bot I made for this [project](https://twitter.com/CCHSNanolabs)
## Introduction
Hello! My name is Brody Pen and I'm a student at Clear Creek High School in Texas. In the first semester of my senior year, I was tasked with making a project for our NASA HUNCH class. A generic Nanolab in which plants can grow in space without any interference from a person in a 30 day mission. You can see more about this [here](http://www.hunchdesign.com/uploads/2/2/0/9/22093000/ag_nano_lab_10-13.pdf)\
\
The most important programming infomation that gave guidance to my ideas are
-  Raspberry Pi for control of water, light, air, camera, timing, power, sensors
-  Everything must fit inside a 10cm x 10cm x 20cm aluminum container (external dimensions) the walls of the aluminum container are 3.18
mm thick.
-  Limited to 2 USB cables for power

Another important thing is that "The purpose of this NanoLab is for it to be versatile enough so that anyone who wants to do a seed or
small plant growth study in zero gravity can make small adjustments to the platform and send up their experiment without having to design
the whole lab from the bottom up."\
This is why I deicided to use a Raspberry Pi Zero W because of the small size and compact components, yet powerful enough to do everything we need. I also picked twitter because of the simplicity of getting a bot set up and ready and the vast amount of people avaliable on the website. 

Without further ado... let's begin!
## Setting up Raspberry Pi Zero W
###### Not neccessary if you have a SD card with raspian already installed
## Running Raspberry Pi Headless Guide
###### Using SSH and VNC
With a standard Raspberry Pi setup, you would need a bunch of wires. A HDMI cable and a monitor, a micro-usb cable to usb, and a keyboard and mouse. However, there is a way to use another computer or laptop and use the Raspberry pi from there! SSH (Secure shell) and VNC (Virtual Network Control) and the tools we need to achieve this. SSH will allow us to connect to the raspberry pi terminal, but VNC will allow us to see and control the Raspberry Pi like another desktop.
## Running Raspberry Pi with SSH
###### Terminal-like control
Ping into the raspberry pi in your wifi
```
ping -c 3 raspberrypi.local
```
SSH into it
```
ssh pi@raspberrypi.local
```
## Running Raspberry Pi with VNC
###### Desktop-like control
