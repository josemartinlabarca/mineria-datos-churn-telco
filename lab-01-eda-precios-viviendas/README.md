# Lab 01 · Análisis exploratorio de precios de viviendas

**IEI097 Minería de Datos · Unidad I · Laboratorio 01** — José Labarca

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/josemartinlabarca/mineria-datos-churn-telco/blob/main/lab-01-eda-precios-viviendas/Lab01_EDA_Labarca_jose.ipynb)

Análisis exploratorio (EDA) de un dataset de ventas de viviendas, enmarcado en la fase de **Comprensión de los Datos** de CRISP-DM: procedencia, estructura, calidad y distribución de las variables antes de cualquier modelo.

## Contenido

| Archivo | Descripción |
|---|---|
| [`Lab01_EDA_Labarca_jose.ipynb`](Lab01_EDA_Labarca_jose.ipynb) | Fuente de datos, estructura, nulos, duplicados, estadística descriptiva, hallazgos y relación con CRISP-DM |

## Datos

**Dataset:** [House price prediction](https://www.kaggle.com/datasets/shree1992/housedata) (Kaggle, shree1992), archivo `data.csv`.

- **4.600 viviendas** (una fila por propiedad vendida) y **18 columnas**.
- 13 columnas numéricas (precio, dormitorios, baños, superficies, año de construcción y renovación) y 5 de texto (fecha, calle, ciudad, código postal y país).
- Sin valores nulos ni filas duplicadas.

## Qué se revisa

1. Procedencia del dataset y unidad de análisis.
2. Tipos de columnas y su significado, más allá del tipo que asigna pandas.
3. Valores nulos y filas duplicadas, sin asumir que un nulo es un cero.
4. Estadística descriptiva y distribución de las variables numéricas.
5. Utilidad del dataset y preguntas pendientes para la fase siguiente.

## Cómo ejecutar

1. Descargar `data.csv` desde Kaggle.
2. Abrir el notebook con el botón **Open in Colab** y ejecutar las celdas en orden.
3. Cuando la celda de carga lo pida, subir `data.csv`.

**Librerías:** pandas, numpy, matplotlib, seaborn.
