# SIP Example Dumps

## INVITE

```
Session Initiation Protocol (INVITE)
INVITE sip:202@[fde1:c0fe::7]:5061 SIP/2.0
Via: SIP/2.0/UDP [fde1:c0fe::777]:5060;branch=z9hG4bK0dd554b7330266dd;rport
Contact: <sip:202-0x80228a2c0@[fde1:c0fe::777]:5060>
Max-Forwards: 70
To: <sip:202@[fde1:c0fe::7]:5061>
From: <sip:202@[fde1:c0fe::777]>;tag=6f4c8bf55baa8514
Call-ID: 5ffb5c06e5ee51e9
CSeq: 64909 INVITE
User-Agent: baresip v0.5.0 (x86_64/freebsd)
Allow: INVITE,ACK,BYE,CANCEL,OPTIONS,REFER,NOTIFY,SUBSCRIBE,INFO,MESSAGE
Supported: gruu
Content-Type: application/sdp
Content-Length: 971

v=0
o=- 953559690 1743778263 IN IP6 fde1:c0fe::7
s=-
c=IN IP6 fde1:c0fe::7
t=0 0
a=tool:baresip 0.5.0
m=audio 17882 RTP/AVP 0 8 96 97 98 99 100 101 102
b=AS:128
a=rtpmap:0 PCMU/8000
a=rtpmap:8 PCMA/8000
a=rtpmap:96 speex/32000/2
a=fmtp:96 mode="6";vbr=off;cng=on
a=rtpmap:97 speex/16000/2
a=fmtp:97 mode="6";vbr=off;cng=on
a=rtpmap:98 speex/8000/2
a=fmtp:98 mode="3";vbr=off;cng=on
a=rtpmap:99 speex/32000
a=fmtp:99 mode="6";vbr=off;cng=on
a=rtpmap:100 speex/16000
a=fmtp:100 mode="6";vbr=off;cng=on
a=rtpmap:101 speex/8000
a=fmtp:101 mode="3";vbr=off;cng=on
a=rtpmap:102 telephone-event/8000
a=fmtp:102 0-15
a=sendrecv
a=label:1
a=rtcp-rsize
a=ssrc:1979608979 cname:sip:202@[fde1:c0fe::7]
a=rtcp-mux
a=ptime:20
m=video 9010 RTP/AVP 96
b=AS:384
a=rtpmap:96 VP8/90000
a=fmtp:96 max-fs=3600
a=sendrecv
a=label:2
a=rtcp-rsize
a=ssrc:59383982 cname:sip:202@[fde1:c0fe::7]
a=rtcp-mux
a=framerate:5
a=rtcp-fb:* nack pli
a=content:main



## RINGING

``` 
SIP/2.0 180 Ringing
Via: SIP/2.0/UDP [fde1:c0fe::777]:5060;branch=z9hG4bK0dd554b7330266dd;rport=47469;received=fde1:c0fe::7
To: <sip:202@[fde1:c0fe::7]:5061>;tag=d5511e06700e8335
From: <sip:202@[fde1:c0fe::777]>;tag=6f4c8bf55baa8514
Call-ID: 5ffb5c06e5ee51e9
CSeq: 64909 INVITE
Server: baresip v0.5.0 (x86_64/freebsd)
Contact: <sip:202-0x80228a2c0@[fde1:c0fe::7]:5060>
Allow: INVITE,ACK,BYE,CANCEL,OPTIONS,REFER,NOTIFY,SUBSCRIBE,INFO,MESSAGE
Content-Length: 0
```

## BUSY

´´´
SIP/2.0 486 Busy Here
Via: SIP/2.0/UDP [fde1:c0fe::777]:5060;branch=z9hG4bK0dd554b7330266dd;rport=47469;received=fde1:c0fe::7
To: <sip:202@[fde1:c0fe::7]:5061>;tag=d5511e06700e8335
From: <sip:202@[fde1:c0fe::777]>;tag=6f4c8bf55baa8514
Call-ID: 5ffb5c06e5ee51e9
CSeq: 64909 INVITE
Server: baresip v0.5.0 (x86_64/freebsd)
Content-Length: 0
´´´ 

## ANSWER

``` 
SIP/2.0 200 Answering
Via: SIP/2.0/UDP [fde1:c0fe::777]:5060;branch=z9hG4bK0dd554b7330266dd;rport=39448;received=fde1:c0fe::7
To: <sip:202@[fde1:c0fe::7]:5061>;tag=1a9508dcad751620
From: <sip:202@[fde1:c0fe::777]>;tag=6f4c8bf55baa8514
Call-ID: 5ffb5c06e5ee51e9
CSeq: 64909 INVITE
Server: baresip v0.5.0 (x86_64/freebsd)
Contact: <sip:202-0x80228a2c0@[fde1:c0fe::7]:5060>
Allow: INVITE,ACK,BYE,CANCEL,OPTIONS,REFER,NOTIFY,SUBSCRIBE,INFO,MESSAGE
Content-Type: application/sdp
Content-Length: 982

v=0
o=- 3146307374 884905685 IN IP6 fde1:c0fe::7
s=-
c=IN IP6 fde1:c0fe::7
t=0 0
a=tool:baresip 0.5.0
m=audio 30308 RTP/AVP 0 8 96 97 98 99 100 101 102
b=AS:128
a=rtpmap:0 PCMU/8000
a=rtpmap:8 PCMA/8000
a=rtpmap:96 speex/32000/2
a=fmtp:96 mode="6";vbr=off;cng=on
a=rtpmap:97 speex/16000/2
a=fmtp:97 mode="6";vbr=off;cng=on
a=rtpmap:98 speex/8000/2
a=fmtp:98 mode="3";vbr=off;cng=on
a=rtpmap:99 speex/32000
a=fmtp:99 mode="6";vbr=off;cng=on
a=rtpmap:100 speex/16000
a=fmtp:100 mode="6";vbr=off;cng=on
a=rtpmap:101 speex/8000
a=fmtp:101 mode="3";vbr=off;cng=on
a=rtpmap:102 telephone-event/8000
a=fmtp:102 0-15
a=sendrecv
a=label:1
a=rtcp-rsize
a=ssrc:143928373 cname:sip:202@[fde1:c0fe::7]:5061
a=rtcp-mux
a=ptime:20
m=video 40792 RTP/AVP 96
b=AS:384
a=rtpmap:96 VP8/90000
a=fmtp:96 max-fs=3600
a=sendrecv
a=label:2
a=rtcp-rsize
a=ssrc:991584193 cname:sip:202@[fde1:c0fe::7]:5061
a=rtcp-mux
a=framerate:5
a=rtcp-fb:* nack pli
a=content:main
```
