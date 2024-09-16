<div style="text-align: center; border-top: 1px solid #ccc; border-bottom: 1px solid #ccc; padding: 10px 0;">
    <h1 style="color: lightblue; font-size: 2em;">Proyecto Labs 1</h1>
</div>

## Descripción

<p style="text-align: justify; text-indent: 2em;">
Limpieza, ordenamiento y análisis de unos datos acerca de Películas, para posterior elaboración de un modelo de recomendación basado en contenido, y su despliegue en una Api, haciendo los ajustes necesarios pensando en la velocidad de respuesta de la misma, sin perder información en el camino. En dicha Api, además de dedicar un endpoint al sistema de recomendación, se programaron otros seis(6) endpoints para responder preguntas asociadas a la data. 
</p>

## Tabla de contenido

1. [Descripción](#descripción)
1. [Enlaces](#enlaces)
1. [Instalación y Requisitos](#instalación-y-requisitos)
1. [Estructura del Proyecto](#estructura-del-proyecto)
1. [Uso y Ejecución](#uso-y-ejecución)
1. [Datos y Fuentes](#datos-y-fuentes)
1. [Metodología](#metodología)
1. [Consideraciones](#consideraciones)
1. [Resultados y Conclusiones](#resultados-y-conclusiones)
1. [Autores](#autores)

## Enlaces

- **Enlace a la Api**
  - https://primeraapirender.onrender.com/docs
- **Enlace al video**
  - https://drive.google.com/file/d/1IFZGzRPhJNy1NZFgwZR5xQmGF3X0UUTJ/view?usp=sharing

## Instalación y Requisitos

**Requisitos:**

- Requisitos para la API
  - Python 3.10
  - fastapi==0.110.1
  - polars==1.6.0
  - numpy==1.26.4
  - joblib
  - uvicorn
- Requisitos para los Notebooks
  - Python 3.10
  - gdown==5.2.0
  - joblib
  - jupyter==1.1.1
  - matplotlib==3.9.2
  - numpy==1.26.4
  - pandas==1.5.3
  - plotly==5.24.0
  - polars==1.6.0
  - pyarrow==17.0.0
  - scikit-learn==1.5.1
  - seaborn==0.13.2

**Pasos de instalación:**

1. Clonar el repositorio: `git clone https://github.com/aliskairraul/Bootcamp-Henry-Proyecto-Lab_1.git`
2. Partamos del echo de que esto debe tratarse como 2 sub-proyectos por separado (un Análisis y una Api). Cree dos carpetas dentro de su ordenador

- Una Carpeta va todo lo referente al analisis y el modelo (Allí va a copiar sólo la Carpeta `notebooks` de este repositorio)
- En la otra Carpeta tendrá todo lo referente a la Api (Allí va `TODO el Repositorio, excepto la Carpeta notebooks`)

4. Crear un entorno virtual en cada carpeta: `python3.10 -m venv nombre_del_entorno`
5. El Archivo `requirements.txt` en la raiz del proyecto son las dependencias para la Api y es el que debe usar para la carpeta en que tenga la Api
6. El Archivo `requirements.txt` que se encuentra dentro de la carpeta `notebooks` es el que debe usar para instalar las dependencias del análisis
7. Activar en cada proyecto el entorno virtual:
   - Windows: `nombre_del_entorno\Scripts\activate`
   - macOS/Linux: `source nombre_del_entorno/bin/activate`
8. Instalar las dependencias: `pip install -r requirements.txt`

## Estructura del Proyecto

1. **Para la parte del Análisis**<br>
   **Nota:** Las carpetas `data`, `datasets_inicial`, `model` y sus contenidos internos se irán creando a medida que vaya ejecutando el codigo. La estructura de Carpetas se crea justo despues de la importación de las librerias en el primer cuaderno Notebook (obligatorio ejecutar la celda). Los archivos se guardarán y transformarán a lo largo de los 4 archivos notebooks, sí no dispone de tiempo para ejecutar todas las celdas (hay procesos que gastan tiempo), despreocupe, a medida que se van a ir necesitando los distintos archivos, ya transformados en el codigo hay la opción de irlos descargando de internet.

- `notebooks/`: Incluye los siguiente:
  - `assets/` Imagenes ilustrativas
  - `data/` Aca se guardaran archivos de trancisión entre un notebook y otro
    - `data_api/` Donde se guardaran los archivos necesarios para las 6 primeras funciones de la Api
    - `data_warehouse` Se guardaran archivos producto de normalización de la data
  - `datasets_inicial/` Aca se descargaran los datasets iniciales
  - `model/` Se guardará el modelo y un archivo parquet necesarios para correr el modelo
  - `01_etl_credit_csv.ipynb`
  - `02_etl_movies_csv.ipynb`
  - `03_normalizando.ipynb`
  - `04_eda_modelo.ipynb`

2. **Para la parte de la Api**

- `data/`: Contiene los archivos `parquet` y `pkl` necesarios para la Api.
- `models/`: EL archivo `base_model.py` con los modelos de respuesta de la Api.
- `routers/` Los archivos `.py` que contienen los distintos endpoints de la Api
- `main.py` Arhivo raiz de la Api
- `requirements.txt` dependencias necesarias para la Api
- `README.md`: Archivo de documentación del proyecto.

## Uso y Ejecución

1. **Para la parte del Análisis**:

- Ejecute los siguientes archivos en el Orden que se nombran a continuación:
  - `01_etl_credit_csv.ipynb`
  - `02_etl_movies_csv.ipynb`
  - `03_normalizando.ipynb`
  - `04_eda_modelo.ipynb`
- Notará que existe una estructura de carpetas.
  - `assets/` Guarda archivos de imagenes
  - `data/` A medida que avance en la ejecusión de los Notebooks se irá llenando, tanto ella como las otras dos carpetas que estan en su interior.
    - `data/data_api/`
    - `data/data_warehouse`
  - `datasets_inicial/` Allí va a colocar los archivos `credits.csv` y `movies_dataset.csv`. Sí no cuenta con ellos, entonces es necesario que tenga una conexión a Internet, y el codigo los descargará cuando los necesite.
  - `model` En esta se guardará el archivo `.pkl` y `.parquet` casi al final del ultimo notebook a ejecutar.

2. **Para la parte de la Api**:

- Asegurese de que la estructura de este repositorio, a excepción de la Carpeta `notebooks`, se copió Integramente en la locación de su computador que dispuso para ello.
- Con el entorno virtual activado ejecute `uvicorn main:app --reload ` espere que se ejecute y desde el navegador `http://127.0.0.1:8000/docs` para que vaya directamente en la documentacion de la Api.

## Datos y Fuentes

<p style="text-align: justify; text-indent: 2em;">
Los archivos <b>movies_dataset.csv</b> y <b>credits.csv</b>, que fueron el punto de partida de este proyecto, fueron suministrados por la Institución Henry.
</p>

## Metodología

<p style="text-align: justify; text-indent: 2em;">
Se realizó un ETL a los datasets, para poder contar con los datos de una forma mas ordenada, para luego poder hacer un EDA y posterior modelamiento a un sistema de recomendación.  En cuanto a este Sistema de Recomendación, se utilizó el modelo de <b>Similitud del Coseno</b>, dado que al no contar con data acerca de preferencias del usuario que introduce el título de la película, ni de ningún otro usuario en general, se imposibilita usar técnicas de <b>Filtrado Colaborativo</b>. 
</p>

## Consideraciones

<p style="text-align: justify; text-indent: 2em;">
La libreria <b>Polars</b> a diferencia de <b>Pandas</b> utiliza multiples nucleos del procesador para hacer sus operaciones, de allí su velocidad. Pero hay que tomar en cuenta, que efectivamente siempre nos va a devolver la misma información, pero es altamente probable que no siempre venga ordenada de la misma manera, ya que no todas las computadoras tienen la misma cantidad de nucleos en su procesador, o es posible que lo ocupado que estén esos nucleos dentro de una misma maquina dependa de la cantidad de procesos que estén abiertos a la hora de ejecutar el codigo.  No quiere decir que la data esté mala, simplemente de que el orden en que van a caer en los distintos dataframe va a ser distinta y pudiera darse el caso de que al querer Normalizar una base de Datos los <b>id</b> de ciertas características como <b>lenguajes</b>, <b>generos</b>, etc se obtengan en distinto orden. 
</p>
<p style="text-align: justify; text-indent: 2em;">
Lo expuesto en el párrafo anterior puede afectar la percepción, sólo desde el punto de vista pedágogico y pudieramos hacer algo "parecido" a lo que hacemos al utlizar funciones random en python, que sembramos una semilla para obtener siempre resultados idénticos. Acá pudiesemos desde un inicio crear una columna "index" desde el principio e ir ordenando las respuestas posteriores por ese "index", sólo para que a la hora de explicar lo sucedido el que vaya replicando el proceso en otra máquina, entienda mas lo que va sucediendo. Esto no lo hice porque sería bajar la velocidad del proceso.
</p>

## Resultados y Conclusiones

<p style="text-align: justify; text-indent: 2em;">
La calidad de las respuestas obtenidas por cualquier análisis, donde se incluya o no, algún modelo de Machine Learning, depende de la <b>Calidad del Dato</b>. En mi opinión las mejores técnicas y modelos van a arrojar resultados inexactos o imprecisos, sí previo a sus implementaciones no se obtienen datos de calidad.   
</p>
<p style="text-align: justify; text-indent: 2em;">
Los modelos de Machine Learning y Redes Neuronales son como cajas mágicas donde depositamos un conjunto de datos y estos nos devuelven unos resultados asombrosos.  Nuestra responsabilidad como Científicos de Datos, es en primera instancia, proporcionar a estos modelos la mejor data posible y coherente con el problema que queremos solucionar, y como segundo Y MUY IMPORTANTE TAMBIEN entender cual es la LOGICA CONCEPTUAL de cada modelo, lo que nos ayuda a entender como se comportan, para manipular, de la mejor forma posible,  la parametrización de los mismos (Tunear).
</p>
<p style="text-align: justify; text-indent: 2em;">
Para este caso de estudio, el saber como se nos presenta la RESPUESTA devuelta por un modelo de <b>Similitud del Coseno<b>, nos dió la oportunidad de extraer de la misma los FRAGMENTOS EXACTOS de información que necesitabamos, lo que nos permitió REDUCIR significativamente el tamaño del archivo que llevaríamos a despliegue, y por ende mejorar la velocidad de respuesta de nuestra API.
</p>
<p style="text-align: justify; text-indent: 2em;">
Conocer como funcionan las distintas librerias que utilizamos para manipular datos, nos da la ventaja de saber donde es mas conveniente utilizar cada una.  Por ejemplo el poder que tiene <b>Pandas</b> a la hora de inferir el esquema de datos de un dataset lo considero personalmente MUY SUPERIOR a <b>Polars</b>, pero esta última tiene mucha mas capacidad a la hora de manejar volumen de información, y mas velocidad para procesar datos.  Si a todo esto le añadimos un poquito de  lógica de programación que sea capaz de detectar anomalías en grandes volumenes de datos (sin necesidad de corregirlas, solo detectarlas, y descartarlas), pudieramos programar un flujo de trabajo que nos permita limpiar grandes volumenes de datos (por baches) utilizando el poder de Pandas y luego unificar todo (ya con esquemas inferidos) y utilizar el poder de Polars para procesarlos, buscando maximizar un entorno de pocos recursos, y planteando la seria posibilidad de ahorrar dinero en la contratación de recursos computacionales (todo sujeto a evaluación indivudual de cada caso, claro esta). 
</p>

## Autores:

Este proyecto fue realizado por: Aliskair Rodríguez.<br>
[linkedin.com/in/aliskair-rodriguez-782b3641](https://www.linkedin.com/in/aliskair-rodriguez-782b3641/)
