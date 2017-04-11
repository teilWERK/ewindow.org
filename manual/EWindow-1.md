EWindow Part 1 - Network Architecture
=====================================

PeerVPN Cleanup
===============

Next Steps:
- Change VPN Key, do not have it in Github
- Move this documentation to own pad infrastructure
- "How to set up your EWindow Network"


## IPv6 Discovery

Server:
    socat UDP6-RECVFROM:6666,fork EXEC:hostname

client:
    socat STDOUT "UDP6-DATAGRAM:[ff02::1%tap0]:6666"

## Multicast DNS

Service Discovery is done through multicast DNS, like described in 
https://tools.ietf.org/html/draft-lee-sip-dns-sd-uri-03#section-3
#TODO read RFC-draft-lee-sip-dns-sd-uri-3

FreeBSD Experience:
  pkg install mdnsd -> installs only mhttp and mquery tools
  pkg install mDNSResponder -> the big ugly Apple thing
  pkg install avahi -> Don't even think of it

-----------------------------
OpenBSD mDNS implementation: http://www.haesbaert.org/openmdns/

Suddendly appeared in pkg! // Needs IPv4 Address
pkg install openmsnd

    mdnsctl browse

-----------------------------------------------------------------
mDNSResponder:
* User mDNSResponderPosix on FreeBSD for more options:
    mDNSResponderPosix -f mdns.conf -

https://forums.freebsd.org/threads/54465/ -> If you use mDNSResponder you need dns/mDNSResponder_nss for name resolution.


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
