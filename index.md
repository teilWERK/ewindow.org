---
title: THE ELECTRONIC WINDOW
---


![the typical CASE di RINGHIERA, in North Italy. Every window is one in front of the other one and interaction is much more than in a flat.](Hackpad-D-export-09Dec2016_files/multifactory.jpg)

## What is it?


The EWindow is videochat device that runs 24/7 in a public space.
The goal is a decentralized, secure 24/7 audiovisual communication system --> Like a window through a wall

The "electronic window" is a direct way to establish connections between rooms and spaces. 
Just imagine a window trough the wall. You just go to the coffee-break area, or to the café, and you can see other people from another space, talk to them, exchange ideas, give and get suggestions on what you’re doing. 

It is intended to link between public/open work/hack/make/share Spaces in different cities. We are building a multi-level network of such spaces, a community of real people, that are making a living in the collaborative economy --> the [Multifactory Network.](MultiFactory.html)


## How does it work?

With a press of a button, the EWindow will connect to another in the same network.
Once the Window is opened, there is a 1:1 encrypted connection.

Each e-window is open all day long from one space to another one. If there are two persons close to the two windows, they can talk and interact.

The E-windows can be set up with low-cost technologies (Raspberry Pi, a Speakerphone, flat monitor, webcam) and is a dedicated single-app device, not a desktop computer, not a smartphone.

If people want to meet in front of the window, they act exactly as if they would plan to meet someone at the bar:

A – meet people by chance: you go, take a coffee, and start talking to someone you don’t know, or someone you know and is taking a coffee at the same time

B – you send a message to someone and just say “see you in 5 minutes at the e-window”

People can meet and start business relationships as well. In what differs compared to a skype call? To make a skype call, you have to ALREADY know who you are calling, you need their contact, and so on. With the electronic window, you can easily interact with people you never met before (but maybe who you think could be interesting, because you’ve seen their video-tutorial-presentation).



# How to become part of the network?

At the current public experimental stage, you can download the image and install it to a Raspberry Pi (3)



Download  
========

Preview Alpha 0.2 from 20th April 2017 can be downloaded here:
http://ewindow.org/ewindow-v0.2-20Apr17.zip

ATTENTION: This version is not secure yet. The access keys are stored on Github. It might potentially compromise your network!
Regard it as experimental.
Help in making the VPN more secure and functional would be super-welcome.
Please contact us if you want to help building a Continous Integration environment. 
See [teilWERK/Image] for instructions, how this image was built from Raspbian Lite on a QEMU-ARM System.

# Features

- SIP Video Soft-Phone implementation based baresip/libre sip stack
- Audio codecs: Opus, PCM/8000, Speex
- Video codec VP8/VP9 (PC), H.264 (Pending RPi HW Implementation)
- BSD-licensed codebase, lean, modular C codebase
- Supports Raspberry Pi hardware-accelerated video output (OpenMAX)
- Command Line Interface


Development  
===========

## How is it implemented?

It's based on a cheap Single Board Computer. --> [Bill of Materials](manual/EWindow-BOM)

The development of ewindow is focussing on two parts:

1) Build a lightweight SIP Video Phone with Raspberry Pi support

    git clone https://github.com/eleKtronicwindow/baresip
    (upstream: https://github.com/alfredh/baresip )

2) Build Integration and dialog-based User Interface scripts

    git clone https://github.com/strfry/ewindow

## Munich Multifactory Cluster

There also is a different development line based on WebRTC, by to Munich Multifactory Cluster:

[https://github.com/munichmakerlab/ewindow_webrtc]

It is told to run on Raspberry Pi 3 with Chrome.

In the future, these lines might be made interoperable again.

## Documentation

The documentation is mostly unwritten, our outdated.
These Links point to pad dumps, mostly old development notes that need
to be converted into a useful manual, step-by-step

- [Part 1 - Network Architecture](manual/EWindow-1)
- [Notes of using baresip with WebRTC Client](devlog/EWindow-7-WebRTC)

### Why don't you just use WebRTC?

While modern WebBrowser work on the Raspberry Pi, the do not use the native video processing capabilities of the VideoCore.



Contact
=======

Jonathan Sieber - mail@strfry.org
