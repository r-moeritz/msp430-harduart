Hardware UART example for MSP430 using mps430-gcc on Linux  
sw@kaltpost.de
http://gpio.kaltpost.de/


Introduction
------------

This example shows how to use hardware UART through USCI_A on the TI
Launchpad with a MSP430G2553 MCU.


Hardware Setup
--------------

The wiring for this example is as follows:

| MSP430   | To              |
| -------- | --------------  |
| RXD P1.1 | TXD serial line |
| TXD P1.2 | RXD serial line |

NOTE: When using the TI Launchpad, `/dev/ttyACM0` could be used as
serial port at 9600 Bauds, but RX/TX must be crossed on the jumper
bridge of the Launchpad.


Compilation
------------

- This project is written for msp430-gcc on Linux, which you can get
from [TI's website](https://www.ti.com/tool/MSP430-GCC-OPENSOURCE).
- For flashing, the [mspdebug](https://github.com/dlbeer/mspdebug)
tool was used (link to GitHub repo).

To compile the source just issue a:

    make

This builds the firmware in the "bin" subdirectory in various formats.


Flashing
------------

To flash the firmware to your Launchpad you could use the
"flash-target" make target:

    make flash-target


Doxygen Docs
------------

If you installed doxygen on your system, you could generate the
HTML-based documentation by calling:

    make gen-docs

This will create the documentation under "doc/gen/html".


Usage
------------

Connecting your Launchpad should give you a new serial device
`/dev/ttyACM0`. Connect to this port at 9600 bauds - e.g. by using
screen:

    screen /dev/ttyACM0 9600

A greeter is shown on the serial line, and you are prompted to press
any key to start the echo demo. After the first keypress, "OK" is
printed, and from then on, every character you type is echoed
back. Every time, a character is received, the red LED on the
launchpad is toggled. The green LED stadily blinks.
