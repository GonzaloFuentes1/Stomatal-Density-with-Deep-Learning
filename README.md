# Stomatal-Density-with-Deep-Learning
Capstone proyect about automatic stoma recognition

Se debe agregar la carpeta datasets para que funcione, esta contiene a las imágenes:
Se encuentra en : https://drive.google.com/drive/folders/1HTy7sWE2mbwLcafHUC7Si18T7syKK-EL?usp=drive_link

En cuanto a las librerias, se encuentra un archivo `requirements.txt`, con tal que se ejecute:

```bash
pip install -r requirements.txt
```

Los modelos de SAM se deben descargar del siguiente link, se recomienta usar la versión pequeña de `sam_b.pt`. Se deben guardar en la carpeta Modelos/SAM/

https://docs.ultralytics.com/es/models/sam/#key-features-of-the-segment-anything-model-sam


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

El repositorio incluye varios notebooks para diferentes propósitos, partes que se hicieron a medida la investigación progresaba. 

1. **[Yolo_training.ipynb](./Yolo_training.ipynb)**: Tiene 
2. **[Contador.ipynb](./Contador.ipynb)**: Notebook que implementa la funcionalidad de conteo de estomas.
3. **[SAM.ipynb](./SAM.ipynb)**: Notebook que utiliza el modelo Segment Anything para segmentación.
4. **[Tests.ipynb](./Tests.ipynb)**: Contiene pruebas relacionadas con los modelos.

Es necesario decir que cada uno de estos archivos contiene una sección de preprocesamiento para ordenar los archivos. Todo esto porque los modelos de YOLO se entrenan con un formato muy específico de carpetas.
Para la investigación se realizaron experimentos en dos metódologias principales:

1. HoldOut: Se ordena una proporción 80% training y 20% testing para el entrenamiento de los datos. Con esta metodología entrenamos nuestros modelos finales. El modelo recomendado para utilizar luego de la investigación es ´HoldOutSimpleYolov10n.pt´
