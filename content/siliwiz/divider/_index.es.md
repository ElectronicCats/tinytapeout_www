---
title: Divisor de Voltaje
description: "Divide un número con 2 resistencias"
weight: 35
---

### Objetivo

* Hacer algo útil
* Demostrar algunas limitaciones de la extracción de circuitos
* Hacer algunas mediciones en la gráfica

En la lección anterior aprendiste los conceptos básicos de SiliWiz. Ahora vamos a poner ese conocimiento en práctica y construir una pequeña máquina de calcular en un chip de silicio. Vamos a construir un divisor de potencial. Esto toma una tensión en, la divide y nos da la respuesta.

![](/images/siliwiz/image55.png?width=20pc)

¿Cuántas conexiones tiene este dispositivo? Necesitamos una para in y out como antes, y vamos a agregar una nueva llamada **vss**. vss también se llama tierra o 0v. Se usa como referencia para el resto del circuito.

Vamos a intentar hacer un divisor de potencial que divida por 2. Entonces, si 4v entra, entonces 2v deberían salir. Eso es realmente fácil, todo lo que necesitamos es hacer que las 2 resistencias tengan la misma resistencia.

Si la tensión de entrada se ve así:

![](/images/siliwiz/image20.png)

¿Qué crees que la tensión de salida debería verse? **Haz una predicción y ve si tienes razón después de haber dibujado el divisor.**

Hay muchas maneras de dibujarlo, pero al menos necesitarás:

* 3 cuadrados **metal1**, etiquetados in, out y vss
* 3 **metal1 vias** para conectar entre **metal1** y **polyres**
* 2 resistores hechos de **polyres** que están unidos entre las 3 conexiones.

### ¿Cómo funciona? ¡Magia!

Otro importante herramienta detrás de las escenas de SiliWiz se llama [Magic](https://www.zerotoasiccourse.com/terminology/magic/). ¡Es una herramienta poderosa pero no es muy amigable para principiantes, lo que es una razón por la que queríamos hacer SiliWiz. Magic ha sido utilizado durante 40 años para ayudar a diseñar chips! ¡Lo estamos usando para [DRC](https://www.zerotoasiccourse.com/terminology/drc/) y [extracción de circuitos](https://www.zerotoasiccourse.com/terminology/pex/).

Como se mencionó anteriormente, tenemos dos capas que en realidad especifican el mismo material, polisilicio y polyres. No hay diferencia entre las dos capas cuando el chip se fabrica. La razón por la que los mantenemos separados es para que el trabajo de Magic sea más fácil cuando extrae el circuito de la imagen que dibujamos.

Una limitación que puede encontrarse al dibujar el divisor es que Magic no puede decir que esto son dos resistencias separadas. Extrae solo una resistencia entre las primeras 2 conexiones.

![](/images/siliwiz/image22.png)![](/images/siliwiz/image24.png)

Tienes que dibujar 2 rectángulos separados, uno para cada resistor:

![](/images/siliwiz/image13.png)

Una vez que su divisor esté terminado, debería ver una simulación como esta:

![](/images/siliwiz/image36.png)

Juega con los controles de simulación para cambiar el min, max y tiempo de subida de la señal de entrada.

* ¿Qué tan cerca está su divisor de dividir la tensión de entrada por 2? ¿Puedes medir cuán preciso es?
* ¿Cómo podrías hacer que el divisor sea más preciso?
* ¿Qué es mejor, formas grandes o pequeñas?
* ¿Puedes hacer un divisor de potencial por 3?

### Solución

Si tienes problemas, [revisa mi solución](https://siliwiz.pages.dev/?preset=resistor).
