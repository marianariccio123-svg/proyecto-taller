# Preguntas para la clienta: versión para Mariana

> Es la versión de trabajo, con todo el razonamiento. La que ve la clienta está en `formulario-clienta.md` (el Google Form) y `mensaje-clienta.txt` (el WhatsApp que acompaña el link).
> La numeración **P1, P2…** es la misma en todos los archivos. Cuando ella conteste "la 7 no la sé", sabés exactamente cuál es.

---

## 0. Con qué criterio elegí y ordené las preguntas

Esta sección es para que aprendas a hacerlo sola la próxima vez.

### 0.1 Cómo las elegí

Recorrí el sistema **de punta a punta**, no solo lo que ella pidió, y me pregunté en cada etapa: *"¿qué necesito saber para poder hacer esto?"*

| Etapa del proyecto | Qué necesito saber | Preguntas |
|--------------------|--------------------|-----------|
| Entender el negocio | Rubro, cómo trabaja, cuánto volumen maneja | P1, P8, P10, P32 |
| Definir el alcance | Qué le duele, qué prioriza, qué quiere primero | P17, P18, P19, P21 |
| Diseñar los datos | Cómo se relacionan facturas, pagos y cuentas | P6, P9, P12, P23, P27, P28, P29 |
| Diseñar los documentos | Qué papeles emite y cómo se imprimen | P4, P5, P14, P15, P16, P22, P24 |
| Decidir dónde corre | Quién lo usa, desde dónde | P2, P3, P34 |
| Cumplir la normativa | Condición fiscal y obligaciones | P7, P20, P37–P42 |
| Ponerlo en marcha | Datos existentes, saldos iniciales | P13, P25, P26 |
| Mantenerlo | Soporte, backups, conectividad | P33 |
| Cerrar el acuerdo | Presupuesto, plazos, criterio de éxito | P21, P35, P36 |

Las filas de *Ponerlo en marcha* y *Mantenerlo* son las que un principiante suele olvidar. La clienta nunca las va a mencionar por su cuenta.

### 0.2 Cómo las repartí entre canales

Cada pregunta va por el canal donde se contesta mejor:

- **Formulario (P1–P21):** preguntas que ella puede contestar sola, sin ayuda y sin mostrarte nada. Casi todas de opción múltiple, porque una opción se elige en 2 segundos y una respuesta escrita cuesta.
- **Reunión (P22–P36):** preguntas que necesitan **ver algo** ("mostrame cómo hacés un remito"), **repreguntar** según la respuesta, o que son **delicadas** (plata). También las que ella no sabría contestar sin entender primero para qué sirven.
- **Contador (P37–P42):** preguntas fiscales. Si se las hacés a ella, lo más probable es que conteste "no sé" y se sienta mal. Además, un error acá tiene consecuencias legales.

### 0.3 Cómo las ordené dentro del formulario

1. **De lo fácil a lo difícil.** Arranca con "¿a qué se dedica tu taller?". Así entra en confianza antes de las preguntas más técnicas.
2. **Agrupadas por tema, siguiendo sus propios circuitos:** su taller → facturas → cobros y pagos → lo que le gustaría. Las preguntas que saltan de tema cansan.
3. **Las abiertas (tipo "contame") van al final y son opcionales.** Si abandona a la mitad, igual tenés las cerradas.
4. **Ninguna pregunta es obligatoria.** Una pregunta obligatoria que no sabe contestar la frena y la hace abandonar.

### 0.4 Cuántas preguntas

El formulario tiene 21 preguntas, de las cuales 15 son cerradas. Calculo 10–15 minutos. Más que eso ya es mucho para alguien que no es técnica y lo hace en un rato libre. Lo que no entra no se pierde: va a la reunión, que tiene su propia guía (Tarea 4).

### 0.5 Qué significa cada campo

- **Por qué importa / qué afecta:** la parte del sistema que depende de la respuesta.
- **BLOQUEANTE:** sin esta respuesta no se puede diseñar esa parte. Las bloqueantes se persiguen hasta tener respuesta.
- **Respuestas probables → impacto:** así ya sabés qué va a cambiar según lo que diga, y podés repreguntar en el momento.
- **¿Contador?:** si la puede responder mejor su contador.
- **Estado / Respuesta:** para completar vos. Estados sugeridos: `PENDIENTE`, `RESPONDIDA`, `PARCIAL` (hay que repreguntar), `DESCARTADA` (no aplica).

---

## 1. Formulario (P1–P21)

### Bloque A: Tu taller

