---
title: THE ELECTRONIC WINDOW
layout: default
---
## What is it?

The EWindow is a video chat device that runs 24/7 in a shared space.
The goal is a decentralized, secure 24/7 audiovisual communication system --> Like a window in a wall.

![A view into the Fablab Munich](images/EWindow_HEi_VOW.jpg)

## What do i need to build it?

- A Raspberry Pi (2 or 3)
- 2 GiB  SD Card
- Monitor (with Cable)
- Speakers
- USB Webcam with microphones
- A button and a bit of jumpwire

If you want to improve the audio/video quality:
- Raspberry PiCam (wide-angle version recommended)
- USB Speakerphone (will replace speakers and microphone)

Download  
========

[http://ewindow.org/ewindow-v0.3.zip]: http://ewindow.org/ewindow-v0.3.zip "Get the Image for Raspberry Pi here"
[http://ewindow.org/ewindow-v0.3.zip]

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

Development  
===========

## How is it implemented?

Development of the EWindow is focused on three parts:

1) Enhancing a lightweight SIP Video Phone with Raspberry Pi support

    git clone https://github.com/alfredh/baresip
    
2) A Qt/QML-based user interface

    git clone https://github.com/strfry/ewindowui

3) Configuration details for a specific platform
    
    git clone https://github.com/strfry/ewindowui

## How does it work?

![the typical CASE di RINGHIERA, in North Italy. Every window is one in front of the other one and interaction is much more than in a flat.](Hackpad-D-export-09Dec2016_files/multifactory.jpg)

Every space has its own window in a common area, like in the breakroom, for example.
With the press of a button, the EWindow will connect to another EWindow in the same network.
Once the Window is opened, there is a # 1:1 encrypted connection. #

The EWindow can be set up with low-cost technologies (Raspberry Pi, a speakerphone, flat monitor, webcam) and is a dedicated single-app device, not a desktop computer or a smartphone.

And why don't just use skype or slack or any other existing video chat software? To make a skype call, you have to ALREADY know who you're calling and their contact information. With the electronic window, you can easily interact with people you've never met before. But you might have seen their video tutorial online...


# Use it for your network: CROWDFUNDING CAMPAIGN

The "electronic window" is a direct way to establish informal and unplanned connections. 
They can be useful for different situations.
If you like this concept and you have a need to connect your coffee break area with the one of some partner of yours, 
WE CAN HELP YOU.

In order to finance the software development and future updates we are planning to launch a CROWDFUNDING CAMPAIGN.
Our supporters will receive 2 or more EWindows to use in their own network.

Subscribe to our newsletter to be notified of WHEN THE CROWDFUNDING CAMPAIGN WILL BE ONLINE.



# How to become part of our network: THE MULTIFACTORY NETWORK?

Our goal is to permanently connect open work/hack/make/share spaces with a similar attitude in different cities around the world.

We are building a multi-level network of such spaces: a community of real people, who make a living in the collaborative economy --> the [Multifactory Network.](MultiFactory.md)

If you're a member of a collaborative, shared workspace and you'd like to join the multifactory network, 
we'd like to meet you!

If a shared workspace wants to join the network, someone representing it needs to:
1. visit another space already in the network
2. agree with the FREE EXCHANGE PROGRAM rules
3. be visited by a member of a space already in the network

For now, you just download and install the image to a Raspberry Pi (3).
In the future, passwords and secure connectivity are planned and this will change the way you become part of the network.


## Code
If you are a developer, you are VERY welcome here:
https://github.com/strfry/ewindow


## Contact
=======

Jonathan Sieber - mail@strfry.org
Lorenza Salati - lorenza@bigmagma.it
