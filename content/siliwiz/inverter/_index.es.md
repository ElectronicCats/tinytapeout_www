---
title: Creando un inversor lógico
description: "Crear una puerta lógica y descubrir sus limitaciones"
weight: 60
---

### Objetivo

* Aprender cómo una combinación de un resistor y un MOSFET puede crear un inversor
* Descubrir las limitaciones de este tipo de inversor
* Medir el consumo de corriente de un inversor NMOS

Un inversor lógico tiene una entrada y una salida. Si la entrada es baja, la salida debe ser alta, y si la entrada es alta, la salida debe ser baja.

<br>

| Entrada | Salida  |
|---------|---------|
| 0       | 1       | 
| 1       | 0       | 

### NMOS

Podemos construir un inversor lógico con un MOSFET de tipo N y un resistor de pull up. Este tipo de inversor se llama inversor NMOS.

![](/images/siliwiz/image32.png)

Si la entrada es baja, la puerta no está cargada y el corriente no fluye a través del MOSFET. El resistor eleva la salida para hacerla alta.

Si la entrada es alta, la puerta está cargada y el MOSFET conduce. Esto baja la salida.

### Dibujar un inversor NMOS

Vea si puede dibujar este inversor usando las habilidades que ya ha aprendido. Aquí está [mi solución](https://app.siliwiz.com/?preset=nmos):

![](/images/siliwiz/image30.png)

Una vez que esté conectado correctamente, seleccione la pestaña **simulation** y debería ver un resultado de simulación como este. Necesitarás las trazas de **in** y **out**.

![](/images/siliwiz/image17.png)

Puede ver que cuando la entrada es baja, la salida es alta. Una vez que la tensión de la puerta llega a aproximadamente 1.5v, la salida ya está cayendo. Y una vez que la tensión es de aproximadamente 2.5v, la salida es menos de 1v.

La desventaja con la lógica NMOS es que los resistores de pullup desperdician un poco de corriente cuando el transistor está encendido.

### Medir el consumo de corriente de un inversor NMOS

Como antes, agregue **i(vdd)\*-1000** a la lista de señales a ser trazadas.

![](/images/siliwiz/image61.png)

Ahora podemos ver que cuando la entrada es baja, el uso de corriente es bajo, pero una vez que encendemos el MOSFET, estamos conectando el resistor a vss, y esto consume corriente.

Intente cambiar el ancho de la puerta y el ancho del resistor. ¿Puede hacer que el inversor cambie más rápido? ¿Y hacerlo más eficiente?

Si tiene millones de estos inversores lógicos, está desperdiciando electricidad como calor y sus chips se calientan y se ralentizan. [CMOS](https://www.zerotoasiccourse.com/terminology/cmos) fue inventado para resolver esta limitación.

En la próxima lección aprenderá cómo dibujar un MOSFET de tipo P, y luego tendrá todo lo que necesita para hacer su propio inversor CMOS.
