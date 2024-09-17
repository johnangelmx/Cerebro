Prima demostración y prueba con el equipo de trabajo, donde se verá el flujo de trabajo completo del sistema.

## Notas de la reunión

1. Quieren subir de forma masiva las cuentas bancarias. - descartado a posterior
2. `Tracker` falta mostrar más estados agregados. - descartado a posterior
3. Hay pagos que son fijos (las rentas). Por lo que no ven necesario autorizar - descartado.
4. El validador nivel 1 debe autorizar primero antes de que pase a nivel 2. - descartado a posterior.
5. Si hay dos validadores del mismo nivel, con que un mismo validador del mismo nivel válido es suficiente para que se continúe. - descartado a posterior.
6. Se quiere ya teniendo un XML cargado, poder reconstruido un PDF con el XML ya cargado, de esta forma ya no sea necesario cargar el PDF de la factura. - descartado a posterior.
7. Crear un folio de transacción, para referenciar el pago y la orden de pago desde SIA con cero papel. - Listo.
8. Crear un `layout` de pagos masivos para SIA, después de que se subieron los comprobantes de pago. (número de orden de pago de SIA, monto de pago y concepto). (filtrado por fecha, no importa los si son interbancarios o BBVA). - Por hacer Juvencio.
9. Filtrado al momento de mapear las facturas, omitir los que no aplican para SIA y que el usuario pueda subir posterior a contabilizar en SIA para que continuar el proceso en cero papel. - Por hacer Don Omar.
10. Las cuentas bancarias, hay que pasarlas al SICPRO. - Por analizar.

## Correcciones de sistema

1. Nombre no encontrado en asignación de centros de costo - Por hacer Don Omar.
2. Agregar una validación extra para que si ya se agregó un centro de costo, este no lo deje agregar otro desde el momento que está creando el prorrateo y no hasta que quiera guardar la solicitud internamente en el componente de prorrateo - descartado a posterior.
3. Del módulo de tesorería, quitar el visor de documentos - Por hacer Juvencio.
4. Agregar un campo a la tabla de orden de pago, en la cual se guardara el número de orden de pago desde SIA - Por hacer Juvencio.