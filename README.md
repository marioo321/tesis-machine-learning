# Tesis Machine Learning – Predicción de Funciones Ejecutivas y Competencias Matemáticas Tempranas

Repositorio correspondiente a mi tesis de pregrado, enfocada en el desarrollo de un modelo de **Machine Learning** para predecir el rendimiento en **competencias matemáticas tempranas** a partir de **funciones ejecutivas** y variables sociodemográficas en niños de 5 a 9 años.

## Objetivo del proyecto

El objetivo principal de esta investigación fue evaluar si es posible predecir el desempeño matemático temprano de niños utilizando medidas cognitivas asociadas a funciones ejecutivas, tales como memoria de trabajo, flexibilidad cognitiva, inhibición y otras variables contextuales. Además, se buscó comparar distintos modelos supervisados, validar estadísticamente sus diferencias y construir un modelo parsimonioso con un subconjunto reducido de variables.

## Problema abordado

Las competencias matemáticas tempranas son un predictor importante del desempeño académico futuro. A su vez, la literatura muestra que ciertas funciones ejecutivas tienen una relación estrecha con el desarrollo de estas habilidades. En este contexto, la tesis busca aportar un enfoque cuantitativo y predictivo que permita identificar tempranamente factores relevantes para el aprendizaje matemático.

## Dataset

El estudio se desarrolló sobre una base de **528 registros** de niños, con **22 variables predictoras** relacionadas con:

* Memoria de trabajo verbal y visoespacial
* Flexibilidad cognitiva
* Velocidad de procesamiento
* Dependencia en tareas ejecutivas
* Edad y variables sociodemográficas/contextuales

Las variables objetivo corresponden a tres indicadores de competencias matemáticas tempranas:

* **CMLR**
* **CMN**
* **CMG**

## Metodología

El proyecto fue abordado como un problema de **regresión multisalida (multi-output regression)**, entrenando modelos capaces de predecir simultáneamente los tres indicadores matemáticos.

### 1. Preparación de datos

* Revisión y organización de la base de datos.
* Selección de variables predictoras y targets.
* Preparación del dataset para entrenamiento, validación y prueba.
* Repetición del proceso en múltiples particiones aleatorias para evaluar estabilidad.

### 2. Modelos implementados

Se entrenaron y compararon cinco algoritmos supervisados basados en árboles de decisión y ensambles:

* **Decision Tree**
* **Random Forest**
* **XGBoost**
* **CatBoost**
* **LightGBM**

### 3. Ajuste de hiperparámetros

Cada modelo fue ajustado mediante **HalvingGridSearchCV**, utilizando búsqueda de hiperparámetros con validación cruzada, priorizando eficiencia computacional y capacidad de generalización.

### 4. Protocolo de validación

* Se realizaron **50 particiones aleatorias** del conjunto de datos.
* En cada ejecución se entrenaron y evaluaron los modelos.
* El desempeño se midió utilizando **Mean Squared Error (MSE)**.

### 5. Comparación estadística de modelos

Para evaluar si las diferencias entre algoritmos eran estadísticamente significativas, se aplicaron pruebas no paramétricas:

* **Friedman**
* **Nemenyi**
* **Wilcoxon**
* **Corrección de Bonferroni**

### 6. Interpretabilidad

Una vez seleccionado el mejor modelo, se utilizó **Permutation Importance** para estimar la relevancia de cada variable en las predicciones y analizar qué funciones ejecutivas explicaban en mayor medida el desempeño matemático.

### 7. Modelo parsimonioso

A partir del ranking de importancia de variables, se construyó un modelo reducido utilizando únicamente las **6 variables más influyentes**, con el fin de evaluar si era posible simplificar el modelo sin perder capacidad predictiva de forma significativa.

## Resultados principales

* **CatBoost** fue el modelo con mejor desempeño general, obteniendo el menor **MSE promedio** en los tres targets.
* Las variables con mayor relevancia predictiva fueron principalmente:

  * **Memoria de Trabajo Verbal**
  * **Edad**
  * **Flexibilidad Cognitiva**
  * **Dependencia en tareas ejecutivas**
* El modelo parsimonioso logró mantener un rendimiento competitivo con una pérdida de precisión acotada, lo que sugiere la posibilidad de diseñar herramientas más simples e interpretables para detección temprana.

## Tecnologías y librerías utilizadas

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Scikit-learn**
* **XGBoost**
* **CatBoost**
* **LightGBM**
* **SciPy**
* **Jupyter Notebook**

## Estructura del repositorio

* `Memoria MAO.pdf` → documento de tesis
* `01_exploracion_y_analisis.ipynb` → notebook con análisis / apoyo de presentación
* `02_modelos_y_evaluacion.ipynb` → notebook con pruebas, modelamiento y evaluación

## Aprendizajes del proyecto

Este trabajo me permitió profundizar en:

* desarrollo y comparación de modelos de Machine Learning,
* validación experimental mediante múltiples particiones,
* ajuste de hiperparámetros,
* análisis de importancia de variables,
* uso de pruebas estadísticas no paramétricas para comparar modelos,
* y construcción de soluciones más interpretables a partir de evidencia cuantitativa.

## Autor

**Mario A. Olivares del Río**
Ingeniero Civil Informático – Universidad Técnica Federico Santa María
