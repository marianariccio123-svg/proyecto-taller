# Preguntas para la dueña del taller: ronda 2

> Surgen de las rondas de diseño con Claude (octubre 2026). Siguen la numeración de `preguntas-clienta.md` (que llegaba hasta P42), así que arrancan en **P43**.
> La parte 1 es para vos, con el porqué de cada pregunta. La parte 2 es el mensaje listo para mandarle por WhatsApp. La parte 3 es lo que va al contador.

---

## Parte 1: versión para Mariana

### Cómo leer la tabla

- **Prioridad:**
  - 🔴 La necesito antes de programar esa parte de la Fase 1.
  - 🟡 Es de la Fase 1, pero mientras tanto el sistema usa un valor por defecto configurable.
  - 🟢 Es de la Fase 2 o 3. Conviene preguntarla ya porque estás con ella.
- **Mientras tanto:** qué hace el sistema hasta que tengamos la respuesta. Ninguna de estas preguntas frena el arranque del proyecto: la estructura, el login, los clientes y los comprobantes se pueden empezar ya.

### Recibos (la prioridad de ella)

| # | Pregunta | Por qué importa | Mientras tanto | Prioridad |
|---|----------|-----------------|----------------|-----------|
| P43 | En el audio dijiste que querías imprimir los recibos sobre papel preimpreso, como los remitos. ¿Te sirve que el sistema arme el recibo completo en PDF (hoja blanca A4), que se pueda mandar por mail o WhatsApp e imprimir si hace falta? | Cambia todo el diseño del recibo (ADR 0002). Un preimpreso obliga a calibrar la impresora y a seguir la numeración de la imprenta. | Se diseña como PDF A4. | 🔴 |
| P44 | Hoy tus clientes no reciben el recibo. ¿Querés que a partir de ahora les llegue por mail automáticamente cada vez que te pagan? ¿Hay clientes a los que no se lo mandarías? | Es un cambio en cómo trata a sus clientes, y el envío automático es una de las automatizaciones centrales. | Se envía automáticamente, con la opción de desactivarlo por cliente. | 🔴 |
| P45 | ¿Los recibos los numerás hoy? Si usás talonario, ¿cuál es el último número que usaste? ¿Arrancamos del 1 o seguimos esa numeración? | Define el número inicial del sistema. | Número inicial configurable, por defecto `0001-00000001`. | 🟡 |
| P46 | Cuando un cliente de contado te paga en el momento, ¿le hacés recibo? ¿Cómo lo anotás hoy? | Decide si una venta de contado genera factura + recibo (propuesta Q10) o solo la factura marcada como pagada. | Se diseña como factura + recibo, con un atajo "Registrar el cobro ahora". | 🟡 |
| P47 | Cuando un cliente te paga, ¿alguna vez te transfiere menos de lo que dice la factura y te manda un "certificado de retención"? ¿Qué clientes lo hacen? | Si pasa, el recibo tiene que registrar la retención. Si no, la factura queda con plata "pendiente" para siempre. | El recibo ya admite retenciones como medio de cobro (Q5). La respuesta confirma si se usa. El contador también lo confirma (P38). | 🟡 |

### Facturas y vencimientos

| # | Pregunta | Por qué importa | Mientras tanto | Prioridad |
|---|----------|-----------------|----------------|-----------|
| P48 | Cuando acordás "a 30 días" con un cliente, ¿los días se cuentan desde la fecha de la factura o desde que el cliente la recibe? Si el vencimiento cae sábado o domingo, ¿pasa al lunes? | Es la regla que calcula el vencimiento (Q11), y de ahí salen el resumen de los martes y los recordatorios. | Días corridos desde la fecha de la factura, sin correr por fin de semana. Siempre editable. | 🟡 |
| P49 | Mirá algunas de tus facturas: ¿alguna dice arriba "Factura de Crédito Electrónica MiPyMEs (FCE)"? ¿A qué clientes? | Las FCE tienen su propio tipo de comprobante y el vencimiento viene escrito en la factura (Q9). | Se cargan los tipos A, B, nota de crédito (NC) y nota de débito (ND). Las FCE se agregan si las usa. | 🟡 |

### Mails y cuentas

