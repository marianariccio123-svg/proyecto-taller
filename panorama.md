# Panorama del Proyecto Albertina

> Documento de orientación. Objetivo: que entiendas dónde estás parada antes de hablar con la clienta.
> Convenciones:
> - `SUPUESTO:` algo que doy por cierto para poder avanzar y que hay que confirmar.
> - **(a confirmar con el contador)**: algo que depende de normativa o de la situación fiscal de la clienta y que no debo afirmar yo.
> - Si digo "no estoy seguro", es literal: no lo tomes como dato.

---

## 1. Cómo se hace un sistema para un cliente, de principio a fin

Un sistema no empieza con código. Empieza por **entender un problema** y termina con **una persona usándolo todos los días**, con alguien que lo mantenga. En el medio hay etapas. En la facultad se ven como teoría (cascada, iterativo, ágil). Acá te las cuento como pasan en la práctica con un cliente chico.

### Las etapas

| # | Etapa | Qué se hace | Qué se entrega | ¿Dónde estamos? |
|---|-------|-------------|----------------|-----------------|
| 0 | **Primer contacto** | La clienta cuenta el problema a grandes rasgos. | Nada formal. Como mucho, notas. | ✅ Hecho (el audio) |
| 1 | **Relevamiento** | Entender cómo trabaja hoy, qué le duele y qué necesita. Preguntar, observar, juntar documentos reales. | Documento de relevamiento: circuitos actuales, documentos, reglas, volumen, usuarios, problemas. | 👉 **Estamos acá, al principio** |
| 2 | **Alcance y propuesta** | Decidir qué entra en el sistema y qué no, en qué orden y cuánto cuesta. | Propuesta con alcance, etapas, plazos y presupuesto. Idealmente firmada o aceptada por escrito. | Próxima |
| 3 | **Diseño** | Decidir cómo va a funcionar: pantallas, datos que se guardan, reglas, tecnología, dónde corre. | Modelo de datos, bocetos de pantallas, decisiones técnicas justificadas. | |
| 4 | **Desarrollo iterativo** | Construir de a partes chicas y mostrárselas a la clienta seguido. | Versiones parciales que ella prueba y comenta. | |
| 5 | **Pruebas** | Probar vos (con casos pensados) y que pruebe ella con casos reales. | Lista de pruebas hechas y errores corregidos. Su aprobación. | |
| 6 | **Puesta en marcha** | Instalar, cargar los datos iniciales (saldos, clientes, proveedores), capacitarla y acompañar los primeros días. | Sistema funcionando, datos migrados, manual corto, capacitación. | |
| 7 | **Soporte y mantenimiento** | Corregir errores, adaptar a cambios (de normativa, del negocio), hacer backups, pedidos nuevos. | Acuerdo de soporte: qué incluye, cuánto cuesta, cómo te contacta. | |

### Términos que aparecen en la tabla

- **Relevamiento:** entender en detalle cómo funciona hoy el negocio antes de proponer nada. *Ejemplo:* no alcanza con saber que "hace recibos". Hay que saber cuántos por mes, qué datos llevan, quién los hace y qué pasa con la copia.
- **Alcance:** la lista explícita de lo que el sistema **va a hacer** y lo que **no**. Es tu principal protección frente al "ya que estás, agregale…". *Ejemplo:* "Incluye recibos y órdenes de pago. No incluye facturación electrónica."
- **Requerimiento funcional / no funcional:** el funcional es *qué hace* el sistema ("emitir un recibo"). El no funcional es *cómo tiene que comportarse* ("que se pueda usar desde el celular", "que no se pierdan datos si se rompe la compu").
- **Iterativo:** en vez de desaparecer 3 meses y volver con todo, entregás partes chicas cada pocas semanas. Así los malentendidos aparecen temprano, cuando corregirlos es barato.
- **MVP (Producto Mínimo Viable):** la versión más chica que ya le sirve de verdad. *Ejemplo:* solo recibos impresos en el preimpreso, sin cuentas corrientes todavía.
- **Prueba de aceptación (UAT, *User Acceptance Testing*):** la clienta usa el sistema con casos reales y dice "sí, esto es lo que necesitaba".
- **Migración de datos:** pasar la información que ya existe (clientes, proveedores, saldos que le deben y que debe) al sistema nuevo. Suele subestimarse y lleva tiempo.
- **Backup (copia de seguridad):** copia de los datos guardada en otro lugar, para recuperarlos si algo falla.

