# Multi-Source Excel Consolidation & Interactive Performance Dashboard

## 📌 Executive Summary
This project addresses a common operational challenge where annual transactional data was fragmented across 12 separate monthly Excel workbooks. Using **Power Query**, the datasets were automatically extracted, cleaned, transformed, and consolidated into a single scalable data model. 

The resulting dataset powers an **Interactive Excel Dashboard** capable of dynamic filtering across specific four-month periods (four-month terms / *cuatrimestres*) or full annual overviews to evaluate key performance indicators (KPIs).

---

## 🛠️ Tech Stack & Tools Used
* **ETL & Data Pipeline:** Power Query (Excel)
* **Data Transformation:** Data Type Casting, Address Parsing, Anomaly Cleaning
* **Visualization & Analytics:** Excel Dashboard (Pivot Tables, Slicers, Custom KPI Calculations)

---

## 🔄 Data Pipeline & Transformation Workflow}

[12 Monthly Excel Files] ➔ [Power Query ETL Engine] ➔ [Data Cleaning & Parsing] ➔ [Consolidated Data Model] ➔ [Interactive Dashboard]

### 1. Extraction & Automated Unification
* **Source Pattern:** 12 individual Excel files named according to their respective months.
* **Consolidation:** Programmatically combined all monthly files using Power Query's folder/file ingestion workflow, guaranteeing a repeatable structure for future periods.

### 2. Data Cleaning & Standardisation
* **Type Assignment:** Validated and enforced proper data types (Dates, Numeric Values, Text) across all merged records.
* **Error Resolution:** Identified and corrected format inconsistencies and edge-case errors present in legacy files.

### 3. Feature Engineering & Parsing
* **Address Decomposition:** Parsed unformatted raw address strings (`Street, City, State + Zip Code`) into individual structured columns:
  * `Street`
  * `City`
  * `State / Postal Code`
* **Purpose:** Enabled granular geographical analysis and state-level KPI filtering within the dashboard.

---

## 📊 Interactive Dashboard & Key Features

* **Dynamic Time Slicing:** Interactive slicers configured by four-month periods (*cuatrimestres*) allowing users to switch effortlessly between Single Term, Multi-Term, and Full Annual comparisons.
* **KPI Metrics:** Custom-calculated metrics highlighting core operational performance, sales volume, and geographical distribution.
* **Visual Clarity:** Streamlined visual design focusing on actionable insights for decision-makers.

---

## 📂 Repository Structure

```text
├── raw_data/          # Source files / sample templates
├── clean_data/        # Consolidated output dataset (.xlsx)
├── dashboard/         # Main Excel workbook containing the Interactive Dashboard
└── README.md          # Project documentation

```

📸 Dashboard Preview

<img width="1264" height="445" alt="db_sales" src="https://github.com/user-attachments/assets/1e91bfd6-b904-42eb-84a0-9b7fdc5b4be0" />

🚀 Key Takeaways & Business Value
Efficiency: Replaced manual copy-paste consolidation with an automated Power Query pipeline.

Scalability: Designed to ingest future monthly reports with zero re-work required.

Data Integrity: Eliminated structural discrepancies and manual entry errors.


---

### 🇦🇷 / 🇪🇸 Versión en Español (`README.md`)

```markdown
# Consolidación Multifuente en Excel e Impacto de Dashboard Interactivo

## 📌 Resumen Ejecutivo
Este proyecto resuelve una problemática operativa habitual: la dispersión de datos transaccionales anuales en 12 archivos independientes de Excel (uno por mes). Mediante el uso de **Power Query**, se extrajeron, limpiaron, transformaron y unificaron de forma automatizada todas las fuentes en un modelo de datos único y escalable.

La base consolidada alimenta un **Dashboard Interactivo en Excel** con capacidad de filtrado dinámico por cuatrimestres o vista anual completa para el análisis de indicadores clave de rendimiento (KPIs).

---

## 🛠️ Herramientas y Tecnologías
* **ETL y Flujo de Datos:** Power Query (Excel)
* **Transformación de Datos:** Tipado estandarizado, parseo de direcciones, limpieza de anomalías
* **Visualización y Analítica:** Dashboard en Excel (Tablas Dinámicas, Segmentación de Datos, KPIs)

---

## 🔄 Pipeline de Datos y Proceso de Transformación

[12 Archivos Excel Mensuales] ➔ [Motor ETL Power Query] ➔ [Limpieza y Parseo] ➔ [Modelo Consolidado] ➔ [Dashboard Interactivo]

### 1. Extracción y Unificación Automatizada
* **Patrón de Origen:** 12 archivos de Excel independientes estructurados con el mes correspondiente en su denominación.
* **Ensamblado:** Combinación programática de las fuentes mediante Power Query, asegurando un proceso replicable para futuros periodos.

### 2. Limpieza y Estandarización
* **Asignación de Tipos de Datos:** Validación y corrección estricta de tipos de datos (fechas, valores numéricos, texto).
* **Depuración de Errores:** Detección y solución de inconsistencias de formato y registros defectuosos.

### 3. Ingeniería de Características y Parseo
* **Descomposición de Direcciones:** Transformación de cadenas de texto complejas (`Calle, Ciudad, Estado + CP`) en columnas independientes:
  * `Calle`
  * `Ciudad`
  * `Estado / Código Postal`
* **Objetivo:** Permitir segmentación geográfica precisa y evaluación de KPIs a nivel provincial/estatal.

---

## 📊 Dashboard Interactivo y Funcionalidades

* **Segmentación Temporal Dinámica:** Filtros interactivos configurados por cuatrimestres, permitiendo alternar entre análisis cuatrimestral específico, comparación entre varios periodos o evaluación anual completa.
* **Métricas KPI:** Indicadores ejecutivos para la toma de decisiones basada en datos.
* **Interfaz Ejecutiva:** Diseño enfocado en legibilidad y análisis rápido.

---

## 📂 Estructura del Repositorio

```text
├── raw_data/          # Source files / sample templates
├── clean_data/        # Consolidated output dataset (.xlsx)
├── dashboard/         # Main Excel workbook containing the Interactive Dashboard
└── README.md          # Project documentation

📸 Vista Previa del Dashboard

<img width="1264" height="445" alt="db_sales" src="https://github.com/user-attachments/assets/1e91bfd6-b904-42eb-84a0-9b7fdc5b4be0" />

🚀 Valor de Negocio y Conclusiones
Eficiencia Operativa: Eliminación del trabajo manual de "copiar y pegar" gracias a la automatización con Power Query.

Escalabilidad: Estructura preparada para incorporar reportes mensuales futuros en segundos.

Calidad de Datos: Corrección de formatos desalineados y erradicación de discrepancias estructurales.
