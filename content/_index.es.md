---
title: "Tiny Tapeout"
images: [/images/tinytapeout.jpeg]
LastModifierDisplayName: deimos hall
---

# ¡Desde una idea hasta el diseño de un chip en minutos!

{{< youtube fblSVCPvCiY >}}

TinyTapeout es un proyecto educativo que hace más fácil y barato que nunca obtener tus diseños manufacturados en un chip real. Consulta lo que otras personas están creando al ver [lo que se ha enviado en la última edición](/es/runs/tt02).

[**¡Ya están abiertas las inscripciones para Tiny Tapeout 3!**](/#submit-your-design)

<div x-data="checkout"> Actualmente hay 
<b x-text="stock['tt-asic-pcb']">...</b> espacios para Diseño + PCB + ASIC y <b x-text="stock['tt-design-only']">...</b> solo para Diseño disponibles</small>. 
</div>

{{<mermaid>}}
gantt
        dateFormat  YYYY-MM-DD
        axisFormat %d-%b
        section You
        Trabaja en tu diseño      :   active,2023-03-01,2023-04-01
        Envía tu diseño           :   active,2023-03-03,2023-04-01
        
        section Us
        Une todos los diseños     :   2023-04-01, 3d
        Envíalo a Efabless          :   2023-04-03, 1d
{{</mermaid>}}

> **Testimonio** Gracias por hacerlo - Siempre quise unirme a estos shuttles de OPenMPW, pero nunca me sentí listo. TinyTapeout me dió un camino para introducirme mientras solo dedicaba una tarde de esfuerzo. ¡Es increíble!

Mira [lo que dicen sobre TinyTapeout](https://twitter.com/search?q=tinytapeout)!

---

# Primeros pasos

* Si eres nuevo en el diseño digital - comienza tomando alguno de nuestras [lecciones aquí](/es/digital_design).
* Después crea tu propio diseño con la [plantilla Wokwi](https://wokwi.com/projects/357178660283991041) o para usuarios avanzados, con [un HDL](/es/hdl).
* Para obtener ayuda y soporte, revisa las [preguntas frecuentes](/es/faq) y [únete a las conversaciones rápidas y amigables en Discord](https://discord.gg/qZHPrPsmt6).

---

# Prepara tu presentación

{{< youtube 5l_TVgu__pg >}}

* [Plantilla de envío a Github](https://github.com/TinyTapeout/tt03-submission-template).
* Si deseas utilizar un HDL como Verilog, por favor revisa [esto](/es/hdl).

---

<style>
  .fullbleed-bg {
    position: absolute;
    top: -8px;
    left: 50%;
    right: 50%;
    margin-left: calc(-50vw - 158px);
    width: 100vw;
    bottom: -8px;
    z-index: -1;
  }
  @media only all and (max-width: 59.938em) {
    .fullbleed-bg {
      margin-left: calc(-50vw - 124px);
    }
  }
  @media only all and (max-width: 47.938em) {
    .fullbleed-bg {
      margin-left: calc(-50vw - 8px);
    }
  }
</style>

<div style="position: relative; padding: 8px 0 16px; margin-bottom: 32px">
  <!-- background color strip -->
  <div style="background: #c8b2f3;" class="fullbleed-bg"></div>

# Envía tu diseño

* Diseño + PCB Física + ASIC = $100 + p&p
* Sólo Diseño = $25
* Al realizar un pedido, estás de acuerdo con nuestros [términos y condiciones](/es/terms).

<style>
  [x-cloak] { display: none !important; }
  .checkout--product { display: flex; align-items: baseline; font-weight: normal; }
  .checkout--product small { display: block; color: gray; }
</style>

<div x-data="checkout" x-cloak>

  <div x-show="soldOut" style="color: red">¡Lo sentimos, están agotados!</div>

  URL del Repositorio del Proyecto:

  <input x-model="repo" x-bind:disabled="validating || validated" type="text" placeholder="https://github.com/user/repo" />

  <div x-show="loading">Loading...</div>
  <button class="button" x-on:click="next()" x-show="!loading" x-bind:disabled="validating || validated">Siguiente</button>

  <div style="color:red" x-show="errorMessage" x-text="errorMessage"></div>
  <div style="color:purple" x-show="validating">Validando repositorio...</div>

<div x-show="validated">

### Por favor, selecciona tu paquete:

<fieldset>
  <label class="checkout--product">
    <input x-model="selectedProduct" value="tt-asic-pcb" type="radio" x-bind:disabled="stock['tt-asic-pcb'] <= 0" />
    <div>
      Ranura de Diseño + PCB física con el chip ($100)
      <small><span x-text="stock['tt-asic-pcb']"></span> disponible</small>
    </div>
  </label>

  <label class="checkout--product">
    <input x-model="selectedProduct" value="tt-design-only" type="radio" x-bind:disabled="stock['tt-design-only'] <= 0"/>
    <div>
      Sólo ranura de Diseño ($25)
      <small><span x-text="stock['tt-design-only']"></span> disponible</small>
    </div>
  </label>
</fieldset>

<button x-on:click="payment()" x-bind:disabled="redirecting">Continua con el pago</button> 
<!-- **<div x-bind:disabled>Submissions will be open on November 9th</div>** -->

<div style="color:red" x-show="checkoutError" x-text="checkoutError"></div>

</div> <!-- validated -->

</div> <!-- checkout -->

{{< checkout-script >}}

</div>

{{% feedback %}}

---

# Regístrate

Regístrate en la lista de correo para recibir las últimas noticias y para asegurarte de no perder la oportunidad de presentar un diseño.

{{< mailchimp >}}

---

> **Testimonio** Acabo de hacer un desplazador de barril de 4 bits usando esta herramienta de http://tinytapeout.com. Es rápido y divertido de usar. Incluso el GDS se generó en cuestión de minutos. Todos deberían probarlo.
