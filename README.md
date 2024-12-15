# Stomatal-Density-with-Deep-Learning
Capstone proyect about automatic stoma recognition

## Datasets
Se debe agregar la carpeta datasets para que funcione, esta contiene a las imágenes:
Se encuentra en : https://drive.google.com/drive/folders/1HTy7sWE2mbwLcafHUC7Si18T7syKK-EL?usp=drive_link

En cuanto a las librerias, se encuentra un archivo `requirements.txt`, con tal que se ejecute:

```bash
pip install -r requirements.txt
```
## SAM
Los modelos de SAM se deben descargar del siguiente link, se recomienta usar la versión pequeña de `sam_b.pt`. Se deben guardar en la carpeta Modelos/SAM/

https://docs.ultralytics.com/es/models/sam/#key-features-of-the-segment-anything-model-sam


## Directory 

El repositorio en local deberia seguir este orden
```
├── datasets/                   # Sets de datos para entrenar el modelo, en formato YOLO. Descargado externamente.
├── Modelos/                    # Modelos entrenados o preentrenados, agregando el modelo SAM elegido
├── runs/                       # Resultados de experimentos y registros
├── Counting.ipynb              # Notebook para contar estomas
├── SAM.ipynb                   # Notebook del modelo Segment Anything
├── Tests.ipynb                 # Notebook con pruebas del proyecto
├── Yolo_training.ipynb         # Notebook del modelo YOLO
├── YOLO8INFO.yaml              # Configuración para YOLOv8 y YOLO10
├── requirements.txt            # Instalador de requerimientos
├── README.md                   # Documentación del proyecto
├── .gitignore                  # Archivo de configuración para Git
```

## Notebooks
El repositorio incluye varios notebooks para diferentes propósitos, partes que se hicieron a medida la investigación progresaba. 

1. **[Yolo_training.ipynb](./Yolo_training.ipynb)**: Notebook para el entrenamiento de los modelos YOLO.
2. **[Tests.ipynb](./Tests.ipynb)**: Contiene pruebas relacionadas con los modelos. Conteo y métricas de error con respecto a la data.
3. **[SAM.ipynb](./SAM.ipynb)**: Notebook que utiliza el modelo Segment Anything para segmentación. Se uso como base para hacer el entregable.
4. **[Counting.ipynb](./Counting.ipynb)**: Notebook que implementa la funcionalidad de conteo de estomas. Se uso como base para hacer el entregable.

Es necesario decir que cada uno de estos archivos contiene una sección de preprocesamiento para ordenar los archivos. Todo esto porque los modelos de YOLO se entrenan con un formato muy específico de carpetas.
Para la investigación se realizaron experimentos en dos metódologias principales:

1. HoldOut: Se ordena una proporción 80% training y 20% testing para el entrenamiento de los datos. Con esta metodología entrenamos nuestros modelos finales. El modelo recomendado para utilizar luego de la investigación es `HoldOutSimpleYolov10n.pt` encontrado en `Modelos/yolov10/`

2. OnePlantOut: Se ordenan las carpetas tal que se eligen todas las imagenes de todas las plantas, a excepción de todas las imagenes de una especie en concreto. Esto ayuda a evaluar finalmente que tanto esta aprendiendo a reconocer estomas independiente de la planta. Se tenia planeado hacer una evaluación del rendimiento en plantas Chilenas del modelo. Pero, los datos no estuvieron a tiempo por lo que no se pudo realizar evaluar esta metodologia. Igualmente, se puede ver que se realizaron modelos para cada una de las plantas del dataset de StoManager1, con el fin de ver en `runs/` métricas de convergencia. Este análisis no llego al reporte final, más que nada por la falta de los datos.



## Recomendations

- Se recomienda fuertemente trabajar con CUDA si su dispositivo tiene una tarjeta de video NVIDIA, para el entrenamiento de los modelos YOLO y para le segmentación. Esta instalación es dependiente de cada dispositivo. Dejamos una referencia de como podria instalarse en cada caso. https://www.tensorflow.org/install/gpu?hl=es-419

- Si se quiere re-entrenar los modelos, es facil ver que se pueden evaluar de manera separada en el notebook de testeo. 

- Considerar que por las dimensiones tratadas, el modelo es lento de entrenar.

- Por ninguna razón implementar el entrenamiento en Google Collab, puesto que para el entrenamiento tendria que hacer una llamada al servidor por cada imagen que utilice de 1 en 1, lo que hace el entrenamiento en tiempos imposibles.

## Creditos y agradecimientos

Este proyecto fue posible gracias al apoyo y colaboración de diversas personas. Agradecemos especialmente a nuestro profesor Alejandro Cataldo por su guía y conocimientos durante el desarrollo de este trabajo. Asimismo, reconocemos a todos los integrantes del grupo Gonzalo Fuentes, Leon Sánchez, Matías Giddings, Nicolás Donoso y Maximiliano Valenzuela.