---
hidden: true
title: "557 4-Bit ALU"
weight: 178
---

## 557 : 4-Bit ALU

* Author: Daniel Kaminski
* Description: 4-Bit ALU with Cornell ECE2300 op-code instructions.
* [GitHub repository](https://github.com/dgkaminski/tto6-submission)
* [GDS submitted](https://github.com/dgkaminski/tto6-submission/actions/runs/8746736738)
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

This project uses the Cornell University ECE2300 (SP24 taught by Zhiru Zhang) ISA to implement a 4-bit ALU. This ALU uses a top-level controller module to pipe the correct inputs and select the correct outputs (src/alu.v). The logical functions are implemented using the following instructions.

| FS | Function | Logical Equivalent |
| ------------- | ------------- | ------------- |
| 000  | ADD  | A + B |
| 001  | SUB  | A - B |
| 010  | SRA (Shift Right Arithmetic) | A>>> |
| 011  | SRL (Shift Right Logical) | A >> |
| 100  | SLL (Shift Left Logical) | A << |
| 101  | AND  | A & B |
| 110  | OR  | A + B |
| 111  | INVALID  | INVALID |

### How to test

Input your first value, A to UI[7:4], and B to UI[3:0]. You then put your function select (FS) input into UIO[2:0], and you can read your Y output at UO[7:4], your carry out at UO[3], overflow at UO[2], negative at UO[1], and zero at UO[0].

### External hardware

None! Just a way to input your desired values and read the outputs.


### IO

| #             | Input    | Output   | Bidirectional   |
| ------------- | -------- | -------- | --------------- |
| 0 | B[0]  | Z  | FS[0]        |
| 1 | B[1]  | N  | FS[1]        |
| 2 | B[2]  | V  | FS[2]        |
| 3 | B[3]  | C  |         |
| 4 | A[0]  | Y[0]  |         |
| 5 | A[1]  | Y[1]  |         |
| 6 | A[2]  | Y[2]  |         |
| 7 | A[3]  | Y[3]  |         |


### Chip location

{{< shuttle-map "tt06" "557" >}}
