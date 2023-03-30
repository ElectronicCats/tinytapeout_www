---
title: Diseñando una resistencia
description: "Aprende los conceptos básicos de SiliWiz mientras creas un componente"
weight: 20
---

### Objetivo

* Aprende los conceptos básicos de SiliWiz
* Cómo dibujar formas básicas y etiquetar terminales
* Entender la vista de sección transversal
* Entender cómo leer la gráfica de simulación
* Entender cómo cambia la resistencia con la forma
* Dónde obtener ayuda

A continuación se muestra una descripción general de la interfaz de usuario de SiliWiz:

![](/images/siliwiz/image54.png)

### ¡Dibuja algunas formas!

Elija qué capa dibujar usando la paleta. Al final de estas lecciones, sabrá qué es cada capa y qué papel juega en la construcción de una puerta lógica.

Vaya a la [página de SiliWiz](https://app.siliwiz.com/?preset=blank), seleccione la capa **polyres** y luego dibuje la primera letra de su nombre en el lienzo.

* Controla qué capas son visibles con el 👁
* Elija qué capa está activa haciendo clic en el color o el texto
* Pase el mouse sobre el texto para obtener una breve descripción del propósito de la capa

![](/images/siliwiz/image59.png)

* Prueba los botones Deshacer ↶ y Rehacer ↷
* El botón Borrar borra todo
* Puede descargar su diseño con el botón Guardar
* Puede cargar un diseño guardado con el botón Cargar

### Capas

Cuando una fábrica desarrolla una forma de hacer un chip, necesita compartir esa información con los diseñadores de chips: ¡tú!

{{% notice tip %}}
Normalmente, necesitarías firmar un documento para decir que no compartirías la información. Con el [PDK](https://www.zerotoasiccourse.com/terminology/pdk/) de código abierto, no necesitas firmar ningún documento antes de comenzar a usarlo.
{{% /notice %}}

Aquí están las capas que se usan para hacer un chip en el proceso de 130 nm de Skywater. Un nanómetro es 1 millón de veces más pequeño que un milímetro. Por lo tanto, el punto al final de esta oración podría ser fácilmente un millón de nanómetros de ancho. Tenga en cuenta que las cifras mostradas en la imagen están en micrómetros (μm).

![](/images/siliwiz/image49.png)

### Pila de SiliWiz

Esta es una pila bastante complicada, por lo que estamos usando una más simple, hecha a medida para SiliWiz. Esto ayuda a mantener las cosas asequibles y rápidas. Tenga en cuenta que un PDK real y fabricable tiene [muchas más capas](https://skywater-pdk.readthedocs.io/en/main/rules/masks.html). La pila de capas de SiliWiz se ve así:

![](/images/siliwiz/image31.png)

{{%expand "¿Te sientes aventurero?" %}}
Si te sientes aventurero, ¡puedes echar un vistazo a la [tech](https://app.siliwiz.com/assets/siliwiz.tech) para el archivo tech y muchas otras cosas!
{{% /expand%}}

Después de que hayamos terminado nuestro diseño, podemos convertir cada capa en una máscara. Una máscara permite que la luz pase por las áreas que coloreamos en las capas. Las máscaras se usan en un proceso llamado fotolitografía.

![](/images/siliwiz/image7.png)

[La fotolitografía](https://www.zerotoasiccourse.com/terminology/photolithography/) es el paso clave que nos permite tomar los patrones que creamos en una herramienta como SiliWiz y miniaturizarlos hasta el nivel de nanómetros. También nos permite colocar fácilmente el mismo diseño sobre la lámina de silicio para hacer los chips individuales. Nos permite usar una imagen preparada del chip para hacer millones de copias de forma confiable y rápida.

{{% notice tip %}}
Algunas capas son "virtuales". Por ejemplo, **polyres** y **polisilicio** son la misma capa física, pero necesitamos tenerlas divididas en 2 capas separadas para que la simulación sepa si queremos dibujar la puerta de un [MOSFET](https://www.zerotoasiccourse.com/terminology/mosfet/), o dibujar un resistor.
{{% /notice %}}

### ¿Qué resistencia tiene tu inicial?

Ahora que hemos dibujado una forma, podemos ejecutar una simulación y averiguar cuán resistente es la letra. La resistencia se mide en [Ohms](https://es.wikipedia.org/wiki/Ohmio). Un resistor es un elemento de circuito con 2 puertos. Cuanto mayor sea la resistencia, más difícil será mover la electricidad a través de él.

La resistencia del polisilicio es proporcional a la superficie transversal y la longitud.

![](/images/siliwiz/image53.png)

En un PDK, no podemos controlar la altura de las capas, la fábrica ya lo ha decidido. En su lugar, podemos controlar el ancho y la longitud. Por lo tanto, si dibuja una forma larga y delgada, tendrá una resistencia más alta, y una forma corta y gorda tendrá una resistencia más baja. Nuestra capa **polyres** tiene una resistencia de 400 ohms por micrómetro cuadrado (μm). Hay 1000 micrómetros en un milímetro.

* Un cuadrado de 1μm x 1μm debería tener 400 Ohms de resistencia.
* Un rectángulo largo y delgado de 10μm de largo x 1μm de ancho debería tener 4000 Ohms de resistencia.
* ¿Cuántos Ohms debería tener un cuadrado de 10μm x 10μm? Debido a que es 10 veces más ancho que el delgado, tendrá 10 veces menos resistencia, por lo que debería ser de 400 Ohms.

Mira tu dibujo, ¿puedes predecir la resistencia?

### Conéctalo

Para medir la resistencia, necesitamos conectar 2 partes de tu inicial a algunos puertos de entrada y salida.

Solo podemos hacer puertos en las capas **metal1** y **metal2**. Si miras el stackup, **metal1** y **metal2** no tocan la capa **polyres**. Primero usamos un **metal1 via** para unir **metal1** y la capa polyres.

Selecciona la capa **metal1 via** y agrega dos vias a tu inicial hecho en **polyres**.

Así es como se ve **metal1 via** desde arriba en mi letra:

![](/images/siliwiz/image16.png)

Y así es como se ve en la vista de sección transversal. Asegúrate de haber seleccionado la pestaña de sección transversal.

![](/images/siliwiz/image52.png)

Arrastra el control deslizante de la sección transversal hacia arriba y hacia abajo para que puedas ver las capas claramente. Si pasas el cursor sobre una forma en la sección transversal, obtendrás un mensaje emergente para decirte el nombre de la capa.

* * *

Ahora agrega 2 **metal1** contactos encima del **metal1 via**. Para simular nuestro diseño, debemos decirle a SiliWiz que queremos que estos contactos sean los puertos de nuestro circuito. Para hacerlo, haz clic en cada contacto **metal1** y elige la opción ‘Set Label’. o S en el teclado.

![](/images/siliwiz/image9.png)

Establece las etiquetas como in y out. Tan pronto como lo hayas hecho, deberías ver que la gráfica de simulación se actualiza. Deberás cambiar de la sección transversal a la pestaña de simulación.

![](/images/siliwiz/image57.png)

![](/images/siliwiz/image63.png)

La abscisa de la gráfica es el tiempo, en microsegundos. Hay 1,000,000 de microsegundos en un segundo. La ordenada es el voltaje. El voltaje se mide en voltios y es la unidad que usamos cuando hablamos de la fuerza del campo eléctrico.

Los portadores de carga, como los electrones, son movidos por los campos eléctricos. Cuanto más fuerte sea el campo, más efecto tendrá sobre un electrón. Los electrones son las ‘partes móviles’ de las máquinas que construimos.

En esta gráfica hay 2 líneas, azul para in y naranja para out. Están justo encima de la otra, por lo que parece que solo hay una línea. Prueba los controles deslizantes para ver cómo afecta la gráfica.

![](/images/siliwiz/image5.png)

Lo que muestra la gráfica es que el voltaje de salida es el mismo que el voltaje de entrada. El voltaje de entrada varía con el tiempo, lo que puedes controlar con los controles deslizantes.

### Añádele un toque especial

Ahora veremos otra parte de SiliWiz para determinar la resistencia de nuestro diseño **polyres**.

Marca la casilla Mostrar SPICE en la parte inferior de la página y echa un vistazo en el cuadro de texto. Busca una línea que diga R0 in out y luego algunos números. ¡Mi letra M tiene una resistencia de 5575 ohmos! ¡Genial! Yo dibujé mi propio resistor.

![](/images/siliwiz/image4.png)

{{% notice tip %}}
Hay mucho que hacer en el archivo [SPICE](https://www.zerotoasiccourse.com/terminology/spice/), pero en estas lecciones lo ignoraremos en su mayoría. SPICE es una parte importante del kit de herramientas de un diseñador de chips. [ngspice](https://ngspice.sourceforge.io/) es la herramienta de código abierto que ejecuta las simulaciones SPICE para SiliWiz. Gracias a [Holger Vogt](https://www.linkedin.com/in/holger-vogt-737ba5a8/) por hacernos una versión especial pequeña.
{{% /notice %}}

Intenta hacer que tu letra tenga una resistencia más alta o más baja. Aquí estoy haciendo una resistencia muy alta:

![](/images/siliwiz/image3.png)

¡Obtuve 37,800 Ohms! ¿Puedes hacer una resistencia aún más alta?