### Cosas que un profesional hace y que es fácil saltearse

Te las marco porque me pediste que te avise:

1. **Acuerdo por escrito del alcance y del precio** antes de desarrollar. Aunque sea un mail o un WhatsApp largo que ella confirme. Sin eso, el proyecto crece sin límite y el precio queda desfasado.
2. **Decidir cómo vas a cobrar tu trabajo**: precio cerrado por etapa, por hora o abono mensual de mantenimiento. No hace falta decidirlo hoy, pero sí antes de la etapa 2.
3. **Datos personales:** vas a manejar datos de clientes y proveedores de ella (CUIT, montos, cuentas bancarias). En Argentina existe la Ley 25.326 de Protección de Datos Personales. No te puedo decir con precisión qué obligaciones concretas te genera este proyecto. Sí te digo que conviene tratar esos datos con cuidado desde el día uno: no compartirlos, no subirlos a lugares públicos, y usar ejemplos tapados cuando pidas ayuda.
4. **Mantenimiento:** el sistema no "se termina". La normativa fiscal cambia, las impresoras cambian y ella va a querer cosas nuevas. Hay que pensar desde ahora quién la atiende si algo falla un lunes a la mañana.
5. **Registrar todo:** cada respuesta de la clienta se anota con fecha. Por eso guardamos el audio tal cual.

---

## 2. Lo que entendí del pedido

### Resumen en una frase

Quiere **dejar de llevar a mano (o en Excel suelto) el seguimiento de lo que le deben sus clientes y lo que ella le debe a sus proveedores**. También quiere **emitir los papeles de ese circuito** (remitos, recibos, órdenes de pago) de forma más prolija y rápida.

### Los dos circuitos que describe

En el audio los mezcla. Dice "circuito de pagos", pero su primer ejemplo es de **ventas** (factura → cuenta corriente de *clientes*). En realidad describe dos circuitos espejados.

#### Circuito A: Ventas y cobros (lo que le deben a ella)

```
  Entrega de trabajo/mercadería
            │
            ▼
       ┌─────────┐   Hoy: Excel + hoja preimpresa (esto YA funciona)
       │ REMITO  │   Documenta QUÉ se entregó.
       └────┬────┘
            │  (¿siempre? ¿un remito por factura? ¿varios? → a preguntar)
            ▼
       ┌─────────┐   ¿Cómo la emite hoy? No lo sabemos.
       │ FACTURA │   Documenta CUÁNTO se le cobra.
       └────┬────┘
            │  "que se cargue en un mensual"   → ¿registro mensual de ventas?
            │  "que se derive a la cuenta corriente del cliente"
            ▼
   ┌────────────────────────────┐
   │ CUENTA CORRIENTE CLIENTE   │   La factura SUMA a lo que el cliente debe.
   └────────────┬───────────────┘
                ▲
                │  El recibo RESTA de lo que el cliente debe.
       ┌────────┴┐
       │ RECIBO  │   Documenta que el cliente PAGÓ.
       └─────────┘   Quiere imprimirlo como el remito, pero "más fácil que Excel".
```

#### Circuito B: Compras y pagos (lo que ella debe)

```
       ┌────────────────────┐
       │ FACTURA PROVEEDOR  │   El proveedor le factura a ella.
       └─────────┬──────────┘
                 │  SUMA a lo que ella le debe al proveedor.
                 ▼
   ┌──────────────────────────────┐
   │ CUENTA CORRIENTE PROVEEDOR   │
   └──────────────┬───────────────┘
                  ▲
                  │  RESTA de lo que ella debe.
       ┌──────────┴──────┐
       │ ORDEN DE PAGO   │   NUEVO: hoy no existe. Quiere un documento con formato:
       └──────────┬──────┘   fecha, proveedor, qué factura(s) paga, monto.
                  │
                  ▼
       Transferencia bancaria + comprobante al proveedor (esto ya lo hace).
```

