Necesito que edites el HTML de mi landing de venta (te lo paso adjunto). Es una sola página que se pega en el editor de Impultienda.

Reglas:
- Cambiá SOLO lo que te pido abajo.
- No toques el CSS, el JavaScript, los links de imágenes, los href="/checkout", ni los atributos data-checkout, data-upsell-toggle, data-upsell-count, data-cart-total, data-cart-savings, ni las variables {{upsell_1_image}} y {{upsell_2_image}}: los usa la tienda.
- Escribí en español rioplatense (de vos).
- Al terminar, devolveme el HTML completo y una lista de lo que cambiaste.

CAMBIO 1: ordenar los bonus igual que en el checkout
En la sección <section class="offer" id="oferta">, dentro de .bonus-grid, reordená las 5 tarjetas article.bonus-card y renumerá su etiqueta .bonus-tag así:
1. BONUS 01 · NUEVO: Ejercicios con una foto (con la clase "bonus-card bonus-special")
2. BONUS 02: Biblioteca de 125 pedidos
3. BONUS 03: Mapas conceptuales y presentaciones
4. BONUS 04: Tutores IA por materia
5. BONUS 05 · NUEVO: Flashcards con IA (con la clase "bonus-card bonus-special")
Cambiá también el alt de cada imagen para que diga el número nuevo (por ejemplo, "Bonus 1: Ejercicios con una foto").
En la sección final (section.final), reemplazá el texto del párrafo .lead por: "Ebook de 21 capítulos + anexo + Ejercicios con una foto + Biblioteca de 125 pedidos + Mapas conceptuales con IA + Tutores IA por materia + Flashcards con IA."

CAMBIO 2: garantía junto al último botón de compra
En la tarjeta de compra (.buy-card), dentro de .buy-info, justo debajo de <span class="cuotas">o pagalo en <b>cuotas sin interés</b></span>, agregá un bloque con la clase guar-mini (la misma que ya existe en el hero, con el mismo ícono SVG de escudo copiado del hero) y este texto:
<b>Garantía de 7 días.</b> Si no te sirve, te devolvemos el 100%. Lo recibís al instante en tu mail.