#### P1. ¿A qué se dedica el taller? ¿Qué hacen y a quién le venden?
- **Por qué importa / qué afecta:** define el vocabulario, qué documentos existen (¿hay presupuestos?, ¿órdenes de trabajo?), si vende servicios o productos (¿hace falta stock?) y si sus clientes son empresas o particulares.
- **BLOQUEANTE:** No, pero orienta todas las demás.
- **Respuestas probables → impacto:**
  - *Trabaja por encargo para otras empresas* (metalúrgica, mecanizado, textil, carpintería): clientes empresas, cuenta corriente habitual, pagos a 30/60 días. Las cuentas corrientes pasan a ser el corazón del sistema.
  - *Atiende particulares* (taller mecánico, arreglos): más cobro al contado. Probablemente importe más la orden de trabajo que la cuenta corriente.
  - *Mezcla:* hay que contemplar ambos tipos de cliente.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P2. ¿Quiénes van a usar el sistema?
- **Por qué importa / qué afecta:** la **arquitectura** (cómo se organiza el sistema por dentro y dónde corre), si hacen falta usuarios con contraseña, permisos y un registro de quién hizo qué.
- **BLOQUEANTE:** Sí, para el diseño.
- **Respuestas probables → impacto:**
  - *Solo ella:* un único usuario, sin permisos, bastante más simple.
  - *Ella y una persona más:* usuarios y contraseñas. Hay que pensar qué pasa si los dos cargan al mismo tiempo.
  - *Varias personas:* permisos por rol (quién puede ver saldos, quién puede anular un recibo) y registro de cambios.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P3. ¿Desde dónde necesitás usarlo?
- **Por qué importa / qué afecta:** si el sistema puede vivir en una sola computadora o tiene que estar en internet. Esto cambia costos mensuales, seguridad y qué pasa cuando se corta internet.
- **BLOQUEANTE:** Sí, para el diseño.
- **Respuestas probables → impacto:**
  - *Solo la PC del taller:* puede funcionar sin internet. Hay que resolver los backups (copias de seguridad) sí o sí.
  - *También desde casa o el celular:* tiene que estar accesible por internet. Eso implica un costo mensual de servidor, cuidar la seguridad y que se vea bien en pantallas chicas.
  - *Hoy solo el taller, pero "capaz más adelante":* conviene diseñar pensando en que puede crecer.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P4. ¿Con qué impresora imprimís los remitos? (marca y modelo)
- **Por qué importa / qué afecta:** el módulo de impresión. No es lo mismo imprimir en una impresora láser o de chorro de tinta con hoja suelta que en una **matricial** (la de agujas, ruidosa, que golpea el papel) con **formulario continuo** (papel en tira, con agujeritos a los costados).
- **BLOQUEANTE:** Sí, para diseñar la impresión. No para empezar el resto.
- **Respuestas probables → impacto:**
  - *Láser o chorro de tinta:* hojas sueltas. Hay que calibrar márgenes en cada impresora.
  - *Matricial:* probablemente use papel continuo con copias. La impresión es más técnica y hay que probarla en su máquina.
  - *No sabe:* pedile una foto de la impresora (materiales).
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P5. El remito preimpreso, ¿tiene copias?
- **Por qué importa / qué afecta:** relacionado con P4. El papel **autocopiativo** (el que copia sin carbónico) necesita que la impresora *golpee* el papel para que la copia salga. Hasta donde sé, con una láser la copia sale en blanco. Lo mismo va a valer para los recibos.
- **BLOQUEANTE:** No, pero condiciona P4.
- **Respuestas probables → impacto:**
  - *Solo original:* cualquier impresora sirve.
  - *Original + duplicado autocopiativo:* casi seguro necesita impresora matricial. Hay que mantenerla.
  - *Imprime dos veces:* está bien, pero la numeración tiene que ser la misma en las dos copias.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

### Bloque B: Facturas

#### P6. ¿Cómo hacés hoy las facturas?
- **Por qué importa / qué afecta:** **la decisión más grande del proyecto.** Define si nuestro sistema *emite* facturas o solo *registra* las que ella hace por otro lado.
- **BLOQUEANTE:** Sí.
- **Respuestas probables → impacto:**
  - *En la página de ARCA (Comprobantes en línea):* lo más probable en un negocio chico. Primera versión: ella sigue facturando ahí y carga la factura en nuestro sistema (doble carga, pero simple). Más adelante se puede evaluar evitar esa doble carga.
  - *Con un programa de facturación:* hay que ver qué hace ese programa. **Puede que ya tenga cuentas corrientes y ella no lo sepa.** También hay que ver si permite sacar los datos (exportar).
  - *Se las hace el contador:* los datos le llegan tarde o no le llegan. Hay que ver cómo se entera ella de lo facturado.
  - *A mano, en talonario:* hay que consultar al contador si eso es válido en su caso.
