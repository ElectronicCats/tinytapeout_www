---
title: Dibujar un MOSFET de tipo P
description: "Aprender sobre el complemento del MOSFET de tipo N, el MOSFET de tipo P"
weight: 70
---

### Objetivo

* Descubrir cómo un MOSFET de tipo P es el complemento de un MOSFET de tipo N
* Aprender que un MOSFET de tipo P necesita un pozo N para aislarlo del substrato P
* Comparar las características de los MOSFET de tipo N y de tipo P

Si cambiamos el tipo de difusión de la puerta y la fuente de tipo N a tipo P, y el cuerpo de tipo P a tipo N, hacemos un tipo de MOSFET que es el opuesto del tipo N que ya hemos visto. Esta versión de MOSFET se llama MOSFET de tipo P.

### Substrato P

Como el MOSFET N, necesitamos el **substrato P** con la conexión a vss.

![](/images/siliwiz/image33.png)

### Pozo N

El MOSFET de tipo N se construyó sobre el substrato de tipo P. Por lo tanto, durante el proceso de difusión N, cuando la puerta protege la región del canal, terminamos con un canal de tipo P. Para un MOSFET de tipo P, esto necesita ser cambiado: necesitamos un canal de tipo N que será protegido por la difusión de tipo P.

Para un MOSFET de tipo P, necesitamos crear una área profunda de difusión de tipo N en el substrato. Esto se llama pozo. La capa que necesitamos usar para dibujar esto se llama **pozo N**. Dibuja un cuadrado más pequeño en el centro usando la capa **pozo N**.

A continuación, dibuja la difusión de tipo P encima de eso usando la capa **difusión P**.

![](/images/siliwiz/image19.png)

El pozo N aísla la difusión P del substrato de tipo P. Se llama pozo porque es profundo, más profundo que las capas de difusión utilizadas para construir la puerta y la fuente del MOSFET.

Una pregunta que puede tener es por qué no usar una capa de difusión N en lugar de una capa de difusión P. Recuerde que la difusión P es nuestra lámina donde se fabricarán todos nuestros dispositivos utilizando fotolitografía. El uso del pozo N nos permite fabricar MOSFET de tipo P mientras mantenemos el material en masa, la lámina de tipo P, igual.

### Tapa de pozo

Al igual que el substrato P necesita estar conectado a vss, necesitamos conectar el **pozo N** a vdd. Use la tapa N, **metal1 via** y **metal1** para hacerlo.

![](/images/siliwiz/image42.png)

### Conéctalo

Conecta la compuerta, la fuente y el drenaje como lo hiciste para el MOSFET de tipo N. Esta vez, la fuente está conectada a vdd y el drenaje a vss.

![](/images/siliwiz/image46.png)

Como antes, elimina la traza **out**, y agrega **i(vdd)\*-1000**.

![](/images/siliwiz/image58.png)

Puedes ver [mi solución aquí](https://app.siliwiz.com/?preset=pmosfet).

### MOSFET de tipo N vs de tipo P

¿Qué notas entre los MOSFET de tipo N y de tipo P? La primera es la trama para N y en la segunda es para P.

![](/images/siliwiz/image41.png)![](/images/siliwiz/image47.png)

* ¿Qué MOSFET conduce mejor?
* Si cambia el tamaño de la capa **difusión P** del MOSFET P, ¿puede mejorar su rendimiento?
* ¿Tienen el mismo umbral de compuerta-fuente?

{{% notice tip %}}
El MOSFET N conduce aproximadamente 2.6 veces mejor que el MOSFET P.

Dibujar un MOSFET P 2.6 veces más ancho que el MOSFET N le dará el mismo rendimiento que el MOSFET N.

Explicación: esto se debe a que la dopaje de tipo N tiene exceso de electrones, que transportan la corriente, en comparación con la dopaje de tipo P que tiene vacíos entre los electrones, y el movimiento de estos "agujeros" de electrones es lo que transporta la corriente. Esto es análogo a que el agua cae rápidamente a través del aire, en comparación con una burbuja de aire que se eleva mucho más lentamente a través del agua. (Explicación alternativa: los automóviles que circulan por una carretera vs un atasco de tráfico donde el vacío entre los automóviles se mueve hacia atrás mientras los automóviles se mueven lentamente hacia adelante).
{{% /notice %}}