### Cómo se relacionan los documentos

| Documento | ¿Quién lo emite? | ¿Qué prueba? | ¿Mueve la cuenta corriente? | Estado hoy |
|-----------|-----------------|--------------|-----------------------------|------------|
| Remito | Ella | Que entregó algo | En general **no** (no tiene precio o no genera deuda por sí solo). SUPUESTO: a confirmar cómo lo usa ella. | Excel + preimpreso, funciona |
| Factura (venta) | Ella | Que el cliente le debe un monto | **Sí**: aumenta la deuda del cliente | Desconocido |
| Recibo | Ella | Que el cliente pagó | **Sí**: disminuye la deuda del cliente | Quiere sistematizarlo |
| Factura (compra) | El proveedor | Que ella le debe al proveedor | **Sí**: aumenta la deuda con el proveedor | Desconocido |
| Orden de pago | Ella | Que ella pagó (uso interno y para el proveedor) | **Sí**: disminuye la deuda con el proveedor | No existe, lo quiere |
| Comprobante de transferencia | El banco | Que la plata salió | No por sí solo: es el respaldo del pago | Lo manda por WhatsApp o mail |

### Lo que quiere, ordenado

1. **Recibos impresos en papel preimpreso**, como ya hace con los remitos, pero sin depender del Excel.
2. **Órdenes de pago con formato** para sus proveedores.
3. **Cuentas corrientes automáticas** de clientes y de proveedores: que cada factura, recibo u orden de pago actualice el saldo sin cargarlo dos veces.
4. **Algún registro mensual** de facturas (el "mensual").
5. **Algo de inteligencia artificial**, sin idea concreta todavía.
6. Una frase clave del final: *"siento que hay como más cosas para pulir todavía"*. Esto casi seguro va a crecer. Hay que definir bien el alcance.

### Sobre la IA

Ella no pidió nada concreto, y está bien. **No hay que forzar IA en el sistema.** Primero tiene que funcionar lo básico. Cuando conozcamos mejor su día a día, vamos a ver si hay tareas repetitivas que la IA realmente simplifique. *Ejemplos a explorar más adelante (no son promesas):* leer una factura de proveedor en PDF y precargar los datos, o responder preguntas como "¿cuánto me debe tal cliente?". Por ahora es un tema para la reunión, no para el diseño.

---

## 3. Conceptos del dominio que necesitás manejar

Agrupados por tema. Donde la normativa importa y no estoy seguro de los detalles, lo marco.

### 3.1 Documentos comerciales

- **Comprobante:** nombre genérico de cualquier papel (o archivo) que respalda una operación: factura, remito, recibo, nota de crédito. *Ejemplo:* "pasame el comprobante" puede ser cualquiera de ellos.
- **Remito:** acompaña la entrega física de mercadería o de un trabajo. Dice *qué* y *cuánto* (en cantidad) se entregó, no necesariamente el precio. El cliente suele firmar una copia como prueba de que lo recibió. *Ejemplo:* "3 piezas mecanizadas según plano 45", firmado por quien las recibió.
- **Factura:** el documento que dice *cuánto se cobra* por lo vendido. Tiene valor fiscal: es lo que ARCA mira para los impuestos.
- **Recibo:** prueba que alguien *pagó*. Dice quién pagó, cuánto, con qué medio (efectivo, transferencia, cheque) y, muchas veces, qué facturas cancela.
- **Orden de pago (OP):** documento que emite *quien paga* (en este caso, ella). Detalla a qué proveedor le paga, qué facturas cancela, cuánto y con qué medio. Es el "recibo al revés". Hasta donde sé suele ser un documento **interno** y no fiscal, pero **(a confirmar con el contador)**, sobre todo si le corresponde hacer retenciones (ver 3.4).
- **Nota de crédito:** corrige una factura *a favor del cliente*: le resta deuda. *Ejemplo:* facturaste $100.000 y el cliente devolvió una pieza de $20.000; emitís una nota de crédito por $20.000.
- **Nota de débito:** lo contrario, *suma* deuda al cliente. *Ejemplo:* intereses por pago atrasado.
- **Formulario preimpreso:** hojas que vienen de la imprenta con el logo, los datos de la empresa y los casilleros. El sistema solo imprime los datos en los lugares justos. *Ejemplo:* su remito actual.
- **Numeración correlativa:** los comprobantes llevan números seguidos, sin saltos ni repetidos (0001-00000123, 0001-00000124…). En los fiscales es una exigencia formal. En los internos es una buena práctica igual.

