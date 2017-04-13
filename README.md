ewindow
=======

The ewindow is a free software project for building a solution for decentralized audiovisual communication appliance device
 
## The Goal
 
## Our Values
We    strongly believe that a free software communication platform is really  needed to protect freedom of speech and e-democracy. Commercial software which you can use for free is not a gift. It’s a Trojan horse.   Systems based on proprietary codes live users   unprotected and their   centralized architectures expose people and   their data.
So,    for us is mandatory to have a free and open system and we understood     that it can only be developed by a huge and diversified group of     developers. The goal is not just to have a videochat system for     makerspaces and FabLabs, but to increase the security and to protect    the  freedom of all of us.

Design goals
------------

* Native Application for single-board-computers (Raspberry Pi et al)
* Works with commodity hardware (USB Webcams)
* Decentralized P2P Signalling


Technical Requirements
======================
 

    - A Raspberry Pi 2/3
    - A USB Speakerphone with built-in echo cancellation 
    - hernet cable with some internet (>1 MBit Upload recommended). do yourself a favor and skip wifi :)     

# EWindow Manual

[Link to Part 1 - Network](manual/EWindow-1.md)


## baresip

### Features

-    SIP Video Soft-Phone implementation based baresip/libre sip stack
-    Audio codecs: Opus, PCM/8000, Speex
-    Video codec VP8/VP9 (PC), H.264 (Pending RPi HW Implementation)
-    BSD-licensed codebase, lean, modular C codebase

 

Download  
========
Latest and previous releases of ewindow SD Card Image for RPi3 can be downloaded here, in the future
 
If you are a shared workspace and you are part of the  MULTIFACTORY NETWORK
download it here and contact us here fore receiving the password to access the network.
 
 
Building and installation  
==================
 

Building baresip:
 
$ git clone https://github.com/creytiv/re
$ git clone https://github.com/creytiv/rem
$ git clone https://github.com/eleKtronicwindow/baresip
 
$ cd re && make && sudo make install && cd ..
$ cd rem && make && sudo make install && cd ../baresip
 
$ make && make install
 
 
Configuration
=============
 
Start baresip once to create config file and  # Test Audio Feedback.
$ ./baresip -e /auloop
 
Edit ~/.baresip/config to 
 
$ echo "<sip:DISPLAYNAME:xxx@example.org;regint=0;" >> ~/.baresip/accounts 
 
Explanation: Add a sip user with any name, password, and domain 
 
 
To build ewindow core and the modules we forked from baresip and we are usi
 
 
 
 
 
 
Documentation
-------------
 
 
 
Doxygen API documentation can be found here. 
The Wiki can be found here??
 
 
Next code rafting
==============
