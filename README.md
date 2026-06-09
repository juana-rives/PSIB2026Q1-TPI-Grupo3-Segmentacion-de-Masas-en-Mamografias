# PSIB2026Q1-TPI-Grupo3-Rives-Yoo-Haag

## Segmentación y extracción de características de masas en mamografías

Repositorio correspondiente al Trabajo Práctico de Imágenes de la materia **Procesamiento de Señales e Imágenes Biomédicas (16.63)**.

## Integrantes

* Haag, Valentina
* Rives, Juana
* Yoo, Jana Gabriela

## Descripción del proyecto

El objetivo del trabajo fue desarrollar y evaluar un pipeline de procesamiento digital de imágenes para segmentar masas mamográficas previamente localizadas en imágenes de la base **CBIS-DDSM**.

El trabajo se centró en la segmentación de la lesión dentro de una ventana local y en la comparación de la máscara obtenida con la máscara de referencia provista por la base de datos. No se abordó la detección automática de masas sobre la mamografía completa ni la clasificación diagnóstica de benignidad o malignidad.

El pipeline implementado incluye:

* Lectura de imágenes DICOM.
* Asociación entre mamografía completa, ROI, máscara de referencia y metadatos del CSV.
* Construcción de una ventana local centrada en la lesión.
* Normalización local de intensidades.
* Preprocesamiento mediante transformación logarítmica y CLAHE adaptativo.
* Segmentación mediante MorphGAC.
* Segmentación mediante K-means.
* Segmentación híbrida combinando MorphGAC y K-means.
* Evaluación mediante métricas de Dice, Jaccard, precisión, sensibilidad y ratio de área.
* Extracción de características simples de forma, borde e intensidad.

## Contenido del repositorio

```text
.
├── README.md
├── requirements.txt
├── .gitignore
├── PSIB2026Q1_TPI_Grupo3_Rives_Yoo_Haag_limpio.ipynb
├── mass_case_description_train_set.csv
└── data/
    └── README.md
```

El notebook incluido en este repositorio corresponde a una versión limpia del código, sin outputs guardados, para facilitar su visualización en GitHub.

Se incluye el archivo `mass_case_description_train_set.csv`, utilizado para asociar los casos procesados con los metadatos disponibles de la base, como identificador del paciente, densidad mamaria, lateralidad, vista mamográfica, forma de la masa, márgenes y patología.

El notebook ejecutado, con las salidas y visualizaciones completas, se entrega por separado mediante enlace a Google Colab/Google Drive junto con el informe y la presentación.

## Base de datos

La base utilizada fue **CBIS-DDSM (Curated Breast Imaging Subset of DDSM)**. Por tamaño, las imágenes DICOM originales, las ROI y las máscaras de referencia no se incluyen en este repositorio.

Para ejecutar el notebook, se espera que los archivos estén disponibles localmente o en Google Drive con una estructura equivalente a la siguiente:

```text
TP-PSIB/
└── TPI/
    ├── IMG/
    │   ├── MG/
    │   ├── ROI/
    │   └── MASK/
    └── mass_case_description_train_set.csv
```

En el notebook, la ruta principal se define mediante la variable:

```python
BASE_DIR = Path("/content/drive/MyDrive/TP-PSIB/TPI")
```

Si la carpeta de trabajo se encuentra en otra ubicación, sólo debe modificarse esa ruta.

## Instalación de dependencias

El notebook fue desarrollado y ejecutado en **Google Colab**. Las principales librerías utilizadas fueron:

* NumPy
* Pandas
* Matplotlib
* pydicom
* SciPy
* scikit-image
* scikit-learn
* Pillow
* IPython

Para instalar las dependencias en un entorno local o en Colab, puede utilizarse:

```bash
pip install -r requirements.txt
```

## Ejecución

Para ejecutar el pipeline:

1. Abrir el notebook `PSIB2026Q1_TPI_Grupo3_Rives_Yoo_Haag_limpio.ipynb`.
2. Montar Google Drive si se trabaja en Colab.
3. Verificar que la variable `BASE_DIR` apunte a la carpeta donde se encuentran las imágenes y el CSV.
4. Ejecutar las celdas en orden.
5. Revisar las tablas, métricas y visualizaciones generadas por el notebook.

El código genera tablas intermedias, métricas de segmentación, comparaciones entre métodos y visualizaciones de control.

## Archivos no incluidos

No se incluyen en el repositorio:

* Imágenes DICOM originales.
* ROI provistas por la base.
* Máscaras de referencia.
* Carpeta completa de CBIS-DDSM.
* Outputs pesados del notebook.
* Resultados intermedios generados durante la ejecución.

Esta decisión se tomó para evitar subir archivos pesados al repositorio y para mantener el código en una versión limpia y reproducible.

## Alcance y limitaciones

El pipeline parte de masas previamente localizadas mediante la información espacial de la máscara de referencia y la ROI. Por lo tanto, no realiza detección automática de lesiones sobre la mamografía completa.

La caracterización cuantitativa de forma, borde e intensidad se utilizó como complemento de la evaluación de segmentación, no como herramienta diagnóstica.

Los parámetros utilizados fueron definidos de manera empírica e iterativa sobre el conjunto analizado, por lo que futuras mejoras podrían incluir una optimización sistemática de parámetros, evaluación sobre un conjunto independiente y una etapa previa de detección automática de regiones sospechosas.

## Entrega

Este repositorio contiene la versión limpia del código. El informe final, la presentación y el enlace al notebook ejecutado con salidas completas se entregan por mail según lo indicado por la cátedra.
