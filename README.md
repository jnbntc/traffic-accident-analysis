# Traffic Accident Analysis

<p>
  <img src="https://img.shields.io/badge/Python-Data_Analysis-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/Jupyter-Notebooks-F37626?style=flat-square&logo=jupyter&logoColor=white" alt="Jupyter" />
  <img src="https://img.shields.io/badge/ML-Classification-333333?style=flat-square" alt="Machine Learning Classification" />
</p>

Proyecto de análisis exploratorio y modelado predictivo sobre datos de accidentes de tránsito.

El objetivo principal es estudiar la variable **`Injury Severity`** y comparar distintos modelos de clasificación para predecir la severidad de las lesiones a partir de características del accidente, del entorno, del vehículo y del conductor.

> **Hallazgo principal:** aunque los modelos evaluados superaron el 80% de accuracy global, el fuerte desbalance de clases redujo de forma importante precision, recall y F1 en las categorías minoritarias más relevantes, como `FATAL INJURY` y `SUSPECTED SERIOUS INJURY`.

## Contenido del repositorio

| Archivo | Propósito |
| --- | --- |
| `dataset_description.ipynb` | Exploración y descripción de las variables del dataset |
| `accident_severity_analysis.ipynb` | Preprocesamiento, análisis exploratorio, entrenamiento y evaluación de modelos |
| `crash_data.csv` | Dataset utilizado por los notebooks |

## Objetivo de modelado

El análisis utiliza variables relacionadas con:

- tipo de colisión;
- límite de velocidad;
- control de tránsito;
- daños del vehículo;
- clima y estado de la superficie;
- condiciones de iluminación;
- consumo de sustancias;
- distracción del conductor;
- estado de la licencia;
- fecha y hora del accidente.

La variable objetivo es **`Injury Severity`**.

## Flujo de análisis

```text
dataset
   ↓
exploración y selección de variables
   ↓
tratamiento de valores faltantes
   ↓
codificación de variables categóricas
   ↓
análisis del desbalance de clases
   ↓
entrenamiento de modelos
   ↓
accuracy + precision + recall + F1
   ↓
matrices de confusión y comparación
```

### Preprocesamiento

El notebook de modelado:

- elimina columnas consideradas irrelevantes para el análisis;
- imputa valores faltantes utilizando la moda;
- codifica variables categóricas mediante `LabelEncoder`;
- analiza la distribución de `Injury Severity`.

La clase **`NO APPARENT INJURY`** es la predominante, generando un desequilibrio significativo en la variable objetivo.

## Modelos evaluados

Se entrenaron y compararon:

- XGBoost
- Extra Trees Classifier
- Decision Tree
- Random Forest
- Support Vector Machine (SVM)
- LightGBM
- CatBoost
- HistGradientBoostingClassifier

## Métricas

La evaluación incluye:

- matriz de confusión;
- accuracy;
- precision ponderada;
- recall ponderado;
- F1-score ponderado;
- classification report.

## Resultados

Todos los modelos evaluados alcanzaron un **accuracy superior al 80%**.

Sin embargo, ese número por sí solo resultó insuficiente para describir la calidad de las predicciones. Las clases minoritarias —especialmente **`FATAL INJURY`** y **`SUSPECTED SERIOUS INJURY`**— presentaron métricas de precision, recall y F1 considerablemente más bajas.

La conclusión principal del ejercicio es que el **desbalance de clases condiciona fuertemente la capacidad de detectar correctamente los casos menos frecuentes**, que son precisamente algunos de los más importantes en este problema.

## Esquema del dataset

<details>
<summary>Ver columnas utilizadas/descriptas en el dataset</summary>

| Columna | Descripción | Tipo |
| --- | --- | --- |
| Report Number | Número único de reporte del accidente | Categórico |
| Local Case Number | Número de caso local | Categórico |
| Agency Name | Agencia que reporta el accidente | Categórico |
| ACRS Report Type | Tipo de reporte ACRS | Categórico |
| Crash Date/Time | Fecha y hora del accidente | Fecha/Hora |
| Route Type | Tipo de vía | Categórico |
| Road Name | Nombre de la vía | Categórico |
| Cross-Street Type | Tipo de vía que cruza | Categórico |
| Cross-Street Name | Nombre de la vía que cruza | Categórico |
| Off-Road Description | Descripción de ubicación fuera de vía | Categórico |
| Municipality | Municipio | Categórico |
| Related Non-Motorist | Información sobre no-motoristas involucrados | Categórico |
| Collision Type | Tipo de colisión | Categórico |
| Weather | Condiciones climáticas | Categórico |
| Surface Condition | Estado de la superficie | Categórico |
| Light | Condiciones de iluminación | Categórico |
| Traffic Control | Tipo de control de tránsito | Categórico |
| Driver Substance Abuse | Sustancias detectadas en el conductor | Categórico |
| Non-Motorist Substance Abuse | Sustancias detectadas en no-motoristas | Categórico |
| Person ID | Identificador de persona | Categórico |
| Driver At Fault | Indicador de responsabilidad del conductor | Booleano |
| Injury Severity | Severidad de las lesiones | Categórico |
| Circumstance | Circunstancias del accidente | Categórico |
| Driver Distracted By | Distracción del conductor | Categórico |
| Drivers License State | Estado de emisión de la licencia | Categórico |
| Vehicle ID | Identificador del vehículo | Categórico |
| Vehicle Damage Extent | Extensión de daños del vehículo | Categórico |
| Vehicle First Impact Location | Ubicación del primer impacto | Categórico |
| Vehicle Second Impact Location | Ubicación del segundo impacto | Categórico |
| Vehicle Body Type | Tipo de carrocería | Categórico |
| Vehicle Movement | Movimiento del vehículo | Categórico |
| Vehicle Continuing Dir | Dirección de continuación | Categórico |
| Vehicle Going Dir | Dirección de circulación | Categórico |
| Speed Limit | Límite de velocidad | Numérico |
| Driverless Vehicle | Indicador de vehículo autónomo | Booleano |
| Parked Vehicle | Indicador de vehículo estacionado | Booleano |
| Vehicle Year | Año del vehículo | Numérico |
| Vehicle Make | Marca del vehículo | Categórico |
| Vehicle Model | Modelo del vehículo | Categórico |
| Equipment Problems | Problemas de equipamiento | Categórico |
| Latitude | Latitud | Numérico |
| Longitude | Longitud | Numérico |
| Location | Ubicación geográfica | Geográfica |

</details>

## Alcance

Este repositorio documenta un ejercicio de Data Science centrado en análisis exploratorio y comparación de modelos de clasificación. Los resultados muestran por qué una métrica agregada como accuracy debe interpretarse con cuidado cuando la variable objetivo está fuertemente desbalanceada.
