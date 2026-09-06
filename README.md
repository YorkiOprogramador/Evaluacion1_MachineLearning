# Informe del Proyecto de Machine Learning

## 1. Problema

El objetivo del proyecto es desarrollar un modelo de Machine Learning capaz de predecir la variable **`popularity`** de canciones de Spotify a partir de sus características musicales y contextuales.

El análisis exploratorio muestra que la popularidad no presenta una relación lineal simple con las variables disponibles, por lo que se plantea estudiar posibles relaciones no lineales e interacciones mediante modelos de aprendizaje automático.

## 2. Objetivo

Construir un modelo predictivo que permita estimar la popularidad de una canción utilizando sus características disponibles en el dataset.

Como parte del proceso, se busca:

* Comprender y explorar los datos.
* Preparar las variables para Machine Learning.
* Analizar correlaciones, redundancias y valores extremos.
* Comparar escenarios con y sin valores atípicos.
* Entrenar y evaluar modelos predictivos.

## 3. Flujo de trabajo: CRISP-DM

El proyecto sigue la metodología **CRISP-DM**, estructurando el trabajo en las siguientes etapas:

1. **Business Understanding:** definición del problema y objetivo de predicción.
2. **Data Understanding:** exploración del dataset, variables, distribuciones, correlaciones y valores extremos.
3. **Data Preparation:** limpieza, selección de variables, separación de entrenamiento y prueba, codificación y tratamiento de outliers.
4. **Modeling:** entrenamiento de modelos de Machine Learning.
5. **Evaluation:** evaluación y comparación del desempeño mediante métricas.
6. **Deployment:** etapa considerada como futura, fuera del alcance actual.

Actualmente se han completado las tres primeras etapas.

## 4. Fuente y características de los datos

El dataset contiene inicialmente **114.000 registros y 21 variables** relacionadas con canciones de Spotify.

Después de eliminar registros duplicados se obtuvieron **89.741 canciones únicas**, utilizando `track_id` como identificador.

La variable objetivo es:

* `popularity`: nivel de popularidad de la canción, con valores entre 0 y 100.

## 5. Preparación de los datos

Se separó la variable objetivo (`popularity`) de las variables predictoras.

Se eliminaron identificadores y variables descriptivas de alta cardinalidad como `track_id`, `artists`, `album_name` y `track_name`, además de `Unnamed: 0`.

También se eliminó `energy` debido a su alta relación con otras variables, principalmente `loudness` y `acousticness`, con el objetivo de reducir redundancia y simplificar el conjunto de predictores.

Las variables utilizadas se dividieron en:

* **Numéricas:** `duration_ms`, `danceability`, `loudness`, `speechiness`, `acousticness`, `instrumentalness`, `liveness`, `valence` y `tempo`.
* **Categóricas:** `explicit`, `key`, `mode`, `time_signature` y `track_genre`.

## 6. Análisis exploratorio

Se analizaron distribuciones, correlaciones, géneros musicales y valores extremos.

Las correlaciones de Spearman con `popularity` fueron débiles, con una asociación máxima cercana a **0,13**. Esto indica que ninguna variable individual explica por sí sola la popularidad y justifica el uso de un enfoque multivariable.

También se identificó una alta relación entre algunas variables predictoras, destacando `energy` con `loudness` y `acousticness`.

## 7. Tratamiento de valores extremos

Se definieron dos escenarios para comparar posteriormente el desempeño de los modelos:

### Escenario 1: Con outliers

Se conservan los valores extremos, considerándolos observaciones potencialmente válidas del comportamiento real de las canciones.

Las variables categóricas se transforman mediante **OneHotEncoder**, mientras que las variables numéricas mantienen sus valores originales.

### Escenario 2: Sin outliers

Se eliminan observaciones extremas mediante el método **IQR (1,5 × IQR)** aplicado sobre las variables numéricas.

Los límites se calculan utilizando únicamente el conjunto de entrenamiento para evitar fuga de información. Posteriormente, se aplican los mismos límites al conjunto de prueba.

En este escenario, las variables numéricas se estandarizan mediante **StandardScaler** y las categóricas mediante **OneHotEncoder**.

## 8. Prevención de Data Leakage

Para evitar fuga de información, primero se dividen los datos en **entrenamiento y prueba**.

Las transformaciones y parámetros calculados a partir de los datos, como los límites del IQR y el escalamiento, se ajustan únicamente utilizando el conjunto de entrenamiento.

De esta forma, el conjunto de prueba permanece independiente y permite realizar una evaluación más confiable.

## 9. Indicadores (KPIs)

Se consideran principalmente:

* **Fuerza de asociación:** correlación de Spearman entre los predictores y `popularity`.
* **Calidad de los datos:** reducción de 114.000 registros a 89.741 registros únicos.
* **Preparación para Machine Learning:** correcta separación de variables, codificación, escalamiento cuando corresponde y prevención de Data Leakage.
* **Desempeño del modelo:** posteriormente se utilizarán **MAE, RMSE y R²**.

## 10. Próxima etapa

El siguiente paso corresponde a la fase de **Modeling**, comenzando con un **DecisionTreeRegressor**.

Se entrenará el mismo modelo en ambos escenarios —con y sin outliers— para comparar sus resultados bajo condiciones equivalentes.

Posteriormente se realizará la **Evaluación**, utilizando MAE, RMSE y R², y se podrán ajustar hiperparámetros como `max_depth`, `min_samples_split` y `min_samples_leaf`.

## 11. Conclusión

El proyecto ha completado las etapas de **comprensión del negocio, comprensión de los datos y preparación de los datos** de CRISP-DM.

El dataset fue depurado, explorado y preparado en dos escenarios diferenciados respecto a los valores extremos. La baja asociación individual entre las variables y `popularity` respalda la utilización de modelos capaces de capturar relaciones no lineales e interacciones.

La siguiente etapa será entrenar y evaluar los modelos para determinar cuál escenario permite obtener mejores resultados predictivos.

----------------------------------------------------------------

FLUJO DE TRABAJO DEL PROYECTO
│
├── 1. Business Understanding
│   └── Definir el problema y objetivo:
│       Predecir la popularidad de canciones de Spotify.
│
├── 2. Data Understanding
│   ├── Cargar y explorar los datos
│   ├── Analizar variables y distribuciones
│   ├── Identificar duplicados y valores faltantes
│   ├── Analizar correlaciones
│   └── Detectar valores extremos
│
├── 3. Data Preparation
│   ├── Eliminar duplicados
│   ├── Separar variable objetivo y predictores
│   ├── Eliminar variables irrelevantes o redundantes
│   ├── Dividir Train / Test
│   │
│   ├── Escenario A: CON OUTLIERS
│   │   ├── Conservar valores extremos
│   │   └── Aplicar OneHotEncoder a categóricas
│   │
│   └── Escenario B: SIN OUTLIERS
│       ├── Detectar y eliminar outliers mediante IQR
│       ├── Aplicar StandardScaler a numéricas
│       └── Aplicar OneHotEncoder a categóricas
│
├── 4. Modeling
│   └── Entrenar DecisionTreeRegressor
│       en ambos escenarios.
│
├── 5. Evaluation
│   ├── Comparar resultados
│   ├── MAE
│   ├── RMSE
│   └── R²
│
└── 6. Deployment
    └── Etapa futura, fuera del alcance actual.