| # | Pregunta | Por qué importa | Mientras tanto | Prioridad |
|---|----------|-----------------|----------------|-----------|
| P50 | ¿El taller tiene página web o un mail propio, del tipo `algo@nombredeltaller.com.ar`? ¿O usan Gmail u otro mail gratuito? | Define el servicio de mails (Q13): con dominio propio va Resend; con Gmail, se manda desde su Gmail. | Los mails no salen de verdad: van a una bandeja de prueba (Mailpit). | 🔴 para poner en producción, no para empezar |
| P51 | ¿Desde qué mail querés que salgan los recibos? ¿A qué mail del taller va la copia de respaldo? | Configuración del remitente y de la copia. | Configurable por variable de entorno. | 🟡 |
| P52 | ¿Hay un mail del taller (no personal tuyo) que podamos usar para crear las cuentas del sistema (Supabase, Cloudflare y el servicio de mail)? ¿Quién tiene acceso a ese mail? | Las cuentas tienen que quedar a nombre del taller (Q2). Si se pierde el acceso a ese mail, se pierde el acceso al sistema. | Desarrollamos en local con Docker; no hace falta la cuenta hasta el primer despliegue. | 🔴 para el primer despliegue |
| P53 | ¿Cómo se llama la otra persona que va a usar el sistema y cuál es su mail? | Para crear su usuario. | Se crea solo el usuario de la administradora. | 🟡 |

### Datos para los PDF y la importación

| # | Pregunta | Por qué importa | Mientras tanto | Prioridad |
|---|----------|-----------------|----------------|-----------|
| P54 | Datos del taller para el encabezado del recibo: razón social, CUIT, dirección, teléfono, mail, número de Ingresos Brutos e inicio de actividades. Y el logo, si tiene, como archivo (imagen o PDF), no como foto. | El encabezado del PDF. Casi todo sale de una factura emitida, así que alcanza con que te mande una. | Se usan datos de ejemplo configurables. | 🔴 para terminar recibos |
| P55 | Mandame los Excel actuales: "ventas mensuales", "cuenta corriente clientes", "cuenta corriente proveedores" y el de cheques. Pueden ser copias. | Para analizar cómo importarlos (Q16) y ver el formato del reporte mensual. | No se programa la importación hasta verlos. | 🔴 para la importación |
| P56 | ¿Desde qué fecha arrancamos con el sistema? Recomiendo el 1° de un mes. En los Excel, ¿tenés cada factura impaga anotada por separado, o solo el total que te debe cada cliente? | Si están las facturas, se importan una por una. Si solo hay un total, se carga un "Saldo inicial" por cliente (Q16). | Se soportan las dos formas. | 🟡 |

### Automatizaciones

| # | Pregunta | Por qué importa | Mientras tanto | Prioridad |
|---|----------|-----------------|----------------|-----------|
| P57 | El resumen de los martes, ¿a qué hora querés recibirlo y a qué mail? | Horario de la tarea programada. | Martes 7:00 (hora de Tucumán), configurable. | 🟡 |
| P58 | ¿Querés que el sistema les mande recordatorios a tus clientes cuando una factura está por vencer o ya se venció? Si querés: ¿cuántos días antes y cada cuánto lo repite si siguen sin pagar? ¿Hay clientes a los que nunca se los mandarías? | Recordatorios automáticos de la Fase 3. Hay que saber si los quiere, porque es algo que ven sus clientes. | No se hace hasta la Fase 3. | 🟢 |
| P59 | El reporte de ventas de fin de mes, ¿te lo mando a vos o directo a tu contador? Si es al contador, ¿cuál es su mail? | Destinatario del cierre mensual de la Fase 3. | Solo a la administradora. | 🟢 |

### Otros pendientes de las fases siguientes

| # | Pregunta | Por qué importa | Mientras tanto | Prioridad |
|---|----------|-----------------|----------------|-----------|
| P60 | ¿Qué operaciones hacés en dólares? ¿Facturás en dólares, o en pesos con una cotización? ¿Te pagan o pagás en dólares? Más o menos, ¿cuántas veces por mes? | Define si alcanza con guardar la moneda y el tipo de cambio, o si hacen falta cuentas corrientes separadas por moneda. | Todo en pesos. La base ya tiene el campo de moneda y el de tipo de cambio. | 🟡 |
| P61 | Con los remitos, ¿querés que el sistema solo los registre o que también los imprima, como tu Excel actual? ¿Qué impresora usás? Sacale una foto donde se vea la marca y el modelo. | Remitos de la Fase 3. | Sin remitos en la Fase 1; la factura tiene un campo opcional para el número de remito. | 🟢 |

---

## Parte 2: mensaje para mandarle por WhatsApp

