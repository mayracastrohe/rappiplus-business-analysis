# 📊 Diagnóstico Estratégico de Negocio — RappiPlus

> **Análisis integral de ventas, rentabilidad, conversión y retención utilizando Python, SQL y Tableau para transformar datos en decisiones de negocio accionables.**

[![Python](https://img.shields.io/badge/Python-Analysis-blue?logo=python&logoColor=white)](https://www.python.org/)
[![PostgreSQL](https://img.shields.io/badge/SQL-PostgreSQL-blue?logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Tableau](https://img.shields.io/badge/Tableau-Dashboard-blue?logo=tableau&logoColor=white)](https://www.tableau.com/)

---

## 🎯 Objetivo del proyecto

Realizar un **diagnóstico estratégico del negocio de RappiPlus**, analizando el comportamiento de las ventas, rentabilidad, marketing, conversión y retención de usuarios.

El objetivo es identificar **oportunidades de crecimiento y cuellos de botella operativos**, transformando los resultados del análisis en insights claros y accionables para apoyar la toma de decisiones de stakeholders no técnicos.

---

## 🧠 Preguntas de negocio

El análisis busca responder preguntas como:

- ¿Cuál es el revenue, profit y margen del negocio?
- ¿Qué productos y categorías tienen mejor desempeño?
- ¿Qué países y canales generan mayor revenue?
- ¿En qué etapa del funnel se concentra la mayor pérdida de usuarios?
- ¿Cómo evoluciona la retención de los usuarios a través de las cohortes?
- ¿El cambio realizado en la interfaz del checkout generó una mejora significativa en la conversión?
- ¿Dónde existen oportunidades de crecimiento?
- ¿Qué factores deberían priorizarse para mejorar el desempeño del negocio?

---

## 🛠️ Herramientas y tecnologías

| Herramienta | Uso |
|---|---|
| 🐍 **Python** | Limpieza, transformación, análisis y visualización de datos |
| 🐼 **Pandas / NumPy** | Manipulación y análisis de datos |
| 📈 **Matplotlib** | Visualización exploratoria |
| 📊 **SciPy / Statsmodels** | Análisis y pruebas estadísticas |
| 🗄️ **PostgreSQL / SQL** | Funnel, cohortes y análisis de comportamiento |
| 📊 **Tableau** | Dashboards interactivos y comunicación de insights |

---

## 📁 Estructura del proyecto

```text
├── notebook_analisis.ipynb
│
├── data/
│   ├── orders_clean.csv
│   ├── catalog_clean.csv
│   └── marketing_clean.csv
│
├── dashboard/
│
└── README.md
```

---

# 🔍 Proceso de análisis

## 1️⃣ Limpieza y preparación de datos

Se identificaron y trataron diferentes problemas de calidad:

- Valores nulos.
- Duplicados.
- Inconsistencias de formato.
- Valores atípicos.
- Devoluciones.

En lugar de eliminar automáticamente los registros considerados atípicos, se utilizaron **banderas para identificarlos y analizarlos por separado**, preservando así la información original y documentando las decisiones tomadas durante el proceso.

---

## 2️⃣ KPIs de negocio

Se calcularon los principales indicadores para evaluar el desempeño financiero y comercial:

- **Revenue**
- **Cost**
- **Profit**
- **Margen**
- **Ticket promedio**
- **Producto más vendido**

También se realizó un análisis crítico del impacto de **5 pedidos atípicos** sobre el ranking de productos más vendidos.

---

## 3️⃣ Funnel de conversión — SQL

Se construyó un **funnel de conversión de 6 etapas utilizando PostgreSQL**, aplicando funciones de ventana como:

- `LAG`
- `ROW_NUMBER`
- `CTE`

### 🔎 Hallazgo clave

El principal cuello de botella se encuentra entre:

`begin_checkout → add_payment_info`

con una disminución de **13,29%**.

Este resultado indica que el proceso de pago representa un punto importante de oportunidad para investigar posibles fricciones en la experiencia del usuario.

---

## 4️⃣ Retención por cohortes — SQL

Se realizó un análisis de **retención semanal para 5 cohortes mensuales**.

### 🔎 Hallazgo clave

La retención se mantiene relativamente estable, aproximadamente entre **40% y 44%**, sin evidencia de un deterioro progresivo entre las cohortes analizadas.

Este comportamiento permite diferenciar el problema de conversión de posibles problemas de retención a largo plazo.

---

## 5️⃣ Test A/B

Se evaluó estadísticamente un cambio realizado en la interfaz del checkout mediante un **test de proporciones de dos muestras**.

### Resultado

**p-value = 0.4161**

No se encontró evidencia estadísticamente significativa de que el cambio en la interfaz haya producido una mejora en la conversión.

Esto significa que, con los datos analizados, no es posible concluir que la nueva versión del checkout haya generado un impacto positivo significativo.

---

# 📊 Dashboards en Tableau

El proyecto incluye dashboards interactivos diseñados para comunicar los resultados de manera clara a usuarios no técnicos.

### 📌 Overview Ejecutivo

Incluye:

- KPIs principales.
- Tendencia de revenue.
- Revenue por país.
- Revenue por canal.

### 📌 Detalle

Incluye:

- Tabla detallada de órdenes.
- Formato condicional para identificar profit positivo y negativo.
- Heatmap de país vs. categoría.
- Drill-through interactivo por producto.

---

# 📈 Principales resultados

### 💰 Desempeño financiero

- **Revenue total:** $51.99M
- **Profit:** $8.84M
- **Margen:** 17,01%

### 🌎 Distribución geográfica

**Argentina y México concentran aproximadamente el 78% del revenue.**

Por otro lado, **Colombia representa una oportunidad de crecimiento**, especialmente dentro de la categoría **Electrónica**.

### 🛒 Conversión

La conversión general del funnel alcanza:

**80,04%**

Sin embargo, el análisis por etapas identifica como principal punto de fricción el paso entre `begin_checkout` y `add_payment_info`.

### 👥 Retención

La retención se mantiene estable entre las cohortes mensuales, aproximadamente entre:

**40% – 44%**

---

# 💡 Insights y oportunidades

A partir del análisis realizado se identifican varias oportunidades:

### 1. Optimizar el proceso de checkout

Investigar las causas de abandono entre `begin_checkout` y `add_payment_info`, ya que representa el principal cuello de botella identificado en el funnel.

### 2. Analizar oportunidades en Colombia

Profundizar en el mercado colombiano, especialmente en la categoría **Electrónica**, para identificar posibilidades de crecimiento.

### 3. Monitorear rentabilidad

No evaluar únicamente el volumen de ventas. El análisis conjunto de **revenue, profit y margen** permite identificar productos y mercados que realmente generan valor para el negocio.

### 4. Continuar monitoreando la retención

Aunque las cohortes muestran una retención relativamente estable, mantener un seguimiento periódico permitirá detectar cambios en el comportamiento de los usuarios.

### 5. Evaluar cambios mediante experimentación

El test A/B demuestra la importancia de validar las decisiones de producto mediante evidencia estadística y no únicamente mediante cambios observados en los indicadores.

---

# 🔗 Dashboard interactivo

### 👉 [📊 Ver Dashboard en Tableau Public](https://public.tableau.com/views/Sprint12_17846898949130/OverviewEjecutivo?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

Explora el dashboard para interactuar con los KPIs, filtros, visualizaciones y análisis desarrollados durante el proyecto.

---

# 📚 Habilidades demostradas

Este proyecto demuestra experiencia práctica en:

- Análisis exploratorio de datos.
- Limpieza y preparación de datos.
- Manipulación de datos con **Pandas y NumPy**.
- Análisis de KPIs de negocio.
- SQL avanzado.
- CTEs y funciones de ventana.
- Análisis de funnel.
- Análisis de cohortes y retención.
- Pruebas estadísticas.
- Interpretación de tests A/B.
- Visualización de datos.
- Construcción de dashboards en Tableau.
- Comunicación de insights para stakeholders no técnicos.
- Transformación de datos en recomendaciones de negocio.

---

## 👩‍💻 Autora

Mayra Alejandra Castro Herrera

**Proyecto desarrollado como parte de mi formación profesional en Análisis de Datos.**

Este proyecto forma parte de mi portafolio y demuestra la aplicación práctica de **Python, SQL, estadística y Tableau** para analizar problemas de negocio y comunicar resultados de manera clara y accionable.

---

⭐ **Si encuentras interesante este proyecto, te invito a explorar el dashboard y revisar el repositorio.**
