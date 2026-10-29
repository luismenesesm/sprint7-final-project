# sprint7-final-project
Analisis de datos de dataset de ConnectaTel del año 2024, como estudio de bootcamps  de en TripleTen.
Proyecto de Análisis de Datos y Aprendizaje: ConnectaTel: segmentación de clientes y patrones de uso.
Análisis exploratorio de los planes, usuarios y uso del servicio de ConnectaTel (operador de telecomunicaciones en Latinoamérica). El proyecto limpia los datos, segmenta a los clientes por edad y nivel de uso y traduce los hallazgos en recomendaciones para el negocio.
Objetivo
Limpiar y validar tres datasets: detectar valores faltantes, sentinels (valores centinela), fechas imposibles y outliers.
Resumir el comportamiento de cada usuario (mensajes, llamadas y minutos de llamada).
Segmentar a los clientes por edad y por nivel de uso, y compararlos por plan.
Identificar los segmentos más valiosos, los patrones de uso extremo y oportunidades para mejorar o crear planes.
Datasets
Archivo
Filas
Contenido
plans.csv
2
Planes disponibles (Basico y Premium): mensajes, GB y minutos incluidos, precio mensual y costos por excedente.
users_latam.csv
4000
Usuarios: user_id, nombre, age, city, reg_date, plan y churn_date (fecha de baja; nula si el usuario sigue activo).
usage.csv
40000
Registros de uso: id, user_id, type (call o text), date, duration (minutos, solo llamadas) y length (caracteres, solo mensajes). Cubre de enero a junio de 2024.


Los archivos CSV deben colocarse en la carpeta data/ del repositorio (ver Cómo ejecutar).
Estructura del repositorio
├── README.md

├── requirements.txt

├── notebooks/

│   └── analisis_connectatel.ipynb

└── data/

    ├── plans.csv

    ├── users_latam.csv

    └── usage.csv
Etapas del análisis
Carga de datos: importación de librerías y lectura de los tres CSV.
Estructura: dimensiones, tipos de datos y resumen con .info().
Valores faltantes: conteo y proporción de nulos por columna.
Sentinels: exploración numérica y categórica para detectar valores que no deberían estar (-999 en age, ? en city).
Fechas: conversión a tipo fecha y detección de años imposibles (registros en 2026).
Corrección: reemplazo de sentinels y fechas imposibles.
Nulos en duration y length: verificación de que dependen de type (nulos estructurales) y decisión de mantenerlos.
Resumen por usuario: mensajes, llamadas y minutos por user_id, combinados con users (user_profile).
Resumen estadístico por usuario y distribución de planes.
Verificaciones adicionales: registros inconsistentes y coherencia temporal.
Distribuciones: histogramas por plan de edad, mensajes, llamadas y minutos.
Outliers: boxplots y límites con el método IQR.
Segmentación por uso: Bajo uso, Uso medio y Alto uso.
Segmentación por edad: Joven, Adulto y Adulto Mayor.
Visualización de los segmentos.
Análisis de apoyo: abandono, ingresos por plan y uso frente a lo incluido en cada plan.
Análisis ejecutivo para stakeholders.
Hallazgos principales
Calidad de los datos: 55 edades con el sentinel -999 (1.4%), 565 usuarios sin ciudad conocida (14.1%), 40 fechas de registro en 2026 (1.0%) y una columna churn_date guardada en notación científica que requería conversión específica.
Segmentos: 19.0% jóvenes, 50.5% adultos y 30.6% adultos mayores; 19.5% de bajo uso, 73.6% de uso medio y 6.95% de alto uso.
Ni la edad ni el plan explican el uso: los clientes Premium (que pagan 2.08 veces el precio de Básico) consumen prácticamente lo mismo que los Básico.
Valor del negocio: Premium es el 35% de la base pero aporta el 53% del ingreso mensual base, y concentra el 54% del ingreso asociado a las bajas.
Abandono: 11.65% global; el segmento de alto uso tiene la tasa más alta (14.0%), aunque el 72.5% de las bajas ocurre en el uso medio.
Outliers: los de mensajes y llamadas son plausibles; en minutos, unas 30 llamadas de exactamente 120 minutos parecen un tope del sistema y deben revisarse.

El detalle y las recomendaciones están en la última sección del notebook.
Cómo ejecutar
Opción A: Google Colab
Abre el notebook directamente desde GitHub en Colab: https://colab.research.google.com/github/TU_USUARIO/TU_REPOSITORIO/blob/main/notebooks/analisis_connectatel.ipynb
Si los CSV no están en el repositorio, súbelos desde el panel de archivos de Colab (carpeta /content/).
Ejecuta Entorno de ejecución → Ejecutar todas.
Opción B: local
git clone https://github.com/TU_USUARIO/TU_REPOSITORIO.git

cd TU_REPOSITORIO

pip install -r requirements.txt

jupyter notebook notebooks/analisis_connectatel.ipynb

El notebook busca los CSV automáticamente en /datasets/, data/, ../data/ y /content/, por lo que funciona sin cambiar rutas en cualquiera de estos entornos.
Guía de reproducción
Coloca plans.csv, users_latam.csv y usage.csv en data/.
Instala las dependencias (requirements.txt).
Ejecuta el notebook de arriba hacia abajo, sin saltar celdas: las secciones posteriores dependen de las limpiezas anteriores (por ejemplo, user_profile se construye con las versiones limpias de users y usage).
Si vuelves a ejecutar una celda de limpieza (como la de age), reinicia el kernel y ejecuta todo desde el principio para evitar aplicar la limpieza dos veces.
Decisiones y limitaciones
Los 55 valores -999 de age se reemplazaron por la mediana (48 años), lo que crea un pico artificial en esa edad.
churn_date se convierte desde nanosegundos Unix (unit='ns'); por la pérdida de precisión, solo es confiable a nivel de día.
Los nulos de duration y length no se imputan: son estructurales (una llamada no tiene longitud y un mensaje no tiene duración).
El registro de uso solo cubre enero a junio de 2024, mientras que las bajas ocurren entre junio y diciembre; la relación entre uso y abandono es indicativa.
El 25.2% de los registros de uso tiene fecha anterior al registro del usuario; se documenta pero no se corrige.
Las diferencias de abandono entre segmentos son pequeñas y no se probaron estadísticamente.
Tecnologías
Python 3, pandas, NumPy, seaborn y matplotlib.
