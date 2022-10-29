# koboto.io

Version: 1.1.0<br>
Release date: 2021/10/11<br>
[www.koboto.io](https://koboto.io/)

These files are the software for the Koboto.io Boards Using Atmega328PB MCU.


## Arduino IDE integration

These files can be used to add all boards of koboto.io support to the Arduino IDE.
Entries for **koboto.io Boards** will appear in the **Boards** menu
when you do this.

For most people, we recommend setting up Koboto Boards support in the Arduino IDE by
installing our boards package through the Boards Manager. (These instructions
can also be found in the user's guide for each controller).

1.  In the Arduino IDE, open the **File** menu (Windows/Linux) or the
    **Arduino** menu (macOS) and select "Preferences".

2.  In the Preferences dialog, find the "Additional Boards Manager URLs" text
    box. Copy and paste the following URL into this box:

    **`https://github.com/Koboto-Boards/Boards-to-ArduinoIDE/raw/koboto.io_V1.0/package_koboto.io_index.json`**

    If there are already other URLs in the box, you can either add this one
    separated by a comma or click the button next to the box to open an input
    dialog where you can add the URL on a new line.

3.  Click the "OK" button to close the Preferences dialog.

4.  In the **Tools > Board** menu, select "Boards Manager..." (at the top of the
    menu).

5.  In the Boards Manager dialog, search for "koboto.io Boards".

6.  Select the "koboto.io Boards" entry in the list, and click the
    "Install" button.

For additional information, including instructions for uploading a sketch and
troubleshooting, refer to the user's guide for your controller.


## ATmega328PB support in the Arduino IDE

These files have been tested with the Arduino IDE version 1.8.5.  Since that
version of the IDE does not have official ATmega328PB support, these files
configure the compiler to target the older ATmega328P, which is very similar to
the PB.  We added extra definitions so you can use all of the new features of
the ATmega328PB, while still being able to compile almost any code that worked
on the older ATmega328P.

Here are some details about what Arduino features work when programming the
koboto boards in the Arduino IDE:

- The `Serial` and `Serial1` objects both work, providing access to UART0 and
  UART1, respectively.
- The "Default I2C bus" sub-menu in the "Tools" menu allows you to choose whether the Wire library and other libraries like it will use TWI0 or TWI1. There is no library support for accessing TWI0 and TWI1 in the same program.
- The "Default SPI bus" sub-menu in the "Tools" menu allows you to choose whether the SPI library and other libraries like it will use SPI0 or SPI1. There is no library support for accessing both SPI0 and SPI1 in the same program.
- `pinMode()`, `digitalRead()`, and `digitalWrite()` should work on every I/O
  pin.
- `analogRead()` should work on every analog pin (A0 through A7).
- `analogWrite()` should work on every pin with PWM.

The ATmega328PB has two new pins, PE0 and PE1, that have no equivalent on the
ATmega328P.  These pins do not yet have official pin numbers in the Arduino
environment, so if you need to use their pin numbers in your code, we recommend
using the constants `SDA1` (for PE0) and `SCL1` (for PE1) that are defined in
our header files.  For example:

```c++
digitalWrite(SDA1, HIGH);
```

## Bootloader

The "bootloader" directory contains the source code and compiled files for
Atmega328PB MCU using "optiboot".

## Version history

- 1.1.0 (2022-10-29): Made the Wire and SPI libraries usable on the A-Star 328PB again. Added menus that let you choose which bus each library will use.
- 1.0.0 (2021-10-11): Start of the project;



