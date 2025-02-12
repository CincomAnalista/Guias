# Guía Paso a Paso: Gestión de Facturas y Cartera Bogotá

## 1. Facturas

### 1.1 Exportar Datos desde Odoo

Accede a:
- **Contabilidad** ➡️ **Clientes** ➡️ **Facturas**.

Filtrar:
- **Facturación precisa**.
- **Equipo de ventas contiene "Bogotá"** (sin filtrar por mes).

Exportar los datos utilizando la plantilla: **"Cartera Bogotá"**.

### 1.2 Procesar el Archivo Exportado

- Ordenar la columna **"Número de factura"** alfabéticamente (de A a Z).
- Identificar el último número de factura en el formato actual y localizar el siguiente número en el archivo descargado.
- En el archivo descargado:
  - Seleccionar las columnas **A a E** desde el número identificado en adelante.
  - Copiar y pegar como valores en el formato.
- **Columna "TOTAL FACTURA" y "SALDO FACTURA"**:
  - Copiar la información de la columna **F** del archivo descargado y pegarla en ambas columnas.
- **Columna "FALTANTE"**:
  - Verificar y arrastrar las fórmulas para completar los cálculos.
- **Revisar los nombres de los vendedores**:
  - Corregir inconsistencias entre minúsculas y mayúsculas para evitar duplicados en el sistema.

---

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

**En caso de discrepancias:**
- Si el soporte de pago no coincide con el monto o falta información, revisar la factura en **Odoo**.
- Verificar si hay transferencias a bancos sin soporte.

### 2.2 Retenciones

- Considerar posibles retenciones aplicadas a algunos clientes:
  - Generalmente de **30,000**, **50,000**, o **60,000**.
  - Aplicar para facturas superiores a **1,272,000**.

---

## 3. Ajustes en el Formato

### 3.1 Crear Columna **"ESTADO DE PAGO"**

- Insertar una columna después de **"SALDO DE FACTURA"** con el nombre: **"ESTADO DE PAGO"**.
- Aplicar la fórmula:
  ```excel
  BUSCARV(número de factura, archivo descargado, rango desde "número de factura" hasta "estado de pago", celda 5)
  ```

### 3.2 Filtrar y Limpiar el Formato

- **Filtrar por "ESTADO DE PAGO"**:
  - Eliminar las facturas que ya están marcadas como **"Pagado"**.
- **Filtrar por "FALTANTE"**:
  - Filtrar por celdas vacías (**rayitas**) y eliminarlas.
- **Antes de guardar la cartera**:
  - Eliminar la columna **"ESTADO DE PAGO"**.

---

## 4. Preparar y Enviar la Cartera

- **Filtrar el formato por nombre de vendedor**.
- **Guardar un archivo individual para cada vendedor**.
- **Enviar los archivos por correo electrónico**:
  - A cada **vendedor** su respectiva cartera.
  - A **Tatiana**, enviar la versión **general** (sin filtros por vendedor).