- **¿Contador?:** Parcialmente (P42).
- Estado: PENDIENTE
- Respuesta:

#### P7. ¿Sos monotributista o responsable inscripta en IVA?
- **Por qué importa / qué afecta:** qué tipo de factura emite y recibe, si los montos llevan IVA separado, cuánto pesan el libro IVA y las retenciones.
- **BLOQUEANTE:** Sí, para diseñar comprobantes y montos.
- **Respuestas probables → impacto:**
  - *Monotributo:* emite factura C, sin IVA discriminado. Más simple.
  - *Responsable Inscripta:* facturas A y B, cada monto con neto + IVA. Más probable que haya retenciones de por medio.
  - *No sé:* totalmente normal. Va al contador.
- **¿Contador?:** Sí, confirmarlo siempre con él o ella.
- Estado: PENDIENTE
- Respuesta:

#### P8. Más o menos, ¿cuántos de estos hacés por mes? (facturas, remitos, cobros, pagos a proveedores)
- **Por qué importa / qué afecta:** el tamaño del problema. También te dice si **vale la pena un sistema** o alcanza con una planilla bien armada.
- **BLOQUEANTE:** No, pero define cuánto esfuerzo invertir.
- **Respuestas probables → impacto:**
  - *Menos de 10 de cada uno:* la solución puede ser muy simple. Un profesional se lo dice aunque eso achique el proyecto.
  - *Decenas a pocos cientos:* un sistema chico se justifica. Importan las búsquedas y los reportes.
  - *Muchos cientos:* importan la velocidad de carga, los atajos y quizás importar datos en vez de tipearlos.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P9. En el audio dijiste "cargar la factura en un mensual". ¿A qué te referías?
- **Por qué importa / qué afecta:** puede ser un reporte, una exportación para el contador o una planilla que ya existe y hay que reemplazar.
- **BLOQUEANTE:** Sí, para esa funcionalidad.
- **Respuestas probables → impacto:**
  - *Una planilla con las ventas del mes:* reporte mensual dentro del sistema.
  - *Lo que le mando al contador:* hay que generar una salida en el formato que pida el contador (P39).
  - *Un resumen para ver cómo vengo:* un tablero de totales.
- **¿Contador?:** Parcialmente.
- Estado: PENDIENTE
- Respuesta:

### Bloque C: Cobros y pagos

#### P10. Tus clientes, ¿te pagan en el momento o después?
- **Por qué importa / qué afecta:** si la cuenta corriente de clientes es central o secundaria.
- **BLOQUEANTE:** Sí, para priorizar.
- **Respuestas probables → impacto:**
  - *Casi todos en el momento:* la cuenta corriente de clientes pierde peso. El foco pasa a los proveedores y a los recibos.
  - *Casi todos después (a 15, 30 o 60 días):* la cuenta corriente de clientes es el corazón. Aparecen los vencimientos y los reclamos de pago.
  - *Mezcla:* hay que soportar las dos cosas.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P11. ¿Cómo te pagan tus clientes y cómo les pagás a tus proveedores? (efectivo, transferencia, cheque, e-cheq, tarjeta)
- **Por qué importa / qué afecta:** qué datos lleva cada recibo y cada orden de pago. Además, si aparecen cheques, hay que seguirlos: cuándo se pueden cobrar, si se depositaron, si se usaron para pagar a otro.
- **BLOQUEANTE:** No, pero puede agregar un módulo entero.
- **Respuestas probables → impacto:**
  - *Solo transferencia:* simple. Alcanza con fecha, monto y banco.
  - *Cheques o e-cheq:* hace falta una "cartera de cheques" (P30).
  - *Efectivo:* conviene pensar en un registro de caja más adelante.
  - *Varios medios en un mismo pago:* cada recibo u orden de pago tiene que admitir varios medios.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P12. ¿Pasa que te paguen (o que pagues) una parte de una factura, o varias facturas juntas en un solo pago?
