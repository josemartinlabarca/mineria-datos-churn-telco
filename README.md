# Minería de Datos · Portafolio del curso

**IEI097 Minería de Datos** · Ingeniería en Informática · Instituto Profesional Santo Tomás  
**Autor:** José Labarca · 2026

![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white)
![scikit--learn](https://img.shields.io/badge/scikit--learn-F7931E?logo=scikitlearn&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?logo=googlecolab&logoColor=white)

Evaluación y laboratorios del curso, cada uno en su carpeta con su propio README. Todos los análisis parten de una pregunta de negocio, justifican cada decisión de preparación y modelado, y terminan en recomendaciones concretas.

## Contenido

| N.º | Actividad | Técnica | Pregunta | Colab |
|---|---|---|---|---|
| U1 | [Evaluación Unidad 1](evaluacion-u1-churn-telco/) | Reglas de asociación + árbol de decisión (CRISP-DM) | ¿Qué clientes de una telco tienen más riesgo de irse? | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/josemartinlabarca/mineria-datos-churn-telco/blob/main/evaluacion-u1-churn-telco/EvaluacionUnidad1Joselabarca.ipynb) |
| 2.6 | [Reglas de asociación](lab-2-6-reglas-asociacion/) | Apriori | ¿Qué productos se compran juntos en un supermercado? | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/josemartinlabarca/mineria-datos-churn-telco/blob/main/lab-2-6-reglas-asociacion/Lab_2_6_Reglas_Asociacion.ipynb) |
| 2.8 | [Regresión lineal](lab-2-8-regresion-lineal/) | Regresión simple y múltiple | ¿Cuándo se puede confiar en un modelo con R² alto? | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/josemartinlabarca/mineria-datos-churn-telco/blob/main/lab-2-8-regresion-lineal/Lab_2_8_Regresion_Lineal.ipynb) |
| 2.10 | [Clustering](lab-2-10-clustering-kmeans-jerarquico/) | K-means y jerárquico | ¿Qué segmentos de clientes hay? ¿A qué países se parece Chile? | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/josemartinlabarca/mineria-datos-churn-telco/blob/main/lab-2-10-clustering-kmeans-jerarquico/Lab_2_10_Clustering_KMeans_Jerarquico.ipynb) |

## Resultados destacados

- **Fuga de clientes:** los contratos mes a mes con fibra óptica duplican el riesgo de fuga (lift 2,06). Un cliente nuevo, mes a mes y sin soporte técnico es el perfil de mayor riesgo.
- **Canasta de compras:** quien compra cerveza lleva salchichas un 22 % más que el cliente promedio; una regla con confianza alta se descartó por tener lift < 1.
- **Regresión:** un R² de 0,98 no basta si los residuos forman una U. En Telco, el modelo reconstruye la lista de precios de cada servicio (R² 0,999) tras excluir variables con leakage.
- **Clustering:** cinco segmentos de clientes con una acción distinta para cada uno. Chile se agrupa con Uruguay y Costa Rica.

## Estructura

```
.
├── evaluacion-u1-churn-telco/
├── lab-2-6-reglas-asociacion/
├── lab-2-8-regresion-lineal/
└── lab-2-10-clustering-kmeans-jerarquico/
```

Cada carpeta tiene el notebook y un README con el problema, los datos, las decisiones, los resultados y cómo ejecutarlo.

## Cómo ejecutar los notebooks

1. Abrir el notebook con su botón **Open in Colab**.
2. Para los laboratorios de la Unidad II, guardar el token de Kaggle en los **Secretos de Colab** (🔑) como `KAGGLE_API_TOKEN` y activar el acceso del notebook. La Evaluación U1 no lo necesita.
3. Ejecutar **Entorno de ejecución → Reiniciar sesión y ejecutar todo**.

Los datasets se descargan al ejecutar. Ningún token ni credencial se guarda en este repositorio.

## Herramientas

Python · pandas · NumPy · matplotlib · seaborn · scikit-learn · SciPy · statsmodels · mlxtend · Google Colab
