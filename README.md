# 🫁 LUNA25: Análisis de Malignidad en Nódulos Pulmonares

Este repositorio contiene el desarrollo de un sistema de diagnóstico asistido por computadora (CAD) para la clasificación de riesgo de malignidad en nódulos pulmonares, utilizando el benchmark **LUNA25** y técnicas de **Deep Learning 3D**.

## 🎯 Objetivos del Proyecto
- **Preprocesamiento Médico:** Implementación de *Windowing* pulmonar (-1000 a 400 HU) y normalización de tensores.
- **Segmentación de ROI:** Aislamiento volumétrico de nódulos para reducir el ruido anatómico (vasos, pleura).
- **Clasificación 3D:** Entrenamiento de modelos basados en **MONAI** (3D-UNet / Vision Transformers) para estimación de malignidad.

## 💻 Stack Tecnológico
| Tecnología | Uso |
| :--- | :--- |
| **Python 3.10** | Lenguaje principal |
| **PyTorch** | Framework de Deep Learning |
| **MONAI** | Librería especializada en IA Médica |
| **SimpleITK** | Procesamiento de imágenes DICOM/MHA |
| **WSL2 (Ubuntu)** | Entorno de desarrollo Linux |
| **NVIDIA CUDA** | Aceleración por GPU (RTX 4060) |

## 📊 Metodología (Pipeline)
1. **Data Ingestion:** Descarga y verificación de los 221GB del dataset LUNA25 vía Zenodo.
2. **Preprocessing:** Aplicación de filtros de densidad (Unidades Hounsfield) y remuestreo espacial.
3. **Training:** Optimización de hiperparámetros para maximizar el **AUC-ROC** y la **Sensibilidad**.
4. **Validation:** Evaluación con métricas clínicas estándar.

## 🛠️ Instalación y Configuración
```bash
# Crear entorno
conda create -n LUNA25 python=3.10 -y
conda activate LUNA25

# Instalar dependencias
pip install torch monai[all] simpleitk pandas matplotlib scikit-learn zenodo-get