- **Por qué importa / qué afecta:** el **modelo de datos** de la cuenta corriente, es decir, cómo se guardan internamente las facturas, los pagos y su relación. Es la base de todo lo demás.
- **BLOQUEANTE:** Sí.
- **Respuestas probables → impacto:**
  - *Siempre factura completa, un pago por factura:* cada pago cancela una factura. Muy simple.
  - *Pagos parciales o de varias facturas:* hace falta **imputación** (decir qué parte de cada pago cancela qué factura) y saldo pendiente por factura.
  - *Pagos a cuenta, sin factura:* hay que manejar saldos a favor que después se aplican.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P13. Hoy, ¿cómo sabés cuánto te debe cada cliente y cuánto le debés a cada proveedor?
- **Por qué importa / qué afecta:** la **migración** (pasar lo que existe al sistema nuevo) y los **saldos iniciales**. Además, te muestra a qué está acostumbrada.
- **BLOQUEANTE:** No para diseñar. Sí para la puesta en marcha.
- **Respuestas probables → impacto:**
  - *Planilla de Excel:* se puede partir de ahí. También te muestra qué columnas le importan.
  - *Cuaderno:* los saldos iniciales se cargan a mano.
  - *Mirando el banco o de memoria:* hay que reconstruir los saldos antes de arrancar. Es una tarea en sí misma, con ella o con el contador.
- **¿Contador?:** Puede ayudar a reconstruir saldos.
- Estado: PENDIENTE
- Respuesta:

#### P14. Cuando un cliente te paga, ¿le das un recibo? ¿Cómo lo hacés?
- **Por qué importa / qué afecta:** si ya existe un formato y una numeración de recibos que respetar, o si se diseñan desde cero.
- **BLOQUEANTE:** Sí, para el módulo de recibos.
- **Respuestas probables → impacto:**
  - *Talonario preimpreso, a mano:* ya hay formato y numeración. Hay que confirmar con el contador si tiene exigencias (P37).
  - *No hago recibos:* se diseñan de cero. Hay que preguntarle si de verdad quiere preimpreso o si le sirve imprimir el recibo **completo en hoja blanca** o mandarlo en PDF. Es mucho más fácil de mantener que calibrar un preimpreso, **si lo fiscal lo permite** (P37).
  - *Solo si me lo piden:* uso poco frecuente. Quizás no sea la prioridad.
- **¿Contador?:** Parcialmente.
- Estado: PENDIENTE
- Respuesta:

#### P15. ¿Qué datos te gustaría que tenga la orden de pago?
- **Por qué importa / qué afecta:** el diseño del documento de orden de pago.
- **BLOQUEANTE:** No. Hay un formato estándar razonable para proponerle.
- **Respuestas probables → impacto:** casi seguro fecha, proveedor, facturas que se pagan, monto y medio de pago. Si agrega *datos de la transferencia* o *firma*, hay que agregar esos campos. Si menciona *retenciones*, es una alerta: va al contador (P38, P40).
- **¿Contador?:** Si hay retenciones, sí.
- Estado: PENDIENTE
- Respuesta:

#### P16. ¿Cómo le harías llegar la orden de pago al proveedor?
- **Por qué importa / qué afecta:** el formato de salida.
- **BLOQUEANTE:** No.
- **Respuestas probables → impacto:**
  - *PDF por WhatsApp o mail:* generar PDF y hacer fácil compartirlo.
  - *Impresa:* formato de impresión.
  - *No se la mando, es para mí:* alcanza con un registro interno prolijo.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

### Bloque D: Lo que te gustaría

#### P17. ¿Qué es lo que más tiempo te lleva o más te molesta hoy de la parte administrativa?
- **Por qué importa / qué afecta:** revela el **dolor real**, que a veces no coincide con lo que pidió. Define prioridades y es donde un sistema (o la IA) genera más valor.
- **BLOQUEANTE:** No, pero es de las más valiosas.
- **Respuestas probables → impacto:** "saber quién me debe" → cuentas corrientes y reportes primero. "Cargar todo dos veces" → evitar doble carga. "Encontrar papeles" → búsqueda y archivo digital.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P18. Si pudiéramos resolver una sola cosa primero, ¿cuál sería?
- **Por qué importa / qué afecta:** define la **primera entrega** (el MVP). Hace que tenga algo útil rápido en vez de esperar todo junto.
- **BLOQUEANTE:** Sí, para el plan de trabajo.
- **Respuestas probables → impacto:** Recibos → primera entrega = recibos + impresión. Órdenes de pago → proveedores primero. Cuentas corrientes → modelo de datos primero, documentos después.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P19. ¿Hay alguna tarea repetitiva que te gustaría que haga la computadora por vos? (acá entra lo de la IA)
- **Por qué importa / qué afecta:** convierte "me interesa la IA" en un caso concreto. **No se pregunta "¿qué querés hacer con IA?"**: se pregunta por la tarea. Después vemos si la IA es la herramienta adecuada o si alcanza una automatización común.
- **BLOQUEANTE:** No. Es opcional.
- **Respuestas probables → impacto:** "cargar las facturas de proveedores" → lectura automática de PDFs, un buen candidato para IA. "Reclamar pagos" → recordatorios automáticos, no hace falta IA. "Nada, no sé" → está perfecto: la IA se deja para una etapa posterior.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P20. ¿Trabajás con un contador? ¿Te parece bien que en algún momento hable con él o ella?
- **Por qué importa / qué afecta:** todas las preguntas fiscales (P37–P42) dependen de esto.
- **BLOQUEANTE:** Sí, para lo fiscal.
- **Respuestas probables → impacto:**
  - *Sí:* se coordina una charla corta con el contador.
  - *Sí, pero prefiere preguntarle ella:* le mandás las preguntas escritas para que se las reenvíe.
  - *No tiene:* el sistema se diseña **sin funciones fiscales**, y hay que ser muy conservadores.
