📑 Guía para generar informe 3M en Quality
🔹 Pasos

Entrar a Quality → apartado Ventas → consulta 3.8 (Informe de ventas por vendedor y línea).

Seleccionar:

Fecha inicial y final del mes del informe.

Línea del proveedor: 3M.

Dar clic en Consultar → Exportar a Excel (formato plano).

Repetir el mismo procedimiento para las 3 sedes:

CINCOM SAS

CINCOM Automotriz

CINCOM Bogotá

Unir los 3 archivos en un solo Excel (copiar y pegar).

🔹 Limpieza del documento

Eliminar las siguientes columnas:

C (Tipo)

F (Teléfonos)

I (Dirección)

J (Tipo de negocio)

U (Nombre de la línea)

V (Nombre de la sublínea)

Filtrar:

Columna Base / Costo = 0 → eliminar filas.

Columna Devuelta ≠ 0 → restar cantidad devuelta a la cantidad facturada.

Dejar todos los valores de Devuelta = 0.

🔹 Columnas adicionales

Nombre del producto sin RF

Fórmula: =SI.ERROR(ESPACIOS(IZQUIERDA(J2;HALLAR("RF";J2)-1));J2)

Esta fórmula elimina la “RF” y lo que está después.

Revisar manualmente productos que puedan cortarse (ejemplo: Interface 5777).

Precio unitario

Calcular: Base ÷ Cantidad Facturada
