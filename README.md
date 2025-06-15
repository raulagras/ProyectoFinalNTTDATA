# Proyecto_Final_NTTDATA
Este es el repositorio del proyecto final del Grupo 1 del master IA &amp; Big Data 2025 de NTTDATA

# 📊 Redes Sociales vs Productividad

Análisis de datos y modelo de predicción que explora la relación entre el uso de redes sociales y la productividad personal, visualizado mediante Power BI e impulsado por modelos de IA desarrollados en Python.

---

## 📌 Descripción del Proyecto

Este proyecto analiza el impacto del uso de redes sociales sobre la productividad utilizando un dataset de Kaggle con 30.000 registros y 19 variables relacionadas con hábitos digitales, salud mental y desempeño personal.

### 🎯 Objetivo

Desarrollar un modelo de regresión para predecir la productividad (`actual_productivity_score`, escala 0–10) a partir de variables como:

- Tiempo diario en redes (`daily_social_media_time`)
- Número de notificaciones
- Uso de apps de enfoque (`uses_focus_apps`)
- Tiempo de pantalla antes de dormir
- Interrupciones durante el trabajo

Los datos se integran en un dashboard de Power BI con análisis interactivo por género, tipo de trabajo y red social preferida.

### 🧩 Aplicaciones

- 📱 Bienestar digital personalizado
- 📈 Análisis organizacional
- 🤖 Sugerencias basadas en IA para mejorar hábitos
- 🧠 Autoconocimiento y gestión del tiempo

---

## ⚙️ Arquitectura Técnica

### 🛠 Herramientas

- **Visualización**: Power BI Desktop (junio 2025)
- **Modelado IA**: Python en Google Colab
  - Librerías: `pandas`, `numpy`, `scikit-learn`, `shap`, `wandb`

### 🧬 Esquema de Datos

- `DimUser`: edad, género, ID
- `DimJob`: tipo de trabajo (Student, IT, Health, etc.)
- `DimSocialMedia`: plataformas preferidas
- `FactProductivity`: variables clave del análisis


## 📊 Visualizaciones en Power BI

- **KPIs**: productividad, estrés, calidad del sueño, tiempo en redes sociales.
- **Gráficos**: segmentaciones por edad, género, tipo de trabajo y plataforma social preferida.
- **Páginas del dashboard**:
  - **Dashboard Principal**: visión general con indicadores clave.
  - **Productivity vs Social Media**: foco en hábitos digitales y su impacto.
  - **Productividad Máxima**: análisis de condiciones óptimas para el desempeño.

---

## 🔄 Pipeline de Datos

### 1. Ingesta y Limpieza

- Dataset: `social_media_vs_productivity.csv`
- Procesado en **Google Colab** usando **PySpark** (30.000 filas, 19 columnas)
- Acciones realizadas:
  - Conversión de tipos de datos
  - Validación de rangos numéricos
  - Conservación y revisión de outliers mediante **IQR**

### 2. Imputación de Nulos
  Se llevan a cabo dos visiones:
- **Imputación por KNN** (K-Nearest Neighbors) para variables numéricas y categóricas.
  
- **Media o mediana**, según presencia de outliers, para variables continuas y categóricas.

### 3. Modelado Predictivo con IA

- **Preprocesamiento**:
  - `StandardScaler`, `LabelEncoder`
  - Selección de características: `SelectKBest`, `PCA`
  - Ajuste de sesgos de distribución con funciones (log, sqrt)
- **Modelos utilizados**:
  - `LinearRegression`
  - `RandomForestRegressor`
  - `GradientBoostingRegressor`
  - `MLPRegressor` (Perceptrón multicapa)
- **Validación**:
  - Cross-validation anidada (5 folds externos, 3 internos)
  - `GridSearchCV` para ajuste de hiperparámetros
- **Evaluación**:
  - Métricas: R², RMSE, MAE
  - Interpretabilidad del modelo: `SHAP`
- **Seguimiento y persistencia**:
  - `wandb` para experimentación
  - Guardado con `joblib` / `pickle`

---

## 📈 Integración con Power BI

- Integración basada en un **modelo estrella** (dimensiones y hechos)
- Visualizaciones y KPIs **interactivos** filtrables por:
  - Género
  - Tipo de trabajo
  - Red social preferida
- **Predicciones del modelo IA** incorporadas como indicadores clave para análisis personalizado



Autores y Créditos

**Agras Basanta Raúl, Esmoris Barreira Javier, García Porteiro Carlota, Marinovic Garrido Camila, Prado Darriba Aaron**

Dataset original: Kaggle - Social Media vs Productivity
