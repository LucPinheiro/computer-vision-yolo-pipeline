# 👁️ Computer Vision YOLO Pipeline

![Python](https://shields.io)
![Ultralytics YOLO](https://shields.io)
![OpenCV](https://shields.io)
![Roboflow](https://shields.io)

Pipeline modular de **Visión Artificial (Computer Vision)** para la detección, seguimiento y conteo de objetos en tiempo real. Este repositorio cubre el ciclo de vida completo de un sistema de visión por computador: gestión y versionado de datos con **Roboflow**, entrenamiento de modelos personalizados con **Ultralytics YOLO** e inferencia de baja latencia con **OpenCV**.

---

## 🏗️ Arquitectura del Pipeline

```text
┌─────────────────┐      ┌──────────────────────┐      ┌─────────────────────────┐
│    ROBOFLOW     │      │   ULTRALYTICS YOLO   │      │         OPENCV          │
│                 │      │                      │      │                         │
│ • Etiquetado    │ ───► │ • Transfer Learning  │ ───► │ • Captura de vídeo      │
│ • Augmentation  │      │ • Entrenamiento      │      │ • Inferencia en vivo    │
│ • Versionado    │      │ • Exportación (.pt)  │      │ • Conteo y alertas      │
└─────────────────┘      └──────────────────────┘      └─────────────────────────┘
```

---

## 🚀 Casos de Uso Incluidos (`use_cases/`)

Además del flujo base de entrenamiento, este repositorio incluye **3 implementaciones prácticas** orientadas a entornos reales de industria, logística e IoT:

| Proyecto | Script | Descripción |
| :--- | :--- | :--- |
| **1. Monitor de Seguridad Industrial (EPP)** | `use_cases/01_ppe_safety_monitor.py` | Detecta en tiempo real si el personal lleva casco y chaleco reflectante, generando alertas visuales ante incumplimientos. |
| **2. Contador Automático de Inventario** | `use_cases/02_inventory_line_counter.py` | Traza una línea virtual sobre el flujo de vídeo y contabiliza productos o cajas en movimiento (preparado para envío vía Webhook a ERP/Odoo). |
| **3. Detección en Flujo Edge / ESP32-CAM** | `use_cases/03_edge_stream_detector.py` | Conecta el motor de inferencia YOLO a cámaras IP / flujos HTTP (como **ESP32-CAM**) optimizando latencia y monitorizando FPS en pantalla. |

---

## 📁 Estructura del Repositorio

```text
computer-vision-yolo-pipeline/
├── data/                               # Datasets descargados desde Roboflow (ignorado en Git)
├── models/                             # Pesos entrenados .pt / .onnx (ignorado en Git)
├── notebooks/                          # Experimentación y análisis exploratorio (Jupyter)
├── src/                                # Core del pipeline
│   ├── download_data.py                # Descarga automatizada de datasets vía API de Roboflow
│   ├── train.py                        # Entrenamiento y validación con Ultralytics YOLO
│   └── inference.py                    # Motor base de detección en tiempo real con OpenCV
├── use_cases/                          # Aplicaciones prácticas listas para ejecutar
│   ├── 01_ppe_safety_monitor.py        # Detección de Equipos de Protección Individual
│   ├── 02_inventory_line_counter.py    # Conteo por cruce de línea virtual
│   └── 03_edge_stream_detector.py      # Inferencia sobre streaming IP / ESP32-CAM
├── .env.example                        # Plantilla de variables de entorno
├── .gitignore                          # Exclusión de archivos pesados y credenciales
├── requirements.txt                    # Dependencias del proyecto
└── README.md                           # Documentación del proyecto
```

---

## ⚙️ Instalación y Configuración

### 1. Clonar el repositorio
```bash
git clone https://github.com
cd computer-vision-yolo-pipeline
```

### 2. Crear entorno virtual e instalar dependencias
```bash
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Configurar credenciales de Roboflow
Crea tu archivo `.env` a partir de la plantilla y añade tu clave privada:
```bash
cp .env.example .env
```
```env
ROBOFLOW_API_KEY=tu_clave_privada_de_roboflow
```

---

## ▶️ Ejecución Rápida

1. **Descargar dataset desde Roboflow:**
   ```bash
   python src/download_data.py
   ```
2. **Entrenar modelo personalizado:**
   ```bash
   python src/train.py
   ```
3. **Ejecutar inferencia base o un caso de uso:**
   ```bash
   python src/inference.py
   # O ejecutar un caso de uso específico:
   python use_cases/02_inventory_line_counter.py
   ```
   *(Pulsa `q` en la ventana de vídeo para detener la ejecución).*

---

## 📊 Rendimiento de Referencia

| Modelo Base | Resolución | Velocidad Estimada | Formatos Soportados |
| :--- | :---: | :---: | :---: |
| `YOLO11n` (Nano) | `640x640` | 45 – 120 FPS | `.pt`, `.onnx`, `TensorRT` |

---

## 🔮 Próximas Mejoras (Roadmap)
- [ ] Exportación automática a **ONNX** para inferencia ligera en CPU y dispositivos Edge.
- [ ] Integración directa mediante **REST API / Webhook** para registrar conteos de stock en **Odoo**.
- [ ] Panel de métricas y registro de eventos en tiempo real.

---

## 👩‍💻 Autora

**Luciana Pinheiro** — *Data, Machine Learning, IA y Automatización*  
🌐 Descubre más proyectos de Data, IA, Odoo e IoT en mi portafolio web.
