# Gestión administrativa del Taller

Sistema para que el Taller registre sus comprobantes, cobros y pagos una sola vez y obtenga solo las cuentas corrientes, los documentos y los avisos que hoy arma a mano en varios Excel.

## Personas y organizaciones

**Taller**:
La empresa metalúrgica dueña del sistema. Es Responsable Inscripta en IVA.
_Evitar_: la clienta, la empresa

**Administradora**:
La persona del Taller que hace el trabajo administrativo y recibe los resúmenes automáticos. Es una de las dos Usuarias.
_Evitar_: la clienta, la dueña

**Usuaria**:
Persona con acceso al sistema. Hay dos y las crea el equipo de desarrollo; no existe registro público.
_Evitar_: cuenta, login

**Cliente**:
Empresa u organización a la que el Taller le vende y le cobra. Nunca se refiere al Taller ni a la Administradora.
_Evitar_: comprador, deudor

**Proveedor**:
Empresa u organización que le vende al Taller y a la que el Taller le paga.
_Evitar_: acreedor

**Contador**:
Profesional externo que liquida los impuestos del Taller y recibe el Reporte mensual de ventas.

## Comprobantes de venta

**Comprobante de venta**:
Documento fiscal ya emitido por el Taller en la web de ARCA y registrado después en el sistema: Factura, Nota de crédito o Nota de débito. El sistema no los emite.
_Evitar_: venta, documento

**Factura**:
Comprobante de venta que genera deuda del Cliente con el Taller.

**Nota de crédito**:
Comprobante de venta que reduce la deuda del Cliente (por error, descuento o devolución).
_Evitar_: devolución, descuento

**Nota de débito**:
Comprobante de venta que aumenta la deuda del Cliente sin ser una Factura.

**Saldo inicial**:
Comprobante interno, no emitido en ARCA, que representa lo que un Cliente debía al empezar a usar el sistema cuando no se conoce el detalle de sus Facturas. Se puede imputar como una Factura.
_Evitar_: saldo anterior, arrastre

**Remito**:
Documento que acompaña la entrega de piezas al Cliente, en talonario con número preimpreso. No genera deuda; termina asociado a una Factura.

## Cobros y cuenta corriente

**Recibo**:
Documento en PDF, numerado correlativamente por el sistema, que registra un cobro recibido de un Cliente, con sus Medios de cobro y sus Imputaciones.
_Evitar_: cobro (como documento), pago (del lado del Cliente)

**Medio de cobro**:
Cada parte de un Recibo según cómo se cobró: transferencia, cheque físico, eCheq, efectivo o Retención. Un Recibo puede combinar varios.
_Evitar_: forma de pago, valor

**Retención**:
Parte de una Factura que el Cliente no paga en dinero porque la retiene como impuesto y entrega un certificado. Cuenta como Medio de cobro.
_Evitar_: descuento, deducción

**Saldo a favor**:
Parte de un Recibo o de una Nota de crédito todavía no imputada a ninguna Factura. Reduce el Saldo del Cliente y queda disponible para imputar después.
_Evitar_: pago a cuenta, anticipo, crédito

**Imputación**:
Asignación de una parte de un Recibo (o de una Nota de crédito) a una Factura o Nota de débito concreta, total o parcial.
_Evitar_: aplicación, cancelación

**Cuenta corriente**:
Historial de movimientos entre el Taller y un Cliente (o Proveedor), con el Saldo resultante. Siempre se deriva de los comprobantes y Recibos; nunca se carga a mano.

**Saldo**:
Lo que un Cliente le debe al Taller en un momento dado (o el Taller a un Proveedor): lo que suma deuda (Facturas y Notas de débito) menos lo que la reduce (Recibos y Notas de crédito), esté imputado o no.

**Pendiente**:
Lo que falta pagar de una Factura o Nota de débito: su total menos sus Imputaciones.
_Evitar_: saldo de la factura, resto

**Condición de pago**:
Si un Cliente paga de contado o en cuenta corriente, y en ese caso con qué Plazo.

**Plazo**:
Cantidad de días acordada con un Cliente o Proveedor para pagar una Factura (30, 45, 60 u otro).

**Vencimiento**:
Fecha en que una Factura debe estar pagada. La sugiere el sistema según el Plazo y la Usuaria puede editarla.

**Anulación**:
Dejar sin efecto un Recibo o un registro sin borrarlo, con motivo, fecha y Usuaria. Lo anulado queda visible.
_Evitar_: borrar, eliminar

## Pagos a proveedores (Fase 2)

**Orden de pago**:
Documento que emite el Taller al pagarle a un Proveedor: fecha, datos del Proveedor, Facturas que paga y medios de pago.
_Evitar_: OP suelta, comprobante de transferencia

**Cartera de cheques**:
Conjunto de cheques físicos y eCheq que el Taller recibió y todavía no depositó, cobró ni entregó.

## Automatizaciones

**Resumen semanal**:
Mail automático de los martes a la Administradora con lo que hay que cobrar y pagar en la semana.
_Evitar_: reporte de los martes

**Reporte mensual de ventas**:
Totales del mes por neto, IVA por alícuota y total, que reemplaza al Excel "ventas mensuales" y se exporta para el Contador.
_Evitar_: el mensual, libro IVA
