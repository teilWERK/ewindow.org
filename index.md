---
title: THE ELECTRONIC WINDOW
layout: default
---

![rollup](images/NEW POSTER ANOTHER IDEA-01.jpg)

## What is it?

Ewindow is a #Social Network# 
#Open Source#  // the code is here: enjoy it //
#Decentralized# // no central control owned by some big corporation using for other purposes your data //
#free# // if you want, you can build up your own network //


The EWindow is a video chat device that runs 24/7 in a shared space.
The goal is a decentralized, secure 24/7 audiovisual communication system --> Like a window in a wall.

![A view into the Fablab Munich](images/EWindow_HEi_VOW.jpg)

## DESIGN DEVELOPMENT + ELECTRONICS


- A Raspberry Pi //3 (2 is ok too)//
- 2 GiB  SD Card
- Monitor (with Cable)
- Speakers //CONNECTED VIA JACK, AND NO VIA USB//
- USB Webcam with microphones 
- A button and a bit of jumpwire


If you want to improve the audio/video quality:
- Raspberry PiCam //wide-angle version recommended//
- USB Speakerphone //will replace speakers and microphone//



Software Development  
===========
## Code
https://github.com/strfry/ewindow

## How is it implemented?

Development of the EWindow is focused on three parts:

1) Enhancing a lightweight SIP Video Phone with Raspberry Pi support

    git clone https://github.com/alfredh/baresip
    
2) A Qt/QML-based user interface

    git clone https://github.com/strfry/ewindowui

3) Configuration details for a specific platform
    
    git clone https://github.com/strfry/ewindowui
    
    
 To Download the Image  
========

[https://ewindow.org/download/ewindow-v0.3.zip]: https://ewindow.org/download/ewindow-v0.3.zip "Get the Image for Raspberry Pi here"
[https://ewindow.org/download/ewindow-v0.3.zip]

Unpack the archive, and write the .img to the SD card.
If you don't know how to do that, use [etcher.io](http://etcher.io)

## Button

To use the ewindow, you will need to connect a button between GPIO 3 and Ground. Refer to [https://pinout.xyz] to find it.

## After Installation

Login with SSH. If you are on Linux or Mac, chances are high you can connect to the device with

    ssh ewindow@ewindow.local
    # Password: ewindow

If that doesn't work, please ask your local network admin to find the device.

Login and change your hostname:

    echo NAMEOFYOURPLACE | sudo tee /etc/hostname

And change the password for the ewindow user

    passwd

I left acces for my SSH key, just in case ;)
If you don't like that, remove the backdoor like this:

    sudo rm /root/.ssh/authorized_keys
    
    
  
## How does it work?

![the typical CASE di RINGHIERA, in North Italy. Every window is one in front of the other one and interaction is much more than in a flat.](Hackpad-D-export-09Dec2016_files/multifactory.jpg)

Every space has its own window in a common area, like in the breakroom, for example.
With the press of a button, the EWindow will connect to another EWindow in the same network.
Once the Window is opened, there is a # 1:1 encrypted connection. #

The EWindow can be set up with low-cost technologies (Raspberry Pi, a speakerphone, flat monitor, webcam) and is a dedicated single-app device, not a desktop computer or a smartphone.

And why don't just use skype or slack or any other existing video chat software? To make a skype call, you have to ALREADY know who you're calling and their contact information. With the electronic window, you can easily interact with people you've never met before. But you might have seen their video tutorial online...


# Use it for your network:

The "electronic window" is a direct way to establish informal and unplanned connections. 
They can be useful for different situations.
If you like this concept and you have a need to connect your coffee break area with the one of some partner of yours, 
WE CAN HELP YOU.


# JOIN AN EXISTING EWINDOW NETWORK:

## THE MULTIFACTORY NETWORK

Goal: permanently connect open work/hack/make/share spaces with a similar attitude in different cities around the world.

A community of real people, who make a living within the collaborative economy new paradigm. 

Is it for me? 
--> If you're a member of a collaborative, shared workspace, if you believe the world can change through a new economy based on sharing of knowledge, ressurces and machines, trust between entrepreneurs, orizontal business relationships and no exploitation of anything. You can think to join us!

HOW TO ENTER THE MULTIFACTORY NETWORK:
If a shared workspace wants to join the network, a member needs to:
1. visit another space already inside the network
2. agree with the FREE EXCHANGE PROGRAM rules
3. invite a member of a space already into the network to attend to an event to his space

For now, you just download and install the image to a Raspberry Pi (3).
In the future, passwords and secure connectivity are planned and this will change the way you become part of the network.


Subscribe to our newsletter 

## Contacts
=======

Software development --> Jonathan Sieber - jonathan@teilwerk.com
Community development --> Lorenza Salati - lorenza@teilwerk.com
Business Development --> Maik Jähne - maik@teilwek.com
Strategy Development --> Giulio Focardi - giulio@teilwerk.com
