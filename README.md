# Clasificación de Señales EEG para Imaginación Motora

Proyecto de clasificación binaria de señales electroencefalográficas (EEG) para tareas de imaginación motora (Motor Imagery) mediante técnicas de aprendizaje automático clásico y deep learning con transfer learning.

## Descripción del Proyecto

Este proyecto implementa y compara diferentes métodos para clasificar señales EEG correspondientes a la imaginación de movimiento de la mano izquierda vs. derecha:

1. **Análisis Exploratorio de Datos (EDA)**: Caracterización completa del dataset
2. **CSP-SVM**: Método clásico basado en Common Spatial Patterns y Support Vector Machines
3. **Transfer Learning Multi-Sujeto**: Red neuronal CNN-LSTM con pre-entrenamiento multi-sujeto y fine-tuning progresivo

## Documentos y Recursos

### Documentos PDF

- **`INFORME_PROYECTO.pdf`**: Informe ejecutivo completo del proyecto
- **`ENTREGA1.pdf`**: Documento de entrega del proyecto

### Video Demostrativo

- **Video en YouTube**: [URL Video](https://youtu.be/g61bGnO3-uM?si=avNTL-X947_bTu-g)

## Estructura del Proyecto

```
eeg-mi-deep-learning/
├── 01 - Análisis Exploratorio de Datos (EDA).ipynb
├── 02 - CSP-SVM.ipynb
├── 03 - Transfer Learning Multi-Sujeto.ipynb
├── INFORME_PROYECTO.pdf    # Informe ejecutivo del proyecto
├── ENTREGA1.pdf            # Documento de entrega
├── data/
│   ├── left_imag/          # Archivos EEG de imaginación izquierda (20 sujetos)
│   └── right_imag/          # Archivos EEG de imaginación derecha (mismos 20 sujetos)
├── results/                 # Resultados y visualizaciones generadas
├── models/                  # Modelos entrenados guardados
├── requirements.txt         # Dependencias para uso local
└── README.md               
```

## Ejecución en Google Colab (Recomendado)

Los notebooks están diseñados para ejecutarse directamente en Google Colab. Colab ya incluye todas las dependencias necesarias preinstaladas.

### Pasos para ejecutar en Colab:

1. **Subir los notebooks a Google Colab**:
   - Abre [Google Colab](https://colab.research.google.com/)
   - Sube los notebooks desde tu repositorio local o desde Google Drive

2. **Subir los datos**:
   - Los notebooks incluyen funciones para descargar automáticamente los datos desde Google Drive
   - Si prefieres subir manualmente, organiza los datos en la estructura:
     ```
     data/
     ├── left_imag/
     └── right_imag/
     ```
   - Luego sube la carpeta `data/` a Colab

3. **Ejecutar los notebooks en orden**:
   - **Notebook 01**: Análisis Exploratorio de Datos
   - **Notebook 02**: CSP-SVM
   - **Notebook 03**: Transfer Learning Multi-Sujeto

### Configuración de Transfer Learning

En el **Notebook 03 (Transfer Learning Multi-Sujeto)**, puedes configurar cuántos sujetos procesar:

- **Por defecto**: `MAX_SUBJECTS = 2` (modo prueba rápida)
- **Para ejecución completa**: Cambia a `MAX_SUBJECTS = None` para procesar los 20 sujetos

Esta configuración permite realizar pruebas rápidas antes de ejecutar el proceso completo que puede tomar varias horas.

## Ejecución Local

Si prefieres ejecutar los notebooks localmente, sigue estos pasos:

### Requisitos del Sistema

- **Python**: 3.11.10 (o compatible con 3.9-3.11)
  - TensorFlow requiere Python 3.9-3.11
  - Para Python 3.12+, se recomienda usar Google Colab

### Instalación

1. **Clonar o descargar el repositorio**:
   ```bash
   git clone <url-del-repositorio>
   cd eeg-mi-deep-learning
   ```

2. **Crear un entorno virtual (recomendado)**:
   ```bash
   python3.11 -m venv venv
   source venv/bin/activate  # En Windows: venv\Scripts\activate
   ```

3. **Instalar dependencias**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Instalar Jupyter** (si no está instalado):
   ```bash
   pip install jupyter notebook
   ```

5. **Iniciar Jupyter Notebook**:
   ```bash
   jupyter notebook
   ```

6. **Ejecutar los notebooks en orden**:
   - Abre y ejecuta `01 - Análisis Exploratorio de Datos (EDA).ipynb`
   - Luego `02 - CSP-SVM.ipynb`
   - Finalmente `03 - Transfer Learning Multi-Sujeto.ipynb`

### Nota sobre requirements.txt

El archivo `requirements.txt` es **solo para uso local**. En Google Colab no es necesario instalarlo ya que todas las dependencias están preinstaladas.

## Datos

### Fuente de Datos

Los datos están disponibles en Google Drive:
- **URL**: https://drive.google.com/drive/folders/1aWFshMYbSlhPTZbLKldJ2Rbv7JZVYwrW

### Estructura de Datos

- **20 sujetos únicos** (S001 a S020)
- Cada sujeto tiene datos de ambas clases:
  - `data/left_imag/SXXX_Task2_PREP_Left.set` → 11 trials de imaginación izquierda
  - `data/right_imag/SXXX_Task2_PREP_Right.set` → 11 trials de imaginación derecha
- **Total**: 440 trials (20 sujetos × 22 trials por sujeto)
- **Formato**: Archivos EEGLAB (.set)

### Descarga Automática

Los notebooks incluyen funciones para descargar automáticamente los datos desde Google Drive si no están presentes localmente.

## Características del Dataset

- **Sujetos**: 20 únicos
- **Trials por sujeto**: 22 (11 izquierda + 11 derecha)
- **Canales EEG**: 64
- **Frecuencia de muestreo**: 128 Hz
- **Duración por trial**: 9 segundos (1152 muestras)
- **Balance de clases**: 50% / 50%

## Resultados

Los resultados se guardan automáticamente en la carpeta `results/`:

- **EDA**: Gráficos y estadísticas descriptivas
- **CSP-SVM**: Modelo entrenado y métricas de evaluación
- **Transfer Learning**: Resultados por sujeto y métricas promedio

## Dependencias Principales

### Para uso local (ver requirements.txt):

- `mne>=1.4.0`: Procesamiento de señales EEG
- `scikit-learn>=1.3.0`: Machine learning clásico
- `tensorflow>=2.15.0`: Deep learning
- `numpy>=1.24.0`, `pandas>=2.0.0`: Análisis de datos
- `matplotlib>=3.7.0`, `seaborn>=0.12.0`: Visualización
- `gdown>=4.7.0`: Descarga de Google Drive
## Tiempos de Ejecución Estimados

- **Notebook 01 (EDA)**: ~5-10 minutos
- **Notebook 02 (CSP-SVM)**: ~1-2 minutos
- **Notebook 03 (Transfer Learning)**:
  - Modo prueba (2 sujetos, `MAX_SUBJECTS = 2`): ~10-30 minutos
  - Modo completo (20 sujetos, `MAX_SUBJECTS = None`): ~1-2 horas

## Notas Importantes

- Los notebooks deben ejecutarse en orden (01 → 02 → 03)
- Para mejor rendimiento en Transfer Learning, se recomienda usar GPU en Colab

