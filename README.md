# 🌍 Predicción de Calidad del Aire con Machine Learning (XGBoost)

Este repositorio contiene el **Proyecto Final de Machine Learning**, enfocado en desarrollar un sistema predictivo de alertas tempranas para la calidad del aire (PM2.5). 

El modelo clasifica la calidad del aire en 5 niveles (Desde "Muy Bueno" a "Muy Malo") utilizando datos meteorológicos y de contaminantes químicos, priorizando la detección de emergencias ambientales mediante técnicas avanzadas de balanceo de datos.

## 🚀 Características Principales

* **Enfoque de Clasificación:** Transformación del problema de regresión a clasificación multiclase para generar alertas sanitarias.
* **Ingeniería de Datos Robusta:**
    * Limpieza de nulos mediante **Interpolación Lineal Temporal** (recuperando ~20% de datos críticos).
    * Vectorización de la Dirección del Viento (Seno/Coseno).
    * Análisis de redundancia con **PCA** (Gases Nitrogenados).
* **Manejo de Desbalance:** Aplicación de **SMOTE** (Synthetic Minority Over-sampling Technique) para garantizar que el modelo aprenda a detectar la clase minoritaria "Muy Malo".
* **Modelado Comparativo:** Evaluación rigurosa entre **Random Forest, KNN y XGBoost**.
* **Sistema de Inferencia:** Script funcional para predicciones en tiempo real basado en input manual.

## 📂 Estructura del Proyecto

El flujo de trabajo se divide en 5 notebooks secuenciales:

1.  `1_Analisis_Exploratorio.ipynb`: Auditoría inicial de los 12 CSVs, detección de nulos y outliers.
2.  `2_Procesamiento_Datos.ipynb`: Unificación de datasets, limpieza (Interpolación), Feature Engineering y creación del Target.
3.  `3_PCA_y_Balanceo_SMOTE.ipynb`: Análisis PCA, Split de datos (Train/Test) y aplicación de SMOTE solo al set de entrenamiento.
4.  `4_Entrenamiento_Evaluacion.ipynb`: Entrenamiento de modelos, cálculo de métricas (Matriz de Confusión, ROC, F1-Score) y selección del mejor modelo (XGBoost).
5.  `5_Codigo_Inferencia.ipynb`: Carga del modelo serializado (`.joblib`) y simulación de predicción con nuevos datos.

## 📊 Resultados del Modelo (XGBoost)

El modelo seleccionado fue **XGBoost** debido a su eficiencia y capacidad de generalización.

* **Accuracy Global en Test:** ~86%
* **Recall en Clase "Muy Malo" (Emergencia):** **0.97**
    * *Interpretación:* El modelo es capaz de detectar el 97% de los eventos críticos reales, priorizando la salud pública.
* **Variable más influyente:** PM10 (validando la correlación física con PM2.5).


## 🛠️ Instalación y Requisitos

Para ejecutar este proyecto localmente:

1.  Clonar el repositorio:
    ```bash
    git clone [https://github.com/NicolasFluxa/Prediccion-Calidad-Aire-ML.git]
    ```
2.  Instalar las dependencias:
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn xgboost imbalanced-learn joblib
    ```

## 📝 Dataset

El dataset unificado consta de **49,703 registros** horarios con 11 variables predictoras:
* **Químicas:** CO, NO, NO2, NOx, O3, PM10, SO2.
* **Meteorológicas:** Humedad, Temperatura, Viento (Componentes Vectoriales).

## ✒️ Autores

* **[Tu Nombre Completo]** - *Desarrollo y Modelado*
* **[Nombre de tu compañero si aplica]**

---
*Proyecto realizado para la asignatura de Machine Learning - 2025.*
