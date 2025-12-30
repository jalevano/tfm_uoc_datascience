# Evaluación Comparativa de Técnicas de Segmentación para Fotografía de Personas con Generación Automática de Recomendaciones vía VLM

**Trabajo de Fin de Máster - Máster en Ciencia de Datos**  
**Universitat Oberta de Catalunya (UOC)**  
**Diciembre 2025**

**Autor:** Jesus Levano.  
---

## Resumen

Este trabajo presenta una evaluación comparativa de cinco modelos de segmentación de instancias aplicados a fotografía de retrato profesional: YOLOv8-seg, Mask2Former, OneFormer, SAM 2.0 y BodyPix. La evaluación se realizó íntegramente en Google Colab gratuito, demostrando la viabilidad de investigación rigurosa con recursos accesibles.

Se evaluaron 143 configuraciones sobre 20 fotografías de retrato anotadas manualmente, generando 2.860 evaluaciones totales con 2.338 resultados válidos (81.7%). El análisis incluye métricas estándar (IoU, Dice), descriptores geométricos (Shapely), análisis textural (Haralick) y validación estadística (ANOVA, η², d de Cohen).

Como componente innovador, se implementó un sistema de mentoría fotográfica mediante Vision Language Model (Gemini 2.5 Flash) que analiza metadatos RAW junto con resultados de segmentación para generar recomendaciones técnicas específicas con valores cuantificados.

---

## Hallazgos Principales

| Modelo | IoU Medio | Desv. Típica | Tiempo (ms) | Observaciones |
|--------|-----------|--------------|-------------|---------------|
| **YOLOv8-seg** | **0.9498** | 0.053 | 80 | Líder en precisión y consistencia |
| OneFormer | 0.8873 | 0.207 | 168 | Configuraciones semantic óptimas |
| Mask2Former | 0.7401 | 0.349 | 168 | Solo ADE20K semantic funcional |
| BodyPix | 0.6559 | 0.174 | Variable | Viable para recursos limitados |
| SAM2 (Prompts) | 0.4614 | 0.375 | 3,075 | Requiere guía de dominio |
| SAM2 (Auto) | 0.3077 | 0.357 | 3,075 | Rendimiento insuficiente |

**Hallazgo estadístico:** La elección del modelo explica el 40.6% de la varianza en IoU (η² = 0.4057, p < 0.001).

---

## Estructura del Repositorio
```
tfm_uoc_datascience/
├── 00_CVAT_Ground_Truth.ipynb          # Procesamiento de anotaciones CVAT
├── 00_ExtraerCaracteristicas.ipynb     # Extracción de características fotográficas
├── 01_mask2former_evaluador.ipynb      # Evaluador Mask2Former
├── 01_oneformer_evaluador.ipynb        # Evaluador OneFormer
├── 02_sam_evaluador.ipynb              # Evaluador SAM 2.0 (modo automático)
├── 02_sam2_evaluados_prompt.ipynb      # Evaluador SAM 2.0 (modo prompts)
├── 03_yolo_evaluador.ipynb             # Evaluador YOLOv8-seg
├── 04_bodypix_evaluador.ipynb          # Evaluador BodyPix
├── 03_Analisis_Fase_1.ipynb            # Análisis exploratorio inicial
├── 03_Analisis_Fase_2A.ipynb           # Validación y limpieza de datos
├── 03_Analisis_Fase_2B.ipynb           # Estadísticas descriptivas
├── 03_Analisis_Fase_2C.ipynb           # Análisis de varianza (ANOVA)
├── 03_Analisis_Fase_2D.ipynb           # Correlaciones fotográficas
├── 03_Analisis_Fase_2E_*.ipynb         # Generación de visualizaciones (4 bloques)
├── 03_Analisis_Fase_2G.ipynb           # Síntesis y recomendaciones
├── 04_VLM_Prompt_Fotografia.ipynb      # Sistema de mentoría VLM
├── 04_VLM_setup_validacion.ipynb       # Validación de integración VLM
├── 99_GenerarVisualizacionesPDF.ipynb  # Exportación de figuras
├── 99_Utilidades_Conversion.ipynb      # Utilidades de conversión de formatos
└── src/models/                         # Módulos auxiliares
```

---

## Modelos Evaluados

### YOLOv8-seg
- **Variantes:** nano, small, medium, large, xlarge
- **Configuraciones:** 4 perfiles de sensibilidad (fast, balanced, sensitive, quality)
- **Total:** 20 configuraciones
- **Resultado:** Líder absoluto con IoU = 0.9498 y mínima variabilidad

### OneFormer
- **Backbones:** Swin-Large (COCO, ADE20K), Swin-Tiny (ADE20K)
- **Tareas:** semantic, instance, panoptic
- **Total:** 36 configuraciones
- **Resultado:** Configuraciones semantic alcanzan IoU = 0.9674 (máximo del estudio)

### Mask2Former
- **Backbones:** Swin-Large, Swin-Base, Swin-Tiny
- **Datasets:** COCO instance, ADE20K semantic
- **Total:** 67 configuraciones
- **Resultado:** Solo ADE20K semantic funcional; COCO instance presenta fallos sistemáticos

### SAM 2.0
- **Variantes:** Tiny, Small, Base-Plus, Large
- **Modos:** Automático (3 configs) y Prompts (4 estrategias)
- **Total:** 28 configuraciones
- **Resultado:** Modo prompts con saliencia alcanza IoU = 0.74; modo automático inadecuado

