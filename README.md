# NovaRetailPlus-E-Commerce-Behavioral-Factors---Correlational-exploratory-analysis.
Which customer behavior factors are most strongly associated with annual revenue generated?  This project is a correlational (exploratory) analysis.  Correlation ≠ causation.

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
