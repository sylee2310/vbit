# Engineering Change Notes for vbit-3 #

This was the first run of the board so there are some modifications required to make the board run. Pictures are at https://picasaweb.google.com/peterk.vt80/VBIT


# ECN 1 #
The power supply is not sufficiently decoupled.

Additional decoupling is added in the form of 100uF surface mount electrolytics. These can be attached by scraping the solder resist from the top. Fit them in these locations.

  * Above L1 between the +3V3 and ground.
  * On the +3V3 line between L6 and ground

# ECN 2 #
The I2C SDA and SCL lines do not have sufficient pull-ups on them. The I2C has to run very slow without them.

The most convenient place to attach these is on the +3V3 side of L1 and L2. Attach a 3k3 0805 resistor to L1, and another one to L2. Then using very fine wire, link the free end of each resistor and go through the SDA and SCL vias and attach to pins 7 and 8 of P5.

# ECN 3 #
It was found that a vital signal had been omitted from the FIFO. One signal from the AVR needs to be connected to the FIFO. The reset signal from the AVR to U2 pin 40 was disconnected and reattached to the FIFO. U2 instead has the reset line permanently pulled high.

  * Remove [R8](https://code.google.com/p/vbit/source/detail?r=8)
  * Cut the trace from P5 - Pin 4.
  * Connect pin 1 of the FIFO to pin 4 of P5. This is best done by connecting to the empty pad of [R8](https://code.google.com/p/vbit/source/detail?r=8), through the adjacent via and then direct to pin4 of P5.
  * U2 Pin 40 is now floating. Use some wire wrap wire to connect this pin to the +3V3 line.

# ECN 4 #
It was found that the power through the IDC connector was very inadequate. The voltage was not enough to drive the SAA chips.

Fit a two pin connector to a suitable location on the XMEGA board to pick up the 3V3 power. Connect the + to the power input side of L1. Connect the common to the common side of C12. An old PC is a very convenient source of ready made cables complete with connectors. The power and reset LEDs have the correct connector.

# ECN 5 #
I have a better method of connecting the MT-X1 board. See the photographs of where to fit the header pins. A 5x2 in XC0 to XD2 and a two pin at 3V3 and GND. The 5x2 can use a serial port ribbon cable from an old PC. This cable must be kept short otherwise crosstalk will cause corrupted signals. The 1x2 can use a two pin speaker/reset button/LED connector also found in an old PC.

Just for historical completeness, this is how I connected the XD200 board.
For convenience in connecting the XMEGA to the VBIT boards a 10x2 way IDC ribbon connector is used. If you have an XD200 board then you must cut the pair of pins XB6 and XB7 and also the pair of pins on Conn19. Then the 10x2 way cable can only fit one way on the XMEGA board.
This is Conn16 and the Conn next to it that has PORT C XC0 to XC7.

Be very careful when fitting the interconnection as a mistake will destroy the board.

# ECN 6 #
For XD200 XMEGA revision A boards, J27 should be closed with a solder blob. MT-X1 has no such modifications.