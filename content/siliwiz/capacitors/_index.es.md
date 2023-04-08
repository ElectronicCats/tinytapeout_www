---
title: Diseñando capacitores
description: "Entender cómo cambia la capacitancia y usar DRC para verificar su diseño"
weight: 40
---

### Objetivo

*  Entender que la capacitancia cambia con el área y la distancia
*  Investigar la capacitancia entre objetos en la misma capa
*  Crear capacitores usando la capa **mimcap**
*  Aprender cómo obtener la mayor capacitancia
*  Verifique su diseño usando el DRC

Hemos dado cuenta de un ejemplo de capacitancia parasitaria: ahora dibujemos intencionalmente un capacitor y veamos cuánto valor podemos crear.

Como se mencionó, un capacitor se forma cuando tenemos 2 formas conductivas separadas por un espacio no conductivo. Intentemos dibujar un capacitor con la capa **metal2**.

![](/images/siliwiz/image8.png)

Use la casilla SPICE para ver la capacitancia. Estás buscando una línea que se vea como **C0 out in** y luego algunos números. Obtuve 0.73fF. La F significa Faradios, la unidad de capacitancia. La f significa femto, ¡hay 1,000,000,000,000,000 femto Faradios en un Faradio! ¡Así que este es un capacitor muy pequeño!

Haga un intento de hacer un valor más grande de capacitor. Con resistencias, una forma larga y delgada ondulada hace una gran resistencia. Con un capacitor, queremos la mayor área. Lo más grande que pude lograr usando solo **metal2** fue 14fF.

### Usando más de 1 capa

Ahora intentemos usar 2 capas, **metal1** y **metal2**. ¿Crees que podremos hacer un capacitor más grande?

![](/images/siliwiz/image15.png)

Yo pensé que mi capacitor sería más grande, pero solo pude lograr 0.22fF. La razón por la que este capacitor no es tan grande como el de **metal2** es que la distancia entre **metal1** y **metal2** es grande en comparación con la brecha que podemos crear en una sola capa. Esto se puede ver si observa la ecuación de la capacitancia de dos placas paralelas:

![](/images/siliwiz/image1.png)

Donde C es la capacitancia, ε es la constante dieléctrica, A es el área de superposición entre sus capas y d es la distancia entre las capas. Cuando aumenta la distancia d entre capas, la capacitancia disminuye.

Los chips no tienen mucho espacio, por lo que hacer capacitores grandes en un chip es difícil. Es por eso que a menudo necesitamos usar capacitores fuera del chip si queremos capacitores realmente grandes.

![](/images/siliwiz/image44.png)

Sin embargo, tenemos una manera de hacer capacitores mejores, y eso es usando la capa **mimcap**. mim significa "metal insulator metal" y es una capa de metal especial que está mucho más cerca de **metal1** que **metal2**.

![](/images/siliwiz/image26.png)

Porque solo podemos poner etiquetas en las capas **metal1** y **metal2**, también necesitamos un **metal2 via** para conectar la capa **metal2** a la capa **mimcap**.

### Ejecute DRC

Dibuja un cuadrado de **metal1** y encima de eso un cuadrado de **mimcap**. Echa un vistazo al informe DRC (debajo de la sección transversal):

![](/images/siliwiz/image64.png)

DRC significa [Design Rule Check](https://www.zerotoasiccourse.com/terminology/drc/). No podemos dibujar lo que queramos y tenerlo hecho en un chip. Una gran parte del PDK incluye reglas DRC que aseguran que solo enviamos diseños a la fábrica que puedan hacer realmente.

Si hace clic en el error, resaltará el problema en el lienzo. Seleccione **metal1** nuevamente y dibuje un cuadrado más grande para que se extienda un poco en todos los lados de la capa **mimcap**. El error desaparecerá cuando se resuelva.

### Capacitancia máxima

Ahora que tenemos un capacitor entre las capas **mimcap** y **metal1**, conectemos las puertas de entrada y salida. Para el **out**, puede agregar una etiqueta a la capa **metal1**. Para conectar un puerto a la capa **mimcap**, primero debe usar **metal2 via** y luego **metal2** encima de eso. Una vez que haya dibujado el cuadrado **metal2**, etiquételo como **in**.

![](/images/siliwiz/image6.png)![](/images/siliwiz/image45.png)

Usando la casilla de verificación SPICE, averigüe su nueva capacitancia. Logré 970fF con el de arriba, así que casi 5000 veces más grande que el que hay entre **metal1** y **metal2**.

¿Qué sucede con la curva de salida cuando hace que la entrada suba más rápido disminuyendo el tiempo de subida?

Ahora el capacitor es mucho más grande que el parasitario que hicimos al experimentar con el resistor en la lección 1, la salida cae mucho más lentamente. Tan lento que realmente no podemos verlo a menos que lo acerque mucho a la gráfica.

![](/images/siliwiz/image39.png)

### Pull down

Al conectar un resistor de **pull down** entre el capacitor y vss podemos drenarlo más rápido.

![](/images/siliwiz/image21.png)

Si no recuerdas cómo hicimos un resistor, [vuelve y echa un vistazo](/es/siliwiz/resistors/#conéctalo). Luego siga estos pasos y vea si puede dibujarlo usted mismo.

1. Dibuja un cuadrado de **metal1 via** para que se conecte al cuadrado de salida **metal1**
2. Dibuja un resistor delgado usando **polyres** - tal vez hazlo de unos 0.5μm de grosor y 20μm de largo.
3. Use otro **metal1 via** en el extremo del resistor
4. Dibuja un cuadrado de **metal1** encima del **metal1 via**
5. Etiqueta el cuadrado **metal1** como **vss**.

![](/images/siliwiz/image38.png)![](/images/siliwiz/image27.png)

Ahora deberías ver la tensión de salida haciendo algo diferente. Si acercamos un poco la gráfica podemos verlo más claramente.

![](/images/siliwiz/image37.png)

Si tienes problemas, [aquí está mi solución](https://app.siliwiz.com/?preset=mimcap).

Experimenta con el tiempo de subida de la entrada, ¿qué sucede con el pulso de salida?

Un uso común para una combinación de un resistor y un capacitor es hacer un filtro. Podemos filtrar algunas frecuencias de las entradas y dejar otras.

Como lleva un tiempo específico para cargar y descargar, este circuito también se puede usar para construir un temporizador.
