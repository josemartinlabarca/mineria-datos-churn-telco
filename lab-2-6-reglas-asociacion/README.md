# Lab 2.6 · Reglas de asociación con Apriori

**IEI097 Minería de Datos · Unidad II · Actividad 2.6** — José Labarca

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/josemartinlabarca/mineria-datos-churn-telco/blob/main/lab-2-6-reglas-asociacion/Lab_2_6_Reglas_Asociacion.ipynb)

Análisis de canasta de compras de un supermercado con el algoritmo **Apriori** (`mlxtend`): itemsets frecuentes, comparación de umbrales e interpretación de reglas en lenguaje de negocio.

## Contenido

| Archivo | Descripción |
|---|---|
| [`Lab_2_6_Reglas_Asociacion.ipynb`](Lab_2_6_Reglas_Asociacion.ipynb) | Carga, preparación, itemsets, reglas, experimento de umbrales e interpretación |

## Datos

**Dataset:** [Groceries Dataset for Market Basket Analysis](https://www.kaggle.com/datasets/rashikrahmanpritom/groceries-dataset-for-market-basket-analysis) (Kaggle).

- Una transacción es la compra de un cliente en un día (`Member_number` + `Date`), como una boleta.
- **14.963 transacciones**, **167 productos distintos**, 2,59 productos por compra en promedio.
- Preparación: nulos, nombres inconsistentes, duplicados dentro de una misma boleta y paso a formato binario (canasta × producto).

## Fases

1. **Itemsets frecuentes:** el soporte mínimo se eligió a partir de la distribución del soporte de cada producto.
2. **Reglas:** ordenadas por lift y luego confianza, porque la confianza sola favorece a los productos que todos compran.
3. **Experimento de umbrales:** varias combinaciones de soporte y confianza mínimos para ver cuántas reglas sobreviven.
4. **Verificación manual:** soporte, confianza y lift de la mejor regla calculados a mano contando transacciones.

## Resultados

| Regla | Soporte | Confianza | Lift | Lectura de negocio |
|---|---:|---:|---:|---|
| cerveza → salchichas | 0,003 | 0,074 | 1,22 | Quien compra cerveza lleva salchichas un 22 % más que un cliente cualquiera |
| vienesas → otras verduras | 0,005 | 0,136 | 1,12 | Compra para una comida completa |
| salchichas → yogur | 0,006 | 0,095 | 1,11 | Relación débil pero frecuente |

**Regla descartada:** cerveza → leche entera tiene la confianza más alta (15,8 %), pero lift 0,999. La leche aparece en el 15,8 % de todas las compras, así que la cerveza no cambia nada: la "confianza alta" solo refleja que la leche es el producto más vendido.

Todos los lift quedan entre 1,01 y 1,22: son asociaciones débiles, y las tres primeras son las únicas que sirven para tomar decisiones.

## Cómo ejecutar

1. Abrir el notebook con el botón **Open in Colab**.
2. Agregar el token de Kaggle en los **Secretos de Colab** (🔑) como `KAGGLE_API_TOKEN` y activar el acceso del notebook.
3. Ejecutar la celda de instalación; tras el reinicio automático, seguir con **Entorno de ejecución → Ejecutar celda seleccionada y siguientes**.

**Librerías:** pandas, matplotlib, mlxtend.
