---
title: Dibuja un MOSFET N
description: "Componentes activos: dibuja un MOSFET y realiza mediciones"
weight: 50
---

### Objetivo

* Introducir MOSFETs como un ejemplo de un componente activo
* Dibujar un MOSFET
* Graficar la curva VGS
* Medir el voltaje de umbral de la puerta

Hasta ahora nos hemos familiarizado con SiliWiz dibujando componentes pasivos. Los componentes pasivos almacenan o usan energía. Los componentes activos pueden controlar el flujo de electricidad, y estos son la clave para construir circuitos más complejos como amplificadores o puertas lógicas.

En esta lección aprenderemos a dibujar un [MOSFET](https://www.zerotoasiccourse.com/terminology/mosfet/). MOSFET significa Metal Oxide Semiconductor Field Effect Transistor.

Un MOSFET es un componente activo con 4 puertos: compuerta, drenaje, fuente y cuerpo.

![](/images/siliwiz/image10.png)

La compuerta se formaba colocando metal sobre una capa aislante de óxido, eso es el MO en MOSFET.

![](/images/siliwiz/image51.png)

Cuando se aplica una tensión entre la compuerta y el cuerpo, se forma un campo eléctrico en el canal. Este campo atrae a los portadores de carga a la región del canal donde pueden trabajar para conducir electricidad. Eso es el FE en MOSFET.

En un MOSFET de tipo N construido en un substrato de tipo P, los portadores de carga mayoritarios son los huecos, y son los portadores minoritarios (los electrones) los que se atraen a la compuerta y forman el canal conductivo entre el drenaje y la fuente.

Eso describe lo que está sucediendo físicamente dentro de un transistor. Si eso no tiene sentido total, no te preocupes. Cómo funciona un MOSFET se hará más claro una vez que comencemos a hacer uno.

### ¡Empecemos a dibujar!

Hasta ahora, hemos estado ignorando la capa base de una placa de silicio. En la mayoría de los casos, esta es una lámina de silicio P [dopada](https://www.zerotoasiccourse.com/terminology/doping/). En lugar de ser silicio puro, tiene una pequeña cantidad de impurezas agregadas para aumentar la conductividad de la lámina, cambiando de aislante a semi-conductor.

Selecciona la capa **p substrate** y dibuja un cuadrado que llene todo el lienzo.

![](/images/siliwiz/image12.png)

El **p substrate** debe conectarse a **vss**. Para hacer eso usamos una área ligeramente dopada de p, llamada **p tap**.

**p tap** es diferente a las capas que ya hemos visto. En lugar de construirse sobre el substrato, se forma dentro del substrato. La máscara se usa como antes, pero en lugar de construir una nueva capa de metal o polisilicio, estamos implantando átomos de un semiconductor de tipo P, por ejemplo Boro.

En la esquina dibuja un pequeño cuadrado de **p tap**. Luego lo conectamos a través de un **metal1 via** a un contacto **metal1** etiquetado **vss**.

![](/images/siliwiz/image33.png)

A continuación, seleccione la capa **n diffusion** y dibuje un cuadrado en el medio. Esto formará tanto el drenaje como la fuente del MOSFET. Al igual que la capa **p tap**, **n diffusion** se forma dentro del **p substrate**, pero usando átomos de un semiconductor de tipo N como el Arsénico.

![](/images/siliwiz/image14.png)

El siguiente paso es dibujar la compuerta. Los MOSFET solían tener su compuerta dibujada con metal, pero ahora la compuerta es mucho más comúnmente hecha de polisilicio. Use la capa **polysilicon** para dibujar la compuerta.

![](/images/siliwiz/image50.png)

Mira la sección transversal - ¡la **n diffusion** se dividió! Ahora tenemos 2 secciones **n type** con un **p type** entre medio. ¿Qué pasó?

### Difusión dividida

Podríamos haber dibujado la compuerta primero y luego la difusión, pero dibujar la difusión primero nos permite alinear más fácilmente la compuerta en el medio. Cuando se hace la placa, la compuerta se coloca primero y luego se usa la máscara de difusión. La compuerta protege el substrato P de la difusión de tipo N, por lo que terminamos con 2 regiones de tipo N y una región de P en el medio.
Esto es esencialmente todo lo que necesitamos para un MOSFET, y si miras el archivo SPICE verás que se ha detectado y extraído un “nmos” por Magic.

![](/images/siliwiz/image25.png)

Sin embargo, para ver cómo funciona nuestro MOSFET, necesitamos conectar la compuerta, el drenaje y la fuente. El cuerpo es el **p substrate**, y ya lo hemos conectado a vss.

### Drenaje, fuente y compuerta

Necesitamos dibujar las capas para conectar la compuerta, el drenaje y la fuente del MOSFET a contactos en **metal1**. Para esto, usaremos 3 **metal1 via**.

![](/images/siliwiz/image48.png)

El **polysilicon** rojo forma la compuerta, pero ¿en qué orden está la fuente y el drenaje? ¡La sección transversal muestra que el MOSFET es simétrico!

Para que un MOSFET de tipo N funcione, el cuerpo necesita mantenerse en el mismo o menor voltaje que uno de los terminales restantes. Normalmente hacemos esto conectando uno de los terminales a la misma tensión que el cuerpo, y históricamente, este terminal se llama fuente. El otro se convierte en el drenaje.

Etiqueta la compuerta **in**, la fuente **vss** y el drenaje **vdd**. Ya hemos conectado el cuerpo a vss. Si te atascas, consulta [mi solución aquí](http://app.siliwiz.com/?preset=nmosfet).

![](/images/siliwiz/image28.png?width=20pc)

### Curvas VGS

En este experimento, veremos lo que sucede cuando aumentamos la tensión de la compuerta de 0v a 5v y medimos la corriente que fluye de vdd a vss. La corriente es una medida de cuántos portadores de carga fluyen por segundo, nos dice cuán “encendido” está el MOSFET. La corriente se mide en [Amps](https://en.wikipedia.org/wiki/Ampere).

Este es uno de los experimentos más importantes que podemos hacer con un MOSFET, y nos ayudará a comprender cómo funcionan en los próximos ejercicios.

En la pestaña de simulación, busque las señales de la gráfica:

![](/images/siliwiz/image29.png)

Haga clic en la x de out para eliminarla y luego haga clic en el botón + para agregar una nueva traza. Escriba **i(vdd)\*-1000**

La i(vdd) significa trazar la corriente en lugar de la tensión. El \*-1000 significa magnificar la señal por -1000 veces. Esto hace que la señal se vea mucho más grande y la invierte. Esto es solo para que se vea como en todos los libros de texto.

![](/images/siliwiz/image23.png)

¿Qué nos muestra el gráfico? Para empezar, cuando la compuerta es inferior a unos 1 volt, no fluye corriente. El MOSFET está apagado. Una vez que pasamos un umbral, el MOSFET comienza a conducir y permite que fluya más y más corriente. Este valor se llama umbral de compuerta-fuente.

Intente cambiar el ancho de la compuerta del MOSFET y vea cómo afecta a la curva. Si queremos que fluya más corriente en la región de saturación, ¿deberíamos usar una compuerta delgada o gruesa?

Si amplía la gráfica, ¿puede medir qué tensión de compuerta es necesaria para que el MOSFET comience a conducir?
