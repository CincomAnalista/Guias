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
