# Deep-Learning
Ruta elegida y Dataset
El proyecto utiliza un dataset de señales de tránsito organizado en carpetas para entrenamiento, validación y prueba. Las imágenes y sus etiquetas están preparadas bajo el formato requerido por YOLOv8. El archivo de configuración data.yaml especifica las rutas y clases del dataset. Este dataset es fundamental para aplicaciones en vehículos autónomos y sistemas avanzados de asistencia al conductor, buscando mejorar la detección en tiempo real de señales de tránsito.

# Cómo obtener el dataset
El dataset para detección y clasificación de señales de tránsito puede obtenerse desde Kaggle, que es una plataforma reconocida para datasets de machine learning. Para descargarlo, es necesario crear una cuenta en Kaggle, iniciar sesión y acceder a la página del dataset específico (por ejemplo, un dataset de señales de tránsito). Luego, se debe descargar el archivo comprimido con las imágenes y etiquetas.
```
!pip install kaggle
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
!kaggle datasets download usuario/nombre-dataset
!unzip nombre-dataset.zip -d /content/car/
```
Estas configuraciones internas garantizan que el dataset esté disponible en el entorno de trabajo y estructurado adecuadamente para el entrenamiento con YOLOv8. Así se asegura un flujo de trabajo reproducible y eficiente para el proyecto.
Para usarlo en Google Colab, se recomienda configurar la API de Kaggle con el archivo kaggle.json que se genera en la cuenta Kaggle (desde la sección API). Este archivo debe subirse al entorno Colab y ubicarse en la carpeta adecuada para permitir la descarga automática del dataset mediante comandos como:
# Cómo ejecutar
Abrir el notebook en Google Colab o Jupyter Notebook.

En Google Colab, seleccionar en el menú "Entorno de ejecución" la opción "Cambiar tipo de entorno de ejecución" y elegir GPU como acelerador de hardware para optimizar el entrenamiento.

Ejecutar las celdas secuencialmente.

Verificar que las rutas y configuraciones en el notebook y en el archivo .yaml apunten correctamente a las carpetas del dataset.

# Cómo entrenar y evaluar
Para entrenar, se define una función que recibe el nombre del modelo YOLOv8 (yolov8n.pt, yolov8s.pt, yolov8m.pt) y la cantidad de epochs. Se pasa la ruta del archivo de configuración .yaml con los datos.

Se entrena cada modelo usando la función y se almacenan los resultados.

La evaluación se realiza usando el método .val() de cada modelo, recuperando métricas como Precisión, Recall, F1 y Accuracy.

El código permite evaluar cada modelo sobre los conjuntos de validación y prueba configurados en el yaml.

# Cómo generar la tabla y el gráfico de métricas
Se extraen las métricas obtenidas para cada modelo y se consolidan en un DataFrame de pandas.

Con matplotlib se grafica cada métrica comparando los tres modelos, facilitando la visualización de su desempeño relativo.

La tabla impresa y el gráfico permiten identificar el modelo con mejor balance en métricas clave para la tarea de detección de señales.

Este README resume el uso básico para desplegar el proyecto, desde la carga del dataset hasta la comparación gráfica del desempeño de modelos YOLOv8 variantes, facilitando su reproducción y análisis.
