# Tienda propia: cómo funcionan la seguridad y los cobros — 2026-11-22

## La idea clave
**Los datos de la tarjeta nunca pasan por nuestra web.** Los maneja Mercado Pago, que está certificado para eso (PCI DSS), igual que hoy con Impultienda. Nosotros solo nos enteramos de que «el pago X por $16.990 fue aprobado» y entregamos el ebook.

Por eso **tarjeta o Mercado Pago no son opciones distintas**: con Mercado Pago la persona puede pagar con **tarjeta de crédito (con cuotas), débito, dinero en cuenta** y, si lo activás, en **efectivo** (Rapipago o Pago Fácil). No hace falta que tenga cuenta de Mercado Pago para pagar con tarjeta.

---

## Dos formas de integrar Mercado Pago

| | **Checkout Pro** (recomendado para empezar) | **Checkout Bricks** (más adelante) |
|---|---|---|
| Cómo se ve | Botón «Comprar» → se abre la página de Mercado Pago → vuelve a tu web | El formulario de tarjeta aparece dentro de tu web |
| Datos de la tarjeta | Solo los ve Mercado Pago | Los cifra el script de Mercado Pago en el navegador, y a tu servidor llega solo un «token» |
| Seguridad | Máxima, con muy poco riesgo de nuestro lado | Alta, pero con más cosas que configurar |
| Esfuerzo | Bajo | Medio |
| Confianza del comprador | Alta (ve la página conocida de Mercado Pago) | Depende de cómo se vea tu web |

**Arrancamos con Checkout Pro** y, si más adelante querés que todo pase dentro de tu web, migramos a Bricks.

---

## Cómo funciona una compra, paso a paso

```
 Comprador            Tu web (servidor)               Mercado Pago            Almacén privado / Mail
    |                        |                             |                          |
 1. Toca «Comprar» ------->  |                             |                          |
    |              2. Arma el pedido con los               |                          |
    |                 precios del CATÁLOGO del servidor    |                          |
    |                 y crea una «preferencia» ----------> |                          |
    |  <------------- 3. Redirige a la página de pago ---- |                          |
 4. Paga con tarjeta, débito, dinero en cuenta... -------> |                          |
    |                        |  <-- 5. Aviso automático (webhook) «pago 123»          |
    |              6. Verifica la firma del aviso          |                          |
    |                 y consulta el pago 123 a MP -------> |                          |
    |                 ¿aprobado? ¿monto correcto? ¿moneda? |                          |
    |              7. Guarda el pedido (una sola vez)      |                          |
    |                 y genera un link de descarga ------------------------------------> |
    |  <------------------------------------------- 8. Mail con el link (vence en 7 días)
 9. Vuelve a tu web: «¡Gracias! Revisá tu mail»            |                          |
```

**Los 3 controles que hacen segura la entrega:**
1. **El precio lo pone el servidor, no el navegador.** Aunque alguien manipule la página, no puede pagar $1 por un ebook de $16.990.
2. **Solo entregamos cuando Mercado Pago confirma.** Verificamos la **firma** del aviso (Mercado Pago lo firma con una clave secreta) y además **le preguntamos directamente** a Mercado Pago si ese pago está aprobado, si el monto es correcto y si la moneda es ARS. La página de «gracias» **no** entrega nada, porque se puede falsificar.
3. **Cada pago se entrega una sola vez.** Si Mercado Pago repite el aviso, no se manda otro mail ni se duplica el pedido.

---

## Cómo protegemos los PDF
- Los PDF se guardan en un **almacén privado**, no en una carpeta pública de la web.
- El comprador recibe un **link firmado que vence** (por ejemplo, a los 7 días o después de 5 descargas). Si lo comparte, deja de funcionar.
- Opcional: **marca de agua con el mail del comprador** en cada página. Desalienta que lo pase.
- Botón «reenviar mi descarga» que pide el mail de compra, por si pierde el link.

---

## Seguridad general (lista de control)

| Tema | Qué hacemos |
|---|---|
| Conexión | HTTPS en todo el sitio (el hosting lo da gratis) |
| Claves | El «Access Token» de Mercado Pago y la clave del mail viven solo en variables secretas del hosting. **Nunca en el código, en el repositorio ni en el chat** |
| Repositorio | Privado, con escaneo de secretos activado |
| Cuentas | **Verificación en 2 pasos** en GitHub, Mercado Pago, hosting, mail y dominio |
| Datos personales | Guardamos lo mínimo (mail, nombre, pedido). Política de privacidad según la **Ley 25.326** |
| Avisos de pago | Firma verificada, consulta a Mercado Pago y protección contra duplicados |
| Abuso | Límite de pedidos por minuto en los endpoints, y sin panel de administración expuesto |
| Respaldo | Copia de los pedidos. Mercado Pago también guarda el historial de cada pago |
| Legales | Términos y condiciones, **botón de arrepentimiento** (obligatorio en Argentina) y datos del vendedor |
| Pruebas | Todo se prueba primero en el **modo de pruebas de Mercado Pago**, con usuarios y tarjetas de prueba. Después, con una compra real tuya |

---

## Herramientas propuestas (todas con plan gratis para empezar)

| Para qué | Herramienta |
|---|---|
| Web y funciones del servidor | Netlify o Vercel |
| Pedidos y PDF privados | Supabase (base de datos y almacén privado) |
| Mails de entrega | Resend o Brevo |
| Cobros | Mercado Pago (Checkout Pro) |
| Código | Repositorio privado en GitHub |

Costo fijo al empezar: **$0**, más el dominio (unos pocos miles de pesos por año). Mercado Pago cobra su comisión por venta, como ahora.

---

## Lo que Impultienda te da hoy y cómo lo cubrimos

| Impultienda | En tu tienda |
|---|---|
| Checkout con Mercado Pago | Checkout Pro, igual de seguro |
| Entrega automática del PDF | Aviso de pago + mail con link que vence |
| Productos extra en el checkout y upsell | Etapa 4 (se construye) |
| Carritos abandonados | Etapa 4: como pedimos el mail antes de pagar, podemos escribirle a quien no termina |
| Garantía y reembolsos | Los reembolsos se hacen desde el panel de Mercado Pago |
| Un solo producto principal por tienda | Todos los ebooks y categorías que quieras |

---

## Tu ventaja: sos QA
Podés armar el **plan de pruebas** de la tienda: pago aprobado, rechazado y pendiente, aviso de pago duplicado, link vencido, reembolso, montos manipulados. Es exactamente lo que hay que probar antes de lanzar.
