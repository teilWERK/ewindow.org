2 - baresip
===========

* make/install baresip

cat > .baresip/config << EOF

EOF


Useful baresip commands:
* baresip -


#outdated
Roadmap: https://github.com/alfredh/baresip/wiki/Roadmap
Issues: https://github.com/alfredh/baresip/issues

https://github.com/alfredh/baresip/issues/196
# SCReAM algorithm https://github.com/EricssonResearch/scream
# SCReAM - Mobile optimised congestion control 
baresip FAQ
-----------

destination address required --> sip_listen ist beschraenkt auf v4 ODER v6


PENDING: The baresip exil build
===============================

* Quite slow
* pkg install gmake
* gmake CC=cc
* git clone https://github.com/creytiv/re
* gmake CC=cc
* WAIT

* vidloop

[http://picamera.readthedocs.io/en/release-1.11/fov.html]

TESTBENCH omx_vidloop

Unknown crash in rpicam.c?
// memcpy

reconstruct vidloop from raspberry pi samples
understand packet sizes, can i instruct codec to cut things into rtp?
what does h264_packetize do for me?
just use vp8?

* VP8 

This is the current choice for RPi2/3

Testing
-------

Requiring network or vidloop is a problem.
call functions directly that should set up a local video feedback;


vc4_allocdev
------------

allow for video_render without tunnel? :D
VP8/9 Soft Codecs FTW!

* Only need to implement video render for fullscreen etc...


WTH is going on
---------------

* Verify State Transitions of OMX components
* Clean up Log interface

Share all the Stuff
-------------------
Welcome to teilWERK sharePAD V0.0.1! 

This pad  text is synchronized as you type, so that everyone viewing this page  sees the same text.  This allows you to collaborate seamlessly on  documents! 
  
  

Old Setup/Compile Manual (Debian)
=================================

git clone https://github.com/creytiv/re
git clone https://github.com/creytiv/rem
git clone https://github.com/eleKtronicwindow/baresip

cd re && make && cd ../rem && make  && ../baresip
ln -s /home/ewindow/baresip ~/.baresip
apt-get install libsrtp0-dev
apt-get install libopus-dev 

apt-get install libvpx-dev #VP8/VP9 Video Codec

apt-get install libgstreamer1.0-dev # GStreamer audio source (Web Radio)

TODO opengles on RPI


SETUP baresip
=============

compile from src, etc etc.

cp ewindow.git/baresip/* $HOME/.baresip
edit .baresip/config:
  sip_listen hostname.ewindow.org:5060
#PROBLEM: Only takes IPv4 addresses??


CURRENT FOCUS: baresip p2p
==================

Problem: No packets flowing after connection
Answer: No IPv6 exchange without ICE??
Success! With restund stun server on calling server (standard config)
Problem: How to specify central server for stun, without giving up P2P??
Answer: ;stunserver=stun.ewindow.org?? in .baresip/accounts
Problem: decode failed
Answer: stunserver=stun:username@stun.ewindow.org
Problem: call: medianat 'ice' failed: Destination address required
Solution: /dial 202@exit.ewindow.org




Problem: Calling baresip crashed because of no TLS key??
Mid-Solution: Don't use TLS (no WebRTC compatibility??)

PROBLEM:

baresip -d202@exe
sip:202@exe: session closed: Destination address required
 - What is going on here?
baresip -d202@exe.ewindow.org
 - Same with v4/v6



Network Troubleshooting
===============

using stunserver: '@exit.ewindow.org'
account: @exit.ewindow.org: decode failed: No such file or directory

Solution:
stunserver=


EWindow Scratchpad
==================

Current
-------

* video_decode tunnel pipeline not working, unknown reasons
* work towards vidloop
* trying to get encoder running

Next
----

$ ack h264_packetize # Found in  in gst_video1/encode.c


Clean up Code
-------------

* Understand Garbage Collection Pattern:
vds = mem_zalloc(sizeof(*vds), destructor);

Next
----

* Works on x86, crash on raspberry??

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 20813800 (LWP 100428/baresip)]
vidsrc_frame_handler (frame=0x2090bee0, arg=0x20836620) at modules/vidloop/vidloop.c:204
204            if (st->vf->ench)

SOLVED: was git version f*ckup


* baresip -6 can talk between

Next
----

* video_encode ??
* video_decode/render ??


baresip
-------

* Why is IPv6 not signalled in ICE-less SDP?
** Native Ipv6 support in baresip?
** Should be: https://edvina.net/sipv6/protocol/

Try: Start baresip with -6 ??




NEXT
----

ack videnc_up # add videnc stubs
# -> include/baresip.h
839:typedef int (videnc_update_h)(struct videnc_state **vesp,
840-                  const struct vidcodec *vc,
841-                  struct videnc_param *prm, const char *fmtp,
842-                  videnc_packet_h *pkth, void *arg);
843-typedef int (videnc_encode_h)(struct videnc_state *ves, bool update,
844-                  const struct vidframe *frame);

# ack -A15 struct.vidcodec include
852:struct vidcodec {
853-    struct le le;
854-    const char *pt;
855-    const char *name;
856-    const char *variant;
857-    const char *fmtp;
858-    videnc_update_h *encupdh;
859-    videnc_encode_h *ench;
860-    viddec_update_h *decupdh;
861-    viddec_decode_h *dech;
862-    sdp_fmtp_enc_h *fmtp_ench;
863-    sdp_fmtp_cmp_h *fmtp_cmph;
864-};



WTF IS FTMP/fmtp?
--> ?? Format Pointer? pointer to string with codec packetization setting

DONE
----

vidloop: open video display (.)
vc4_allocdev=
vidloop: enabled encoder H264 (25 fps, 500000 bit/s)
vidloop: enabled decoder H264
videnc_update
vidloop: update encoder failed: Exec format error


static int videnc_update(struct videnc_state **vesp,
                  const struct vidcodec *vc,
                  struct videnc_param *prm, const char *fmtp,
                  videnc_packet_h *pkth, void *arg)
{
    puts("videnc_update");
    
}

gdb --args ./baresip -e/vidloop\ h264

Breakpoint 1, videnc_update (vesp=0x8022ee400, vc=0x8026013b8, prm=0x7fffffffe588, fmtp=0x0, pkth=0x80b6c5fc0 <packet_handler>, 
    arg=0x8022ee2c0) at modules/vc4/vc4.c:131
warning: Source file is more recent than executable.

131        puts("videnc_update");
Current language:  auto; currently minimal
(gdb) print *vesp
$1 = (struct videnc_state *) 0x0
(gdb) print *vc
$2 = {le = {prev = 0x0, next = 0x803435548, list = 0x6363e0, data = 0x8026013b8}, pt = 0x0, name = 0x802400e55 "H264", 
  variant = 0x802400e5a "packetization-mode=0", fmtp = 0x0, encupdh = 0x802400c10 <videnc_update>, 
  ench = 0x802400a60 <videnc_encode>, decupdh = 0x802400c50 <viddec_update>, dech = 0x802400a10 <viddec_decode>, 
  fmtp_ench = 0x802400c80 <h264_fmtp_enc>, fmtp_cmph = 0x802400d10 <h264_fmtp_cmp>}
(gdb) print *prm
$3 = {bitrate = 500000, pktsize = 1480, fps = 25, max_fs = 4294967295}
(gdb) 


Packet handler reached into encode_update:
typedef int (videnc_packet_h)(bool marker, const uint8_t *hdr, size_t hdr_len,
                  const uint8_t *pld, size_t pld_len, void *arg);
                  // hdr is RTP header??

* Got it, was return 0;

DONE
----

Why is decode function not called?
Put stuff in bellagio omx --> not available on freebsd

* What can i instead, if neither Raspi nor bellagio omx is available?
* Get Callbacks for window managment!
* Not called because videnc never starts viddec starts output?
--> Look at hello_encode

* Need to pass pkth handler function from update to encode
ack videnc_state

solution:

    info("passing random junk to pkth\n");
    ves->pkth(false /* no marker */, 0 /* no hdr */, 0 /* hdr_len */, 
        frame, 123, ves->arg);
        
