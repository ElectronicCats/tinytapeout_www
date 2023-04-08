---
title: "De FPGA a ASIC"
description: "Consideraciones para personas que pasan de FPGA a ASIC"
---

# Reinicio

La mayoría de las FPGAs permiten declaraciones iniciales y los flops a menudo se inicializan en cero. Este no es el caso para las ASICs, donde los flops tendrán un valor aleatorio inicial al encenderse. Las declaraciones iniciales no están permitidas, así que debes usar un reinicio explícito.

{{< youtube 78MBLqm0OAQ >}}

# Combinacional vs Secuencial

En un FPGA, todos sus registros estan "libres", siendo que cada LUT tiene un flip-flop asignado, por lo mismo las personas estan acostumbradas a hacer flujos y registros grandes. Mas en un ASIC estas combinaciones de células son las mas "caras" en terminos de área, por lo que es mejor hacer uso de logica combinacional y solo usar flip-flops cuando sea necesario. Esto podría significar hacer más niveles profundos de lógica combinacional con menos flip-flops de por medio.

# Pruebas

Además de las pruebas funcionales con un simulador y un banco de pruebas, deberías considerar las pruebas a nivel de compuerta. Esto permite simular tu diseño real de tu GDS (post síntesis).

Puedes encontrar un ejemplo del [flujo de trabajo de Github action para la simulación a nivel de compuerta aquí](https://github.com/TinyTapeout/tt03-verilog-demo/blob/main/.github/workflows/gds.yaml#L99). Este se encarga de instalar los modelos para las células estándar.
