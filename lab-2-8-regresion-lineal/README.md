# Lab 2.8 · Regresión lineal

**IEI097 Minería de Datos · Unidad II · Actividad 2.8** — José Labarca

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/josemartinlabarca/mineria-datos-churn-telco/blob/main/lab-2-8-regresion-lineal/Lab_2_8_Regresion_Lineal.ipynb)

Regresión lineal simple y múltiple con `scikit-learn` sobre tres datasets reales. La pregunta central no es qué tan alto es el R², sino **si se puede confiar en el modelo y por qué**: residuos, data leakage, multicolinealidad y heterogeneidad entre subgrupos.

## Contenido

| Archivo | Descripción |
|---|---|
| [`Lab_2_8_Regresion_Lineal.ipynb`](Lab_2_8_Regresion_Lineal.ipynb) | Tres bloques: regresión simple, múltiple y transferencia al dataset propio |

## Bloques

| Bloque | Tipo | Dataset | Variable objetivo |
|---|---|---|---|
| 1 | Simple | [Breast Cancer Wisconsin](https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data) | `perimeter_mean`, `area_mean` |
| 2 | Múltiple | [FIFA 19](https://www.kaggle.com/datasets/karangadiya/fifa19) | `Overall` (+ desafío `Value`) |
| 3 | Múltiple | [Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) | `MonthlyCharges` |

## Resultados

| Modelo | R² prueba | ¿Se puede confiar? |
|---|---:|---|
| `perimeter_mean ~ radius_mean` | 0,996 | Sí: residuos aleatorios y relación lineal real (P = 2πr) |
| `area_mean ~ radius_mean` | 0,981 | No del todo: R² alto, pero residuos en U porque la relación es cuadrática |
| `Overall ~ 9 atributos` | 0,777 | Con reservas: subestima sistemáticamente a los arqueros |
| `MonthlyCharges ~ servicios` | 0,999 | Sí: sin leakage, generaliza y reconstruye la lista de precios |

## Decisiones clave

- **Data leakage:** en FIFA se excluyen `Potential`, `Value`, `Wage` y `Release Clause` porque se derivan del Overall. En Telco se excluye `TotalCharges` (≈ `MonthlyCharges × tenure`) y `Churn`, que ocurre después del cobro.
- **Multicolinealidad:** con VIF > 10 se eliminan `BallControl`, `Dribbling` y `LongPassing`. En Telco, la codificación 1/0 por servicio deja todos los VIF bajo 3 y evita las columnas duplicadas que genera `get_dummies` directo.
- **Heterogeneidad:** el modelo de FIFA tiene sesgo casi nulo en general, pero un residuo medio de +1,26 en arqueros. En Telco se comparan subgrupos por MAE y no por R², porque el grupo sin internet casi no varía.
- **Interpretación:** en Telco el coeficiente de fibra óptica es ≈ 50 USD/mes sobre un cliente sin internet; el modelo recupera la tarifa de cada servicio.

## Cómo ejecutar

1. Abrir el notebook con el botón **Open in Colab**.
2. Agregar el token de Kaggle en los **Secretos de Colab** (🔑) como `KAGGLE_API_TOKEN` y activar el acceso del notebook.
3. Ejecutar **Entorno de ejecución → Reiniciar sesión y ejecutar todo**.

**Librerías:** pandas, numpy, matplotlib, seaborn, scikit-learn, statsmodels.
