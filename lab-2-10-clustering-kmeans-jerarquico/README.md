# Lab 2.10 · Clustering: K-means y jerárquico

**IEI097 Minería de Datos · Unidad II · Actividad 2.10** — José Labarca

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/josemartinlabarca/mineria-datos-churn-telco/blob/main/lab-2-10-clustering-kmeans-jerarquico/Lab_2_10_Clustering_KMeans_Jerarquico.ipynb)

Laboratorio de aprendizaje no supervisado con dos familias de clustering sobre datos reales sin etiquetas. Cada ejercicio sigue las mismas fases: **hipótesis → exploración → preparación → modelado y evaluación → interpretación**.

> Un cluster significa «estas observaciones son cercanas bajo *estas* variables, *esta* transformación, *esta* distancia y *estos* parámetros». Ningún grupo de este trabajo es un ranking ni una verdad oculta en los datos.

## Contenido

| Archivo | Descripción |
|---|---|
| [`Lab_2_10_Clustering_KMeans_Jerarquico.ipynb`](Lab_2_10_Clustering_KMeans_Jerarquico.ipynb) | Notebook único con ambos ejercicios |

## Ejercicio 1 · K-means: segmentación de clientes

**Dataset:** [Mall Customer Segmentation Data](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python) (200 clientes × 5 columnas).

**Pregunta:** ¿qué segmentos de clientes justifican comunicaciones distintas?

- **Variables del modelo:** ingreso anual y puntaje de gasto, estandarizados. `CustomerID` y `Gender` quedan fuera de la distancia.
- **Elección de k = 5**, sostenida por tres evidencias:
  - *Estructura:* silueta máxima (≈ 0,55) y codo en el mismo punto.
  - *Estabilidad:* misma partición con distintas semillas y ARI ≈ 0,99 en submuestras del 80 %.
  - *Utilidad:* cada grupo se describe en una frase y pide una acción distinta.
- **Experimento de escala:** con ingreso en k$ el resultado no cambia al estandarizar (ambas variables tienen casi la misma dispersión), pero con el ingreso en dólares el modelo sin estandarizar corta solo por ingreso.

| Segmento | Perfil | Acción propuesta |
|---|---|---|
| Premium activos | Ingreso alto, gasto alto | Fidelización VIP |
| Acomodados cautelosos | Ingreso alto, gasto bajo | Mensajes de calidad y valor |
| Jóvenes entusiastas | Ingreso bajo, gasto alto | Promociones en redes y novedades |
| Ahorradores ajustados | Ingreso bajo, gasto bajo | Ofertas de precio y básicos |
| Clientes promedio | Ingreso y gasto medios | Newsletter general y pruebas A/B |

## Ejercicio 2 · Clustering jerárquico: ¿con qué países se parece Chile?

**Dataset:** [Unsupervised Learning on Country Data](https://www.kaggle.com/datasets/rohan0301/unsupervised-learning-on-country-data) (167 países × 10 columnas).

- **Muestra:** 33 países, todos los de América disponibles en el dataset más 6 referencias de la OCDE (España, Portugal, Grecia, Polonia, Nueva Zelanda y Corea del Sur).
- **Dendrogramas** con enlaces *single*, *complete*, *average* y *ward*, más la comparación de ward con y sin estandarizar. Sin estandarizar, los grupos son franjas de PIB per cápita.
- **Corte elegido:** ward en 4 grupos (saltos de altura, silueta y utilidad interpretativa).
- **Resultado:** Chile se agrupa con las economías sudamericanas de ingreso medio; sus vecinos más cercanos son **Uruguay y Costa Rica**. Polonia y Corea del Sur se le unen recién a un nivel más alto de la jerarquía.
- **Comparación con K-means** (mismo k): tabla de contingencia y ARI. Ambos métodos coinciden en los extremos y difieren en cómo dividen el bloque latinoamericano.

## Cómo ejecutar

1. Abrir el notebook con el botón **Open in Colab**.
2. Agregar el token de Kaggle en los **Secretos de Colab** (🔑) como `KAGGLE_API_TOKEN` y activar el acceso del notebook.
3. Ejecutar **Entorno de ejecución → Reiniciar sesión y ejecutar todo**.

Los datasets se descargan con `kagglehub`. Resultados reproducibles con `random_state = 42` y `n_init = 10`.

**Librerías:** pandas, numpy, matplotlib, seaborn, scikit-learn, SciPy.

## Limitaciones

- Los grupos dependen de las variables, la escala, la distancia y la muestra elegidas.
- En países, varias variables están muy correlacionadas (ingreso y PIB per cápita, por ejemplo), por lo que la riqueza y la salud pesan doble en la distancia.
- El *Spending Score* lo asigna el centro comercial con una regla desconocida. Los segmentos describen ese puntaje, no a las personas.
- No se emiten juicios de valor sobre países a partir de su grupo.
