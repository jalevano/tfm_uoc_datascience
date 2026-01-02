# Evaluación Comparativa de Técnicas de Segmentación para Fotografía de Personas con Generación Automática de Recomendaciones vía VLM

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red.svg)](https://pytorch.org/)
[![License](https://img.shields.io/badge/License-CC%20BY--NC--ND%203.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-nd/3.0/es/)
[![UOC](https://img.shields.io/badge/UOC-Máster%20Data%20Science-green.svg)](https://www.uoc.edu/)

## Información del Proyecto

| Campo | Descripción |
|-------|-------------|
| **Título** | Evaluación comparativa de técnicas de segmentación para fotografía de personas con generación automática de recomendaciones vía VLM |
| **Autor** | Jesús L. |
| **Titulación** | Máster en Ciencia de Datos |
| **Universidad** | Universitat Oberta de Catalunya (UOC) |
| **Fecha** | Diciembre 2025 |

---

## Resumen

Este trabajo presenta una evaluación comparativa de técnicas avanzadas para la segmentación de personas en fotografías, analizando cinco modelos representativos de paradigmas arquitectónicos diversos: **SAM 2.0**, **Mask2Former**, **OneFormer**, **YOLOv8-seg** y **BodyPix**, en el contexto específico de fotografía de retrato profesional.

La metodología consiste en la evaluación independiente de los cinco modelos sobre un dataset de 20 fotografías de retrato anotadas manualmente, aplicando métricas especializadas como IoU y Dice Coefficient, complementadas con análisis geométrico mediante descriptores de Shapely y Mahotas.

### Hallazgos Principales

- **YOLOv8-seg** emerge como líder con IoU medio de **0.9498** y la menor variabilidad del estudio
- La elección del modelo explica el **40.6%** de la varianza en rendimiento (η²=0.4057)
- Los modelos fundacionales (SAM2) requieren guía de dominio para competir con modelos especializados
- Las intuiciones fotográficas sobre bokeh y complejidad de fondo no se confirman empíricamente

---

## Resultados Visuales por Modelo

Las siguientes visualizaciones muestran el rendimiento comparativo de cada modelo evaluado sobre fotografías representativas del dataset.

### YOLOv8-seg (Mejor Rendimiento Global)

<p align="center">
  <img src="docs/images/_DSC0143_umbral0_3.png" alt="YOLOv8 Large Segmentation" width="800"/>
</p>

**Configuración:** YOLOv8 Large | conf≥0.3 | 1 persona detectada (conf=0.92)

YOLOv8-seg alcanza el mejor rendimiento del estudio con IoU=0.9498 y desviación típica de 0.053, demostrando precisión elevada y consistencia excepcional independientemente de la configuración seleccionada.

---

### OneFormer (ADE20K Semantic)

<p align="center">
  <img src="docs/images/_DSC0023.png" alt="OneFormer ADE20K Swin-Tiny Semantic" width="800"/>
</p>

**Configuración:** ADE20K | Swin-Tiny | semantic | t=0.75

OneFormer con configuración semántica produce máscaras limpias y bien definidas. Las configuraciones semantic alcanzan IoU=0.9674, superando marginalmente a YOLOv8 en casos individuales, aunque con mayor variabilidad global.

---

### Mask2Former (ADE20K Semantic)

<p align="center">
  <img src="docs/images/_DSC0147_20251020_221040.png" alt="Mask2Former Large ADE Semantic" width="800"/>
</p>

**Configuración:** large_ade | baja_sensibilidad | conf=1.00

Mask2Former con ADE20K semantic alcanza IoU=0.954, siendo la única configuración funcional de este modelo. Las variantes COCO instance presentaron fallos sistemáticos debido a la arquitectura multi-query.

---

### SAM 2.0 con Prompts de Saliencia

<p align="center">
  <img src="docs/images/_DSC0411_20251029_212141.png" alt="SAM2 Hiera Tiny con Saliency Prompts" width="800"/>
</p>

**Configuración:** sam2_hiera_tiny | saliency_moderate | 2 personas detectadas

SAM2 con estrategias de prompting basadas en saliencia visual alcanza IoU=0.74, mejorando significativamente respecto al modo automático (IoU=0.31). La elección de estrategia de prompting es crítica (η²=0.231).

---

### SAM 2.0 Automático (Sobre-segmentación)

<p align="center">
  <img src="docs/images/_DSC0084.png" alt="SAM2 Tiny Quality - Sobresegmentación" width="800"/>
</p>

**Configuración:** TINY-quality | 11 máscaras generadas | 7 clasificadas como "personas"

El modo automático de SAM2 ilustra el problema de sobre-segmentación: sin guía de dominio, el modelo fragmenta la imagen en múltiples regiones sin priorizar el sujeto humano. Mediana de IoU=0.017 indica que más del 50% de evaluaciones produjeron segmentaciones prácticamente nulas.

---

### BodyPix (Limitaciones de Arquitectura Web)

<p align="center">
  <img src="docs/images/_DSC0987_20251116_172755.png" alt="BodyPix MobileNetV1 0.75" width="800"/>
</p>

**Configuración:** mobilenet_v1_075 | baja_sensibilidad | T=0.5 | Área persona: 39.7%

BodyPix presenta fragmentación visible en la máscara debido a las limitaciones de resolución interna de MobileNetV1. Con IoU medio de 0.6559, demuestra que la simplicidad arquitectónica tiene un coste en precisión, aunque mantiene consistencia predecible.

---

## Resultados Cuantitativos

### Ranking de Modelos por IoU

| Modelo | IoU Medio | Desv. Típica | Mediana | Tiempo (ms) |
|--------|-----------|--------------|---------|-------------|
| **YOLOv8-seg** | 0.9498 | 0.053 | 0.955 | 80 |
| OneFormer | 0.8873 | 0.207 | 0.964 | 3,200 |
| Mask2Former | 0.7401 | 0.349 | 0.953 | 168 |
| BodyPix | 0.6559 | 0.174 | 0.673 | ~50 |
| SAM2 (prompts) | 0.4614 | 0.375 | 0.459 | 1,200 |
| SAM2 (auto) | 0.3077 | 0.360 | 0.017 | 3,075 |

### Configuraciones TOP-10 por IoU

| Rank | Modelo | Configuración | IoU |
|------|--------|---------------|-----|
| 1 | OneFormer | COCO_swin_semantic_t0.40 | 0.9674 |
| 2 | OneFormer | COCO_swin_semantic_t0.60 | 0.9674 |
| 3 | OneFormer | COCO_swin_semantic_t0.75 | 0.9674 |
| 4 | OneFormer | COCO_swin_semantic_t0.85 | 0.9674 |
| 5 | OneFormer | ADE20K_swin_semantic_t0.40 | 0.9643 |
| 6 | OneFormer | ADE20K_swin_panoptic_t0.40 | 0.9644 |
| 7 | YOLOv8 | xlarge_balanced | 0.9567 |
| 8 | YOLOv8 | xlarge_fast | 0.9567 |
| 9 | YOLOv8 | medium_balanced | 0.9553 |
| 10 | Mask2Former | large_ade_semantic | 0.9540 |

---

## Acceso a Datos y Resultados

### Repositorio de Datos (Google Drive)

Los resultados completos de evaluación, máscaras de segmentación y visualizaciones están disponibles en:

**[Acceder a Resultados Completos (Google Drive)](https://drive.google.com/drive/folders/1wTIxvuOvCWIxrBfbmA8ZqBv4L3W3DFGJ?usp=drive_link)**

> **Nota sobre acceso:** Durante el período de evaluación del TFM (hasta resolución académica), el acceso está restringido a usuarios con cuenta **@uoc.edu**. Una vez finalizado el proceso de evaluación, el enlace se abrirá al público general para facilitar la reproducibilidad de la investigación.

---

## Estructura del Repositorio

```
tfm_uoc_datascience/
│
├── 00_CVAT_Ground_Truth.ipynb           # Procesamiento de anotaciones CVAT
├── 00_ExtraerCaracteristicas.ipynb      # Extracción de características fotográficas
│
├── 01_mask2former_evaluador.ipynb       # Evaluador Mask2Former
├── 01_oneformer_evaluador.ipynb         # Evaluador OneFormer
├── 02_sam_evaluador.ipynb               # Evaluador SAM2 automático
├── 02_sam2_evaluados_prompt.ipynb       # Evaluador SAM2 con prompts
├── 03_yolo_evaluador.ipynb              # Evaluador YOLOv8-seg
├── 04_bodypix_evaluador.ipynb           # Evaluador BodyPix
│
├── 03_Analisis_Fase_1.ipynb             # Análisis exploratorio inicial
├── 03_Analisis_Fase_2A.ipynb            # Ranking y estadísticas descriptivas
├── 03_Analisis_Fase_2B.ipynb            # ANOVA y tamaños de efecto
├── 03_Analisis_Fase_2C.ipynb            # Análisis por modelo
├── 03_Analisis_Fase_2D.ipynb            # Correlaciones fotográficas
├── 03_Analisis_Fase_2E_*.ipynb          # Visualizaciones (Bloques 1-4)
├── 03_Analisis_Fase_2G.ipynb            # Síntesis comparativa
│
├── 04_VLM_setup_validacion.ipynb        # Configuración API Gemini
├── 04_VLM_Prompt_Fotografia.ipynb       # Sistema de mentoría VLM
│
├── 99_GenerarVisualizacionesPDF.ipynb   # Generación de figuras
├── 99_Utilidades_Conversion.ipynb       # Utilidades de conversión
│
├── docs/
│   └── images/                          # Imágenes para README
│
├── src/
│   └── models/                          # Código fuente de modelos
│
└── README.md                            # Este archivo
```

---

## Requisitos Técnicos

### Entorno de Ejecución

- **Plataforma:** Google Colab (gratuito)
- **GPU:** Tesla T4 (16GB VRAM)
- **Python:** 3.8+
- **Sesiones:** ~12 horas máximo

### Dependencias Principales

```python
# Deep Learning
torch>=2.0.0
torchvision>=0.15.0
transformers>=4.30.0

# Modelos específicos
ultralytics>=8.0.0          # YOLOv8
segment-anything-2          # SAM 2.0
tf-bodypix                  # BodyPix

# Análisis y visualización
numpy>=1.24.0
pandas>=2.0.0
scipy>=1.10.0
matplotlib>=3.7.0
seaborn>=0.12.0

# Métricas geométricas
shapely>=2.0.0
mahotas>=1.4.0
opencv-python>=4.7.0
```

---

## Reproducibilidad

### Ejecución Secuencial Recomendada

1. **Preparación de datos:**
   ```
   00_CVAT_Ground_Truth.ipynb → 00_ExtraerCaracteristicas.ipynb
   ```

2. **Evaluación de modelos:**
   ```
   01_mask2former_evaluador.ipynb
   01_oneformer_evaluador.ipynb
   02_sam_evaluador.ipynb
   02_sam2_evaluados_prompt.ipynb
   03_yolo_evaluador.ipynb
   04_bodypix_evaluador.ipynb
   ```

3. **Análisis estadístico:**
   ```
   03_Analisis_Fase_1.ipynb → 03_Analisis_Fase_2A.ipynb → ... → 03_Analisis_Fase_2G.ipynb
   ```

4. **Sistema VLM:**
   ```
   04_VLM_setup_validacion.ipynb → 04_VLM_Prompt_Fotografia.ipynb
   ```

### Notas de Reproducibilidad

- Todos los notebooks incluyen instalación de dependencias al inicio
- Los checkpoints permiten reanudar ejecución tras desconexiones de Colab
- Las semillas aleatorias están fijadas para reproducibilidad
- El dataset de 20 fotografías no se incluye por restricciones de derechos de imagen

---

## Citación

Si utilizas este trabajo en tu investigación, por favor cita:

```bibtex
@mastersthesis{jesus2025segmentacion,
  title={Evaluación comparativa de técnicas de segmentación para fotografía 
         de personas con generación automática de recomendaciones vía VLM},
  author={Jesús L.},
  school={Universitat Oberta de Catalunya},
  year={2025},
  type={Trabajo de Fin de Máster},
  program={Máster en Ciencia de Datos}
}
```

---

## Licencia

Este trabajo está sujeto a una licencia [Creative Commons Reconocimiento-NoComercial-SinObraDerivada 3.0 España](http://creativecommons.org/licenses/by-nc-nd/3.0/es/).

---

## Contacto

- **Autor:** Jesús L.
- **Repositorio:** [github.com/jalevano/tfm_uoc_datascience](https://github.com/jalevano/tfm_uoc_datascience)
- **Universidad:** Universitat Oberta de Catalunya (UOC)
