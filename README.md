# sprint7-final-project
Analisis de datos de dataset de ConnectaTel del año 2024, como estudio de bootcamps  de en TripleTen.
Proyecto de Análisis de Datos y Aprendizaje Automático
Este proyecto tiene como objetivo principal realizar un análisis exploratorio de datos (EDA) y construir un modelo predictivo para extraer insights valiosos y generar métricas clave a partir de los datos proporcionados.

🎯 Objetivo del Proyecto
Comprender la estructura y distribución de los datos de entrada.
Limpiar y preprocesar la información (tratamiento de valores nulos, atípicos y codificación de variables).
Desarrollar y evaluar modelos de Machine Learning/Análisis Estadístico para responder a las preguntas clave del problema.
Proporcionar un flujo de trabajo reproducible e interpretable.

📊 Datasets Utilizados
El análisis se alimenta de los siguientes conjuntos de datos (ubicados normalmente en la carpeta data/ o descargados dinámicamente en el notebook):
Dataset Principal (dataset_principal.csv): Contiene la información base para el análisis, incluyendo atributos demográficos, categóricos y numéricos.
Dataset Complementario (dataset_secundario.csv) (opcional): Datos adicionales integrados mediante operaciones de cruce (merge/join).
Nota: Revisa las celdas iniciales del notebook para verificar si los datasets se cargan localmente o desde un repositorio remoto / enlace directo de Google Drive.

🛠️ Etapas del Análisis
El proyecto está dividido en las siguientes fases metodológicas:
Carga y Exploración Inicial (EDA):
Inspección de tipos de datos, dimensiones y primeras filas.
Resumen estadístico descriptivo (mean, std, cuartiles).
Identificación de valores faltantes y duplicados.
Preprocesamiento y Limpieza de Datos:
Imputación o eliminación de datos nulos.
Transformación de variables categóricas (One-Hot Encoding / Label Encoding).
Escalado/Normalización de variables numéricas (StandardScaler / MinMaxScaler).
Análisis Exploratorio Visual:
Gráficos de distribución (histogramas, boxplots).
Matriz de correlación para identificar relaciones clave entre variables.
Modelado y Entrenamiento:
División del conjunto de datos en Entrenamiento (Train) y Prueba (Test).
Selección y entrenamiento de algoritmos de clasificación/regresión.
Evaluación de Resultados:
Cálculo de métricas de rendimiento (Accuracy, Precision, Recall, $F1\text{-}score$, MSE, R2, etc.).
Visualización de resultados (Matriz de confusión, Curva ROC, Importancia de Variables).

🚀 Cómo Ejecutar el Notebook
La forma más rápida y recomendada de ejecutar este proyecto es a través de Google Colab.
Opción 1: Abrir directamente en Google Colab
Haz clic en el siguiente enlace o abre Google Colab.
Ve a la pestaña GitHub e ingresa la URL de este repositorio.
Selecciona el archivo .ipynb correspondiente para abrirlo.
Opción 2: Ejecución Local (Jupyter Notebook / VS Code)
Si prefieres ejecutarlo localmente en tu computadora:
Clonar el repositorio:
git clone https://github.com/tu-usuario/tu-repositorio.git
cd tu-repositorio
Crear y activar un entorno virtual:
python -m venv venv
# En Windows:
venv\Scripts\activate
# En macOS/Linux:
source venv/bin/activate
Instalar dependencias:
pip install -r requirements.txt
Iniciar Jupyter:
jupyter notebook

📋 Guía de Reproducción Rápida
Para reproducir la totalidad de los análisis y resultados obtenidos:
Asegurar la disponibilidad de los datos:
Si utilizas Google Colab, ejecuta las primeras celdas para descargar automáticamente los datos o cargar tu Drive (google.colab.drive.mount('/content/drive')).
Si ejecutas en local, asegura que los archivos .csv se encuentren en la carpeta data/ dentro del directorio raíz.
Fijar la semilla aleatoria (Random Seed):
Para garantizar que las particiones de datos y el entrenamiento de los modelos sean identicos, verifica que el parámetro random_state esté fijado (ej. random_state=42).
Ejecutar todas las celdas:
En Google Colab / Jupyter: Haz clic en el menú superior Entorno de ejecución (Runtime)  Ejecutar todas (Run all).

📁 Estructura del Repositorio
├── data/                  # Archivos de datos (CSV, JSON, etc.)
├── notebooks/             # Notebooks de Jupyter / Google Colab (.ipynb)
├── src/                   # Scripts de Python auxiliares (opcional)
├── README.md              # Descripción del proyecto
└── requirements.txt       # Librerías y versiones requeridas

🤝 Contribuciones y Contacto
Si deseas aportar o consultar sobre este proyecto, no dudes en abrir un Issue o enviar un Pull Request.
