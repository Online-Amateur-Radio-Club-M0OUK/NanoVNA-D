NanoVNA - Very tiny handheld Vector Network Analyzer
==========================================================
[release]: https://github.com/DiSlord/NanoVNA-D/releases

<div align="center">
<img src="/doc/nanovna.jpg" width="480px">
</div>

# About

NanoVNA is very tiny handheld Vector Network Analyzer (VNA). It is
standalone with lcd display, portable device with battery. This
project aim to provide an RF gadget but useful instrument for
enthusiast.

This repository contains source of NanoVNA firmware.

This is an OARC fork with the aim of adding a few feature to the firmware.

[![Build status](https://github.com/Online-Amateur-Radio-Club-M0OUK/NanoVNA-D/actions/workflows/makefile.yml/badge.svg?branch=master)](https://github.com/Online-Amateur-Radio-Club-M0OUK/NanoVNA-D/actions/workflows/makefile.yml)

## Prepare ARM Cross Tools

**UPDATE**: Recent gcc version works to build NanoVNA, no need old version.

### MacOSX

Install cross tools and firmware updating tool.

    $ brew tap px4/px4
    $ brew install gcc-arm-none-eabi-80
    $ brew install dfu-util

### Linux (ubuntu)

Download arm cross tools from [here](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads).

    $ wget https://developer.arm.com/-/media/Files/downloads/gnu-rm/8-2018q4/gcc-arm-none-eabi-8-2018-q4-major-linux.tar.bz2
    $ sudo tar xfj gcc-arm-none-eabi-8-2018-q4-major-linux.tar.bz2 -C /usr/local
    $ PATH=/usr/local/gcc-arm-none-eabi-8-2018-q4-major/bin:$PATH
    $ sudo apt install -y dfu-util

## Fetch source code

Fetch source and submodule.

    $ git clone https://github.com/DiSlord/NanoVNA-D.git
    $ cd NanoVNA
    $ git submodule update --init --recursive

## Build

Just make in the directory.

    $ make

## Flash firmware

First, make device enter DFU mode by one of following methods.

* Jumper BOOT0 pin at powering device
* Select menu Config->DFU (needs recent firmware)

Then, flash firmware using dfu-util via USB.

    $ dfu-util -d 0483:df11 -a 0 -s 0x08000000:leave -D build/ch.bin

Or simply use make.

    $ make flash

## Companion Tools

There are seveal numbers of great companion PC tools from third-party.

* [NanoVNA-App software](https://github.com/OneOfEleven/NanoVNA-H/blob/master/Release/NanoVNA-App.rar) by OneOfEleven
* [NanoVNASharp Windows software](https://drive.google.com/drive/folders/1IZEtx2YdqchaTO8Aa9QbhQ8g_Pr5iNhr) by hugen79
* [NanoVNA WebSerial/WebUSB](https://github.com/cho45/NanoVNA-WebUSB-Client) by cho45
* [Android NanoVNA app](https://play.google.com/store/apps/details?id=net.lowreal.nanovnawebapp) by cho45
* [NanoVNASaver](https://github.com/mihtjel/nanovna-saver) by mihtjel
* [TAPR VNAR4](https://groups.io/g/nanovna-users/files/NanoVNA%20PC%20Software/TAPR%20VNA) supports NanoVNA by erikkaashoek
* see [python](/python/README.md) directory to use NanoVNA with Python and Jupyter Notebook.

## Documentation

* [NanoVNA User Guide(ja)](https://cho45.github.io/NanoVNA-manual/) by cho45. [(en:google translate)](https://translate.google.com/translate?sl=ja&tl=en&u=https%3A%2F%2Fcho45.github.io%2FNanoVNA-manual%2F)

## Reference

* [Schematics](/doc/nanovna-sch.pdf)
* [PCB Photo](/doc/nanovna-pcb-photo.jpg)
* [Block Diagram](/doc/nanovna-blockdiagram.png)
* Kit available from https://ttrf.tk/kit/nanovna

## Note

Hardware design material is disclosed to prevent bad quality clone. Please let me know if you would have your own unit.

## Credit
* [@DiSlord](https://github.com/DiSlord/)

## Based on code from:
* [@edy555](https://github.com/edy555)

### Contributors
* [@OneOfEleven](https://github.com/OneOfEleven)
* [@hugen79](https://github.com/hugen79)
* [@cho45](https://github.com/cho45)

