---
hidden: true
title: "33 Asynchronous Down Counter"
weight: 215
---

## 33 : Asynchronous Down Counter

* Author: Alen Music
* Description: Counter
* [GitHub repository](https://github.com/AlenMusic12/jku-tt06-downcounter)
* [GDS submitted](https://github.com/AlenMusic12/jku-tt06-downcounter/actions/runs/8630006877)
* [Wokwi](https://wokwi.com/projects/384437973887503361) project
* [Extra docs]()
* Clock: 0 Hz

<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->


### How it works

The Project is a Asynchronous 3 Bit Down Counter.In the asynchronous counter, an external clock pulse is provided for only the first Flip-Flop, thereafter the output of the 1st Flip-Flop acts as a clock pulse for the second Flip-Flop and so on. In the case of synchronous Flip-Flops, all
the Flip-Flops are triggered simultaneously by an external clock pulse.

### How to test

Pressing the button in succession will make the counter count.

### External hardware

7SEG-Display


### IO

| #             | Input    | Output   | Bidirectional   |
| ------------- | -------- | -------- | --------------- |
| 0 |   |   |         |
| 1 |   |   |         |
| 2 |   |   |         |
| 3 |   |   |         |
| 4 |   |   |         |
| 5 |   |   |         |
| 6 |   |   |         |
| 7 |   |   |         |


### Chip location

{{< shuttle-map "tt06" "33" >}}
