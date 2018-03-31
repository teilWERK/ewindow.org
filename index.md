---
title: THE ELECTRONIC WINDOW
layout: default
---

# Ewindow is a TECHNOLOGICAL DEVICE 
## for a NEW REVOLUTIONARY __Social Network__. 

### 1. __OPEN SOURCE__ 
// the code is here [ewindow Code](https://github.com/teilWERK) enjoy it //
### 1. __DECENTRALISED__ 
// no central control owned by some corporation using your data for other purposes //
### 1. __FREE__ 
// Everything for making it by your own is shared //

[LEARN MORE ABOUT EWINDOW](pages/introduction.html)

# Why we started this project based on free software?
-->     WE BELIEVE it is time to do a STEP BACK and RETHINK on how to use technologies for comunication purposes:

### The E-window is based on a free Open Source software and accessible to everybody as we strongly believe that a free software communication platform is necessary to protect freedom of speech and e-democracy. 
#### And it’s easy and cheap to build it by yourself of an estimated cost around 300 euros. 
#### It can be replicated anywhere in the world with no hardware problems. 
#### We would like to spread it in the South of the World to have direct and non-mediated communication with startups and local entrepreneurs, build partnerships between peers, build a decentralised communication system, non depending on top down policies. 

It is a tunnel for comunication you find is physical spaces.
## it is like a window in a wall:
![the typical CASE di RINGHIERA, in North Italy. Every window is one in front of the other one and interaction is much more than in a flat.](Hackpad-D-export-09Dec2016_files/multifactory.jpg)

##### We think this tool can break down physical, political and mnemonic walls.


# THE STORY

After some years of trials and experiments on instant communication we decided it was time to do something bigger and we involved the Verbund Offener Werkstaetten (D) which decided to join us in the long process of making the community and spreading awarness around this theme.

Then, to maintain the software development we created a small company TEILWERK.

![rollup](images/NEW POSTER ANOTHER IDEA-01.jpg)


## How does it work?

Ewindow is a dedicated single-app device, not a desktop computer or a smartphone.

Many different EWindows, all togheter, can make their own social network. Imagine you want to connect 3 different spaces. 
Every space has its own window in a common area, like in the coffebreak, a corridor, the kitchen.
With the press of a button, the EWindow will connect to another EWindow in the same network.
Once the Window is opened, there is a # 1:1 encrypted connection. 

### And why don't just use skype or slack or any other existing video chat software? 
To make a skype call, you have to ALREADY know who you're calling and their contact information. With the electronic window, you can easily interact with people you've never met before. But you might have seen their video tutorial online...

Of course for this end, we had to develop a user-friendly interface that requires no mediators such as a keyboard or a mouse. 

To build the e-window , you need a monitor , a small computer such raspberry pie 2, a webcam and a pair of speakers. All the E–window need to operate after is a Stable video and audio connection  and Small band usage (short bandwidth). The appearance is customizable  and could easily be altered and adjusted .

# BUY

EWindow solves two current problems: first it let team members working in different buildings, cities or countries to share daily life and common values which is crucial team building. Second it lowers the email communication that in the last years increased so much that it loses power on communication.

[TO LEARN MORE](pages/imagedownload.html)


# DESIGN 

THe development of the design..

*FRAME  
There is no one frame, every space build his own.

# Have a look to some existing frames:

![R84 ewindow](images/photo5827694945186721529.jpg)
done by Fabrizio

![Munich Fablab](images/photo5237893242777872680.jpg)
done by Felix

The HEI MUNICH 
![A view into the Fablab Munich](images/EWindow_HEi_VOW.jpg)
done by HEI Team


# HARDWARE DEVELOPMENT

While starting this project one of the requirement was to find low-cost technologies. 
After many trials (and errors) we went up with a simple and accessible configuration.

*ELECTRONICS LIST
- A Raspberry Pi //3 (2 is ok too)//
- 2 GiB  SD Card
- Monitor (with Cable)
- Speakers //CONNECTED VIA JACK, AND NO VIA USB//
- USB Webcam with microphones 
- A button and a bit of jumpwire

[TO LEARN MORE ABOUT ELECTRONIC PARTS](pages/hardware.html)


pages/hardware.html
TO LEARN MORE ABOUT THE ELECTRONIC PARTS
---
If you would like to improve the audio/video quality:
- Raspberry PiCam //wide-angle version recommended//
- USB Speakerphone //will replace speakers and microphone//

