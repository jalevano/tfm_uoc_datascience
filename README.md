# TFM Roadmap: Evaluación Comparativa de Técnicas de Segmentación para Fotografía de Personas con Generación Automática de Recomendaciones vía VLM

## 🎯 Objetivos del Proyecto

### Objetivo General
Realizar una evaluación comparativa sistemática de técnicas estado del arte para segmentación de personas en diferentes contextos fotográficos y demostrar la viabilidad de generar recomendaciones técnicas automáticas mediante Vision Language Models.

### Objetivos Específicos

1. **OE1:** Implementación de Framework de Evaluación
2. **OE2:** Desarrollo de Métricas Especializadas
3. **OE3:** Benchmark Comparativo Completo
4. **OE4:** Demo de Recomendaciones VLM

## 🗓️ Timeline Detallado

### Mes 1: Setup + Baseline (Semanas 1-4)

#### Semana 1-2: Setup Técnico e Implementación
- [ ] **Configuración del entorno de desarrollo**
  - [ ] Setup GPU computing environment
  - [ ] Instalación de dependencias principales
  - [ ] Configuración de repositorio Git
- [ ] **Implementación de modelos base**
  - [ ] MaskDINO setup y testing
  - [ ] SAM 2.0 implementation
  - [ ] BodyPix integration
  - [ ] YOLOv8-seg configuration
- [ ] **Documentación inicial**
  - [ ] README del proyecto
  - [ ] Guía de instalación
  - [ ] Estructura de carpetas

#### Semana 3-4: Pipeline de Evaluación
- [ ] **Desarrollo del framework de evaluación**
  - [ ] Pipeline de procesamiento de imágenes
  - [ ] Sistema de logging y tracking
  - [ ] Configuración de experimentos
- [ ] **Primeros benchmarks**
  - [ ] Tests básicos con dataset pequeño
  - [ ] Validación del pipeline
  - [ ] Métricas básicas (IoU, Dice, etc.)
- [ ] **Preparación de datos**
  - [ ] Colección y organización de imágenes
  - [ ] Categorización por contextos fotográficos
  - [ ] Ground truth inicial

**Entregables Mes 1:**
- ✅ Pipeline de evaluación funcional
- ✅ Implementación de los 4 modelos
- ✅ Framework de testing básico
- ✅ Dataset inicial categorizado

---

### Mes 2: Métricas + Validación (Semanas 5-8)

#### Semana 5-6: Desarrollo de Métricas Especializadas
- [ ] **Análisis de requerimientos específicos**
  - [ ] Investigación de métricas para fotografía
  - [ ] Análisis de casos edge en segmentación de personas
  - [ ] Definición de criterios de calidad
- [ ] **Implementación de métricas custom**
  - [ ] Métricas de calidad de bordes
  - [ ] Evaluación de coherencia espacial
  - [ ] Métricas sensibles al contexto fotográfico
- [ ] **Testing y calibración**
  - [ ] Validación con casos conocidos
  - [ ] Ajuste de parámetros
  - [ ] Comparación con métricas estándar

#### Semana 7-8: Validación Humana + Ground Truth
- [ ] **Diseño de protocolo de evaluación humana**
  - [ ] Criterios de evaluación para expertos
  - [ ] Interfaz para anotación
  - [ ] Protocolo de inter-annotator agreement
- [ ] **Creación de ground truth**
  - [ ] Selección de imágenes representativas
  - [ ] Anotación manual de calidad
  - [ ] Validación cruzada
- [ ] **Análisis de correlación**
  - [ ] Correlación métricas automáticas vs. humanas
  - [ ] Identificación de discrepancias
  - [ ] Refinamiento de métricas

**Entregables Mes 2:**
- ✅ Suite de métricas especializadas validadas
- ✅ Ground truth dataset anotado
- ✅ Protocolo de evaluación humana
- ✅ Análisis de correlación métricas

---

### Mes 3: Benchmark Completo (Semanas 9-12)

#### Semana 9-10: Evaluación Sistemática
- [ ] **Configuración de experimentos masivos**
  - [ ] Diseño experimental por categorías
  - [ ] Configuración de batch processing
  - [ ] Sistema de monitoreo de experimentos
- [ ] **Ejecución del benchmark**
  - [ ] Evaluación por contexto fotográfico:
    - [ ] Retratos con fondo uniforme
    - [ ] Fotografía en exteriores
    - [ ] Condiciones de iluminación difícil
    - [ ] Múltiples personas
    - [ ] Poses complejas
- [ ] **Recolección de datos**
  - [ ] Métricas de accuracy por modelo
  - [ ] Tiempo de procesamiento
  - [ ] Uso de recursos computacionales

