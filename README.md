# Guía Paso a Paso: Gestión de Facturas y Cartera Bogotá

## 1. Facturas
### 1.1 Exportar Datos desde Odoo
Accede a:
- **Contabilidad** ➡️ **Clientes** ➡️ **Facturas**.
- Filtrar:
  - **Facturación precisa**.
  - **Equipo de ventas contiene "Bogotá"** (sin filtrar por mes).
- Exportar los datos utilizando la plantilla: **"Cartera Bogotá"**.

### 1.2 Procesar el Archivo Exportado
- Ordenar la columna **"Número de factura"** alfabéticamente (de A a Z).
- Identificar el último número de factura en el formato actual y localizar el siguiente número en el archivo descargado.
- En el archivo descargado:
  - Seleccionar las columnas **A a E** desde el número identificado en adelante.
  - Copiar y pegar como valores en el formato.
- Columna **"TOTAL FACTURA"** y **"SALDO FACTURA"**:
  - Copiar la información de la columna **F** del archivo descargado y pegarla en ambas columnas.
- Columna **"FALTANTE"**:
  - Verificar y arrastrar las fórmulas para completar los cálculos.
- Revisar los nombres de los vendedores:
  - Corregir inconsistencias entre minúsculas y mayúsculas para evitar duplicados en el sistema.

## 2. Soportes
### 2.1 Descargar y Registrar Soportes de Pago
- Descargar los soportes de pago desde el correo.
- Anotar los datos en el control de la cartera de Bogotá.
- Buscar cada factura en el formato:
  - **"Valor Cancelado"**: Registrar el monto pagado.
  - **"Fecha Soporte"**: Ingresar la fecha del pago registrada en el soporte descargado.
- Si el valor total de la factura ha sido cancelado:
  - Marcar la fila en **verde**.
- Si es un **abono parcial**, añadir un comentario indicando **"Abono"**.
  - Generalmente, los vendedores especifican si es un abono o un pago total.
- En caso de discrepancias:
  - Si el soporte de pago no coincide con el monto o falta información, revisar la factura en **Odoo**.
  - Verificar si hay transferencias a bancos sin soporte.

### 2.2 Retenciones
- Considerar posibles retenciones aplicadas a algunos clientes:
  - Generalmente de **30,000, 50,000, o 60,000**.
  - Aplicar para facturas superiores a **1,272,000**.

## 3. Ajustes en el Formato
### 3.1 Crear Columna "ESTADO DE PAGO"
- Insertar una columna después de **"SALDO DE FACTURA"** con el nombre: **"ESTADO DE PAGO"**.
- Aplicar fórmula: **BUSCARV(número de factura, archivo descargado, rango desde "número de factura" hasta "estado de pago", celda5)**.

### 3.2 Filtrar y Limpiar el Formato
- Filtrar por **"ESTADO DE PAGO"**:
  - Eliminar las facturas que ya están marcadas como **"Pagado"**.
- Filtrar por **"FALTANTE"**:
  - Filtrar por celdas vacías (rayitas) y eliminarlas.
- Antes de guardar la cartera:
  - Eliminar la columna **"ESTADO DE PAGO"**.

## 4. Preparar y Enviar la Cartera
- Filtrar el formato por **nombre de vendedor**.
- Guardar un archivo individual para cada vendedor.
- Enviar los archivos por correo electrónico:
  - A cada vendedor su respectiva cartera.
  - A Tatiana, enviar la versión general (sin filtros por vendedor).

---

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

-- 

# Guía para generar reportes de proveedores

## General
1. Se genera:
   - **1 informe mensual por proveedor.**
   - **1 informe trimestral** para el proveedor **Saint Gobain** (además de los mensuales).

2. Usar Odoo como fuente principal.
3. Utilizar la plantilla correspondiente dentro de la carpeta **Documentos 1** => **Informes de proveedores**.

---

## Pasos Generales (Odoo)
1. Ir a:
   **Contabilidad** > **Clientes** > **Facturas**.
2. Aplicar filtro personalizado: **"Facturación precisa"**.
3. Descargar plantilla: **"Fact. detallada"**.
4. Realizar limpieza del documento:
   - Eliminar columnas **H a L**.
   - Filtrar equipo de ventas por:
     - **Jorge Mendoza**.
     - **Obed Sanabria**.
     - Especificar los nombres del equipo de ventas en la columna **Vendedor**.
   - Eliminar filas donde el **precio unitario** sea **0**.
   - Filtrar los productos en la columna **Producto/Nombre** y eliminar los productos que contengan **"(AM)" o "( AM)"**.
5. Filtrar por **marca** para cada proveedor y proceder según las plantillas específicas.

---

