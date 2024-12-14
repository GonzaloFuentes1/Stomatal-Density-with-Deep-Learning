# Stomatal-Density-with-Deep-Learning
Capstone proyect about automatic stoma recognition

Se debe agregar la carpeta datasets para que funcione, esta contiene a las imágenes:
Se encuentra en : https://drive.google.com/drive/folders/1HTy7sWE2mbwLcafHUC7Si18T7syKK-EL?usp=drive_link

En cuanto a las librerias, se encuentra un archivo `requirements.txt`, con tal que se ejecute:

```bash
pip install -r requirements.txt
```

Los modelos de SAM se deben descargar del siguiente link, se recomienta usar la versión pequeña de `sam_b.pt`.

https://docs.ultralytics.com/es/models/sam/#key-features-of-the-segment-anything-model-sam

El repositorio en local deberia seguir este orden
```
├── Modelos/                    # Modelos entrenados o preentrenados
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