## Button
To use the ewindow, you will need to connect a button between GPIO 3 and Ground. Refer to [https://pinout.xyz] to find it.

--


# SOFTWARE 

The EWindows are based on a software developed for running on affordable technologies (such as Raspberry Pi *raspberryPi is a open-source hardware computer. is like a small computer that you can use for prototyping.*, a flat monitor, a webcam, Linux). 
The OS is Raspbian which is a free operating system, optimized for the Raspberry Pi hardware, that coincides with the open standards as in public, transparent and accessible to everyone. It provides an encrypted and secure connection.

It is also optimized to be efficiently used on most hardware from single board computers such as the raspberry pi to high end pc’s.  And it facilitates further experimentation with new hardware of software features.


## DOWNLOAD 
### THE IMAGE FOR THE RASPBY
[DOWNLOAD IT HERE](pages/imagedownload.html)

-
imagedownload.html

## To Download the Image  

1.
[https://ewindow.org/download/ewindow-v0.3.zip]: https://ewindow.org/download/ewindow-v0.3.zip "Get the Image for Raspberry Pi here"
[https://ewindow.org/download/ewindow-v0.3.zip]

1.
Unpack the archive, and write the .img to the SD card.
If you don't know how to do that, use [etcher.io](http://etcher.io)


## GETTING STARTED

[GETTING STARTED](pages/gettingstarted.html)

-
gettingstarted.html

## After the [installation of the IMAGE](pages/imagedownload.html)

you can join the MULTIFACTORY EXISTING NETWORK:

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
-


## IMPLEMENTATION

[HOW IT IS IMPLEMENTED](pages/softwareimplementation.html)

-
softwareimplementation.html
## How is it implemented?

Development of the EWindow is focused on three parts:

1) Enhancing a lightweight SIP Video Phone with Raspberry Pi support

    git clone https://github.com/alfredh/baresip
    
2) A Qt/QML-based user interface

    git clone https://github.com/teilWERK/ewindow-core

3) Some configuration scripts for specific platforms
    
    git clone https://github.com/teilWERK/ewindow-scripts

4) A set of build recipes for Alpine Linux

    git clone https://github.com/teilWERK/ewindow-aports

5) Script to put everything together in a bootable live image:

    git clone https://github.com/teilWERK/ewindow-builder
-    
    


    
    
# EWINDOW NETWORKS  
The "electronic window" is a direct way to establish informal and unplanned connections. 
They can be useful for different situations. 

[BUILD YOUR OWN EWINDOW NETWORK](pages/setupyourownnetwork.html)

## JOIN THE EXISTING EWINDOW NETWORK

### THE MULTIFACTORY NETWORK

The multifactory is  a network of shared workspace across Europe and the EWindow is a tool that ensures the constant circulation of ideas in sharing knowledge and in exchanging skills and professional services between the spaces involved.
A community of real people, who make a living within the collaborative economy new paradigm. 

[LEARN MORE](MultiFactory.html)


# FUTURE DEVELOPMENT

The EWindow is a technological community tool and not a personal communications tool.
The EWindow offers a third way.

[LEARN MORE](future.html)


future.html
-
# How it can be used in the Future?

Today's communication technologies are challeging our society and how people interact and exchange between each others. A lot of time is spent in front of a smartphone or computer monitor and squares are progresively abandoned. 
People is always and immediately reachable everywhere and at any time. 
We think to refuse technology, and act as it wasn't existing, is not the solution.
We believe technology can be an ally and not an enemy.
Ewindows are physical devices but are not personal devices, they are community devices. 
Ewindows can combine the need of physical community spaces with the technological progress on communication.

Social Network platforms are managed by corporate companies which sell data users give to them for free. This unbalanced relationship between users and platform providers leads to a dangerous manipulation of information and abuse of power which is attaking democracy.
For those who are aware of this limitation of freedom imposed by facebook, what's up, skype and all others, there are two solutions: or to join only free and decentralised social networks, which are lighs spots in the darkness: like diaspora or jabber or to stay away from technologies.

The EWindow is a community tool and not a personal tool,
The EWindow offers a third way.

Througn technology we can connect each other from everywhere in the world, we can share skills and experiences. An we do not want to loose this opportunity.

But how not to loose freedom?

It is the solution to real problem faced by many different communities of interest and it is an answer to an urgent need. 
EWindow can become a new practical and common way of communicating by moving ideas, in local community spots.
You have to go out from your home, join a real local community and then, from then, you ffind an Ewindow spot wich can connect you with the rest of the world.
This would result in a faster, better, cheaper way to share ideas, projects and works.

The EWindow can be adapted to local or personal needs in emerging communities in Africa or other developing communities and could be used to form orizontal and unconventional partnerships between enterprises, startups, actors of international cooperation ,NGOs, Universities and Research Centers and Countries from Global South.

--

# NEWSLETTER

Subscribe to our newsletter 

# CONTACTS

[Get in touch with us](contacts.html)

-
contacts.html
Community development --> Lorenza Salati - lorenza@teilwerk.com

Business Development --> Maik Jähne - maik@teilwek.com

Strategy Development --> Giulio Focardi - giulio@teilwerk.com

Software development --> Jonathan Sieber - jonathan@teilwerk.com
-
