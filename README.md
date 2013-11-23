# fbvnc #

Patched framebuffer VNC client for view-only use on the Raspberry Pi

Features:

* Minimal binary (25KB)
* Very fast framebuffer rendering (16-bit over Ethernet is pretty much instantaneous)
* View-only support (for digital signage)

TODO:

* Fix naive authentication code so that it supports RFB 3.8 auth modes and we can use Macs as servers

----
## Original README ##

There is already a framebuffer VNC client for Linux:

<http://pocketworkstation.org/fbvnc.html>

While this also comes with some bugs, and its size seems not suitable for tiny embeded system.

Then I found this fbvnc project:

<http://repo.or.cz/w/fbvnc.git>

Very lightweight, some function works fine, sadly still some bugs with this fbvnc.

So, I decide to make this fbvnc project better for embeded system.
These things should be done later:

* try to fix 16/32 bits color display bug (DONE)
* add VNC authentication support (DONE)
* better mouse event support (DONE)
* ...

## Notes about framebuffer depth (Raspbery Pi) ##

This fbvnc project assumes framebuffer color depth is 32bit.

If your framebuffer device has some bug for 32bit framebuffer (like Raspberry Pi)
or doesn't support 32bit framebuffer at all, 
then you need to change size of framebuffer depth in fbvnc.c

For Raspbery Pi (display well in 16bit framebuffer), you need to change:

typedef unsigned int fbval_t;

to:

typedef unsigned short fbval_t;