- **¿Contador?:** —
- Estado: PENDIENTE
- Respuesta:

#### P21. ¿Para cuándo te gustaría tenerlo funcionando?
- **Por qué importa / qué afecta:** el tamaño de la primera entrega y la propuesta.
- **BLOQUEANTE:** No para diseñar. Sí para la propuesta.
- **Respuestas probables → impacto:** "lo antes posible" → primera entrega mínima. "Sin apuro" → etapas más cómodas. "Para una fecha" (por ejemplo, principio de año) → se planifica hacia atrás desde esa fecha.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

---

## 2. Para la reunión presencial (P22–P36)

No van en el formulario porque hay que **ver**, **repreguntar** o porque son **delicadas**. La Tarea 4 va a tener la guía de cómo encararlas.

#### P22. Mostrame cómo hacés un remito hoy, de principio a fin.
- **Por qué importa / qué afecta:** observarla trabajar muestra pasos que ella no contaría porque los tiene automatizados: dónde busca los datos del cliente, qué hace si se equivoca, cómo acomoda la hoja en la impresora.
- **BLOQUEANTE:** Sí, para diseñar la carga y la impresión.
- **Respuestas probables → impacto:** si copia datos de otro lado, hace falta un catálogo de clientes y productos. Si ajusta la hoja a mano en cada impresión, la calibración es crítica.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P23. ¿Cada remito termina en una factura? ¿Una factura puede juntar varios remitos? ¿Hay remitos que nunca se facturan?
- **Por qué importa / qué afecta:** la relación entre remito y factura en el modelo de datos, y si conviene el reporte "remitos pendientes de facturar".
- **BLOQUEANTE:** Sí, para vincular remitos con facturas.
- **Respuestas probables → impacto:** 1 a 1 → vínculo simple. Varios en una factura → relación varios-a-uno. Hay remitos sin facturar → reporte de pendientes (útil para no olvidarse de cobrar).
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P24. Los remitos (y recibos, si hay) ¿vienen numerados de imprenta? ¿Qué hacés si se arruina una hoja?
- **Por qué importa / qué afecta:** numeración y **anulación** de comprobantes. Si la numeración viene impresa, el sistema tiene que seguirla y no inventar la suya. Una hoja arruinada es un comprobante anulado que tiene que quedar registrado.
- **BLOQUEANTE:** Sí, para el módulo de impresión.
- **Respuestas probables → impacto:** número impreso → el sistema pide o sugiere el número de la próxima hoja. Sin número → el sistema numera solo.
- **¿Contador?:** Sí, sobre las exigencias formales (P37).
- Estado: PENDIENTE
- Respuesta:

#### P25. ¿Cuántos clientes y proveedores activos tenés? ¿Dónde están sus datos (CUIT, dirección, teléfono)?
- **Por qué importa / qué afecta:** carga inicial de clientes y proveedores (migración).
- **BLOQUEANTE:** No para diseñar. Sí para la puesta en marcha.
- **Respuestas probables → impacto:** en un Excel → se pueden importar. En su cabeza o en facturas viejas → carga manual, hay que planificar el tiempo.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P26. ¿Desde cuándo arrancamos? ¿Cargamos lo viejo o empezamos con "a tal fecha me deben esto"?
- **Por qué importa / qué afecta:** la estrategia de puesta en marcha.
- **BLOQUEANTE:** No para diseñar. Sí para arrancar.
- **Respuestas probables → impacto:** saldos iniciales a una fecha → rápido y recomendable. Cargar historia → mucho más trabajo, solo si hay una razón clara (por ejemplo, ver facturas viejas impagas).
- **¿Contador?:** Puede validar los saldos iniciales.
- Estado: PENDIENTE
- Respuesta:

