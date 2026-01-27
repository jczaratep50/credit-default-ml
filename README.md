# Credit Risk Modeling — Default Prediction

Este proyecto tiene como objetivo construir y evaluar un modelo de riesgo crediticio para la predicción de **default**, abordando explícitamente el problema de **desbalance de clases**, común en aplicaciones financieras reales.

## Estructura del Proyecto

El proyecto se desarrolla en **dos notebooks principales**:

### 1. Exploratory Data Analysis (EDA)
- Análisis de la variable objetivo (TARGET)
- Identificación de desbalance de clases.
- Diagnóstico de Calidad de Datos
- Reducción Inicial de Variables
- Importancia de variables mediante Mutual Information y XGBoost
- Insights iniciales del modelado

### 2. Modelado y Evaluación
- Preparación de datos (encoding, splits train / validation / test)
- Entrenamiento de modelos:
  + Regresión Logística
  + Árbol de Decisión
  + XGBoost
- Comparación mediante métricas:
  + ROC-AUC
  + Recall (default)
  + Precision (default)
- Ajuste de:
  + *scale_pos_weight*
  + Umbral de decisión
 - Selección y evaluación final del modelo sobre el conjunto de prueba

## Métricas de Evaluación

Dado el fuerte desbalance de clases, se priorizan métricas enfocadas en la clase minoritaria (default):

- **ROC-AUC**: capacidad discriminativa global
- **Recall (default)**: detección efectiva de clientes en default
- **Precision (default)**: control de falsos positivos

## Modelo Final Seleccionado

**XGBoost**, ajustando:
- scale_pos_weight $\approx 0.75$
- Umbral de decisión = 0.3

Resultados finales en conjunto de prueba:
- ROC-AUC $\approx 0.75$
- Recall (default) $\approx 0.91$
- Precision (default) $\approx 0.11$

Este modelo logra un balance adecuado entre capacidad predictiva y detección de eventos de default, alineado con los objetivos del negocio.

## Conclusiones
- Modelos complejos presentan mejor discriminación global, pero requieren ajustes explícitos para capturar la clase minoritaria.
- El ajuste del umbral de decisión es clave para controlar el trade-off entre recall y precision.
- XGBoost ofrece la mejor flexibilidad para adaptar el modelo a distintos objetivos de riesgo.