#### Semana 11-12: Análisis de Resultados
- [ ] **Análisis estadístico**
  - [ ] Comparación de rendimiento por modelo
  - [ ] Análisis de significancia estadística
  - [ ] Identificación de fortalezas/debilidades
- [ ] **Análisis de trade-offs**
  - [ ] Velocidad vs. Calidad
  - [ ] Recursos vs. Precisión
  - [ ] Robustez vs. Especialización
- [ ] **Documentación de patterns**
  - [ ] Casos de uso óptimos por modelo
  - [ ] Recomendaciones de aplicación
  - [ ] Limitaciones identificadas

**Entregables Mes 3:**
- ✅ Benchmark completo de los 4 modelos
- ✅ Análisis estadístico detallado
- ✅ Documentación de trade-offs
- ✅ Recomendaciones de uso por contexto

---

### Mes 4: Demo VLM Integration (Semanas 13-16)

#### Semana 13-14: Setup VLM APIs
- [ ] **Investigación y selección de VLMs**
  - [ ] Evaluación de GPT-4V, Claude, Gemini Pro Vision
  - [ ] Análisis de capacidades y costos
  - [ ] Setup de APIs y autenticación
- [ ] **Prompt Engineering**
  - [ ] Diseño de prompts para análisis compositivo
  - [ ] Testing de respuestas VLM
  - [ ] Optimización de prompts para recomendaciones
- [ ] **Integración técnica**
  - [ ] Pipeline de llamadas API
  - [ ] Manejo de rate limits y errores
  - [ ] Caching y optimización

#### Semana 15-16: Demo Funcional + Evaluación
- [ ] **Desarrollo del demo**
  - [ ] Interface para cargar imágenes
  - [ ] Visualización de segmentaciones
  - [ ] Display de recomendaciones VLM
- [ ] **Testing y refinamiento**
  - [ ] Testing con casos diversos
  - [ ] Refinamiento de la experiencia de usuario
  - [ ] Optimización de rendimiento
- [ ] **Evaluación de calidad**
  - [ ] Evaluación humana de recomendaciones
  - [ ] Análisis de correlación calidad-utilidad
  - [ ] Métricas de viabilidad técnica

**Entregables Mes 4:**
- ✅ Demo funcional de VLM integration
- ✅ Pipeline automatizado de recomendaciones
- ✅ Evaluación de calidad de recomendaciones
- ✅ Análisis de viabilidad comercial

---

### Mes 5: Documentación TFM (Semanas 17-20)

#### Semana 17-18: Escritura de Memoria
- [ ] **Estructura de la memoria**
  - [ ] Introducción y motivación
  - [ ] Estado del arte y trabajo relacionado
  - [ ] Metodología y diseño experimental
  - [ ] Resultados y análisis
  - [ ] Demo VLM y proof of concept
  - [ ] Conclusiones y trabajo futuro
- [ ] **Redacción de secciones**
  - [ ] Revisión bibliográfica completa
  - [ ] Descripción detallada de metodología
  - [ ] Análisis exhaustivo de resultados
  - [ ] Documentación técnica del demo

#### Semana 19-20: Preparación Final
- [ ] **Preparación de presentación**
  - [ ] Slides para defensa (20-30 slides)
  - [ ] Demo en vivo preparado
  - [ ] Anticipación de preguntas
- [ ] **Revisiones finales**
  - [ ] Revisión completa de la memoria
  - [ ] Corrección de errores y formato
  - [ ] Verificación de referencias
- [ ] **Entrega final**
  - [ ] Código completo documentado
  - [ ] Memoria TFM finalizada
  - [ ] Materiales de presentación

**Entregables Mes 5:**
- ✅ Memoria TFM completa (80-120 páginas)
- ✅ Presentación para defensa
- ✅ Código fuente completo y documentado
- ✅ Dataset y resultados experimentales

## 🛠️ Stack Tecnológico

### Modelos de Segmentación
- **MaskDINO:** Para detección y segmentación de instancias
- **SAM 2.0:** Segment Anything Model v2
- **BodyPix:** Modelo especializado en segmentación de personas
- **YOLOv8-seg:** YOLO v8 con capacidades de segmentación

### Vision Language Models
- **GPT-4V:** Para análisis compositivo avanzado
- **LLaVa:** Debo valorar esta opción

### Herramientas de Desarrollo
- **Python 3.8+:** Lenguaje principal
- **PyTorch:** Framework de deep learning
- **OpenCV:** Procesamiento de imágenes
- **Matplotlib/Plotly:** Visualización de resultados
- **Jupyter Notebooks:** Experimentación y análisis
- **Git/GitHub:** Control de versiones

## 💰 Presupuesto Estimado

### Recursos Computacionales
- **GPU Computing:** €400-600 (RTX 4090, 3h/día × 4 meses)
- **Cloud Storage:** Drive de UOC

