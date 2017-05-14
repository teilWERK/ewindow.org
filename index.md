---
title: THE ELECTRONIC WINDOW
---
## What is it?

The EWindow is a video chat device that runs 24/7 in a shared workspace space.
The goal is a decentralized, secure 24/7 audiovisual communication system --> Like a window in a wall

# Features

- SIP Video Soft-Phone implementation based baresip/libre sip stack
- Audio codecs: Opus, PCM/8000, Speex
- Video codec VP8/VP9 (PC), H.264 (Pending RPi HW Implementation)
- BSD-licensed codebase, lean, modular C codebase
- Supports Raspberry Pi hardware-accelerated video output (OpenMAX)
- Command Line Interface

![the typical CASE di RINGHIERA, in North Italy. Every window is one in front of the other one and interaction is much more than in a flat.](Hackpad-D-export-09Dec2016_files/multifactory.jpg)

## How does it work?

With a press of a button, the EWindow will connect to another one in the same network.
Once the Window is opened, there is a 1:1 encrypted connection.

The E-windows can be set up with low-cost technologies (Raspberry Pi, a Speakerphone, flat monitor, webcam) and is a dedicated single-app device, not a desktop computer, not a smartphone.

And why don't just use skype? To make a skype call, you have to ALREADY know who you are calling, you need their contact. With the electronic window, you can easily interact with people you never met before. But you might have seen their video tutorial online...


# Use it for your network

The "electronic window" is a direct way to establish connections between rooms and spaces. 
Just imagine a window in the wall.
If you need to have a long lasting video communication with someone for any reason, do it.
You can use the ewindow in a closed network, as you like. 


# How to become part of the multifactory network?

Our goal is to permanently connect open work/hack/make/share spaces with similar attitude in different cities around the world.

We are building a multi-level network of such spaces, a community of real people, who make a living in the collaborative economy --> the [Multifactory Network.](MultiFactory.md)

If you are member of a collaborative shared workspace and you would like to join the multifactory network. 
We are open to meet you!

If a shared workspace want to join the network some members on behalf of the space has to:
1. visit another space already into the network
2. agree with the FREE EXCHANGE PROGRAMM rules
3. being visited by one member of one space already into the network

Right now you just download and install the image to a Raspberry Pi (3).
In the future passwords and secure connectivity are planned and this will change the way you become part of the network.

Download  
========

Preview Alpha 0.2 from 20th April 2017 can be downloaded here:
http://ewindow.org/ewindow-v0.2-20Apr17.zip

ATTENTION: This version is not secure. The access keys are stored on Github. It might potentially compromise your network!
Regard it as experimental.
Help in making the VPN more secure and functional would be super-welcome.
Please contact us if you want to help building a Continous Integration environment. 
See [https://github.com/teilWERK/Image] for instructions, how this image was built from Raspbian Lite on a QEMU-ARM System.


Development  
===========

## How is it implemented?

It's based on a cheap Single Board Computer. --> [Bill of Materials](manual/EWindow-BOM.md)

The development of ewindow is focussed on two parts:

1) Build a lightweight SIP Video Phone with Raspberry Pi support

    git clone https://github.com/eleKtronicwindow/baresip
    (upstream: https://github.com/alfredh/baresip )

2) Build Integration and dialog-based User Interface scripts

    git clone https://github.com/strfry/ewindow

## Munich Multifactory Cluster

A different line of development is happening in the MunichMakerLab:

[https://github.com/munichmakerlab/ewindow_webrtc]

It is told to run on Raspberry Pi 3 with Chrome.

In the future, these lines might be made interoperable again.

## Documentation

The relevant information is hidden in a obfuscated mix of documentation and development notes, on our etherpad server.
More of this will be released step-by-step, once we get a grip of our pad infrastructe ;-)

- [Part 1 - Network Architecture](manual/EWindow-1.md)
- [Notes of using baresip with WebRTC Client](devlog/EWindow-7-WebRTC.md)

### Why don't you just use WebRTC?

While modern WebBrowser work on the Raspberry Pi, the do not use the native video processing capabilities of the VideoCore.



Contact
=======

Jonathan Sieber - mail@strfry.org