## Plantilla 3M
1. **Filtrar marca:** **3M**.
2. **Campos a completar:**
   - **Código:** Líneas de factura / referencia interna.
   - **Descripción:** Líneas de factura / producto / nombre.
   - **RUC:** Usar plantilla "IDENT/CIUDAD", buscar por razón social en la columna 3 (es el NIT).
   - **Razón social:** Nombre del socio.
   - **Cantidad:** Líneas de factura / cantidad.
   - **Unidad:** "UND" (en todos los casos).
   - **Precio unitario:** "0" (en todos los casos).
   - **Precio total:** "0" (en todos los casos).
   - **Moneda:** "COP".
   - **Fecha:** Fechas de factura/recibo.
   - **Ubigeo:** Dejar en blanco.
   - **Número de documento:** Número de la factura.
   - **Tipo de documento:** "FA".
   - **Mercado / Categoría:** "NO DEFINIDO".
   - **Vendedor del distribuidor:** "NO DEFINIDO".
   - **Zona / Mercado:**
     1. Descargar plantilla de **Odoo** > **Contactos**.
     2. Exportar con la plantilla "IDENT/CIUDAD".
     3. Usar **BUSCARV** por razón social en la columna 2.
   - **Ciudad del punto de venta:** Copiar y pegar "Zona/Mercado".
   - **Distrito del punto de venta:** Buscar el departamento de la ciudad.

---

## Plantilla Kimberly y Wypall
1. **Filtrar marca:** Kimberly y Wypall.
   - Eliminar productos con **(AM)** o **( AM)**.
2. **Ordenar por vendedor:**
   1. **Fernando Rua.**
   2. **Luis Carlos.**
   3. Los demás, sin orden específico.
3. **Campos a completar:**
   - **NIT:** Usar plantilla "IDENT/CIUDAD" al final.
   - **Empresa:** Nombre de razón social.
   - **Producto:** Nombre del producto.
   - **Referencia:** Líneas de factura / referencia.
   - **Fecha Factura:** Fecha de la factura/recibido.
   - **Factura:** Número de la factura.
   - **COD Vendedor:** Extraer de archivos anteriores.
   - **Precio unitario:** Líneas de factura / precio unitario.
   - **Base imponible:** Líneas de factura / subtotal.
   - **Cantidad facturada:** Líneas de factura / cantidad.
4. **Subtotal:** Sumar el importe subtotal por vendedor en la columna **Base imponible**.

---

## Plantilla Schneider
0. **Plantilla**: SELLOUT_CINTASYCOMUNICACIONES_SALES_(se pone la fecha actual).
1. **Filtrar marca:** Schneider y Dexson.
2. **Ordenar por vendedor:**
   1. **Fernando Rua.**
   2. **Luis Carlos.**
   3. Los demás, sin orden específico.
3. **Campos a completar:**
   - **Distributor ID:** Se deja el número que está en la plantilla por defecto.
   - **Factura:** Número.
   - **Fecha de la venta:** Fecha de la factura/recibido.
   - **Tax ID:** Número de documento del cliente.
   - **Nombre del cliente:** Nombre o razón social.
   - **Producto:**
     1. Descargar de **Odoo** > **Inventario** > **Producto** > **Variantes de producto**.
     2. Aplicar filtro personalizado: **"Proveedores contiene: Schneider".**
     3. Exportar con la plantilla "Inventario de Schneider".
     4. Usar **BUSCARV** con el nombre del producto en la columna 2 "Código del producto".
   - **Cantidad:** Líneas de factura / cantidad.
   - **Canal de ventas:** Se deja "E0".
   - **Código postal:** Descargar los usuarios de Odoo. Usar plantilla "IDENT/CIUDAD", buscar con **BUSCARV** por nombre del cliente y seleccionar la columna de código postal.
   - **Ciudad:** Usar plantilla "IDENT/CIUDAD", buscar con **BUSCARV** por nombre del cliente y seleccionar la columna correspondiente.
   - **País:** Por defecto, "Colombia".

---

## Plantilla Schneider inventario
0. **Plantilla**: SELLOUT_CINTASYCOMUNICACIONES_INV_2025-02-06 (se pone la fecha actual).
1. **Archivo descargado - Inventario Schneider:** Se utiliza el archivo descargado para obtener el inventario de Schneider.
2. **Campos a completar:**
   - **Distributor ID:** Se deja el número que está en la plantilla por defecto.
   - **Factura:** Número.
   - **Producto:** Se seleccionan los productos que tengan el código Schneider.
   - **Cantidad:** Se selecciona la cantidad.

---

## Plantilla Saint Gobain
1. **Filtrar marca:** Norton, Carborundum, Tekbond.
2. **Estructura similar a la plantilla Schneider:**
   - Agregar subtotales por vendedor.
