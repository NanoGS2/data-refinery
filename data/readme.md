🧹 Data Cleaning & Quality Log (Customer Dataset)

An audit and data sanitation process was performed on a dataset containing 10,000 customer records. 
Below is the itemized transformation matrix detailing the data cleaning rules applied to each column:

| Column | Initial Type | Data Quality Issue | Business Logic / Applied Transformation | Final Type |
| :--- | :--- | :--- | :--- | :--- |
| **CustomerID** | `Text / Int` | Inconsistent formatting (some records lacked the 'C' prefix) and blank values. | Extracted numeric IDs and applied a standardized `C` + ID prefix. Null values were preserved as blank to maintain Primary Key integrity. | `Text` (e.g., `C100`) |
| **Name** | `Text` | Unintended leading and trailing whitespaces. | Applied `Trim` function and standardized text formatting to Title Case. | `Text` |
| **Gender** | `Text` | Categorical inconsistency and casing issues (`f`, `female`, `Male`, `male`). | Converted to Title Case and mapped entries to unify the categorical variable into two distinct classes (`Female` and `Male`). | `Text` (Categorical) |
| **Age** | `Float` | Presence of outliers/out-of-range values (`-5`, `200`) and regional decimal parsing issues. | Handled noise by converting aberrant values to `null`. This retains the commercial transaction record while eliminating demographic bias. | `Integer` (Nullable) |
| **City** | `Text` | Hidden leading/trailing whitespaces. | Applied `Trim` function. | `Text` |
| **Signup_Date** | `Text` | Corrupted text strings (`not_a_date`, `missing`) mixed with valid `DD/MM/YYYY` dates. | Replaced noise strings with `null` and parsed data types using explicit *Locale Settings* (Spanish/LATAM). | `Date` (`DD/MM/YYYY`) |
| **Last_purchase_date**| `Text` | Corrupted text strings (`missing`, `not_a_date`). | Replaced invalid entries with `null` and applied strict date type casting. | `Date` (`DD/MM/YYYY`) |
| **purchase_amount**| `Float` | Legacy system sentinel values (`-999.00`) and U.S. decimal point formatting conflicts. | Filtered out negative sentinel values and casted types via *Locale Settings* (`English US`) to handle the `.` decimal separator correctly. | `Decimal / Currency` |
| **feedback_score**| `Float` | Numerical formatting inconsistencies. | Standardized numeric scale and data type casting. | `Decimal / Integer` |
| **email** | `Text` | Mixed casing and incomplete/unformatted email addresses. | Applied batch lowercase conversion (`Lowercase`) and basic structural validation. | `Text` |
| **Phone_number** | `Text / Int` | Non-numeric strings (`abc123`), placeholder zeros (`0`), and missing leading zeros (9 vs. 10 digit lengths). | Replaced invalid strings with `null`, casted to String, and applied left zero padding (`Text.PadStart` to 10 digits) to enforce uniform length. | `Text` (10 digits) |
| **Country** | `Text` | Whitespaces and minor categorical naming inconsistencies. | Applied `Trim` function and standardized country name values. | `Text` |


Se realizo un proceso de auditoria y saneamiento sobre un conjunto de 10.000 registros de clientes. A continuación se detalla la matriz de transformaciones aplicada columna por columna:

| Columna | Tipo Inicial | Problema Detectado (Data Issue) | Regla de Negocio / Transformación Aplicada | Estado Final |
| :--- | :--- | :--- | :--- | :--- |
| **CustomerID** | `Text / Int` | Formato inconsistente (algunos con prefijo 'C', otros numéricos simples) y celdas vacías. | Se extrajo el identificador numérico y se aplicó prefijo homogéneo `C` + ID. Las entradas nulas se mantuvieron vacías para preservar la integridad de la clave primaria. | `Text` (Ej: `C100`) |
| **Name** | `Text` | Espacios en blanco no visibles al inicio/final (*Whitespace*). | Aplicación de función `Recortar` (*Trim*) y estandarización a formato Título (*Capitalize*). | `Text` |
| **Gender** | `Text` | Categorías dispersas y con distinta capitalización (`f`, `female`, `Male`, `male`). | Formateo a *Title Case* y mapeo condicional para unificar la variable categórica en dos clases únicas (`Female` y `Male`). | `Text` (Categoría) |
| **Age** | `Float` | Presencia de *outliers* y valores aberrantes (`-5`, `200`) e inconsistencia regional en decimales. | Tratamiento de valores ruidosos mediante conversión a valores nulos (`null`). Preserva el registro comercial evitando sesgos en métricas demográficas. | `Integer` (Acepta `null`) |
| **City** | `Text` | Espacios invisibles (*Whitespace*). | Aplicación de función `Recortar` (*Trim*). | `Text` |
| **Signup_Date** | `Text` | Cadenas de texto corruptas (`not_a_date`, `missing`) mezcladas con fechas en formato `DD/MM/YYYY`. | Reemplazo de cadenas basura por `null` y conversión de tipo mediante *Configuración Regional* (Español/LATAM). | `Date` (`DD/MM/YYYY`) |
| **Last_purchase_date**| `Text` | Texto basura (`missing`, `not_a_date`). | Sustitución de valores corruptos por `null` y parseo estricto a tipo Fecha. | `Date` (`DD/MM/YYYY`) |
| **purchase_amount**| `Float` | Presencia de valores sentinela/basura de sistemas heredados (`-999.00`) y punto decimal de EE. UU. | Eliminación de valores negativos sentinela y conversión explícita con *Configuración Regional* (`Inglés EE.UU.`) para parsear correctamente el punto decimal `.`. | `Decimal / Currency` |
| **feedback_score**| `Float` | Inconsistencias de formato numérico. | Estandarización de escala y tipo de dato. | `Decimal / Integer` |
| **email** | `Text` | Mayúsculas/minúsculas desordenadas y dominios/registros incompletos. | Conversión masiva a minúsculas (*Lowercase*) y filtrado/validación de estructura básica. | `Text` |
| **Phone_number** | `Text / Int` | Registros con texto no numérico (`abc123`), ceros sueltos (`0`) y pérdida del `0` inicial (longitudes de 9 y 10 dígitos). | Reemplazo de texto ruidoso por `null`, conversión a *String* y aplicación de relleno con ceros a la izquierda (`Text.PadStart` a 10 dígitos). | `Text` (10 dígitos) |
| **Country** | `Text` | Espacios e inconsistencia categórica. | Aplicación de `Trim` y estandarización de nombres de países. | `Text` |
