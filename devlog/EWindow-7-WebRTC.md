

Thanks for the hint on dtls_srtp. I once found this the hard way by debugging, but just couldn't remember it this time. Maybe there could be a better error message than "no common audio codecs found"?
After 2 days of fiddling, i was able to make a local WebRTC connection from Firefox to baresip. :D

I'm very keen on getting this to work, but i have 2 questions regarding the SIP protocol:

1) What is the minimum viable SIP exchange that baresip needs to happily make a connection?

I currently send an INVITE from the browser to baresip, get back 180 Ringing (ignoring that for now), then get receive the 200 Answering response.

That seems to be enough for baresip to start the session, but of course it expects an ACK, keeps re-sending the Answer, and times out after a while. But is this the only remaining piece in the SIP signalling communication?

2) How to send the ICE-Trickle candidates from the browser to baresip?

I worked around this by just waiting for the ICE gathering to finish in the browser, before sending the initial SDP Offer to baresip. What would be the correct way to deliver extra ICE candidate through SIP? is it feasible to do that without touching the SIP/SDP too much (i'm still trying to get away without a SIP client library for parsing, etc...)


The SDP Offer from the Chromium browser now contains this line:
a=rtcp:9 IN IP4 0.0.0.0

baresip trys to connect through RTCP correct right IP, on Port 9, which obviously fails. Any idea why Chromium chooses this weird port number?


Firefox just refuses to make any connection to the websocket.

I'm trying to get away without using a SIP library, just

On 07.04.2017 18:33, Alfred E. Heggestad wrote:
> On 07/04/17 04:26, Jonathan Sieber wrote:
>>
>> I found the baresip_ws branch, respectively re/sip_websock, and was able to make a WebSocket connection from Chromium into baresip code work.
>>
>> There seems to be a race condition where libre sometimes doesn't "find" the incoming websocket, and starts a HTTP WS request to the remote address with '/path'
>>
>> But eventually, the INVITE will arrive, but baresip replies with 488 Not Acceptable, because have_common_audio_codecs() returned false.
>>
>> I learned something about the sdp parsing code, trying to find out why there wouldn't be any codec candidates left in the audio stream object, but i'm entangled in unknown
>> data structures and can not find out where exactly the sdp code rejects the candidates
>>
>> What was the current state of the websocket branch(es) as a server, anyway?
>> It's seems like it's really close to work and do something really cool with it... ;D
>>
>>
>
> Hi Jonathan,
>
>
> for webrtc interop the ice.so and dtls_srtp.so modules must be loaded
> and used. You need to use the same RTP profile as the webrtc endpoint
> you are talking to, most likely UDP/TLS/RTP/SAVPF.
>
>
> regarding SIP over Websockets, I did some work on this earlier but
> it is far from complete. I am not planning to work on this any time
> soon, so if we want to add support for this we need to ask the
> community for help.
>
>
>
>
> /alfred 



_____________________________________________

SIP2WebRTC Bridge
=================

Call me on https://webrtc.sipthor.net/call/strfry@sip2sip.info

Mirror teilWERK.pads.ccc.de to ewindow.org or strfry.org/teilWERK

EWindow Browser Access
======================

Though this is beyond the functionality of a static window,
we want interaction between the window and users visiting the website.


WebRTC Client
=============


Now
---

Set up HackMD! -> FreeBSD PhantomJS npm issue -> 


Before
------

Before i go home, i need to take the Web Client with me.
Call me on http://ewindow.org

After
-----

Found some trivial example code "WebRTC-Example" on github
Problems with baresip connectivity
* Could not reproduce SIP invite/connect with netcat + 0.sip/*.sip
* Full SIP library for browser use?? idk
* small node-ish proxy
* attempt at goproxy


# WebRTC

https://www.mizu-voip.com/Software/WebPhone.aspx // commercial product // doesnt support p2p ??

https://www.rfc-editor.org/rfc/rfc7363.txt

Troubleshooting
===============

"Destination Address Required"
------------------------------

 -> System can not send a packet to this address
Possible Reasons:
* Bound to wrong interface

Check for

    net_interface          tap0

in .baresip/config


Connection stops after short time:
* Check for rtp_timeout option


Video is not Fullscreen
-----------------------

Try software scaler module...
    module swscale.so

WebRTC
======

Starting of Sylk, (commercial service provice sipthor.net)
Get an account on sip2sip.info

Figure out audio codecs:

estar@sip2sip.info: {0/TLS/v4} 200 OK (SIP Thor on OpenSIPS XS 1.11) [1 binding]
call: alloc with params laddr=127.0.0.1, af=AF_INET
ice: new session with STUN-server at sip2sip.info (username=estar)
call: no common audio codecs - rejected

sip2sip.info server logs are a blessing

G722/8000/1
a=rtpmap:109 opus/48000/2
a=rtpmap:9 G722/8000/1
a=rtpmap:0 PCMU/8000
a=rtpmap:8 PCMA/8000
a=setup:actpass


    gmake CC=cc\ -g baresip
    lldb37 baresip
    -> the variable name reveals, it's actually about video codecs!
    --> lldb37 stepped in a trap and led me in account_debug??
    gdb baresip
    b have_common_audio_codecs
    
    sc = sdp_media_rformat(stream_sdpmedia(audio_strm(call->audio)), NULL);


10 minutes of tedious ack grepping
--> re/src/sip/msg.c:media_decode

later:
--> ((sdp_media*)m)->rfmtl is empty list


AAAH:
---> The real problem is call->audio ->strm->sdp->rfmtl is empty
       How should it be filled?
       audio_alloc
        stream_alloc
         sdp_media_add
          media_alloc
           it's not there??
           
---> rfmtl It should be filled later by sdp_decode

ack rfmtl -> b set

GDB hates me:
(gdb) print call->audio->strm->sdp->rfmtl
Segmentation fault

### RESOLUTION: Use mediaenc=srtp instead of dtls_srtp

  Actually baresip is saying there are no common encryption schemes,
  not audio codecs


Baresip
=======

* OMX code working, but kinda crashy in slow circumstances
* exit-hack wasn't necessary, neither was it effective
* now process dies of memory starvation
* vcgencmd doesn't exist on FreeBSD, get over it
* Next: Try baresip with void linux setup

Network Architecture
--------------------

Good: Automatic naming by 

Tutorial
--------

* How to solve the different small problems with baresip


FAQ
---

icegath: {audio.1} STUN Request failed: Operation timed out
icegath: {audio.2} STUN Request failed: Operation timed out
ice: gather error: Operation timed out (0 )
call: medianat 'ice' failed: Operation timed out

---> Check for public v4/v6 / net_interface configu

;stunserver=stun:ewindow.org
found
no common audio codecs found -> module srtp.so


---
ice: audio.1: no remote candidates found (address = 81.23.228.129:59302)

reSTUNd
-------


