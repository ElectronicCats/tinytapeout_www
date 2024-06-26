---
hidden: true
title: "419 DJ8 8-bit CPU"
weight: 9
---

## 419 : DJ8 8-bit CPU

* Author: DaveX
* Description: DJ8 8-bit CPU with parallel Flash / RAM interface
* [GitHub repository](https://github.com/dvxf/tt06-dj8)
* [GDS submitted](https://github.com/dvxf/tt06-dj8/actions/runs/8750935211)
* HDL project
* [Extra docs]()
* Clock: 14000000 Hz

<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->


### How it works

DJ8 is a 8-bit CPU, originally developped for XCS10XL featuring:

* 8 x 8-bit register file
* 3-4 cycles per instruction
* 15-bit address bus
* 8-bit data bus

#### Memory Map

| From | To | Description
|--|--|--|
| 0x0000 | 0x7fff | External memory
| 0x8000 | 0xffff | Internal Test ROM (256 bytes, mirrored)

###### External memory map if using the recommended setup (see [pinout](#pinout))

| From | To | Description
|--|--|--|
| 0x2000 | 0x3fff | External RAM (32 bytes)
| 0x4000 | 0x5fff | External Flash ROM (16KB)

#### Pinout

Due to TT06 IO constraints, pins are shared between *Address bus LSB* and *Data bus OUT*. It means that during memory write instructions, the address space is only 64 bytes.

| Pins | Standard mode | During memory write execute+writeback cycles
|--|--|--|
| ui[7..0] | Data bus IN | Data bus IN
| uio[7..0] | Address bus LSB (7..0) | ***Data bus OUT***
| uo[6..0] | Address bus MSB (14..8) | Address bus MSB (14..8)
| uo[7] | Write Enable | Write Enable

You can connect a 8KB parallel Flash ROM + 32b SRAM without
external logic and use uo[6] for RAM OE# and uo[5] for Flash ROM OE#.

To get a bidirectional data bus (needed for SRAM), uio bus must be connected to ui bus with resistors. To be tested!

#### Reset

At reset time, PC is set to 0x4000.

All other registers are set to 0x80.

### How to test

An internal test ROM with two demos is included for easy testing. Just select the corresponding DIP switches at reset time to start the demo (technically, a ***jmp GH*** instruction will be seen on the data bus thanks to the DIP switches values, with GH=0x8080 at reset).

#### Demo 1: Rotating LED indicator

| SW1 | SW2 | SW3 | SW4 | SW5 | SW6 | SW7 | SW8 |
|--|--|--|--|--|--|--|--|
| 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |

No external hardware needed. This demo shows a rotating indicator on the 7-segment display. Its speed can be changed with DIP switches, the internal delay loop is entirely deactivated when all switches are reset.

#### Demo 2: Bytebeat Synthetizer

| SW1 | SW2 | SW3 | SW4 | SW5 | SW6 | SW7 | SW8 |
|--|--|--|--|--|--|--|--|
| 0 | 0 | 0 | 0 | 0 | 1 | 1 | 0 |

Modem handshakes sound like music to your hears? It's your lucky day! Become a DJ thanks to 256 lo-fi glitchy settings.

Connect a speaker to uo[4] or use [Tiny Tapeout Simon Says PMOD](https://github.com/urish/tt-simon-pmod).

It is highly recommended to add a simple low-pass RC filter on the speaker line to filter out the buzzing 8kHz carrier. Ideal cut-off frequency between 3kHz and 8kHz, TBD.

Set SW1 and/or SW2 at reset time to adjust speed in case the design doesn't run at 14MHz.

### External hardware

* No external hardware needed for demos
* Otherwise: Parallel Flash ROM + optional SRAM


### IO

| #             | Input    | Output   | Bidirectional   |
| ------------- | -------- | -------- | --------------- |
| 0 | data in 0  | address out 8  | address out 0 / data out 0        |
| 1 | data in 1  | address out 9  | address out 1 / data out 1        |
| 2 | data in 2  | address out 10  | address out 2 / data out 2        |
| 3 | data in 3  | address out 11  | address out 3 / data out 3        |
| 4 | data in 4  | address out 12  | address out 4 / data out 4        |
| 5 | data in 5  | address out 13  | address out 5 / data out 5        |
| 6 | data in 6  | address out 14  | address out 6 / data out 6        |
| 7 | data in 7  | write enable  | address out 7 / data out 7        |


### Chip location

{{< shuttle-map "tt06" "419" >}}