### 3.2 Fiscal (Argentina)

Esta es la parte donde más cuidado hay que tener. Te doy lo básico para que no te pierdas en una charla. **Las decisiones concretas las valida su contador.**

- **ARCA (ex AFIP):** el organismo nacional que recauda impuestos. Autoriza las facturas y define qué comprobantes son obligatorios y cómo.
- **CUIT:** número que identifica a cada contribuyente (persona o empresa) ante ARCA. Todo cliente y proveedor que facture tiene uno. *Ejemplo:* 20-12345678-9.
- **Condición frente al IVA:** define qué tipo de factura emite y recibe cada uno. Las más comunes:
  - *Responsable Inscripto (RI):* discrimina IVA en sus facturas.
  - *Monotributista:* régimen simplificado; paga una cuota fija y no discrimina IVA.
  - *Exento* y *Consumidor Final* son otras condiciones posibles.
- **Tipos de factura (A, B, C…):** dependen de la condición de quien emite y de quien recibe. A grandes rasgos: el RI le emite **A** a otro RI y **B** a consumidores finales o monotributistas; el monotributista emite **C**. Hay otros casos, como la **M**. **(a confirmar con el contador cuáles aplican a ella)**.
- **Factura electrónica y CAE:** hoy la mayoría de los contribuyentes emite factura electrónica. Cada factura la autoriza ARCA en el momento, que devuelve un **CAE (Código de Autorización Electrónico)**: un número que la hace válida. *Ejemplo práctico:* si ella hoy factura desde la web de ARCA ("Comprobantes en línea") o con otro programa, el CAE ya lo resuelve eso. **Que nuestro sistema emita facturas electrónicas sería un proyecto en sí mismo** y hay que decidir si entra o no.
- **CAI (Código de Autorización de Impresión):** hasta donde sé, los comprobantes impresos por imprenta (como los remitos preimpresos) llevan un CAI y una fecha de vencimiento que la imprenta tramita ante ARCA. **No estoy seguro de qué exigencias aplican hoy a sus remitos y recibos preimpresos. (a confirmar con el contador)**. Importa porque, si el preimpreso tiene numeración y CAI propios, el sistema tiene que respetar esa numeración.
- **Punto de venta:** es el primer bloque del número de comprobante (el "0001" de 0001-00000123). Identifica desde dónde se emite. Una empresa puede tener varios.
- **Libro IVA / subdiario de ventas y compras:** registro mensual de todas las facturas emitidas y recibidas, que el contador usa para liquidar el IVA. SUPUESTO: el "mensual" del audio podría ser esto, o una planilla propia de control. **Hay que preguntarlo.**
- **Período fiscal:** en IVA es mensual. Por eso el "mensual" tiene sentido: todo se cierra mes a mes.

### 3.3 Cuentas corrientes (el corazón del pedido)

