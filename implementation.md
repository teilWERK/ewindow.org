---
title: THE ELECTRONIC WINDOW
layout: default
---

Development of the EWindow Software is focused on several parts:

1) SIP portocol 
We use the standard protocol for IP (video) telephony, SIP optimised for light supports, as Raspberry Pi.
Our implementation is based on the minimalistic SIP client Cash dip. This has proven to be suitable, with low
hardware resources to enable an acceptable connection quality, because it has a modular design and is designed to support special
video hardware resources.

    git clone https://github.com/alfredh/baresip
    
2) A Qt/QML-based user interface

    git clone https://github.com/teilWERK/ewindow-core

3) Some configuration scripts for specific platforms
    
    git clone https://github.com/teilWERK/ewindow-scripts

4) A set of build recipes for Alpine Linux
The complete system is based on the Linux distribution Alpine Linux, from
that automatically creates pre-configured live images.

    git clone https://github.com/teilWERK/ewindow-aports

5) ECho Cancelation
The echo suppression for undisturbed hands-free communication is based on
currently on pulse audio or code from the Google WebRTC project.

6) Script to put everything together in a bootable live image:

    git clone https://github.com/teilWERK/ewindow-builder

