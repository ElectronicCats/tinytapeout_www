---
hidden: true
title: "162 RGB Mixer"
weight: 67
---

## 162 : RGB Mixer

* Author: Zhe Wang
* Description: Zero to ASIC demo project
* [GitHub repository](https://github.com/zhwa/zeroasic)
* [GDS submitted](https://github.com/zhwa/zeroasic/actions/runs/8593557831)
* HDL project
* [Extra docs]()
* Clock: 10000000 Hz

<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->


### How it works

Debounce the inputs, drive an encoder module, and output a PWM signal for each encoder.

### How to test

Twist each encoder and the LEDs attached to the outputs should change in brightness.

### External hardware

Use 3 digital encoders attached to the first 6 inputs.


### IO

| #             | Input    | Output   | Bidirectional   |
| ------------- | -------- | -------- | --------------- |
| 0 | enc0 a  | pwm0  |         |
| 1 | enc0 b  | pwm1  |         |
| 2 | enc1 a  | pwm2  |         |
| 3 | enc1 b  |   |         |
| 4 | enc2 a  |   |         |
| 5 | enc2 b  |   |         |
| 6 |   |   |         |
| 7 |   |   |         |


### Chip location

{{< shuttle-map "tt06" "162" >}}
