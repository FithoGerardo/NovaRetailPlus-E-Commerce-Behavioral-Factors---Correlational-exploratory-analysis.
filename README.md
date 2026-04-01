# NovaRetailPlus-E-Commerce-Behavioral-Factors---Correlational-exploratory-analysis.

# Customer Behavior Analysis – Business Insights Project

[Go back to the portfolio](https://fithogerardo.github.io/Gerardos_Portfolio/)

This project focuses on analyzing **customer behavior patterns** to identify key relationships between engagement, monetization, retention, and marketing investment.

The analysis explores **correlations between behavioral variables**, detects **structural patterns**, and generates **business-oriented insights** to support decision-making.

Which customer behavior factors are most strongly associated with annual revenue generated?  This project is a correlational (exploratory) analysis.  Correlation ≠ causation.

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-orange)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-green)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Charts-yellow)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-red)

---

# Project Objective

The goal of this project is to analyze customer behavior in order to:

- Identify **key drivers of revenue generation**
- Understand **engagement patterns (visits and purchases)**
- Analyze **customer retention and churn behavior**
- Evaluate the role of **premium membership**
- Assess the effectiveness of **targeted advertising**
- Generate **actionable business insights**

---

# Datasets

The dataset contains **15,000 records and 12 variables**, with no missing values.

## Numerical Variables

- `edad`
- `nivel_ingreso`
- `visitas_mes`
- `compras_mes`
- `gasto_publicidad_dirigida`
- `satisfaccion`
- `ingreso_anual`

Key characteristics:

- Wide distribution of income levels
- Low average purchases (mean ≈ 1.2)
- ~25% of customers generate **zero revenue**
- High variability in `ingreso_anual`

---

## Binary Variables

- `miembro_premium`
- `abandono`

Key insights:

- Premium users: ~13.9%
- Churn rate: ~15%
- Premium retention: **95.6% vs 83.2% (non-premium)**

---

## Categorical Variables

- `id_cliente`
- `tipo_dispositivo`
- `region`

Highlights:

- Mobile dominates (~65%)
- Regions are relatively balanced
- No strong association between device and region

---

# Analysis Workflow

The project follows a structured analytical approach:

## 1. Data Exploration
- Dataset structure validation
- Variable type verification
- Distribution analysis

---

## 2. Data Cleaning
- Type corrections (e.g., age)
- Validation of variable ranges
- Consistency checks

---

## 3. Feature Understanding
- Behavioral variables analysis
- Identification of key segments (active vs inactive users)

---

## 4. Correlation Analysis

Different statistical methods were applied:

- **Pearson** → linear relationships
- **Spearman** → monotonic relationships
- **Point-biserial** → numeric vs binary
- **Cramér's V** → categorical relationships

Key findings:

- `compras_mes` vs `ingreso_anual`: **0.97 (very high)**
- `visitas_mes` vs `gasto_publicidad_dirigida`: **0.58 (moderate-high)**
- `miembro_premium` vs `abandono`: **-0.12 (low, inverse)**

---

## 5. Behavioral Patterns

### Monetization

- Revenue is almost entirely explained by number of purchases
- Strong structural dependency detected

### Engagement

- Visits correlate with purchases and marketing exposure
- High variability suggests additional hidden factors

### Retention

- Premium users show significantly higher retention
- However, statistical correlation remains low

---

## 6. Key Business Segmentation

A critical structural segmentation emerges:

- **Active customers (with purchases)**
- **Inactive customers (no purchases)**

~25% of users belong to the inactive group, representing the main opportunity for growth

---

# How to Run the Project

## Run in Google Colab

1. Open Google Colab  
2. Upload the notebook:

`notebooks/Project-NovaRetail_Gerardo_Olm.ipynb`

3. Upload the dataset file(s)

`data/novaretail_comportamiento_clientes_2024.csv`

5. Run all cells sequentially

---

# Reproducibility Guide

To reproduce the analysis:

1. Load the dataset
2. Validate and clean data
3. Analyze variable distributions
4. Compute correlations (Pearson, Spearman, Biserial, Cramér)
5. Visualize relationships (heatmaps, scatterplots)
6. Identify behavioral segments
7. Interpret business implications

The notebook is structured sequentially for easy replication.

---

# Key Insights

## 1. Monetization (Critical)

- Strong correlation between purchases and revenue
- Large segment of users generates no revenue

**Business implication:**
Focus on **activation (0 → 1 purchase)** rather than increasing frequency.

---

## 2. Premium Membership

- Strong retention difference
- Weak statistical correlation

**Business implication:**
Premium is a **value indicator**, not a primary retention driver.

---

## 3. Targeted Advertising

- Moderate relationship with visits
- High dispersion

**Business implication:**
Marketing allocation is **not fully optimized** → opportunity for better targeting.

---

## 4. Structural Segmentation

- Active vs inactive users is the most important split

**Business implication:**
All strategies must be segmented — mixing both groups dilutes insights.

---

# Limitations

- Correlation does not imply causation
- Possible structural collinearity (`compras_mes` vs `ingreso_anual`)
- High proportion of zero values affects distributions :contentReference[oaicite:7]{index=7}

---

# Next Steps

## Segmentation

