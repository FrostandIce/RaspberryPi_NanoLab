# RaspberryPi_NanoLab
###### A step by step guide on how to set up a Raspberry Pi Zero W to take pictures and tweet them online!
**Contains infomation for how to have plug and play fuctionality and how to run the Pi headlessly**\
This is meant to be followable for anyone with no coding and raspberry pi experience.\
This is the twitter bot I made for this [project](https://twitter.com/CCHSNanolabs)
## Introduction :wave: 
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
## Setting up Raspberry Pi Zero W :mortar_board:
###### Not neccessary if you have a micro SD card with raspian already installed
If you bought a standard Raspberry Pi Zero W kit, you might already have everything needed to run! Place the micro SD card and turn on the Raspberry Pi and it will turn on. However! If you're SD card does not have raspian installed, it won't run. Plug in the micro SD card into a computer or a SD card reader and head over to the Raspberry Pi [website](https://www.raspberrypi.org/software/)\
You can download the OS manually or through the Raspberry Pi Imager. I recommand you use the imager and follow the instructions.

A common question is: which OS should you download?\
I recommend *Raspberry Pi OS with desktop and recommended software*, this allows you to interact with the Raspberry Pi similar to any desktop. Lite would be command-line only.

After flashing the OS to micro SD card, everything ready to go! Plug in the power supply and a monitor with the micro SD card on the pi and it should flicker to life.
However, if you're making a project where having a monitor, keyboard, and mouse becomes a issue... consider running it headlessly!
## Running Raspberry Pi Headless Guide using MacOS :computer:
###### Using SSH and VNC 
With a standard Raspberry Pi setup, you would need a bunch of wires. A HDMI cable and a monitor, a micro-usb cable to usb, and a keyboard and mouse. However, there is a way to use another computer or laptop and use the Raspberry pi from there! SSH (Secure shell) and VNC (Virtual Network Control) and the tools we need to achieve this. SSH will allow us to connect to the raspberry pi terminal, but VNC will allow us to see and control the Raspberry Pi like another desktop.
## Running Raspberry Pi with SSH
###### Terminal-like control
Before we can begin, there are a few things that might be blocked on your computer and must be allowed to establish a SSH connection. MacOS needs the firewall to be turned off for computer sharing to occur. Head over to your settings go to privacy and turn these off to establish a SSH connection.
Next, you have to connect the raspberry pi to your wifi and also enable SSH which is off by default. 
This requires you to add two files to the micro SD card that the Pi will run on.
The first file will configure the wifi and must be called **wpa_supplicant.conf**, inside add the following code.
```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=US
     
network={
    ssid="YOURSSID"
    psk="YOURPASSWORD"
}
```
There are 3 variables you might need to change.\
**country=US** might need to be changed to a different country if you aren't from the US. Find your country code [here](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2).\
**ssid = "YOURSSID"** will be changed to the SSID you are trying to connect to.\
**psk = "YOURPASSWORD"** will be changed to the SSID password.\
With this, you have configure for the wifi! Next you must enable SSH.\
All you need to do is add a empty file with the name **SSH** into the micro SD card.\
This will enable SSH for the Pi, but it is not neccessary if your Pi is older than 2014 because it might be enabled by default.\
With these files in the SD card, plug in the Micro SD card and the 5V power supply into the Raspberry Pi and turn it on!\

On the Raspberry Pi Zero W, a blinking led should start lighting up. That means you are getting power in the Raspberry Pi.\
With your desktop/laptop **On the __same__ wifi network** as the Raspberry Pi, trying pinging the Pi with your terminal with this command.
```
ping -c 3 raspberrypi.local
```
This pings it 3 times. If all is well, it should give you a response time.\
If you don't get this message, please check out the list below. It's a list of possible problems and solutions that helped me!\
- **wpa_supplicant.conf** needs to be strictly formatted. One example is when people add a space between the ssid and the "YOURSSID". It should be ssid="YOURSSID". ~~ssid= "YOURSSID"~~ will **not** work! Also take the time to make sure the **wpa_supplicant.conf** has the correct country_code, SSID, and password.
- Also make sure both devices are connected to the same wifi. Whatever wifi you put in the **wpa_supplicant.conf** should be the same you are connected to.
- If using a VPN, turn it off! VPN disguises your IP address when you use the internet, making its location invisible to everyone. This is great for privacy, but terrible if you are actually trying to connect a Raspberry Pi to a personal computer.
- If none of these work, Turn it off and then on again. Wait another minute and redo the pinging process!
SSH into it
```
ssh pi@raspberrypi.local
```
## Running Raspberry Pi with VNC
###### Desktop-like control
Find out the ip address of the raspberry pi
```
ifconfig
```
## Sources
###### Helpful places to go!
- [Adafruit learn](https://learn.adafruit.com/)
- [Raspberry Pi learn] (https://www.raspberrypi.org/learn/)
- [Raspberry Pi software] (https://www.raspberrypi.org/software/)
