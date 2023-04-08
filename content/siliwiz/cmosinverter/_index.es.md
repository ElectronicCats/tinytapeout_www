---
title: Dibujar un inversor CMOS
description: "Entender el beneficio de CMOS y explorar celdas estándar"
weight: 80
---

### Objetivo

* Entender el beneficio de CMOS
* Aprender qué es una celda estándar
* Compare su diseño con la celda estándar Sky130
* Próximos pasos

Como hemos visto, un inversor NMOS es ineficiente porque está desperdiciando energía a través del resistor. La lógica CMOS reemplaza el resistor de pull up con un MOSFET de tipo P. Como el tipo P es la versión complementaria del tipo N, llamamos a este tipo de lógica Metal Oxida Complementario o CMOS por sus siglas en inglés.

![](/images/siliwiz/image35.png?width=20pc)

Hay muchas maneras de dibujar esto, pero es bastante habitual usar la misma pieza de polisilicio como puerta para ambos tipos P y N. Si se atasca, puede verificar [mi solución aquí](https://app.siliwiz.com/?preset=inverter).

![](/images/siliwiz/image56.png)

Y la simulación muestra que el inversor CMOS está funcionando bien:

![](/images/siliwiz/image40.png)

También agregué la corriente en las trazas de simulación. Puede ver que obtenemos un pequeño pico cuando el inversor opera, pero en cualquiera de los estados altos o bajos, la corriente es muy baja. Esta eficiencia es la razón por la cual CMOS sigue siendo el tipo de puertas lógicas más comúnmente utilizado en las computadoras.

### Celdas estándar

Hemos visto cómo dibujar y hacer un inversor lógico, pero hay muchos otros tipos de puertas lógicas como AND, OR y NOT. ¡Siéntase libre de intentar dibujar algunos por su cuenta! Comparta sus diseños con nosotros en el [canal de la comunidad de Discord](https://discord.gg/e3FK68Z98y). Use el hashtag [#SilliWiz](https://twitter.com/search?q=siliwiz&src=typed_query) en las redes sociales.

Una PDK típica incluirá cientos de celdas estándar. Aquí está el inversor estándar de Skywater 130nm:

![](/images/siliwiz/image62.png)

¿Puede identificar los MOSFET de tipo P y N? ¿Puede ver las puertas de entrada y salida? [Aquí está una vista en 3D](https://gds-viewer.tinytapeout.com/?model=https://tinytapeout.github.io/sky130B-cells-gltf/cells/sky130_fd_sc_hd__inv_1.gds.gltf) de la misma celda:

![](/images/siliwiz/image18.png)

Una cosa que hace que las celdas estándar sean estándar es que todas tienen la misma altura y la parte superior e inferior siempre incluye la fuente de alimentación vdd y vss. Esto nos permite poner muchas celdas juntas en una cuadrícula.

Aquí está una vista en 3D de algunas celdas estándar juntas, alimentadas por las líneas azules vss y vdd.

![](/images/siliwiz/image11.png)

¿Puede encontrar un inversor?

Y aquí vemos cómo los cables conectan las celdas en una máquina digital más compleja:

![](/images/siliwiz/image43.png)

Si desea explorar este diseño por su cuenta:

* [aquí está el visor 3D](https://gds-viewer.tinytapeout.com/?model=https://tinytapeout.github.io/tt02-test-invert/tinytapeout.gds.gltf)
* [el diseño lógico](https://wokwi.com/projects/341535056611770964)
* [más información sobre el diseño](https://tinytapeout.com/runs/tt02/000/)

### ¿Qué sigue?

[¡Deje su opinión!](https://forms.gle/fY5phQRc2dnzBRmf9) Háganos saber sus pensamientos e ideas para mejorar. También puede usar este formulario para solicitar más información sobre SiliWiz y TinyTapeout para escuelas y universidades.

* Comparta una foto de su diseño en las redes sociales con el [#SiliWiz hashtag](https://twitter.com/search?q=siliwiz&src=typed_query)
* [¡Aprenda a usar puertas lógicas para construir circuitos simples y obtenerlos fabricados!](http://tinytapeout.com/es/)
* [¡Tome el curso avanzado de Matt Zero to ASIC!](https://zerotoasiccourse.com)
* Intente dibujar diagramas de palos con [Stixu](https://stixu.io/)
* [Mira videos en el canal de youtube del curso Zero to ASIC](https://youtube.com/zerotoasic)
* [Regístrese en la lista de correo](https://zerotoasiccourse.com/newsletter)
* [Únase a la comunidad de discord](https://discord.gg/e3FK68Z98y), ¡y háganos saber qué piensa de SiliWiz!
* [Contribuya a SiliWiz](https://github.com/wokwi/siliwiz/issues)

Gracias y créditos
------------------

SiliWiz es un proyecto de [Matt Venn](https://mattvenn.net/). Gracias a todos los probadores y en particular a:

* Tim Edwards y Holger Vogt por ayudar a crear SiliWiz,
* Eric Smith y Thomas Parry por ideas de lecciones y revisión.
