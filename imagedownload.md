---
title: THE ELECTRONIC WINDOW
layout: default
---

## Operations to install the Operanting System

### FOR PRO:
1. Download the image
Here you get the Image for Raspberry Pi http://imagedev.toxblinkenwall.org/
2. Install it to the SD card
Unpack the archive, and write the .img to the SD card.



### FOR BEGINNERS:
### Setup a new System from scratch
1.	Download ETCHER [https://www.balena.io/etcher/]
2.	Install ETCHER on your PC
3.	download the Raspi Image from http://imagedev.toxblinkenwall.org/
4.	save the image on your PC
5.	insert an SD card (minimum 4 Gb) in your PC (or use an adapter)
6.	no need to format the SD card
7.	start ETCHER
8.	FLASH the SD card with the downloaded image. To do this:
a.	In ETCHER select the desired image (image-Raspbian-lite.zip)
b.	In ETCHER select the drive where the SD card is (E:, F:, etc)
c.	Click on “Flash” and wait several minutes
9.	Unbox the Raspberry. DO NOT connect to power!
10.	Put the SD card in the slot (SD contacts towards the Raspberry)
11.	Connect the RaspyCAM to it’s connector
(the central one, find out the right direction)
12.	Connect the USB audio device
13.	Connect the HDMI Monitor
14.	Connect the LAN Cable
15.	NOW Connect the Power Supply
16.	You’ll see text scrolling. THIS IS GOOD.
17.	You’ll have a BLACK SCREEN with four lines of text highlighted in white.
reading “ToxBlinkenwall v0.99.xy”
18.	Now take an USB stick
19.	Format the USB stick (FAT 32)
20.	Insert the USB stick into a USB slot ON THE RASPBERRY
21.	Wait 10 seconds
22.	Now only this USB stick is paired with this eWindow/ToxBlinkenwall
23.	DO NOT lose the data on this USB Stick, it is important. you can backup the files and directories from the Stick to your PC.


### Add a new “Friend” to call
1.	insert the USB stick into your PC
2.	open the folder “backup”
3.	Choose one of the files named book_entry_#.txt
4.	The number of this file is the number you’ll use to dial that window (entry_1, entry_2, etc.)
5.	Copy this file from backup directory to the root directory
6.	Open the file
7.	Copy the code [ToxID] of the window you want to connect
8.	Save the file
9.	Insert the stick in the Raspberry
10.	Wait 10 seconds
11.	The new window is now added
12.	take out the USB stick, and put it in your PC
13.	Open the folder “backup”
14.	Open the file named toxid.txt (with any program to read .txt)
15.	Copy the code
16.	Send to the person you want to connect.
!!!THIS CODE WILL WORK JUST ONE TIME AND IS VALID JUST FOR 1 HOUR!!!
17.	To get a new code (to connect more “Friends”) put the USB stick into the Raspberry and repeat

### Recover if your eWindow ToxBlinkenwall has some critical issue
1.	disconnect the Raspberry from the Power Supply
2.	insert a NEW working SD card (minimum 4 Gb) in your PC
3.	no need to format the SD card
4.	start ETCHER
5.	FLASH the SD card with the downloaded image
6.	Put the SD card into the Raspberry
7.	NOW Connect the Power Supply
8.	You’ll see text scrolling. THIS IS GOOD.
9.	You’ll have a BLACK SCREEN with four lines of text highlighted in white.
reading “ToxBlinkenwall v0.99.xy”
10.	insert the USB stick into your PC
11.	now delete the file usb_auth_hash.txt
12.	copy all book_entry* files from the backup directory to the root directory of the USB stick
13.	copy the savedata.tox file from the backup directory to the root directory of the USB stick
14.	now put the USB stick into the Raspberry
15.	wait a few Minutes, your old backup data will be restored to the new Image and all your “Friends” will also be connected again
16.	this this take some time, and the Program will restart
17.	You’ll have a BLACK SCREEN with four lines of text highlighted in white. reading “ToxBlinkenwall v0.99.xy”, and your Phonebook and “Friends” should also be restored (and displayed correctly on the screen)
18.	now take out the USB stick
19.	put the USB stick into your PC
20.	delete the savedata.tox and all the book_entry* files from the root directory of the USB stick
21.	and put it back into the Raspberry
22.	now wait again 10 seconds
23.	now your system should be restored and you also have a new backup on your USB stick


In 2017, the ToxBlinkenwall project was created BY Zoff from Vienna, we recently met him and joined our forces. The ToxBlinkenwall operating system now provides the technological base to implement the eWindow too. 

The current software repositories we are trying to give our help to improve are: 
https://github.com/Zoxcore/ToxBlinkenwall
https://github.com/Zoxcore/ToxBlinkenwall_raspi_lite_image

