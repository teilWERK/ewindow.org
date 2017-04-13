# ewindow

ewindow is a free software project for for internet audiovisual communication, that can run on a cheap single-board-computer, like a Raspberry Pi

## The Goal

We strongly believe that a free software communication platform is
really needed to protect freedom of speech and e-democracy.
Commercial software which you can use for free is not a gift. It’s a Trojan horse.
Systems based on proprietary code leave users unprotected and their centralized architectures expose people and  their data.
So, for us is mandatory to have a free and open system and we understood
that it can only be developed by a huge and diversified group of developers.
The goal is not just to have a videochat system for Makerspaces and FabLabs, but to increase the security
and to protect the freedom of all of us.

Technical Requirements
======================

- A Raspberry Pi 2/3
- A USB Speakerphone with built-in echo cancellation, or, a I2S Soundcard with Mic Input
- Ethernet cable with some internet (>1 MBit Upload recommended). do yourself a favor and skip wifi :)


Community
=========

[Learn here how to become part of the multifactory network...](MultifactoryModel.md)


Features
--------

- SIP Video Soft-Phone implementation based baresip/libre sip stack
- Audio codecs: Opus, PCM/8000, Speex
- Video codec VP8/VP9 (PC), H.264 (Pending RPi HW Implementation)
- BSD-licensed codebase, lean, modular C codebase


Development  
===========

The development of ewindow is focussing on two parts:

1) Baresip extensions for Raspberry Pi

    git clone https://github.com/eleKtronicwindow/baresip

2) Integration and User Interface scripting

    git clone https://github.com/strfry/baresip


Download  
========
Latest and previous releases of ewindow can be downloaded here. 

If you are a shared workspace and you are part of the  MULTIFACTORY NETWORK
download it here and contact us here fore receiving the password to access the network.


Building and installation  
==================



Building baresip:

$ git clone https://github.com/creytiv/re
$ git clone https://github.com/creytiv/rem
$ git clone https://github.com/alfredh/baresip

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


To build ewindow core and the modules we forked from baresip and we are using ( GNU/BSD Make)

tutorials
======

To build ewindow with default options: 
$ 
$
$ 

Default templates for configuration files will be created here: $HOME/.baresip  You can now edit the files "config" and "accounts" to customize your installation.  




Design goals
------------
 
 
 
 
Documentation
-------------



Doxygen API documentation can be found here. 
The Wiki can be found here??


Next code rafting
==============




# Stuff

[Unfinished Readme](README.md)
[Old D Hackpad](Hackpad-D-export-09Dec2016.html)


