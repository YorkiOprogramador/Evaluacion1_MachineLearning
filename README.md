# Evaluacion1_MachineLearning
Repositorio para el desarrollo de la evaluación 1 de Machine Learning grupo 4 

## 1. Descripción del problema de negocio y objetivos del proyecto

**Problema de Negocio:**
En la competitiva industria musical actual, discográficas, productores y artistas independientes se enfrentan al desafío de comprender qué factores técnicos y acústicos determinan el éxito comercial de una pista en plataformas de streaming. Las decisiones basadas en intuición ya no son suficientes. Se requiere un enfoque analítico riguroso para identificar las características musicales que impulsan la "popularidad" de una canción, mitigando así el riesgo asociado a la inversión en producción y marketing[cite: 1, 2].

**Objetivos del Proyecto:**
* Ejecutar un Análisis Exploratorio de Datos (EDA) exhaustivo sobre el dataset de pistas musicales para descubrir patrones ocultos y relaciones acústicas clave[cite: 1].
* Auditar y depurar la matriz de datos, solucionando inconsistencias, valores nulos y duplicados mediante criterios estadísticos y lógicos[cite: 1, 2].
* Estructurar un conjunto de datos limpio, validado y éticamente equilibrado, dejándolo en condiciones óptimas para el entrenamiento futuro de un algoritmo de Machine Learning predictivo[cite: 1, 2].

## 2. Definición de KPIs para resolver el problema

Para medir la calidad de la etapa de preparación de datos y garantizar un modelamiento confiable, se han definido los siguientes Indicadores Clave de Desempeño (KPIs) de calidad de datos[cite: 1, 2]:
* **Tasa de Completitud de Datos:** Reducir a menos del 5% la cantidad de valores nulos (NaN) en variables acústicas críticas mediante técnicas de imputación (media, mediana, moda) o eliminación justificada, preservando la validez algebraica de los algoritmos[cite: 2].
* **Tasa de Duplicidad:** Lograr un 0% de pistas musicales duplicadas en el set final para evitar que el modelo de Machine Learning sufra de sobreajuste (*overfitting*)[cite: 2].
* **Tratamiento de Anomalías (Outliers):** Auditar el 100% de los valores extremos detectados en métricas (como la duración de la canción o los decibeles), diferenciando correctamente entre errores de sistema y realidades acústicas atípicas pero legítimas[cite: 2, 6].
* **Cumplimiento Ético (Fairness):** Validar que la purga de registros no elimine desproporcionadamente géneros musicales minoritarios o artistas subrepresentados, evitando así la introducción de sesgos o exclusión algorítmica[cite: 1, 2].

## 3. Descripción de las fuentes de datos

* **Archivo Principal:** `Spotify_Tracks_Dataset.csv`[cite: 1].
* **Tipo de Datos:** Datos estructurados[cite: 6].
* **Características del Dataset:** El conjunto se compone de una matriz tabular con filas correspondientes a pistas musicales y columnas que representan sus metadatos (como nombre y artista) e indicadores acústicos extraídos de la API de Spotify (ej. *danceability*, *energy*, *acousticness* y la variable objetivo: *popularity*)[cite: 1].
* **Herramientas de Colaboración:** El dataset original y depurado se resguarda dentro del directorio `data/` del repositorio[cite: 1]. El equipo gestiona las versiones, revisiones (*code reviews*) y documentación de forma colaborativa mediante GitHub y Markdown para asegurar total transparencia y reproducibilidad técnica[cite: 2, 9].

## 4. Preparación y análisis exploratorio de datos (EDA)

El EDA actúa como una auditoría clínica de obligatoria ejecución para comprender el comportamiento intrínseco de las pistas musicales antes de aplicar cualquier aproximación algorítmica[cite: 1, 4]:

**A. Preparación (Data Cleaning):**
* Inicialización del entorno con librerías estadísticas en Python (Pandas, Numpy, Matplotlib, Seaborn)[cite: 2, 6].
* Tratamiento de valores faltantes (NaN) y depuración exhaustiva de registros duplicados que pudieran contaminar el entrenamiento del modelo[cite: 2].

**B. Exploración Visual (EDA):**
* **Análisis Univariado:** Examen detallado de distribuciones, tipos de variables y el rango de la popularidad mediante histogramas y gráficos de caja (*boxplots*) para identificar valores atípicos[cite: 2, 4, 6].
* **Análisis Bivariado y Correlaciones:** Trazado de mapas de calor (*heatmaps*) para revelar cómo interactúan las variables simultáneamente, exponiendo, por ejemplo, qué atributos de audio correlacionan más positivamente con el índice de popularidad[cite: 2, 4].
* **Auditoría Ética:** Evaluación exhaustiva de sesgos de confirmación o muestreo. Se reconoce que la recolección de datos no es neutral y se aplican criterios para no amplificar asimetrías históricas de la plataforma[cite: 2, 9].

## 5. Metodología utilizada (CRISP-DM)

Este proyecto se desarrolla alineado al estándar de la industria **CRISP-DM** (Cross-Industry Standard Process for Data Mining), cubriendo en esta etapa las tres primeras fases críticas[cite: 1]:

1. **Business Understanding (Comprensión del Negocio):** Se definió el problema crítico de la industria de la música para optimizar recursos analizando el éxito en Spotify, traduciéndolo en objetivos claros y KPIs analíticos medibles[cite: 1].
2. **Data Understanding (Comprensión de los Datos):** Se procedió a cargar la matriz `Spotify_Tracks_Dataset.csv` y ejecutar el EDA para explorar las relaciones estructurales e identificar deficiencias[cite: 1, 8].
3. **Data Preparation (Preparación de los Datos):** Se aplicaron acciones estadísticas y éticas sobre los datos anómalos, duplicados y ausentes. El resultado es un dataset íntegro, balanceado y listo para ser ingresado exitosamente en la futura etapa de modelamiento (*Modeling*)[cite: 1, 5].