- Option 1: Active vs inactive users  
- Option 2: High vs low engagement (visits)

## Modeling

- Option 1: First purchase prediction model  
- Option 2: Churn prediction model  

## Marketing Optimization

- Reallocate budget toward high-conversion users :contentReference[oaicite:8]{index=8}

---

# Key Skills Demonstrated

- Exploratory Data Analysis (EDA)
- Statistical Correlation Analysis
- Behavioral Segmentation
- Business Insight Generation
- Data Visualization

---

## Author

Gerardo Olmedo – Data Analyst

---

[Go back to the portfolio](https://fithogerardo.github.io/Gerardos_Portfolio/)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Analysis Workflow

The project follows a structured data analysis process.

## 1️. Data Exploration
- dataset inspection
- variable types review

---

## 1.1. Working with copies
- Avoid mistakes in original datasets

---

## 2. Data Cleaning
- Fixing invalid age values

---

## 2.1 Identifying columns
- Numeric columns
- Categorical columns
- Bollean columns

---

Diagnóstico inicial de variables numéricas

- `edad` [18 - 75]; median 38; Población adulta bien distribuida, sin sesgos extremos hacia jóvenes o adultos mayores.
- `nivel_ingreso` [\$8,000 - \$74,790.84]; mean \$30,019.70; std \$9,833.16; Clientes de diferentes capacidades económicas; no hay concentración extrema en un segmento.
- `visitas_mes` [1 - 25]; median 10; Mayoría de clientes visita la plataforma ~10 veces/mes; patrón predecible.
- `compras_mes` [0 - 8]; mean 1.20 (sesgada hacia compras bajas). 25% de clientes no compran (percentil 25 = 0); Esto marca dos segmentos: ***compradores activos vs. pasivos***.
- `gasto_publicidad_dirigida` [0 - 75.51]; distribución simétrica; Existe inversión diferenciada en publicidad; no todos los clientes reciben igual presupuesto.
- `satisfaccion` [1 - 5]; distribución simétrica; Clientes relativamente satisfechos (promedio superior a 3.5); sin extremos de insatisfacción masiva.
- `ingreso_anual` [0 - 244.69]; Suma total \$548,912.7; Muchos clientes sin ingresos; Sesgo positivo leve; std 34.48 muy alta respecto a la media (elevada dispersión); ~25% de clientes genera 0 ingresos (percentil 25 = 0); esto marca la principal segmentación del problema: ***clientes activos vs. inactivos***.

Recomendación: Considerar análisis segmentado (clientes con compras vs. sin compras) para correlaciones más claras

---

Diagnóstico inicial de variables binarias
- `abandono`
- - Activos 0: 12,739 (84.93%)
- - Inctivos 1: 2,261 (15.07%)

Potencial relación inversa con ingreso_anual (clientes que abandonen vs. que permanezcan).

- `miembro_premium`
- - Premium 1: 2,089 (13.93%)
- - No premium 0: 12,911 (86.07%)

Potencial relación con ingreso_anual.

- **Análisis cruzado**:

Categoría |----------- Count --| % del Total | Interpretación

No premium Activos:----10,741 | 71.60% --| Núcleo de clientes base

No premium Inactivos:---2,170 | 14.46% --| Riesgo: clientes base que se van

Premium Activos:--------1,998 | 13.32% --| Clientes de valor (retención alta)

Premium Inactivos:---------91 | 00.60% --| Riesgo bajo: retención premium muy alta

Hallazgo clave:

- Retención premium: (1,998 / 2,089) = 95.6%
- Retención base: (10,741 / 12,911) = 83.2%
- La suscripción premium correlaciona fuertemente con retención

---

**RECOMENDACIONES PARA ANÁLISIS**

1. Segmentación obligatoria:
- Clientes activos (compras_mes > 0) vs. inactivos
- Esto mejorará claridad de correlaciones

2. Variables listas para correlación:
- satisfaccion (sin ceros, varianza controlada)
- visitas_mes (distribución limpia)
- edad (rango simétrico)
- compras_mes, ingreso_anual (requieren tratamiento de ceros)

3. Relaciones esperadas a explorar:

- miembro_premium → ingreso_anual (correlación fuerte esperada)
- abandono → ingreso_anual (correlación negativa esperada)
- visitas_mes × compras_mes → ingreso_anual (patrón de engagement)

---

Diagnóstico inicial de variables categóricas

- `tipo_dispositivo`
- móvil (9,818 / ~65%)
- escritorio (3,720 / ~25%)
- tablet (1,462 / ~10%)

Distribución claramente desbalanceada: el móvil domina. No requiere transformación, pero conviene considerar el desbalance al interpretar resultados por segmento.

- `region`
- norte (4,395 / ~29%)
- oeste (3,810 / ~25%)
- sur (3,726 / ~25%)
- este (3,069 / ~20%)

Distribución relativamente equilibrada entre regiones. No requiere transformación adicional.

---

**Análisis cruzado**:

La proporción entre dispositivos se mantiene consistente en todas las regiones (móvil siempre predomina ~65%), lo que sugiere que no hay una concentración geográfica atípica por tipo de dispositivo. No se detectan combinaciones vacías ni anomalías.
