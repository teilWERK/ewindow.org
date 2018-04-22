---
title: THE ELECTRONIC WINDOW
layout: default
---

## After the [installation of the IMAGE](imagedownload.md)

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

Use the button to bring up the contact list (GPIO3 or USB Keyboard).
Press short to skip, press long to select an open window to connect to.

If you run into any problems, contact me via mail to ewindow@strfry.org
