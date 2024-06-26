---
hidden: true
title: "267 Current Mode Trigger"
weight: 118
---

## 267 : Current Mode Trigger

* Author: Alfiero Leoni
* Description: Hysteresis Trigger working with input currents
* [GitHub repository](https://github.com/alfiero88/tt07-current-mode-trigger)
* [GDS submitted](https://github.com/alfiero88/tt07-current-mode-trigger/actions/runs/9319952670)
* Analog project
* [Extra docs]()
* Clock: 0 Hz

<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->


### How it works

The current mode trigger is a Schmitt trigger, therefore with hysteresis, that takes currents as input instead of voltages and produces a digital output that rises from 0 to 1 when the input current overcomes the first threshold and falls from 1 to 0 when the current falls below the second threshold. The hysteresis thresholds are internally set with reference currents. In particular, the rising edge current threshold is fixed, while the falling edge trigger can be adjusted by means of an external voltage reference. The current mode trigger is useful to detect signals coming from devices that work in current mode, such as photodiodes, SPADs, and Silicon photomultipliers. The latter represents an emerging technology for LIDAR systems, medical diagnosis, and particle physics detection systems, where even a single photon can be detected and converted into a photocurrent. In this sense, the current mode trigger can quickly detect a rare event of specific particle detection, as in the experiments for Dark Matter research.

### How to test

The trigger can be tested with current input signal (such as a triangular wave) and the output should be monitored to look for digital transitions. A reference voltage of 0.9 V should be applied to teh vref pin, while the falling threshould can be set by applying a voltage between 1.45 and 1.55V to the vgf pin.

### External hardware

A Current signal generator is needed, such as the keithley 2450 Sourcemeter or any equivalent SMU, to produce the input signal. As an alternative, a current could be generated by means of a voltage source with a series resistance. In any case, the input current range should be around tens of microAmperes. A tunable Voltage supply is needed to produce the voltage references and a fast oscilloscope can be used to monitor the trigger output


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

### Analog pins

| `ua`#        | `analog`#        | Description         |
| ------------ | ---------------- | ------------------- |
| 0 | 6 | input           |
| 1 | 7 | input           |
| 2 | 9 | output           |
| 3 | 8 | input           |

### Chip location

{{< shuttle-map "tt07" "267" >}}