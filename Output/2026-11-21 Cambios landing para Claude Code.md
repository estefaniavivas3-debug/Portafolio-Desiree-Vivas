# Cambios en la landing: instrucciones para Claude Code — 2026-11-21

**Cómo usarlo:** copiá desde «PROMPT» hasta el final y pegáselo a Claude Code, junto con el HTML de la landing que está publicado ahora. Si publicaste la v2, es `Output/2026-11-19 Landing completa v2.html`.

**Antes de pasarlo, confirmá 3 cosas.** Los cambios 2, 3 y 4 dependen de tus respuestas:
- **A.** Cuando alguien paga en Mercado Pago, ¿le aparecen **cuotas sin interés** de verdad? (Probalo hasta la pantalla de cuotas.)
- **B.** ¿Se puede pagar con tarjeta **sin tener cuenta** de Mercado Pago?
- **C.** ¿Vas a **sacar «Aprendé a programar»** del checkout?

Al final hay otra lista con lo que se cambia en el **panel de Impultienda**, no en el código.

---

## PROMPT

Necesito que edites el HTML de mi landing de venta (te lo paso adjunto). Es una sola página que se pega en el editor de Impultienda. Reglas:
- Cambiá **solo** lo que te pido abajo. No toques el CSS, el JavaScript, los links de imágenes, los `href="/checkout"`, los atributos `data-checkout`, `data-upsell-toggle`, `data-upsell-count`, `data-cart-total` ni `data-cart-savings`, ni las variables `{{upsell_1_image}}` / `{{upsell_2_image}}`: los usa la tienda.
- Escribí en español rioplatense (de **vos**).
- Al terminar, devolveme el HTML completo y una lista de lo que cambiaste.

### Cambio 1: ordenar los bonus igual que en el checkout
En la sección `<section class="offer" id="oferta">`, dentro de `.bonus-grid`, reordená las 5 tarjetas `article.bonus-card` y renumerá sus etiquetas `.bonus-tag` así:
1. BONUS 01 · NUEVO: Ejercicios con una foto (clase `bonus-card bonus-special`)
2. BONUS 02: Biblioteca de 125 pedidos
3. BONUS 03: Mapas conceptuales y presentaciones
4. BONUS 04: Tutores IA por materia
5. BONUS 05 · NUEVO: Flashcards con IA (clase `bonus-card bonus-special`)

Cambiá también el `alt` de cada imagen para que diga el número nuevo («Bonus 1: …»). En la sección final (`section.final`), reordená la lista del párrafo `.lead` en ese mismo orden: «Ebook de 21 capítulos + anexo + Ejercicios con una foto + Biblioteca de 125 pedidos + Mapas conceptuales con IA + Tutores IA por materia + Flashcards con IA.»

### Cambio 2: cuotas (hacelo SOLO si te digo que NO hay cuotas sin interés)
Reemplazá todas las menciones a «cuotas sin interés» por un texto que no prometa cuotas:
- `<span class="cuotas">o pagalo en <b>cuotas sin interés</b></span>` (aparece 3 veces) → `<span class="cuotas">Pagá con <b>tarjeta, débito o dinero en Mercado Pago</b></span>`
- `<small class="pm-s">Cuotas sin interés</small>` (aparece 2 veces) → borralo.
- En la tarjeta «Sin riesgo» de la sección `#por-que`: «Un solo pago, sin suscripción y en cuotas sin interés.» → «Un solo pago, sin suscripción.»
- En las preguntas frecuentes, borrá entero el `<details>` «¿Puedo pagar en cuotas?».
- En la barra fija de abajo (`.sticky`): `<small>o en cuotas sin interés</small>` → `<small>Pago único</small>`

### Cambio 3: aclarar el pago (hacelo SOLO si te confirmo que se puede pagar sin cuenta)
En el bloque `.after-buy` de la oferta, cambiá el primer paso:
- Antes: `<li><b>Pagás con Mercado Pago</b><span>Tarjeta de crédito, débito o dinero en cuenta.</span></li>`
- Después: `<li><b>Pagás con Mercado Pago</b><span>Con tarjeta de crédito o débito, o con dinero en cuenta. No necesitás crearte una cuenta.</span></li>`

Y en las dudas rápidas (`.quick-faq`) agregá al principio:
`<details><summary>¿Necesito cuenta de Mercado Pago?</summary><p>No. Podés pagar con tu tarjeta de crédito o débito sin crear una cuenta. Si ya tenés cuenta, también podés usar tu dinero disponible.</p></details>`

### Cambio 4: sacar «Aprendé a programar» (hacelo SOLO si te confirmo que lo saco del checkout)
En `<section class="more" id="mas-productos">`:
- Borrá entero el `<article class="prod">` que contiene `data-upsell-toggle="2"`.
- Cambiá el texto `.lead` de esa sección por: «Se compra por separado y complementa el ebook principal: te enseña a responder como te evalúan, en escritos y orales.»
- Cambiá el título `h2` por: «¿Querés ir un paso más allá? Sumá la Guía de examen»
- En el comentario HTML de arriba de la sección, actualizá la lista de upsells para que diga solo «1 = Guía de examen».
- Dejá la grilla `.prod-grid` con un solo producto, centrado (agregale `style="max-width:440px;margin-inline:auto"`).

### Cambio 5: confianza junto al último botón de compra
En la tarjeta de compra (`.buy-card`, dentro de `.buy-info`), justo debajo de `<span class="cuotas">…</span>` (o del texto que lo reemplace), agregá:
`<div class="guar-mini"><span><b>Garantía de 7 días.</b> Si no te sirve, te devolvemos el 100%. Lo recibís al instante en tu mail.</span></div>`
Usá la misma clase `guar-mini` que ya existe en el hero (con su ícono SVG de escudo, copiándolo del hero).

---

## Lo que NO es código: cambiarlo en el panel de Impultienda

1. **Descripción de «Aprendé a programar»:** reemplazá «Fotografía realista de un estudiante joven programando de…» por *«Instalá Python paso a paso y usá la IA como tutor para aprobar programación, con ejercicios y simulacros de parcial.»*
2. **Contador «X personas están comprando ahora mismo»:** desactivalo.
3. **Precio tachado del ebook:** cambialo de $84.950 a **$29.990**, igual que en la landing.
4. **Productos adicionales del checkout:** dejá solo la **Guía de examen**. Volvé a poner el **Plan de estudio** después de la compra.
5. **Carritos abandonados:** activá la recuperación si Impultienda la tiene.
6. **Mercado Pago:** revisá los pagos rechazados y pendientes, y si se puede, sumá transferencia.

Fuentes del vault: Output/2026-11-21 Revisión del checkout.md, Raw/2026-11-21 Capturas checkout (transcripcion).md, Raw/2026-11-19 Landing HTML (extractos).md.
