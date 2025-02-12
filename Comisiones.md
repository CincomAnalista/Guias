# Paso a Paso para las Comisiones /Baq

## 1. Condiciones Generales
- Los vendedores deben vender **62 millones** en ventas; lo que se venda por encima de ese valor genera comisión.
- Se les paga dependiendo del **margen** y la **cantidad de días** que se demoran en pagar.

## 2. Odoo
- **Descargar**: **Contabilidad** ➡️ **Clientes** ➡️ **Facturas**.
  - Filtrar **"Facturación Precisa"**.
  - Filtrar por **"Mes que se genera"**, luego por **"Equipo de ventas"** que contenga **Barranquilla - Jorge Mendoza - Obed Sanabria**.
  - Exportar como **"líneas de fact-OV"**.
- **Descargar plantilla** "líneas de factura - ov".

## 3. Documento
- Cambiar el nombre del vendedor de los equipos de venta **Jorge Mendoza** y **Obed Sanabria** al campo de **vendedor**.
- Quitar equipos de venta, llenar información con **"buscar espacios en blanco"** y luego poner el valor de arriba.
- Revisar la línea de la factura (**producto/referencia interna**).
- Revisar valores **"líneas de facturas/subtotal"** y **"línea de factura/línea de orden de venta/subtotal"**:
  - Si están en **0**, eliminarlos.
  - La orden de venta solo saca el **costo lista**.
- **Calcular el margen**: **(sub - (cant x costo lista)) / sub**.
- **Calcular la utilidad**: **sub - (cant x costo lista)**.

## 4. Formato
- Insertar las columnas:
  - **Días x pago** (después del nombre del socio de la factura).
  - **Concatenar** (después de líneas de factura/Id) para **Fernando y Thamara**.
  - **Costo lista x fact** (después del subtotal) (- sub * costo_lista).

## 5. Kimberly
- **BuscarV** con (columna concatenada) y cambiar el **costo lista** de la orden de venta.

## 6. Calcular Días x Pago
- Todas las ventas con **bajo margen** se dejan dentro de los **62 millones iniciales** para ganar comisión.
- Descargar datos desde **Contabilidad** ➡️ **Clientes** ➡️ **Pagos**.
  - Exportar con la plantilla **"datos días x cliente"**.
- Limpiar la información con **buscar celdas en blanco**.
- Exportar facturas conciliadas y añadirlas a la hoja **"pagos"**.
- Para la columna **"Días x Pago"**, hacer un **"BuscarV"** con el nombre del cliente en la tabla dinámica de la hoja **"días x pago"**.