#### P27. Cuando hay una devolución, un descuento o un error en una factura, ¿cómo lo resolvés?
- **Por qué importa / qué afecta:** si hay que manejar **notas de crédito y de débito** en las cuentas corrientes.
- **BLOQUEANTE:** No, pero se agrega al modelo de datos.
- **Respuestas probables → impacto:** "hago nota de crédito" → hay que registrarlas. "Nunca pasa" → se deja para después.
- **¿Contador?:** Parcialmente.
- Estado: PENDIENTE
- Respuesta:

#### P28. ¿Tus facturas y las de tus proveedores tienen vencimiento? ¿Tenés plazos acordados con cada uno?
- **Por qué importa / qué afecta:** alertas de vencimiento y reportes de antigüedad de saldos (cuánto se debe y hace cuánto).
- **BLOQUEANTE:** No.
- **Respuestas probables → impacto:** sí → campo de vencimiento y alertas ("esta semana vencen…"). No → se omite.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P29. ¿Alguna vez facturás, cobrás o pagás en dólares? ¿Ajustás precios seguido?
- **Por qué importa / qué afecta:** si el sistema tiene que manejar varias monedas y tipo de cambio. En Argentina puede pasar y cambia bastante el modelo de datos.
- **BLOQUEANTE:** Sí, si la respuesta es "sí".
- **Respuestas probables → impacto:** solo pesos → simple. Dólares a veces → moneda por comprobante y tipo de cambio. Esto hay que saberlo **antes** de diseñar.
- **¿Contador?:** Parcialmente.
- Estado: PENDIENTE
- Respuesta:

#### P30. (Solo si usa cheques) ¿Necesitás seguir los cheques: cuándo se pueden cobrar, si los depositaste, si los usaste para pagar?
- **Por qué importa / qué afecta:** agrega un módulo de "cartera de cheques".
- **BLOQUEANTE:** No. Puede quedar para una etapa posterior.
- **Respuestas probables → impacto:** sí → módulo propio. No → alcanza con registrar el número de cheque en el recibo o la orden de pago.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P31. ¿Qué te gustaría poder consultar rápido? (quién me debe, a quién le debo, qué vence, cuánto facturé en el mes…)
- **Por qué importa / qué afecta:** los **reportes**. Muchas veces son lo que la clienta realmente mira todos los días.
- **BLOQUEANTE:** No.
- **Respuestas probables → impacto:** cada respuesta es un reporte o una pantalla. Priorizar 2 o 3.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P32. Además de remitos, facturas, recibos y pagos, ¿qué otros papeles o tareas administrativas hay en el taller? (presupuestos, órdenes de trabajo, stock, caja, sueldos…)
- **Por qué importa / qué afecta:** detecta el **alcance futuro** ("siento que hay más cosas para pulir"). No es para agregarlo ya, sino para diseñar sin cerrarle la puerta.
- **BLOQUEANTE:** No.
- **Respuestas probables → impacto:** cada respuesta va a una lista de "etapas futuras". Ojo: **sueldos** es un tema fiscal y laboral delicado que en general no conviene meter en un sistema propio.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P33. ¿Quién te ayuda hoy si se rompe la compu? ¿Hay buena conexión a internet en el taller? ¿Hacés copias de seguridad del Excel?
- **Por qué importa / qué afecta:** mantenimiento y continuidad. Si todo pasa a un sistema y se pierde, se pierde la administración del taller.
- **BLOQUEANTE:** Sí, para decidir dónde corre el sistema (junto con P3).
- **Respuestas probables → impacto:** internet inestable → el sistema tiene que funcionar sin conexión o tolerar cortes. Nadie la ayuda → vos sos el soporte y hay que acordarlo (P35).
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P34. (Si hay más de un usuario) ¿Hay información que otras personas no deberían ver o no deberían poder cambiar?
- **Por qué importa / qué afecta:** los permisos.
- **BLOQUEANTE:** Sí, si P2 = varias personas.
- **Respuestas probables → impacto:** "los saldos solo los veo yo" → permisos por rol.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

