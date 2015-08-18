# Overview #

The structure of the AVR code comes from the Mattair demo program. The program demos the various hardware features and there is a simple text menu used to select the tests. The VBIT code is added as another test. The advantage is that all of the tedious framework especially the USB comms is taken care for you.


# Outline #

These are the steps to get a working VBIT. Unfortunately there are no detailed instructions as yet but this should give you an idea of how I did it. Look in the code for an example of how I did it with the old Mattair board.

  * Download the latest version of the source code from http://xmega.mattair.net/code.html
  * Place the VBIT code in the XMEGA section alongside the other demos. I use Tortoise SVN and checkout vbit into the right place which is ../MT-X1/XMEGA/vbit
  * Edit the makefile to compile VBIT. I use Notepad++ for all text editing. In the SRC list you need to add this list
```
    vbit/vbit.c				\
    vbit/p830f1.c                        \
    vbit/fifo.c                          \
    vbit/tables.c                        \
    vbit/packet.c                        \
    vbit/i2c.c                        \
    vbit/vbi.c                        \
    vbit/databroadcast.c              \
    vbit/sdfilemanager.c             \
    vbit/page.c             \
    vbit/crca.c             \
    vbit/Lib/RingBuff.c		\
```
  * Download MinIni and put that in the XMEGA folder. It needs a little customising in minGlue.h. Also add this to the SRC list.
```
	minini/minIni.c			\	
```
Try doing a make. If it is anything like mine it fails in a hail of missing stuff like avr\_compiler.h, all of the USB bridge stuff and the SD card. We will attack that next time.
  * Add VBIT to the menu list.
  * Set VBIT to start automatically by jumping directly to the VBIT code.