vidloop: enabled encoder H264 (25 fps, 500000 bit/s)
vidloop: enabled decoder H264
videnc_update: *vesp=(nil)
viddec_updateEnabled codec: H264

Set static int viddec_update(struct viddec_state **vdsp, 
vdsp to something, viddec_decode gets called

* give newline to viddec_update/decode        

* analyse viddec_data
viddec_update *vdsp=(nil), vc=0x8026015d8, fmtp=

* analyse viddec_decode

Breakpoint 1, viddec_decode (vds=0x1337, frame=0x7fffdfffdd70, intra=0x7fffdfffdd67, marker=false, seq=0, mb=0x80ba36040)
    at modules/vc4/vc4.c:117

(gdb) print marker
$1 = false
(gdb) print *frame
$2 = {data = 0x7fffdfffdd70, linesize = 0x7fffdfffdd90, size = {w = 0, h = 0}, fmt = 704}
(gdb) 

  

* where the Heck is vidframe ??
--> ../rem/include/rem_vid.h

/** Video frame */
struct vidframe {
    uint8_t *data[4];      /**< Video planes        */
    uint16_t linesize[4];  /**< Array of line-sizes */
    struct vidsz size;     /**< Frame resolution    */
    enum vidfmt fmt;       /**< Video pixel format  */
};


--> Re-include #include <rem.h>


Port to Raspi
-------------

Merge stuff, forgot to commit etc. etc.

    videnc_update: vesp=0x20836758viddec_updateEnabled codec: H264
    [New Thread 20813800 (LWP 100407/baresip)]

    Program received signal SIGSEGV, Segmentation fault.
    [Switching to Thread 20813800 (LWP 100407/baresip)]
    vidsrc_frame_handler (frame=0x2090bee0, arg=0x20836620) at modules/vidloop/vidloop.c:204
    204            if (st->vf->ench)

Solved: Git version fup

Next
----

* Understand Garbage Collection Pattern:
vds = mem_zalloc(sizeof(*vds), destructor);
* Clean up code

* Get video_decode to work. Is it running?
* Can it work with small packets?

DUMP
====


/*
typedef void (vidisp_resize_h)(const struct vidsz *size, void *arg);

typedef int  (vidisp_alloc_h)(struct vidisp_st **vp,
                  const struct vidisp *vd, struct vidisp_prm *prm,
                  const char *dev,
                  vidisp_resize_h *resizeh, void *arg);
typedef int  (vidisp_update_h)(struct vidisp_st *st, bool fullscreen,
                   int orient, const struct vidrect *window);
typedef int  (vidisp_disp_h)(struct vidisp_st *st, const char *title,
                 const struct vidframe *frame);
typedef void (vidisp_hide_h)(struct vidisp_st *st);
*/






Today - Donnerstagg
================

Got something to send back
tried video_decode+video_render without much success


Next
====

* Clean up Code
* Setup where x220 client only receives
* 

video_render only:
http://home.nouwen.name/RaspberryPi/documentation/ilcomponents/video_render.html


OpenMAX video_render
--------------------

Difference between egl_render and video_render OpenMAX components with graphics:
https://www.youtube.com/watch?v=F_bVJLc2tbE


http://home.nouwen.name/RaspberryPi/documentation/ilcomponents/video_render.html
* Trying to dig through OMX headers


    /**  
     * Port format parameter.  This structure is used to enumerate the various 
     * data input/output format supported by the port.
     * 
     * STRUCT MEMBERS:
     *  nSize              : Size of the structure in bytes
     *  nVersion           : OMX specification version information
     *  nPortIndex         : Indicates which port to set
     *  nIndex             : Indicates the enumeration index for the format from 
     *                       0x0 to N-1
     *  eCompressionFormat : Compression format used in this instance of the 
     *                       component. When OMX_VIDEO_CodingUnused is specified, 
     *                       eColorFormat is used 
     *  eColorFormat       : Decompressed format used by this component
     *  xFrameRate         : Indicates the video frame rate in Q16 format
     */
    typedef struct OMX_VIDEO_PARAM_PORTFORMATTYPE {
        OMX_U32 nSize;
        OMX_VERSIONTYPE nVersion;
        OMX_U32 nPortIndex;
        OMX_U32 nIndex;
        OMX_VIDEO_CODINGTYPE eCompressionFormat; 
        OMX_COLOR_FORMATTYPE eColorFormat;
        OMX_U32 xFramerate;
    } OMX_VIDEO_PARAM_PORTFORMATTYPE;

NEXT
====

* Build sample code with generate_test_card and omx.video_render ??
* Build sample code to call the OMX stuff without baresip??

https://github.com/tjormola/rpi-openmax-demos


hello_rawvideo
--------------

Modified hello_video to play to with video_render only.

Open Questions:
* How to set input port resolution?
* Which input format work?

http://home.nouwen.name/RaspberryPi/documentation/ilcomponents/video_render.html

Request OMX_VIDEO_PORTDEFINITIONTYPE ??
=======================================

less /usr/local/include/IL/OMX_Component.h # PARAM_ types??
less /usr/local/include/IL/OMX_Video.h

typedef struct OMX_VIDEO_PORTDEFINITIONTYPE {
    OMX_STRING cMIMEType;
    OMX_NATIVE_DEVICETYPE pNativeRender;
    OMX_U32 nFrameWidth;
    OMX_U32 nFrameHeight;
    OMX_S32 nStride;
    OMX_U32 nSliceHeight;
    OMX_U32 nBitrate;
    OMX_U32 xFramerate;
    OMX_BOOL bFlagErrorConcealment;
    OMX_VIDEO_CODINGTYPE eCompressionFormat;
    OMX_COLOR_FORMATTYPE eColorFormat;
    OMX_NATIVE_WINDOWTYPE pNativeWindow;
} OMX_VIDEO_PORTDEFINITIONTYPE;



Brand new hello_pi example encode_mmal: https://github.com/raspberrypi/firmware/tree/master/opt/vc/src/hello_pi/hello_mmal_encode
===========================


if (OMX_SetParameter(ILC_GET_HANDLE(video_render), OMX_IndexParamVideoPortFormat, &format) != OMX_ErrorNone) {
    puts("fucking error setting format on video_render");
    exit(-23);
}


NEXT
====

* get rid of ilclient lib
* Get control of viddisp api
* Research OMX_VIDEO_CodingAutoDetect

Useful OpenMAX Function
-----------------------
###Known
* OMX_Init / OMX_Deinit


###Unknown
* OMX_GetState
* OMX_UseBuffer
* OMX_AllocateBuffer / OMX_FreeBuffer
* OMX_EmptyThisBuffer / OMX_FillThisBuffer
* OMX_ComponentNameEnum
** Is this useful at all? It reports to much stuff that is not supported later

** Also: OMX_GetComponentsOfRole / OMX_GetRolesOfComponent
            puts("get port roles");
          
          char* roles[32];
          int num_roles = 32;
          OMX_GetRolesOfComponent("OMX.broadcom.video_render", &num_roles, roles);
          
          int i;
          for (i = 0; i < num_roles; i++) {
              puts(roles[i]);
          }
* OMX_GetHandle / OMX_FreeHandle
** Allocates and loads a component to memory, returns handle
* OMX_SetupTunnel
* OMX_GetContentPipe??

* OMX_SendCommand

Enable the component port number
    OMX_SendCommand(comp->comp, OMX_CommandPortEnable, portIndex, NULL);

* OMX_UseBuffer

    OMX_UseBuffer(video_render, )


Port Definition
---------------

$1 = {nSize = 96, nVersion = {s = {nVersionMajor = 1 '\001', nVersionMinor = 1 '\001', nRevision = 2 '\002', nStep = 0 '\0'}, 
    nVersion = 131329}, nPortIndex = 90, eDir = OMX_DirInput, nBufferCountActual = 3, nBufferCountMin = 2, nBufferSize = 15360, 
  bEnabled = OMX_TRUE, bPopulated = OMX_FALSE, eDomain = OMX_PortDomainVideo, format = {audio = {cMIMEType = 0x0, 
      pNativeRender = 0x0, bFlagErrorConcealment = 160, eEncoding = 64}, video = {cMIMEType = 0x0, pNativeRender = 0x0, 
      nFrameWidth = 160, nFrameHeight = 64, nStride = 160, nSliceHeight = 64, nBitrate = 0, xFramerate = 0, 
      bFlagErrorConcealment = OMX_FALSE, eCompressionFormat = OMX_VIDEO_CodingUnused, 
      eColorFormat = OMX_COLOR_FormatYUV420PackedPlanar, pNativeWindow = 0x0}, image = {cMIMEType = 0x0, pNativeRender = 0x0, 
      nFrameWidth = 160, nFrameHeight = 64, nStride = 160, nSliceHeight = 64, bFlagErrorConcealment = OMX_FALSE, 
      eCompressionFormat = OMX_IMAGE_CodingUnused, eColorFormat = OMX_COLOR_FormatUnused, pNativeWindow = 0x0}, other = {
      eFormat = OMX_OTHER_FormatTime}}, bBuffersContiguous = OMX_FALSE, nBufferAlignment = 16}


yuvvideo
--------

yuvvideo uses video_render without libilclient

* New Github repo: rpi-openmax



NEXT
====

* master baresip viddisp interface, give stuff to omx
