---
title: EWindow Part 1 - Network Architecture
---

The EWindow is designed to be part of a VPN (Virtual Private Network),
representing the local cluster of trusted partner-spaces.

# PeerVPN

Currently we use [PeerVPN](https://github.com/peervpn/peervpn)
It is a lightweight Layer-2 (TAP Device) Virtual Network.
Encryption is based on a PSK (pre-shared key)

# Future Work

[cjdns](https://github.com/cjdelisle/cjdns)

# Basic Ideas



## Echt dezentrales Netwerk / Truly decentral networking

[Link Collection @C3D2](https://wiki.c3d2.de/Echt_Dezentrales_Netz/en)

# De-centralized Network Architecture

## Links
cjdns paper: https://github.com/cjdelisle/cjdns/blob/master/doc/Whitepaper.md

https://projectedn.wordpress.com/cutting-edge-technologies/


[HyperBorea CJDNS Network](https://hyperboria.net/)

-----------------------------------------------------------------

------------------------------------------------------------------

https://lists.freebsd.org/pipermail/freebsd-ports/2004-September/015760.html

??? setsockopt - SO_RECV_ANYIF: Protocol not available
sockstat -64 -p 5353 -> killall mdnsd

### dns-sd

basic concepts: registration domain // browsing domain


## PeerVPN

All EWindows are in a common, trusted layer-2 VPN.
The software used for this is PeerVPN ( https://peervpn.net )

## IPv6 Address Scheme

For easy discovery/addressing, the PeerVPN startup script sets a IPv6 address on tap0 derived from a static prefix, and the mac address of the ethernet. Which on the Raspberry Pi, is derived from the Hardware ID.

Static Prefix: fde1:c0fe::/64

Example:
    $ ifconfig eth0
    [...]
    ether f0:de:f1:b8:38:ec
    [...]
    
    tap0 Address = fde1:c0fe::f0de:f1b8:38ec

This address is registered by the network administrator under HOSTNAME.ewindow.org , and thus used for reaching other windows


## Discovery

Unfortunately, tap0's own MAC address is determined randomly by the OS. That means we can find the other clients on the network through IPv6 broadcast pings, but we can not identify them:

    $ ping6 ff02::1%tap0
    PING6(56=40+8+8 bytes) fe80::2bd:43ff:fe32:7300%tap0 --> ff02::1%tap0
    16 bytes from fe80::2bd:43ff:fe32:7300%tap0, icmp_seq=0 hlim=64 time=0.086 ms
    16 bytes from fe80::2bd:15ff:fe66:b600%tap0, icmp_seq=0 hlim=64 time=19.302 ms(DUP!)

The fe80:: address is derived from the MAC address of tap0.
To make it predictable, we set the MAC address to a slightly modified version of the ethernet adapters address:

em0 ether: f0:de:f1:b8:38:ec
