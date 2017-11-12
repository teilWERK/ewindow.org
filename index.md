---
title: THE ELECTRONIC WINDOW
---
## What is it?

The EWindow is a video chat device that runs 24/7 in a shared space.
The goal is a decentralized, secure 24/7 audiovisual communication system --> Like a window in a wall.

![A view into the Fablab Munich](images/EWindow_HEi_VOW.jpg)

# Features

- SIP video softphone implementation based on a baresip/libre sip stack
- Audio codecs: Opus, PCM/8000, Speex
- Video codecs: VP8/VP9 (PC), H.264 (Pending RPi HW Implementation)
- BSD-licensed, lean, and modular C codebase
- Supports Raspberry Pi hardware-accelerated video output (OpenMAX)
- Command line interface


Development  
===========

## How is it implemented?

It's based on a cheap, single-board computer. --> [Bill of Materials](manual/EWindow-BOM.md)

Development of the EWindow is focused on two parts:

1) Enhancing a lightweight SIP Video Phone with Raspberry Pi support

    git clone https://github.com/alfredh/baresip

2) A small python script that handles automatic connection buildup

    git clone -b python https://github.com/strfry/ewindow
    
3) A Qt/QML-based user interface with support for hardware buttons

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

Download  
========

THE RASPBERRY PI IMAGE BELOW IS OUTDATED. Write me a mail to get notified when the new version is released

~~Preview Alpha 0.2 from 20th April 2017 can be downloaded here:~~
http://ewindow.org/ewindow-v0.2-20Apr17.zip

ATTENTION: This version is not secure. The access keys are stored on Github. It could potentially compromise your network!
Regard it as experimental.
Help in making the VPN more secure and functional would be super welcome.
Please contact us if you want to help build a continous integration environment.
See [https://github.com/teilWERK/Image] for instructions on how to build this image on a QEMU-ARM-based Raspbian Lite system.


## Documentation

The relevant information is hidden in a, obfuscated mix of documentation and development notes on our etherpad server.
More of this will be released step-by-step once we get a grip on our pad infrastructure. ;-)


### Why don't you just use WebRTC?

While modern web browsers work on the Raspberry Pi, they don't use the native video processing capabilities of the VideoCore.


Contact
=======

Jonathan Sieber - mail@strfry.org
Lorenza Salati - lorenza@bigmagma.it
