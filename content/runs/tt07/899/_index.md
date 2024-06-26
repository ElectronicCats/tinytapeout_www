---
hidden: true
title: "899 Reversible logic based Ring-Oscillator Physically Unclonable Function (RO-PUF)"
weight: 32
---

## 899 : Reversible logic based Ring-Oscillator Physically Unclonable Function (RO-PUF)

* Author: Syed Farah Naz, Shivam Bhardwaj, Ambika Prasad Shah
* Description: Reversible logic based Ring-Oscillator Physically Unclonable Function (RO-PUF)
* [GitHub repository](https://github.com/shivam7086/tt07-verilog-RO_PUF)
* [GDS submitted](https://github.com/shivam7086/tt07-verilog-RO_PUF/actions/runs/9018187608)
* HDL project
* [Extra docs]()
* Clock: 0 Hz

<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->


### How it works

We have introduced a fault-tolerant system featuring a ring-oscillator (RO) based Physcially Unclonable Function (PUF), utilizing a reversible logic (RL) design. The proposed system comprises of Fault-Tolerant RL-based inverter design and the Reversible RO-PUF module. This RO-PUF design consists of several cascaded chains of DFGs (functioning as inverter/buffer as and when required). We have used 64 ROs, divided into groups of 32 ROs in our proposed RO-PUF architecture. Each of these 32 ROs is connected to two 32×1 MUXs (Mux-1 and Mux-2), which select an RO according to the bit combination given in the select lines. The output of the selected RO is fed to the input of the counter, which counts the number of pulses generated by the RO until a certain condition is reached, as specified in the comparator design. The comparator takes input from the output of the two counters (Counter-1 and Counter-2), which are continuously changing. When any of the two counters reaches its specified maximum value of 32 bits, the current 32-bit count value of the slower counter is latched onto the output of the PUF. The 5-bit challenges are randomly generated with the help of a linear feedback shift register (LFSR). The select lines of both the 32×1 MUXs are connected with challenge bits so that unique ROs are selected for comparison. Since the frequency of each RO is different due to process variations, when one of the two chosen ROs attains its specified maximum count value, the frequency count of the other RO will be different, and we will get a unique response for each challenge.

### How to test

We have tested the design on Vivado and OpenRoad Flow Script.

### External hardware

Default


### IO

| #             | Input    | Output   | Bidirectional   |
| ------------- | -------- | -------- | --------------- |
| 0 | rst_n  | Respose_1  |         |
| 1 | ena  | Respose_2  |         |
| 2 | Challenge_1  | Respose_3  |         |
| 3 | Challenge_2  | Respose_4  |         |
| 4 | Challenge_3  | Respose_5  |         |
| 5 | Challenge_4  | Respose_6  |         |
| 6 |   | Respose_7  |         |
| 7 |   | Respose_8  |         |


### Chip location

{{< shuttle-map "tt07" "899" >}}