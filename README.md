# Clasificación de Manzanas por Color (Color Based Classification)

## Descripción
Proyecto para clasificar imágenes de manzanas rojas y verdes usando el color promedio (BGR) y el algoritmo K-Nearest Neighbors (KNN). Utiliza procesamiento de imágenes (OpenCV).
El objetivo inicial era proponer una forma diferente de resolver este conflicto, el dataset es muy pequeño, pero se observaba que la manera de clasificar colores mediante diferentes métodos.

## Flujo del Proyecto
1. Carga de imágenes (entrenamiento y prueba).
2. Preprocesamiento: limpieza de fondos blancos y redimensionamiento.
3. Extracción de características: promedio de color BGR.
4. Entrenamiento del modelo KNN (k=3).
5. Evaluación con métrica Accuracy.

## Tecnologías
- Python
- Librerías: OpenCV, NumPy, Matplotlib, scikit-learn

## Instalación
```bash
pip install opencv-python numpy matplotlib scikit-learn
```

## Ejecución
Ejecutar el notebook en Google Colab o localmente:
```bash
jupyter notebook TP1_manz_vyr.ipynb
```

## Autores
- Franco A.
- Ailén Iglesias Barrera

## Licencias y Observaciones
Licencia de uso académico e investigación.

## Análisis y resolución

    Extracción de características: cuál fue la aproximación, pasos seguidos (diagrama en bloque) y parámetros elegidos.

La elección final presentada para este trabajo fue pensar la extracción de características que se basó en procesar imágenes (luego de normalizarlas) para poder obtener un vector a partir del valor promedio de color BGR (Azul, Verde y Rojo) de cada imagen. Esto lo trabajamos en grupo en dos modelos, al final decantamos por el presentado, pero también hicimos una prueba utilizando el perfil de color HSV, el concepto que ambos coincidimos es pensar la extracción de color y generar un promedio de los mismos (en el caso que no dejamos, se realizaba por bandas de lower green y upper green también con las dos franjas de rojo y generando un promedio de verde y otro de rojo, pasando esa información al modelo y de ese modo correr una regresión logística). En ambos casos la búsqueda fue similar luego de conversar nos pareció más directo esta solución presentada.

El diagrama en bloques del proceso sería: Extracción de características y clasificación: Carga de imágenes --> Lectura de imágenes --> Limpieza de fondos blancos a negros --> Redimensionamiento a 100 x 100 --> Promedio de color BGR --> Vector de características (3 valores, una dimensión para cada color) --> División de datos en conjuntos de prueba y entrenamiento --> Entrenamiento del modelo KNN --> Predición con el modelo KNN --> Evaluación (Accuracy).

Parámetros elegidos:

    redimensionamiento: se redimensionaron las imágenes en 100x100px
    promedio de color BGR: para cada valor se calculó el promedio de cada uno de los 3 canales, azul verde y rojo.
    numero de vecinos k, se eligió el k = 3 teniendo en cuenta los promedios elegidos, uno para cada canal.

    Clasificación: mencionar la técnica utilizada -no explicar teóricamente-.

Se eligió el modelo de clasificación KNN K- Nearest Neighbors. Para agrupar las imágenes de pruebas a alguna de las 3 grupos asignados y de esta forma determinar si la nueva imagen pertenece a alguno de los grupos (manzanas verdes o rojas).

    Evaluación: explicar cómo se llevó a cabo el análisis del rendimiento del modelo (proceso elegido y resultados).

Para la evaluación se utilizó el conjunto de predicción con el modelo entrenado sobre las características de las imágenes en el conjutno de prueba (test_images). Se calcularon las métricas: Accuracy: se calcula la exactitud general del modelo. Resultados: Precisión: 1.0 (donde indica que el modelo clasfició correctamente todas las imágenes -es un número tan exacto debido a que el conjunto de datos es muy pequeño).
