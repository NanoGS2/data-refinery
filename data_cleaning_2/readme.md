# 🛒 E-Commerce Sales Data Cleaning & ETL Project

Data Source: https://www.kaggle.com/datasets/ruchikakumbhar1806/customer-messy-data?select=messy_customer_data.csv

## 📌 English

### 📑 Project Overview
This project focuses on performing an **End-to-End Data Cleaning & Transformation Process (ETL)** on a raw e-commerce sales dataset (`messy_ecommerce_sales_data.csv`) using **Power Query**. The objective was to eliminate noise, standardize schemas, handle invalid data types, and recalculate metrics to produce a reliable dataset for business intelligence and downstream analytics.

---

### 📊 Dataset Transformation Matrix

| Column | Initial Type | Data Quality Issue | Business Logic / Applied Transformation | Final Type |
| :--- | :--- | :--- | :--- | :--- |
| **Customer_Name** | Text | Leading whitespace in header (` Customer_Name`). | Trimmed column header and text values using `Text.Trim`. | Text |
| **Order_ID** | Text | Duplicate transaction IDs present. | Standardized text format and removed duplicate order entries based on primary key rules. | Text |
| **Order_Date** | Text | Stored as text in `MM/DD/YYYY` format. | Converted to native `Date` data type using `English (United States)` locale parsing. | Date |
| **Product** | Text | Inconsistent text casing across product entries. | Applied `Capitalize Each Word` to ensure proper item naming conventions. | Text |
| **Category** | Text | Whitespace in header (` Category`), missing values (`null`), and case inconsistencies (`electronics`, `ELECTRONICS`, `electronic`). | Trimmed header. Applied `Capitalize Each Word` to unify values into standard categories (`Electronics`, `Books`, `Home`, `Sports`, `Clothing`). | Text |
| **Quantity** | Text / Mixed | Missing values (`null`), negative values (`-2`, `-5`), and non-numeric characters (`4a`). | Parsed as `Integer`. Replaced/removed errors and filtered out non-positive quantities (`Quantity > 0`). | Int64 (Integer) |
| **Price** | Text / Mixed | Missing values (`null`) and invalid text strings (`abd`). | Parsed as `Decimal`. Replaced non-numeric strings with `null` or filtered invalid price rows. | Currency / Double |
| **Payment_Method** | Text | Unstandardized values across payment types. | Trimmed text and validated category list (`Cash on Delivery`, `PayPal`, `Bank Transfer`, `Credit Card`). | Text |
| **Status** | Text | Categorical values needing validation. | Trimmed whitespace and confirmed category consistency (`Processing`, `Shipped`, `Delivered`, `Cancelled`, `Returned`). | Text |
| **Total** | Decimal / Null | Missing values, uncalculated totals, and math inconsistencies with `Quantity * Price`. | Removed original corrupted `Total` column. Generated a Custom Column: `Total = [Quantity] * [Price]`. | Currency / Double |

---

### 🛠️ Key Cleaning Steps Summary
1. **Header Whitespace Cleanup:** Applied `Trim` across all column headers to fix leading space anomalies.
2. **Text Normalization:** Standardized casing in `Product` and `Category` using `Capitalize Each Word`.
3. **Data Type Correction:** Converted `Order_Date` to `Date` (Locale US) and forced `Quantity` and `Price` into numerical fields.
4. **Data Hygiene & Anomaly Removal:** Removed non-numeric values (`'abd'`, `'4a'`), negative quantities (`<= 0`), and full-row duplicate records.
5. **Metric Recalculation:** Recomputed `Total` as a derived column (`Quantity * Price`) to enforce 100% mathematical integrity across all transactions.

---
---

## 📌 Español

### 📑 Descripción del Proyecto
Este proyecto se enfoca en llevar a cabo un proceso completo de **Limpieza y Transformación de Datos (ETL)** sobre un dataset de ventas de comercio electrónico (`messy_ecommerce_sales_data.csv`) utilizando **Power Query**. El objetivo principal consistió en eliminar ruido, estandarizar esquemas, manejar tipos de datos no válidos y recalcular métricas para generar un dataset confiable apto para Business Intelligence y análisis posterior.

