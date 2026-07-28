# 🔬 Data Cleaning & ETL Pipeline: Water Quality Laboratory Register (Mendoza)

## 📌 Project Overview
This project focuses on the Extraction, Transformation, and Loading (ETL) pipeline for a public dataset containing water and effluent sampling records in the province of Mendoza, Argentina. 

The raw dataset presented several structural and data quality challenges, such as double-level headers (MultiIndex), non-exclusive pivot flags, and unstandardized text fields. A Python ETL pipeline using Pandas was developed to transform the raw spreadsheet into a clean, normalized, and tabular format ready for exploratory data analysis (EDA) and reporting.

---

## 🛠️ Data Challenges & Applied Solutions

1. **Multi-level Headers (MultiIndex Structure):**
   * *Issue:* The original `.csv` file used two top rows to group feature categories.
   * *Solution:* Bypassed redundant headers using `header=1` and mapped sub-columns dynamically via index positioning and categories.

2. **Multi-Select Binary Flags (Unpivoting & Atomicity):**
   * *Issue:* `ANALISIS` (Analysis Type) and `OPERADOR` (Operator/Client) columns contained binary flags (`1`) scattered across multiple non-exclusive columns.
   * *Solution:* Consolidated active flags into unified, human-readable comma-separated strings per record.

3. **Text Standardization & Data Cleaning:**
   * Trimmed leading and trailing whitespace across all string fields (`.strip()`).
   * Standardized text casing and typos (e.g., `factibilidad` $\rightarrow$ `Factibilidad`).
   * Homogenized variations in entity/operator acronyms (`AySAM`, `O.G.C.`, `D.G.E.`, `D.G.I.`, etc.).

---

## 📊 Theoretical Discussion: Database Normalization (1NF)
While consolidating attributes into comma-separated strings improves human readability in flat files (Excel/CSV), it strictly violates the **First Normal Form (1NF)** due to the lack of atomic values.

For ingestion into a **Relational Database (SQL)** or an **Analytical Data Model (Power BI / Data Warehouse)**, the recommended approaches are:
* **Relational SQL Model ($N:M$):** Decompose the entity into normalized tables (`Samples`, `Analysis_Types`, `Sample_Analysis_Junction`).
* **Analytical Model:** Apply a row-level expansion (`.explode()`) in Pandas or Power Query to convert each combination into an individual record.

---

## 📂 Repository Structure
* `notebooks/`: Google Colab Jupyter Notebook containing the documented Python ETL pipeline.
* `data/`: Raw input dataset (`raw/`) and cleaned outputs in CSV/Excel (`processed/`).

---

## 🧰 Tech Stack
* **Language:** Python 3.x
* **Libraries:** Pandas
* **Environment:** Google Colab / Jupyter Notebooks
--------------------------------------------------------------

# 🔬 ETL y Limpieza de Datos: Registro de Laboratorio de Agua (Mendoza)

## 📌 Descripción del Proyecto
Este proyecto aborda la limpieza, normalización y transformación (ETL) de un dataset público con registros de toma de muestras de agua y efluentes en la provincia de Mendoza. 

El conjunto de datos original presentaba serios problemas de estructura (encabezados de doble nivel, banderas no excluyentes en formato pivoteado y faltas de estandarización en textos). Se desarrolló un script en Python (Pandas) para transformar la estructura a un formato tabular consolidado y apto para análisis.

---

## 🛠️ Desafíos de Datos y Soluciones Aplicadas

1. **Estructura Múltiple de Encabezados (MultiIndex):**
   * *Problema:* El archivo `.csv` original utilizaba dos filas superiores para agrupar categorías.
   * *Solución:* Se omitió la fila redundante (`header=1`) y se mapearon dinámicamente las subcolumnas por índice y categoría.

2. **Banderas de Selección Múltiple (Pivot Unpivoting & Atomicidad):**
   * *Problema:* Las columnas de `ANALISIS` y `OPERADOR` contenían marcas binarias (`1`) distribuidas a lo largo de varias columnas no excluyentes.
   * *Solución:* Se consolidaron las banderas activas en cadenas descriptivas unificadas por muestra.

3. **Estandarización y Calidad de Texto:**
   * Eliminación de espacios en blanco al inicio/final de las celdas (`.strip()`).
   * Normalización de términos (ej. `factibilidad` -> `Factibilidad`).
   * Corrección de variaciones en nombres de entidades operadoras (`AySAM`, `O.G.C.`, `D.G.E.`, etc.).

---

## 📊 Discusión Teórica: Normalización de Bases de Datos (1NF)
Aunque la consolidación de atributos en cadenas separadas por comas facilita la lectura humana en archivos planos (Excel/CSV), el resultado viola la **Primera Forma Normal (1NF)** debido a la falta de atomicidad en los valores.

Para la ingesta en un **modelo de datos relacional (SQL)** o **Power BI**, se propone:
* **Modelo SQL ($N:M$):** Descomponer la entidad en tablas independientes (`Muestras`, `Analisis`, `Muestras_Analisis`).
* **Modelo Analítico:** Aplicar un desglose (`.explode()`) en Pandas/Power Query para llevar cada combinación a un registro individual.

---

## 📂 Estructura del Repositorio
* `notebooks/`: Cuaderno de Google Colab con el código documentado.
* `data/`: Datasets de entrada (raw) y salida (processed).

---

## 🧰 Tecnologías Utilizadas
* **Lenguaje:** Python 3.x
* **Librerías:** Pandas
* **Entorno:** Google Colab / Jupyter Notebooks