- **Cuenta corriente:** el registro de todos los movimientos con un cliente (o proveedor) y el saldo resultante. Es como un resumen de tarjeta de crédito, pero por cliente.

  *Ejemplo, cuenta corriente del cliente "Metalúrgica X":*

  | Fecha | Comprobante | Debe | Haber | Saldo |
  |-------|-------------|------|-------|-------|
  | 01/09 | Factura A 0001-00000120 | 100.000 | | 100.000 |
  | 05/09 | Factura A 0001-00000125 | 50.000 | | 150.000 |
  | 10/09 | Recibo 0001-00000040 | | 80.000 | 70.000 |

  Metalúrgica X le debe $70.000 a ella.

- **Debe y Haber:** las dos columnas de toda cuenta. En la cuenta de un cliente, lo que *aumenta* lo que nos debe (facturas, notas de débito) va al Debe. Lo que *disminuye* su deuda (recibos, notas de crédito) va al Haber. En la cuenta de un proveedor se invierte: sus facturas van al Haber (le debemos más) y nuestras órdenes de pago al Debe. No hace falta que lo memorices, pero ella o su contador van a usar estas palabras.
- **Saldo:** la diferencia entre Debe y Haber: cuánto se debe en este momento.
- **Imputación (o aplicación) de un pago:** decir *qué factura(s)* cancela un pago. *Ejemplo:* el recibo de $80.000 ¿cancela la factura 120 completa ($100.000)? No: la cancela parcialmente y quedan $20.000 pendientes de esa factura. Es un tema de diseño importante. Ella pidió "qué factura le estamos pagando", así que parece querer imputación por factura, no solo un saldo total.
- **Pago parcial / pago a cuenta:** un pago que no cancela una factura completa (*parcial*) o que se hace sin asociarlo a ninguna factura (*a cuenta*). Pasa mucho en la vida real.
- **Saldo inicial:** lo que cada cliente o proveedor debía el día que se empieza a usar el sistema. Sin esto, las cuentas corrientes arrancan mal. Es parte de la migración.
- **Antigüedad de saldos:** reporte que muestra cuánto se debe y hace cuánto (0–30 días, 31–60, más de 60…). Sirve para saber a quién reclamarle. No lo pidió, pero suele ser muy útil.
- **Condición de venta:** si se vende **al contado** o **en cuenta corriente** (el cliente paga después, por ejemplo a 30 días).

### 3.4 Pagos y bancos

- **Medios de pago:** efectivo, transferencia, cheque, **e-cheq** (cheque electrónico), tarjeta. Un mismo recibo o una misma OP pueden combinar varios. *Ejemplo:* $50.000 por transferencia más un cheque de $30.000.
- **Comprobante de transferencia:** lo que genera el home banking. Es el respaldo bancario del pago, pero no dice qué facturas se pagan. Por eso tiene sentido la orden de pago.
- **Retenciones y percepciones:** mecanismos por los que ARCA o las provincias (a través de Ingresos Brutos) obligan a ciertas empresas a descontar un porcentaje de impuesto al pagar (**retención**) o a sumarlo al cobrar (**percepción**), y depositarlo al fisco. *Ejemplo:* si ella fuera agente de retención, al pagarle $100.000 a un proveedor podría transferirle menos y darle un certificado de retención por la diferencia. **No sé si le aplica: depende de su situación. (a confirmar con el contador)**. Si le aplica, cambia bastante el diseño de las órdenes de pago y de los recibos, porque sus clientes también podrían retenerle a ella.
- **Conciliación bancaria:** comparar lo que dice el sistema con lo que dice el extracto del banco, para detectar diferencias. No lo pidió, pero es el paso natural siguiente una vez que las OP y los recibos están en el sistema.

### 3.5 Actores

- **Clienta (o usuaria):** ella. Quién más va a usar el sistema está por verse.
- **Contador:** profesional externo que lleva los impuestos y, a veces, la contabilidad. **Es un aliado clave**: sabe qué exige ARCA para su caso y qué información necesita recibir de ella cada mes. Conviene tener al menos una charla con él o ella.
- **Clientes del taller** y **proveedores del taller:** las otras partes de cada cuenta corriente.

---

## 4. Qué está claro y qué no

### ✅ Claro

