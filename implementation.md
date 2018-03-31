---
title: THE ELECTRONIC WINDOW
layout: default
---

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
