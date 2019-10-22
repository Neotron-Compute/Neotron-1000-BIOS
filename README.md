# Neotron 1000 BIOS

This is the BIOS for the Neotron 1000. It implements the Neotron BIOS API (a hardware-abstraction layer used by the Neotron OS).

## Hardware

The Neotron 1000 is a heavily revised version of the [Monotron](https://github.com/thejpster/monotron). It uses an STM32H7 CPU running at 400 MHz, and has 512 KiB of main SRAM (plus additional smaller blocks of SRAM for cache).

## Status

This BIOS is a work in progress. Bits of the Monotron firmware will be ported over one at a time. The todo list is:

* [ ] Get it booting
* [ ] UART
* [ ] SD Card
* [ ] Text Mode (80 x 36)
* [ ] Audio
* [ ] Bitmap Mode (400 x 300)

## Memory Map

The Neotron 1000 has 1024 KiB of Flash and 512 KiB of main RAM. The Flash layout is:

* First 256 KiB of Flash for the BIOS
* Next 64 KiB of Flash for the OS
* Next 64 KiB of Flash for the Shell

The RAM layout is flexible - the BIOS takes as much as it needs, then passes the OS the definitions of how much RAM is available and where it is located. The OS then dynamically allocates almost everything it needs from that. The BIOS is also responsible for configuring the stack, and moving the interrupt vector table to RAM.
