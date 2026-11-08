# Evaluación Unidad 1 · Fuga de clientes Telco

**IEI097 Minería de Datos · Unidad I** — José Labarca

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/josemartinlabarca/mineria-datos-churn-telco/blob/main/evaluacion-u1-churn-telco/EvaluacionUnidad1Joselabarca.ipynb)

Proyecto completo con la metodología **CRISP-DM** para encontrar qué perfiles de clientes de una empresa de telecomunicaciones tienen más riesgo de irse y convertirlo en reglas de retención.

## Contenido

| Archivo | Descripción |
|---|---|
| [`EvaluacionUnidad1Joselabarca.ipynb`](EvaluacionUnidad1Joselabarca.ipynb) | Problema, datos, limpieza, EDA, reglas de asociación, árbol de decisión y síntesis |

## Problema

Perder un suscriptor significa dejar de recibir su pago mensual y además pagar de nuevo el costo de captar un reemplazo. La pregunta es qué combinaciones de contrato, servicios y forma de pago concentran la fuga, para diseñar campañas de retención preventivas.

**Dataset:** Telco Customer Churn (IBM Sample Data Sets, también en [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn); 7.043 clientes). Tasa base de fuga: **26,5 %**.

## Preparación

- `TotalCharges` tenía 11 valores en blanco, todos de clientes con `tenure = 0` (aún sin facturar): se imputó 0.
- `customerID` se descartó por ser un identificador sin poder de generalización.
- `tenure` y `MonthlyCharges` se discretizaron en intervalos para Apriori, que trabaja con variables binarias.

## Resultados

### Reglas de asociación (soporte ≥ 8 %, lift > 1,2)

| Regla → Churn = Yes | Soporte | Confianza | Lift |
|---|---:|---:|---:|
| Contrato mes a mes + fibra óptica | 16,5 % | 54,6 % | 2,06 |
| Contrato mes a mes + sin soporte técnico | 19,2 % | 50,4 % | 1,90 |
| Contrato mes a mes + pago con cheque electrónico | 14,1 % | 53,7 % | 2,02 |

### Árbol de decisión (CART, entropía, profundidad 3)

| Camino | Clasificación | Acción propuesta |
|---|---|---|
| Mes a mes → sin soporte técnico → antigüedad ≤ 10,5 meses | Se va | Onboarding de 90 días con 3 meses de soporte prioritario gratis |
| Contrato anual o bianual | Se queda | Promoción de migración a contrato anual al mes 6 |

La profundidad se limitó a 3 para evitar sobreajuste y para que el equipo comercial pueda leer el árbol directamente.

## Cómo ejecutar

1. Abrir el notebook con el botón **Open in Colab**.
2. Ejecutar **Entorno de ejecución → Reiniciar sesión y ejecutar todo**.

El CSV se descarga directamente del [repositorio público de IBM](https://github.com/IBM/telco-customer-churn-on-icp4d), así que no hace falta token de Kaggle.

**Librerías:** pandas, numpy, matplotlib, seaborn, mlxtend, scikit-learn.