#### P35. ¿Cuánto tenés pensado invertir? ¿Estás dispuesta a pagar un costo mensual (servidor, mantenimiento)?
- **Por qué importa / qué afecta:** el alcance real y la arquitectura. Una solución en internet suele tener costo mensual. Además, tu soporte también tiene un costo.
- **BLOQUEANTE:** Sí, para la propuesta.
- **Respuestas probables → impacto:** presupuesto chico → la primera etapa tiene que ser mínima y con costos mensuales bajos o nulos. Presupuesto razonable → se puede planificar por etapas.
- **¿Contador?:** No.
- **Nota:** es un tema delicado. Va en persona, nunca en un formulario. Si todavía no sabés cuánto cobrar, preguntale primero qué espera, sin tirar un número (ver "Cosas que tenés que averiguar vos").
- Estado: PENDIENTE
- Respuesta:

#### P36. Dentro de unos meses, ¿cómo te darías cuenta de que el sistema te sirvió?
- **Por qué importa / qué afecta:** el **criterio de éxito**, es decir, qué tiene que pasar para que el proyecto se considere bien hecho. Es tu referencia para la aceptación y para defender el trabajo.
- **BLOQUEANTE:** No, pero ordena todo lo demás.
- **Respuestas probables → impacto:** "saber en un minuto cuánto me deben" → se prioriza ese reporte. "No escribir más a mano" → se prioriza la emisión de documentos.
- **¿Contador?:** No.
- Estado: PENDIENTE
- Respuesta:

---

## 3. Para el contador (P37–P42)

Se las hacés vos al contador, o se las mandás a la clienta para que las reenvíe. Todas tocan normativa. **No las contestes vos por suposición.**

#### P37. ¿Qué requisitos tienen sus remitos y recibos? ¿Tienen que ser fiscales, con CAI, electrónicos? ¿Qué datos son obligatorios?
- **Por qué importa / qué afecta:** si el sistema puede imprimir en hoja blanca o si hace falta preimpreso de imprenta, y qué datos no pueden faltar.
- **BLOQUEANTE:** Sí, para recibos y remitos.
- **Respuestas probables → impacto:** preimpreso con CAI obligatorio → el sistema respeta la numeración de la imprenta. Admite comprobante no fiscal → mucha más libertad de formato.
- **¿Contador?:** Sí.
- Estado: PENDIENTE
- Respuesta:

#### P38. ¿Ella es agente de retención o percepción (de IVA, Ganancias o Ingresos Brutos)? ¿Sus clientes le retienen a ella?
- **Por qué importa / qué afecta:** si es agente, cada orden de pago puede llevar retenciones y certificados. Si le retienen, los recibos cobran menos que la factura y la diferencia tiene que quedar registrada.
- **BLOQUEANTE:** Sí, para órdenes de pago y recibos.
- **Respuestas probables → impacto:** no es agente y no le retienen → simple. Es agente → módulo de retenciones (complejo; hay que evaluar si conviene hacerlo o que lo siga resolviendo el contador). Le retienen → campo de retenciones sufridas en el recibo.
- **¿Contador?:** Sí.
- Estado: PENDIENTE
- Respuesta:

#### P39. ¿Qué información le pedís cada mes y en qué formato?
- **Por qué importa / qué afecta:** una exportación que le ahorre trabajo a ella y al contador. Es probablemente el "mensual" (P9).
- **BLOQUEANTE:** No.
- **Respuestas probables → impacto:** "mandame las facturas en PDF" → exportación de archivos. "Un Excel con columnas X" → exportación en ese formato.
- **¿Contador?:** Sí.
- Estado: PENDIENTE
- Respuesta:

#### P40. ¿La orden de pago tiene algún requisito formal? ¿Tiene que ir acompañada de algo?
- **Por qué importa / qué afecta:** el diseño de la orden de pago.
- **BLOQUEANTE:** No, salvo que haya retenciones (P38).
- **Respuestas probables → impacto:** "es un documento interno, libre" → se diseña a gusto de ella. "Con certificado de retención" → depende de P38.
- **¿Contador?:** Sí.
- Estado: PENDIENTE
- Respuesta:

#### P41. ¿Cuánto tiempo hay que conservar los comprobantes y registros, y en qué forma?
- **Por qué importa / qué afecta:** los backups y el archivo. El sistema no puede permitir borrar lo que la ley exige guardar. **No sé el plazo exacto que aplica en su caso y no lo voy a inventar.**
- **BLOQUEANTE:** No para empezar. Sí antes de poner en producción.
- **Respuestas probables → impacto:** define políticas de conservación y que los comprobantes se anulen en vez de borrarse.
- **¿Contador?:** Sí.
- Estado: PENDIENTE
- Respuesta:

