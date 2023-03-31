---
title: Parásitos
description: "Cómo obtenemos parásitos no deseados en los circuitos y qué significa eso"
weight: 30
---

### Objetivos

* Entiende qué significa parásito en microelectrónica
* Ver cómo obtenemos capacitancia y resistencia no deseadas en nuestros circuitos

¿Qué crees que pasará con la línea de salida naranja cuando elimines una parte de tu inicial? Haz una predicción. Para eliminar una parte, selecciónala y luego elige "eliminar" o presiona la tecla D.

¿Qué sucede? ¿Lo esperabas? Probablemente obtuviste algo como yo:

![](/images/siliwiz/image34.png)

La línea de entrada azul sigue haciendo lo que estaba haciendo, pero la salida naranja tiene una bonita curva ahora. Lo que está sucediendo es que incluso si no hay un circuito directo para que la electricidad fluya a través de tu letra, hemos hecho un pequeño condensador al tener 2 elementos conductores separados con un pequeño espacio no conductivo. Un condensador es un elemento de circuito con 2 puertos. El campo eléctrico entre los 2 elementos funciona para mantener la tensión a través de la placa igual. El condensador se carga a medida que la entrada sube, pero luego se desvanece lentamente hasta 0 una vez que la entrada deja de cambiar.

¿Qué sucede con la curva de salida cuando haces que la entrada suba más rápido disminuyendo el tiempo de subida?

### Capacitancia parásita

Este tipo de efecto se llama **capacitancia parásita**. No lo queríamos ni lo esperábamos, pero está ahí porque así es como funciona el mundo. Los parásitos a menudo son imperceptibles a una escala más grande, pero el condensador que acabas de hacer solo tiene 1μm de ancho y tiene un efecto notable en la salida de tu circuito. Analizar los parásitos es una parte importante de la microelectrónica y no se puede ignorar si queremos que nuestros chips funcionen correctamente.

### Resistencia parásita

¿Por qué el condensador se descargó a cero? ¡Porque también tiene una **resistencia parásita** que permite que la electricidad se escape!

