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
