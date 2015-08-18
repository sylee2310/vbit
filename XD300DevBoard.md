Note Justin called the XD300 board the XD200 Revision B. Neither board is available. Instead use the MT-X1.
# XD200 XMEGA Development Board #

You might be wondering about why I'm using the XD300. As a development board it has a lot of sensible features. All of the I/O is brought out on pin arrays that are easy to find and fit. It has a separate USB chip so the main processor is not burdened with the traffic. The main processor is programmed by the USB chip so there are no restrictions on things like clocks or fuses. Having an SD card really makes things easy when it comes to page storage. It also comes loaded with a handy USB bridge so you don't have to write one. And it is all based on the GCC AVR tool chain so nothing more to pay.

As for the XMEGA itself it has much more sophisticated ports than the standard AVRs. It also has a lot of timers which a teletext project seems to need a lot of.

You don't have to use an XMEGA or even an AVR based controller. All that you need to control VBIT is I2C, SPI and one bit each of input and output. I'm not saying it would be that easy to redo it, just that it is possible. A faster processor with a few MB of ram could play pages direct from ram and make it much easier to update.

The XD200 board has different levels of build. Probably the best one for this project is the XD200 with peripherals but without the headers or joystick switch. Otherwise you will have to cut pins off where they get in the way.
Get the MT-X1 board bare and only fit the headers that you need, otherwise they will get in the way.