> Es más corto y sin tecnicismos. Si preferís, llevalo impreso a la reunión. Las preguntas con 🔴 son las más importantes: si no contesta todo, que conteste esas.

```
¡Hola! 😊 Ya estoy armando el diseño del sistema. Me quedaron algunas dudas. No hace falta que contestes todo junto: podés mandarme audios con el número de la pregunta. Si alguna no la sabés, no pasa nada.

*Recibos*
1. Me habías dicho que te gustaría imprimir los recibos en papel preimpreso, como los remitos. ¿Te sirve que el sistema arme el recibo completo en PDF, que se pueda mandar por mail o WhatsApp y también imprimir? Es mucho más simple y no depende de la impresora.
2. ¿Querés que a tus clientes les llegue el recibo por mail automáticamente cada vez que te pagan? ¿Hay alguno al que no se lo mandarías?
3. ¿Usás talonario de recibos? Si sí, ¿cuál es el último número que usaste?
4. Cuando un cliente te paga en el momento (de contado), ¿le hacés recibo?
5. ¿Algún cliente te transfiere menos de lo que dice la factura y te manda un "certificado de retención"? ¿Cuáles?

*Facturas*
6. Cuando acordás "a 30 días", ¿se cuenta desde la fecha de la factura o desde que el cliente la recibe? Si vence un sábado o domingo, ¿pasa al lunes?
7. ¿Alguna de tus facturas dice "Factura de Crédito Electrónica MiPyMEs"? ¿A qué clientes?

*Mails*
8. ¿El taller tiene página web o un mail propio (tipo algo@nombredeltaller.com.ar), o usan Gmail?
9. ¿Desde qué mail querés que salgan los recibos? ¿Y a qué mail del taller te mando la copia?
10. Para crear las cuentas del sistema necesito un mail del taller (no uno personal) al que tengas acceso siempre. ¿Cuál puede ser?
11. ¿Cómo se llama la otra persona que va a usar el sistema y cuál es su mail?

*Para arrancar*
12. Mandame una factura que hayas hecho (de ahí saco los datos del taller para el recibo) y el logo, si tenés, como archivo.
13. Mandame una copia de los Excel: ventas mensuales, cuenta corriente de clientes, cuenta corriente de proveedores y cheques.
14. ¿Desde qué fecha te gustaría empezar a usar el sistema? Lo ideal es el 1° de un mes.

*Avisos automáticos*
15. El resumen de los martes, ¿a qué hora y a qué mail te lo mando?
16. ¿Querés que el sistema les mande a tus clientes un aviso cuando una factura está por vencer o ya venció? Si sí, ¿cuántos días antes?
17. El reporte de ventas de fin de mes, ¿te lo mando a vos o directo a tu contador?

*Más adelante*
18. ¿Qué cosas hacés en dólares y más o menos cada cuánto?
19. Con los remitos, ¿querés que el sistema solo los anote o que también los imprima? ¿Me sacás una foto de la impresora donde se vea la marca y el modelo?

¡Gracias! 💪
```

Equivalencias entre el mensaje y la tabla:

| Mensaje | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Tabla | P43 | P44 | P45 | P46 | P47 | P48 | P49 | P50 | P51 | P52 | P53 | P54 | P55 | P56 | P57 | P58 | P59 | P60 | P61 |

---

## Parte 3: para el contador

Siguen pendientes las de `preguntas-clienta.md`. Con lo que ya sabemos, las más importantes son estas:

| # | Pregunta | Para qué |
|---|----------|----------|
| P37 | ¿El recibo puede ser un documento no fiscal generado por el sistema, en PDF? ¿Qué datos no pueden faltar? | Confirmar el ADR 0002 (recibo en PDF). |
| P38 | ¿Sus clientes le hacen retenciones (IVA, Ganancias, Ingresos Brutos, SUSS)? ¿Ella es agente de retención? | Confirmar las retenciones en los recibos (Fase 1) y en las órdenes de pago (Fase 2). |
| P39 | ¿En qué formato necesita el reporte mensual de ventas? (columnas, Excel) | Diseñar la exportación del reporte mensual. |
| P62 (nueva) | ¿Emite Factura de Crédito Electrónica MiPyMEs? ¿A qué clientes? | Tipos de comprobante (complementa P49). |
| P63 (nueva) | ¿Cómo hay que registrar las operaciones en dólares? ¿Hace falta llevar cuentas corrientes en dólares separadas? | Diseño de la moneda (complementa P60). |