### BodyPix
- **Variantes:** MobileNetV1 0.50, MobileNetV1 0.75
- **Configuraciones:** 4 niveles de sensibilidad × 3 umbrales
- **Total:** 24 configuraciones
- **Resultado:** IoU = 0.66, viable para aplicaciones con recursos limitados

---

## Sistema de Mentoría VLM

El sistema integra análisis multimodal mediante Gemini 2.5 Flash:

**Entradas:**
- Métricas del archivo RAW (brillo, contraste, saturación, nitidez, SNR)
- Métricas de segmentación (IoU, Boundary IoU, Precision, Recall)
- Métricas de composición (posición del sujeto, espacio negativo, saliencia)
- Imagen editada con overlay de máscara de segmentación

**Salidas (formato JSON):**
- Evaluación de decisiones de edición
- Fortalezas detectadas con métricas de soporte
- Máximo 3 recomendaciones priorizadas con valores numéricos concretos
- Sugerencias de fondo basadas en teoría del color (códigos hexadecimales)

---

## Requisitos Técnicos

### Entorno de Ejecución
- Google Colab (GPU T4, 16GB VRAM)
- Python 3.8+

### Dependencias Principales
```
torch>=2.0
transformers>=4.30
ultralytics>=8.0
opencv-python>=4.8
numpy>=1.24
pandas>=2.0
scipy>=1.10
matplotlib>=3.7
seaborn>=0.12
shapely>=2.0
mahotas>=1.4
```

### APIs Externas
- Google Gemini API (para componente VLM)

---

## Reproducibilidad

### Estructura de Datos en Google Drive
```
/TFM/
├── dataset/
│   ├── fotos_editadas/           # 20 fotografías de evaluación
│   └── ground_truth/             # Máscaras anotadas manualmente
├── resultados/
│   ├── mask2former/              # Predicciones por configuración
│   ├── oneformer/
│   ├── sam2_auto/
│   ├── sam2_prompts/
│   ├── yolov8/
│   └── bodypix/
├── analisis/
│   ├── metricas_fusionadas.csv   # Dataset consolidado (235 columnas)
│   └── visualizaciones/          # Figuras generadas
└── caracteristicas/
    └── caracteristicas_raw.csv   # 148 características fotográficas
```

### Ejecución Secuencial
1. `00_CVAT_Ground_Truth.ipynb` - Procesar anotaciones
2. `00_ExtraerCaracteristicas.ipynb` - Extraer características RAW
3. `0X_*_evaluador.ipynb` - Ejecutar cada modelo
4. `03_Analisis_Fase_*.ipynb` - Análisis estadístico
5. `04_VLM_*.ipynb` - Sistema de mentoría

---

## Resultados Clave

### Conclusiones Principales

1. **YOLOv8-seg es la opción óptima** para segmentación de personas en fotografía de retrato, combinando máxima precisión (IoU = 0.95) con mínima variabilidad y alta eficiencia computacional.

2. **El rendimiento en benchmarks genéricos no predice el rendimiento en dominios especializados.** Mask2Former y SAM 2.0, líderes en COCO, presentaron limitaciones significativas en fotografía de retrato.

3. **Las intuiciones fotográficas no siempre se confirman:**
   - El bokeh no mejora la segmentación (IoU fondo nítido: 0.746 vs bokeh: 0.664)
   - Los fondos complejos no la dificultan (complejo: 0.707 vs simple: 0.651)
   - El alto contraste la perjudica (bajo: 0.715 vs alto: 0.630)
   - La nitidez es el único predictor consistente (d = 0.30)

4. **Los modelos fundacionales requieren conocimiento de dominio** para competir con modelos especializados.

### Recomendaciones por Escenario

| Escenario | Modelo Recomendado | Justificación |
|-----------|-------------------|---------------|
| Producción con volumen alto | YOLOv8 nano/small | 18-25 ms, IoU > 0.94 |
| Edición individual máxima calidad | OneFormer COCO semantic | IoU = 0.967 |
| Aplicación web/móvil tiempo real | YOLOv8 nano | 18 ms, 60 MB GPU |
| Pipeline híbrido casos complejos | YOLOv8 → SAM2 prompts | Detección + refinamiento |
| Recursos computacionales mínimos | YOLOv8 nano | Viable en CPU |

---

## Trabajo Futuro

- **Pipeline híbrido YOLOv8→SAM2:** Evaluación cuantitativa de refinamiento de bordes
- **Generación de fondos basada en colorimetría:** Integración con modelos generativos
- **Extensión a otros dominios fotográficos:** Producto, arquitectura, fauna
- **Validación de recomendaciones VLM:** Estudios con usuarios reales

---

## Citación
```bibtex
@mastersthesis{levanolevano2025segmentacion,
  author  = {Lévano Lévano, Jesús A.},
  title   = {Evaluación comparativa de técnicas de segmentación para fotografía 
             de personas con generación automática de recomendaciones vía VLM},
  school  = {Universitat Oberta de Catalunya},
  year    = {2025},
  type    = {Trabajo de Fin de Máster},
  address = {Barcelona, España}
}
```

---

## Licencia

Este trabajo está sujeto a una licencia [Creative Commons Reconocimiento-NoComercial-SinObraDerivada 3.0 España](http://creativecommons.org/licenses/by-nc-nd/3.0/es/).

---

## Contacto

Para consultas sobre este trabajo, contactar a través del repositorio de GitHub.

**Nota:** Por restricciones de derechos de imagen, no se incluyen las fotografías originales en alta resolución.
