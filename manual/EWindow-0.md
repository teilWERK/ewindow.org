Building and installation  
=========================

Link to manual, software components baresip, (Peer)VPN, ncurses menu

Building baresip:

```
$ git clone https://github.com/creytiv/re
$ git clone https://github.com/creytiv/rem
$ git clone https://github.com/alfredh/baresip

$ cd re && make && sudo make install && cd ..
$ cd rem && make && sudo make install && cd ../baresip

$ make && make install

```

Configuration
=============

Start baresip once to create config file and  # Test Audio Feedback.
$ ./baresip -e /auloop

Edit ~/.baresip/config to 

$ echo "<sip:DISPLAYNAME:xxx@example.org;regint=0;" >> ~/.baresip/accounts 

Explanation: Add a sip user with any name, password, and domain 


To build ewindow core and the modules we forked from baresip and we are using ( GNU/BSD Make)