### APIs y Servicios
- **VLM API Calls:** €100-150 (estimado 1000-2000 llamadas)

**Total Estimado:** €600-750

## 📊 Criterios de Éxito

### Técnicos
- [ ] Pipeline de evaluación reproducible funcionando
- [ ] Benchmark completo de 4 modelos ejecutado
- [ ] Métricas especializadas validadas
- [ ] Demo VLM integration funcional

### Académicos
- [ ] Análisis comparativo riguroso documentado
- [ ] Contribución metodológica en métricas
- [ ] Proof of concept de viabilidad comercial
- [ ] Memoria TFM de calidad académica

### Impacto
- [ ] Código open source disponible
- [ ] Dataset benchmark para la comunidad
- [ ] Framework replicable para futuras investigaciones

## ⚠️ Riesgos y Mitigaciones

### Riesgos Técnicos
- **Problemas de compatibilidad entre modelos**
  - *Mitigación:* Testing temprano y entornos virtuales separados
- **Limitaciones computacionales**
  - *Mitigación:* Optimización de batch size y uso de cloud computing si necesario
- **Calidad de APIs VLM**
  - *Mitigación:* Testing de múltiples proveedores y fallbacks

### Riesgos de Timeline
- **Retrasos en implementación**
  - *Mitigación:* Buffers de tiempo y priorización de objetivos core
- **Complejidad subestimada**
  - *Mitigación:* Approach iterativo y scope ajustable

## 📝 Notas de Implementación

### Setup Inicial
1. Configurar entorno conda con Python 3.8+
2. Instalar CUDA y drivers GPU
3. Clonar repositorios de modelos base
4. Configurar APIs de VLM