- Tiene dos circuitos: **cobros a clientes** y **pagos a proveedores**, y quiere que ambos alimenten **cuentas corrientes**.
- Hoy imprime **remitos** desde Excel sobre un **preimpreso**, y eso funciona.
- Quiere **recibos** con el mismo mecanismo de impresión, pero más simple que Excel.
- Quiere **órdenes de pago** con formato: fecha, proveedor, factura(s) que paga, monto.
- Paga a proveedores por **transferencia** y les manda el comprobante.
- No es técnica: el sistema tiene que ser **muy simple de usar**.
- Le interesa la IA, sin un uso concreto.
- Espera que el pedido crezca ("hay más cosas para pulir").

### ❓ Ambiguo (hay que preguntarlo)

| Tema | Por qué es ambiguo |
|------|--------------------|
| "Cuando yo haga una factura" | ¿Dónde y cómo factura hoy? ¿En la web de ARCA, con un programa, o se la hace el contador? Define si el sistema **emite** facturas o solo **registra** las que ya existen. Es la decisión más grande del proyecto. |
| "Cargarla en un mensual" | ¿Es el libro IVA para el contador, una planilla propia de ventas del mes, o un resumen para ella? |
| "Circuito de pagos" | Dice pagos, pero su ejemplo es de cobros. Hay que confirmar si quiere **ambos** circuitos y en qué orden de prioridad. |
| Relación remito → factura | ¿Cada remito se factura? ¿Varios remitos van a una factura? ¿Hay remitos que nunca se facturan? |
| Recibos | ¿Ya tiene recibos preimpresos? ¿Con qué numeración? ¿Cuántos emite por mes? ¿Un recibo cancela varias facturas? |
| Órdenes de pago | ¿Una OP puede pagar varias facturas? ¿Paga facturas en partes? ¿Le corresponde hacer retenciones? |
| "Más fácil que Excel" | ¿Qué le resulta difícil hoy del Excel? ¿Cargar datos, alinear la impresión, encontrar cosas? |
| IA | ¿Qué tarea le gustaría no hacer más? Esa respuesta vale más que "¿qué querés con IA?". |

### 🚫 Falta por completo (ella no lo mencionó y un sistema real lo necesita)

- **Rubro del taller** y qué vende: servicios, piezas, ambos.
- **Volumen:** cuántos remitos, facturas, recibos y pagos por mes. Cambia mucho el diseño si son 10 o 500.
- **Usuarios:** ¿solo ella? ¿Alguien más carga datos? ¿Necesita permisos distintos?
- **Dónde lo va a usar:** ¿una sola PC en el taller? ¿también desde su casa o el celular?
- **Impresora:** qué modelo es y si el preimpreso tiene copias (original y duplicado). Si las tiene, puede que use impresora matricial y eso condiciona cómo se imprime. SUPUESTO a verificar: todavía no sabemos qué impresora usa.
- **Condición fiscal** de ella: ¿RI o monotributista? ¿Es agente de retención?
- **Situación actual de las cuentas corrientes:** ¿hoy las lleva en algún lado? ¿En Excel, en un cuaderno, en la cabeza? De ahí salen los saldos iniciales.
- **Contador:** quién es, qué le pide cada mes y en qué formato.
- **Reportes** que necesita ver: quién le debe, a quién le debe, qué vence esta semana.
- **Datos históricos:** ¿quiere cargar operaciones viejas o arrancar de cero con saldos iniciales?
- **Backups y continuidad:** qué pasa si se rompe la PC. Hoy, con Excel, probablemente nadie lo pensó.
- **Presupuesto y plazos:** cuánto está dispuesta a invertir y para cuándo lo necesita.
- **Criterio de éxito:** ¿cómo sabemos que el sistema "funciona" para ella? *Ejemplo:* "que en 2 minutos pueda saber cuánto me debe cada cliente".

---

## Próximo paso

Con este panorama, la **Tarea 3** es convertir los "ambiguos" y los "faltantes" en preguntas concretas, priorizadas y en dos versiones: una para vos y otra para mandarle a ella.
