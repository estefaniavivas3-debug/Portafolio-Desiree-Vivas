# Landing: «¿Por qué elegirnos?» v2 — 2026-11-19

Este archivo reemplaza el borrador `2026-11-19 Landing - Por qué comprarnos.md`. Lo escribí después de leer el HTML real de la página.

Tu página **ya tiene** una sección «¿Por qué elegirnos?» y es buena. El problema es **dónde está**: aparece en el puesto 11 de 15, después de la oferta y de las reseñas. Quien llega desde Meta con el celular casi nunca baja tanto.

Esta versión:
- responde de forma directa a «¿por qué te compraría a vos?»;
- conecta con los dos anuncios que vendieron, «Finales de diciembre» y «Buscá tu carrera»;
- usa las mismas clases CSS que ya tenés, así que se pega sin tocar el estilo.

---

## Cambio 1: mover la sección

**Ahora:** … Contenido → Oferta → Para quién es → Reseñas → **Por qué elegirnos** → Garantía → FAQ …

**Propuesta:** … Contenido → **Por qué elegirnos (v2)** → Oferta → …

Así la persona ve la razón para elegirte justo antes del precio, y no después.

---

## Cambio 2: reemplazar la sección por esta (HTML listo para pegar)

Reemplazá todo el bloque que empieza con `<!-- POR QUÉ NOSOTROS` y termina en su `</section>` por este:

```html
<!-- POR QUÉ NOSOTROS v2: responde "¿por qué te compraría a vos?". Va justo ANTES de la sección de oferta (#oferta). -->
<section class="sec-white why" id="por-que">
  <div class="wrap">
    <p class="eyebrow">¿Por qué comprarnos a nosotros?</p>
    <h2>Hay mucha info gratis sobre IA. Lo que no hay es un método para aprobar.</h2>
    <p class="lead" style="margin-top:16px">En YouTube y TikTok encontrás trucos sueltos y tenés que probar horas hasta que algo funcione. Acá tenés todo ordenado, con los pedidos ya armados y pensado para estudiantes de Argentina, para que llegues a tus finales preparado y no solo con un resumen.</p>
    <div class="why-grid">
      <div class="why-card"><span class="why-ico">⏱️</span><h3>Pensado para quien no tiene tiempo</h3><p>Si estudiás y trabajás, no podés pasarte la noche probando qué pedirle a la IA. Te damos una rutina de 45 minutos por día que sí entra en tu semana.</p></div>
      <div class="why-card"><span class="why-ico">📝</span><h3>Te prepara para el examen, no solo para resumir</h3><p>Simulacros con el estilo de tu cátedra, orales con repreguntas y corrección con nota. Los errores los descubrís antes, no en el aula.</p></div>
      <div class="why-card"><span class="why-ico">🇦🇷</span><h3>Hecho para cómo se estudia acá</h3><p>CBC, ingresos, terciarios, profesorados, parciales, finales y orales. Rutas para cada situación y tutores de IA para 20 materias, sea cual sea tu carrera.</p></div>
      <div class="why-card"><span class="why-ico">🎯</span><h3>Para aprender, no para copiar</h3><p>La IA te explica, te toma examen y te corrige. El trabajo lo hacés vos, y por eso después lo podés defender en un oral.</p></div>
      <div class="why-card"><span class="why-ico">📋</span><h3>Listo para usar hoy, sin saber de tecnología</h3><p>+200 pedidos para copiar y pegar, simuladores interactivos y 5 bonus. Funciona con las versiones gratis de ChatGPT y Claude. Si sabés usar WhatsApp, sabés usar esto.</p></div>
      <div class="why-card"><span class="why-ico">🛡️</span><h3>Sin riesgo</h3><p>Un solo pago, sin suscripción y en cuotas sin interés. Lo recibís al instante en tu mail y es tuyo para siempre. Si en 7 días no te sirve, te devolvemos el 100%.</p></div>
    </div>
    <div class="why-cta">
      <p class="hand" style="margin-bottom:14px">Los finales de diciembre ya están acá. Cada semana cuenta.</p>
      <a class="btn cta" href="/checkout" data-checkout>Quiero mi ebook + 5 bonus →</a>
    </div>
  </div>
</section>
```

**Qué cambia respecto de la que tenés:**
- El título responde a la pregunta del cliente: *gratis hay info, lo que no hay es un método para aprobar*.
- La primera tarjeta es el dolor que más te vende: **estudiás y trabajás, no tenés tiempo**.
- Saqué «Actualizado a noviembre 2026» y «Personas reales», porque ya aparecen en la barra superior y en las reseñas, y metí «Te prepara para el examen».
- El cierre suma la urgencia de **finales de diciembre**, que es lo que dice tu anuncio ganador.
- Todo lo que afirma ya está en tu página: 45 minutos por día, 20 materias, versiones gratis, 7 días, cuotas. No inventé nada.

---

## Cambio 3 (opcional, rápido): que la landing diga lo mismo que el anuncio

Tu anuncio ganador habla de los **finales de diciembre**, pero la página no los menciona en ningún lado. Cuando alguien hace clic y no encuentra lo que le prometió el anuncio, se va.

Un cambio mínimo en la barra superior:

```html
<div class="topbar">Preparate para los <b>finales de diciembre</b> · Ebook + 5 bonus · Garantía de 7 días · Entrega inmediata</div>
```

Si después ves que el carrusel de carreras es el que más vende, podés probar en su lugar: «Para tu carrera, sea cual sea».

---

## Antes de publicar: 2 cosas para revisar

1. **El precio tachado no coincide.** En la landing el ebook aparece «antes $29.990», pero en la configuración de Impultienda que me pasaste figura **$84.950**. Si la persona ve un número en la página y otro en el checkout, desconfía. Elegí uno y usalo en los dos lados.
2. **Reseñas.** La página muestra 9 reseñas con nombre. Según tus métricas, las ventas por anuncios todavía son pocas. Si algunas reseñas son de lectores que lo recibieron gratis o de pruebas, conviene que sean reales y que tengas su permiso. Meta y la ley de defensa del consumidor penalizan las reseñas inventadas, y una sola que se descubra te quita la confianza que construye toda la página. Si todas son reales, perfecto: ignorá esto.

Fuentes del vault: Raw/2026-11-19 Landing HTML (extractos).md, Wiki/Estudia con IA, Wiki/Campaña de ventas 2026-11-16, Wiki/Cliente ideal de Estudia con IA.