#### P42. ¿Cómo factura hoy: modalidad, puntos de venta? ¿Le convendría otra forma si el sistema lo permitiera?
- **Por qué importa / qué afecta:** complementa P6. Informa si en el futuro tiene sentido que el sistema emita facturas electrónicas.
- **BLOQUEANTE:** No, para la primera etapa.
- **Respuestas probables → impacto:** si el contador prefiere que siga como está → el sistema solo registra facturas. Si ve bien integrar → etapa futura, con estudio aparte.
- **¿Contador?:** Sí.
- Estado: PENDIENTE
- Respuesta:

---

## 4. Cosas que tenés que averiguar vos (no la clienta)

| # | Qué averiguar | Para qué |
|---|---------------|----------|
| A1 | **Sistemas de gestión que ya existen** para pymes o talleres en Argentina, y cuánto cuestan. | Un profesional siempre evalúa **"comprar vs. construir"**. Si existe algo que ya resuelve el 80% por poca plata, tenés que poder decírselo, o poder explicar por qué lo tuyo es mejor para ella. Es tu principal argumento frente a la clienta. |
| A2 | Cómo funciona **"Comprobantes en línea"** de ARCA, desde el lado de un usuario. | Entender cómo factura ella hoy (P6) sin depender de su explicación. |
| A3 | El **régimen de emisión de comprobantes** de ARCA. Creo que es la **RG 1415**, pero verificalo; no estoy segura de que sea la vigente ni de sus actualizaciones. | Llegar a la charla con el contador sabiendo de qué habla (P37). No es para decidir sola. |
| A4 | Lo básico de la **Ley 25.326 de Protección de Datos Personales**. | Saber qué cuidados tener con los datos de clientes y proveedores de ella. |
| A5 | Cómo se **calibra la impresión sobre preimpresos**: medir posiciones en milímetros y compensar diferencias entre impresoras. | Entender el problema técnico antes de elegir cómo resolverlo. |
| A6 | **Cuánto cobrar y cómo presupuestar**: precio por etapa, por hora o abono de mantenimiento. Preguntale a docentes o a colegas que hagan trabajos freelance. | Tener una respuesta cuando salga P35. Ir a la reunión sin esto es un error típico. |
| A7 | Qué **modelos de orden de pago y recibo** usan otras empresas. Seguramente la clienta **recibe** órdenes de pago de sus propios clientes. | Proponerle un formato concreto en vez de preguntarle "¿qué querés que tenga?". |

---

## 5. Materiales que le pedimos y para qué sirve cada uno

Se piden por WhatsApp (ver `mensaje-clienta.txt`), no por el formulario: subir archivos en Google Forms obliga a iniciar sesión con Google (hasta donde sé) y la puede trabar. Puede tapar nombres y montos en todos.

| # | Material | Para qué te sirve |
|---|----------|-------------------|
| M1 | **Foto de un remito preimpreso vacío y de uno ya impreso** | Ver los casilleros, qué datos lleva y cómo cae la impresión. Además, **pedile que te dé una hoja física vacía en la reunión**: para calibrar la impresión se mide sobre papel real, no sobre una foto (que deforma las medidas). |
| M2 | **Una copia del Excel de remitos** (puede ser con datos inventados) | Ver cómo está armado: qué campos carga, si tiene fórmulas, cómo resolvió la impresión. Es tu mejor "especificación" de lo que ya funciona. |
| M3 | **Una factura que ella haya emitido** (foto o PDF) | Ver tipo de factura (A, B o C), punto de venta, si es electrónica (CAE) y desde dónde se emitió. Ayuda con P6 y P7. |
| M4 | **Un recibo, si hace** | Formato y numeración existentes (P14). |
| M5 | **Un comprobante de transferencia a un proveedor** | Qué datos del pago ya existen y se pueden copiar a la orden de pago. |
| M6 | **Una factura de un proveedor** | Qué recibe ella. Es la base para cargar facturas de proveedores y el candidato número uno para automatizar con IA (P19). |
| M7 | **Lo que use hoy para saber cuánto le deben y cuánto debe** (planilla o foto del cuaderno) | Migración y saldos iniciales (P13). |
| M8 | **El "mensual", si existe** | Entender P9 sin adivinar. |
| M9 | **Foto de la impresora**, donde se vea la marca y el modelo | P4 y P5. |
| M10 | **Si algún cliente le manda órdenes de pago cuando le paga, una de ejemplo** | Un modelo real para proponerle el formato de sus propias órdenes de pago. |