### Estructura de Proyecto
```
tfm-segmentation-benchmark/
├── 📁 src/
│   ├── 📁 models/                    # Implementaciones de modelos
│   │   ├── 📁 maskdino/             # MaskDINO específico
│   │   │   ├── __init__.py
│   │   │   ├── config.py            # Configuración MaskDINO
│   │   │   ├── model.py             # Wrapper del modelo
│   │   │   ├── predictor.py         # Predicción específica
│   │   │   ├── requirements.txt     # Deps específicas MaskDINO
│   │   │   └── test_maskdino.py     # Tests unitarios
│   │   ├── 📁 sam2/                 # SAM 2.0 específico
│   │   │   ├── __init__.py
│   │   │   ├── config.py
│   │   │   ├── model.py
│   │   │   ├── predictor.py
│   │   │   ├── requirements.txt
│   │   │   └── test_sam2.py
│   │   ├── 📁 bodypix/              # BodyPix específico
│   │   │   ├── __init__.py
│   │   │   ├── config.py
│   │   │   ├── model.py
│   │   │   ├── predictor.py
│   │   │   ├── requirements.txt
│   │   │   └── test_bodypix.py
│   │   ├── 📁 yolov8/               # YOLOv8-seg específico
│   │   │   ├── __init__.py
│   │   │   ├── config.py
│   │   │   ├── model.py
│   │   │   ├── predictor.py
│   │   │   ├── requirements.txt
│   │   │   └── test_yolov8.py
│   │   ├── base_model.py            # Interfaz común
│   │   └── model_factory.py         # Factory pattern
│   ├── 📁 evaluation/               # Framework de evaluación
│   │   ├── __init__.py
│   │   ├── evaluator.py            # Evaluador principal
│   │   ├── benchmark.py            # Sistema de benchmark
│   │   ├── comparator.py           # Comparación entre modelos
│   │   └── reporters.py            # Generación de reportes
│   ├── 📁 metrics/                  # Métricas especializadas
│   │   ├── __init__.py
│   │   ├── segmentation_metrics.py # IoU, Dice, etc.
│   │   ├── photography_metrics.py  # Métricas para fotografía
│   │   ├── edge_quality.py         # Calidad de bordes
│   │   └── human_correlation.py    # Correlación con evaluación humana
│   ├── 📁 vlm_integration/          # Demo VLM
│   │   ├── __init__.py
│   │   ├── llava_integration.py    # Integración LLaVA
│   │   ├── prompt_engineering.py   # Prompts optimizados
│   │   ├── recommendation_engine.py # Motor de recomendaciones
│   │   └── demo_interface.py       # Interface del demo
│   └── 📁 utils/                    # Utilidades
│       ├── __init__.py
│       ├── data_loader.py          # Carga de datos
│       ├── visualization.py        # Visualización
│       ├── logger.py               # Sistema de logging
│       ├── config_manager.py       # Gestión de configuraciones
│       └── gpu_utils.py            # Utilidades GPU
├── 📁 configs/                      # Configuraciones centralizadas
│   ├── 📁 models/                   # Configs por modelo
│   │   ├── maskdino_config.yaml
│   │   ├── sam2_config.yaml
│   │   ├── bodypix_config.yaml
│   │   └── yolov8_config.yaml
│   ├── 📁 experiments/              # Configs de experimentos
│   │   ├── benchmark_full.yaml     # Benchmark completo
│   │   ├── quick_test.yaml         # Test rápido
│   │   └── ablation_study.yaml     # Estudios de ablación
│   └── main_config.yaml            # Configuración principal
├── 📁 data/
│   ├── 📁 raw/                      # Imágenes originales
│   │   ├── 📁 portraits/           # Retratos
│   │   ├── 📁 outdoor/             # Exteriores
│   │   ├── 📁 group_photos/        # Fotos grupales
│   │   └── 📁 challenging/         # Casos difíciles
│   ├── 📁 processed/                # Datos procesados
│   │   ├── 📁 resized/             # Imágenes redimensionadas
│   │   ├── 📁 normalized/          # Normalizadas
│   │   └── 📁 augmented/           # Data augmentation
│   ├── 📁 annotations/              # Ground truth
│   │   ├── 📁 masks/               # Máscaras de segmentación
│   │   ├── 📁 bboxes/              # Bounding boxes
│   │   └── metadata.json          # Metadatos de imágenes
│   └── dataset_info.yaml           # Información del dataset
├── 📁 experiments/                  # Resultados de experimentos
│   ├── 📁 maskdino/                # Resultados MaskDINO
│   │   ├── 📁 2025-06-15_run1/     # Experimento específico
│   │   └── 📁 2025-06-16_run2/
│   ├── 📁 sam2/                    # Resultados SAM 2.0
│   ├── 📁 bodypix/                 # Resultados BodyPix
│   ├── 📁 yolov8/                  # Resultados YOLOv8
│   └── 📁 comparative/             # Análisis comparativos
│       ├── 📁 speed_comparison/
│       ├── 📁 accuracy_comparison/
│       └── 📁 final_benchmark/
├── 📁 notebooks/                    # Jupyter notebooks
│   ├── 📁 exploration/             # Exploración de datos
│   │   ├── 01_data_exploration.ipynb
│   │   └── 02_image_analysis.ipynb
│   ├── 📁 model_testing/           # Testing de modelos
│   │   ├── 01_maskdino_test.ipynb
│   │   ├── 02_sam2_test.ipynb
│   │   ├── 03_bodypix_test.ipynb
│   │   └── 04_yolov8_test.ipynb
│   ├── 📁 evaluation/              # Análisis de resultados
│   │   ├── 01_metrics_analysis.ipynb
│   │   ├── 02_comparative_analysis.ipynb
│   │   └── 03_visualization.ipynb
│   └── 📁 vlm_demo/               # Demo VLM
│       └── 01_llava_integration.ipynb
├── 📁 scripts/                      # Scripts de automatización
│   ├── setup_models.py            # Setup automático de modelos
│   ├── run_benchmark.py           # Ejecutar benchmark
│   ├── download_data.py           # Descargar datasets
│   ├── process_results.py         # Procesar resultados
│   └── generate_report.py         # Generar reporte final
├── 📁 tests/                       # Tests unitarios
│   ├── 📁 unit/                    # Tests unitarios
│   ├── 📁 integration/             # Tests de integración
│   └── 📁 performance/             # Tests de rendimiento
├── 📁 docs/                        # Documentación
│   ├── 📁 setup/                   # Guías de instalación
│   ├── 📁 models/                  # Documentación de modelos
│   ├── 📁 api/                     # Documentación API
│   └── methodology.md             # Metodología del TFM
├── 📁 requirements/                # Gestión de dependencias
│   ├── base.txt                   # Dependencias base
│   ├── maskdino.txt              # Específicas MaskDINO
│   ├── sam2.txt                  # Específicas SAM 2.0
│   ├── bodypix.txt               # Específicas BodyPix
│   ├── yolov8.txt                # Específicas YOLOv8
│   ├── llava.txt                 # Específicas LLaVA
│   ├── dev.txt                   # Desarrollo
│   └── gpu.txt                   # GPU/CUDA
├── 📁 docker/                      # Containerización
│   ├── Dockerfile.base           # Base image
│   ├── Dockerfile.maskdino       # MaskDINO specific
│   ├── Dockerfile.gpu            # GPU version
│   └── docker-compose.yml        # Orquestación
├── .gitignore                      # Git ignore
├── .pre-commit-config.yaml        # Pre-commit hooks
├── pyproject.toml                 # Configuración del proyecto
├── setup.py                       # Instalación del paquete
└── README.md                      # Documentación principal
```