---

### 📊 Matriz de Transformación del Dataset

| Columna | Tipo Inicial | Problema de Calidad de Datos | Lógica de Negocio / Transformación Aplicada | Tipo Final |
| :--- | :--- | :--- | :--- | :--- |
| **Customer_Name** | Texto | Espacios sobrantes al inicio en el nombre de columna (` Customer_Name`). | Se limpiaron los espacios en el encabezado y texto utilizando la función `Recortar` (`Text.Trim`). | Texto |
| **Order_ID** | Texto | Presencia de transacciones duplicadas. | Se estandarizó el formato de texto y se eliminaron registros duplicados según reglas de clave primaria. | Texto |
| **Order_Date** | Texto | Almacenado como texto en formato `MM/DD/YYYY`. | Se transformó a tipo de dato `Fecha` nativo aplicando la configuración regional `Inglés (Estados Unidos)`. | Fecha |
| **Product** | Texto | Inconsistencia en el uso de mayúsculas y minúsculas. | Se aplicó la transformación `Poner en Mayúsculas Cada Palabra` para homogeneizar la nomenclatura de productos. | Texto |
| **Category** | Texto | Espacios en el encabezado (` Category`), valores nulos y variantes de texto (`electronics`, `ELECTRONICS`, `electronic`). | Se recortó el encabezado. Se aplicó `Poner en Mayúsculas Cada Palabra` para unificar categorías (`Electronics`, `Books`, `Home`, `Sports`, `Clothing`). | Texto |
| **Quantity** | Texto / Mixto | Valores faltantes (`null`), cantidades negativas (`-2`, `-5`) y caracteres alfanuméricos (`4a`). | Conversión a `Número Entero`. Se eliminaron errores de conversión y se filtraron valores no positivos (`Quantity > 0`). | Entero (Int64) |
| **Price** | Texto / Mixto | Valores faltantes (`null`) y cadenas de texto no numéricas (`abd`). | Conversión a `Número Decimal`. Se manejaron los valores no numéricos como nulos o se descartaron las filas corruptas. | Moneda / Decimal |
| **Payment_Method** | Texto | Necesidad de validación de valores categóricos. | Se limpiaron espacios sobrantes y se validaron los métodos (`Cash on Delivery`, `PayPal`, `Bank Transfer`, `Credit Card`). | Texto |
| **Status** | Texto | Validación del estado de las órdenes. | Se eliminaron espacios en blanco y se unificaron las categorías de estado (`Processing`, `Shipped`, `Delivered`, `Cancelled`, `Returned`). | Texto |
| **Total** | Decimal / Nulo | Valores nulos, registros sin calcular e inconsistencias matemáticas con `Quantity * Price`. | Se eliminó la columna `Total` original corrupta. Se creó una Columna Personalizada: `Total = [Quantity] * [Price]`. | Moneda / Decimal |

---

### 🛠️ Resumen de Pasos de Limpieza Realizados
1. **Limpieza de Encabezados:** Se aplicó `Recortar` a todas las columnas para eliminar espacios ocultos en los nombres de variables.
2. **Normalización de Texto:** Se homogeneizaron mayúsculas y minúsculas en `Product` y `Category` mediante `Poner en Mayúsculas Cada Palabra`.
3. **Corrección de Tipos de Datos:** Se convirtió `Order_Date` a formato `Fecha` (usando Locale US) y se forzó `Quantity` y `Price` a valores numéricos.
4. **Higiene de Datos y Remoción de Anomalías:** Se depuraron valores alfanuméricos en campos numéricos (`'abd'`, `'4a'`), cantidades negativas (`<= 0`) y filas completamente duplicadas.
5. **Recálculo de Métricas:** Se reconstruyó la columna `Total` mediante una columna derivada (`Quantity * Price`), garantizando un $100\%$ de consistencia matemática en las transacciones.
