# Análisis Comparativo de Algoritmos de Machine Learning
## Clasificación de Flechas Direccionales en Imágenes 8×8
ESTE ARCHIVO NO ES EL ARCHIVO ENTREGABLE, SOLO ES UN README INFORMATIVO

[![Python](https://img.shields.io/badge/Python-3.13-blue.svg)](https://python.org)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.20.0-orange.svg)](https://tensorflow.org)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.7.2-green.svg)](https://scikit-learn.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Lab-red.svg)](https://jupyter.org)

---

## 👥 Integrantes del Equipo

- **Abraham Ceballos Rodriguez**
- **Seuma Rayo Sauna** 
- **Sebastian Botia**
- **Juan Agamez**

---

## 📋 Resumen del Proyecto

Este proyecto presenta un **estudio experimental exhaustivo** sobre la clasificación de flechas direccionales en imágenes de baja resolución (8×8 píxeles). El objetivo principal es **comparar la efectividad** de diferentes algoritmos de machine learning en la tarea de clasificación multiclase de patrones visuales simples.

### 🎯 Problema de Investigación

Clasificar imágenes de flechas direccionales en **cuatro categorías**:
- ⬆️ **up** (arriba)
- ⬅️ **left** (izquierda)  
- ⬇️ **down** (abajo)
- ➡️ **right** (derecha)

Utilizando únicamente información de píxeles en escala de grises de imágenes de **8×8**.

---

## 🔬 Metodología Experimental

### Algoritmos Evaluados

El estudio implementa **cinco enfoques algorítmicos distintos**:

| Algoritmo | Descripción | Tipo |
|-----------|-------------|------|
| **Regresión Logística** | Modelo lineal con regularización | Lineal |
| **Árboles de Decisión** | Particionamiento recursivo del espacio | Basado en reglas |
| **Random Forest** | Ensemble de árboles con bootstrap | Ensemble |
| **Perceptrón Multicapa (MLP)** | Redes neuronales feed-forward | Red Neuronal |
| **DNN (TensorFlow/Keras)** | Redes neuronales profundas | Deep Learning |

### 🎛️ Optimización de Hiperparámetros

- **Método**: GridSearchCV con validación cruzada estratificada (k=5)
- **Espacios de búsqueda**: Específicamente diseñados para cada algoritmo
- **Evaluación**: Conjunto de prueba independiente

### 📊 Métricas de Evaluación

- **Accuracy** - Precisión general del modelo
- **F1-Score** - Media armónica entre precisión y recall  
- **Precision** - Proporción de predicciones positivas correctas
- **Recall** - Proporción de casos positivos identificados correctamente

---

## 📁 Estructura del Proyecto

```
Arrows8MLP/
├── arrows8.ipynb              # Notebook principal con experimentos
├── arrows8_keras_format.npz   # Dataset de flechas 8x8
├── requirements.txt           # Dependencias del proyecto
├── README.md                 # Documentación del proyecto
└── arrows8_env/              # Entorno virtual (no incluido en repo)
```

---

## 🚀 Instalación y Uso

### Prerrequisitos

- Python 3.13 o superior
- Git

### 1. Clonar el Repositorio

```bash
git clone https://github.com/Sebatianbotia/Arrows8MLP.git
cd Arrows8MLP
```

### 2. Crear y Activar Entorno Virtual

```bash
# Crear entorno virtual
python -m venv arrows8_env

# Activar entorno (Windows)
.\arrows8_env\Scripts\Activate.ps1

# Activar entorno (Linux/Mac)
source arrows8_env/bin/activate
```

### 3. Instalar Dependencias

```bash
pip install -r requirements.txt
```

### 4. Ejecutar el Notebook

```bash
# Iniciar Jupyter Lab
jupyter lab

# Abrir arrows8.ipynb y ejecutar celdas secuencialmente
```

---

## 📊 Dataset

### Características del Dataset

- **Formato**: Archivos NPZ (NumPy compressed)
- **Tamaño de imagen**: 8×8 píxeles
- **Canales**: Escala de grises (1 canal)
- **Clases**: 4 direcciones de flechas
- **Total de muestras**: 12,391 imágenes

### División del Dataset

| Conjunto | Muestras | Propósito |
|----------|----------|-----------|
| **Entrenamiento** | ~4,274 | Entrenamiento de modelos |
| **Validación** | ~4,058 | Optimización de hiperparámetros |
| **Prueba** | ~4,059 | Evaluación final |

### Análisis de Calidad

✅ **Sin valores faltantes (NaN)**  
✅ **Sin valores infinitos**  
✅ **Datos normalizados** en rango [0,1]  
✅ **Dataset balanceado** entre clases  
✅ **Correlación espacial** entre píxeles vecinos  

---

## 🏆 Resultados Esperados

### Rendimiento Típico

Todos los modelos evaluados muestran **excelente capacidad de generalización** (accuracy > 95%) en este problema de clasificación de patrones visuales simples.

### Observaciones Clave

- **GridSearchCV** resulta en mejoras consistentes sobre configuraciones por defecto
- **Métodos ensemble** (Random Forest) tienden a mostrar mayor robustez
- **Redes neuronales** requieren mayor tiempo de entrenamiento pero logran alta precisión
- **Optimización automática** de hiperparámetros es fundamental para el rendimiento

### Tiempo de Ejecución Estimado

| Fase | Tiempo Estimado |
|------|----------------|
| **Análisis exploratorio** | 5-10 minutos |
| **Preprocesamiento** | 2-3 minutos |
| **Experimentos ML** | 60-90 minutos |
| **Análisis de resultados** | 3-5 minutos |

---

## 🛠️ Dependencias Principales

### Machine Learning
- `scikit-learn==1.7.2` - Algoritmos de ML tradicionales
- `tensorflow==2.20.0` - Deep Learning
- `keras==3.12.0` - Interface de alto nivel para TensorFlow

### Análisis de Datos
- `numpy==2.3.4` - Computación numérica
- `pandas==2.3.3` - Manipulación de datos
- `matplotlib==3.10.7` - Visualización
- `seaborn==0.13.2` - Visualización estadística

### Entorno de Desarrollo
- `jupyter==1.1.1` - Notebooks interactivos
- `jupyterlab==4.4.10` - IDE para notebooks
- `ipykernel==7.1.0` - Kernel de Python

---

## 📈 Flujo de Trabajo

### 1. Exploración de Datos
- Carga del dataset NPZ
- Visualización de muestras
- Análisis de distribución de clases
- Matriz de correlación entre píxeles

### 2. Preprocesamiento
- Verificación de tipos de datos
- One-hot encoding de etiquetas
- Vectorización para algoritmos clásicos
- División en conjuntos de entrenamiento y prueba

### 3. Experimentación
- Configuración de espacios de hiperparámetros
- Validación cruzada estratificada
- Optimización con GridSearchCV
- Evaluación en conjunto de prueba

### 4. Análisis de Resultados
- Comparación de métricas
- Visualización de rendimiento
- Matrices de confusión
- Ranking de algoritmos

---

## 🤝 Contribución

Para contribuir al proyecto:

1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit tus cambios (`git commit -am 'Agregar nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Crea un Pull Request

---

## 📄 Licencia

Este proyecto es de uso académico y está disponible bajo la licencia MIT.

---

## 🔗 Referencias

- [Scikit-learn Documentation](https://scikit-learn.org/stable/)
- [TensorFlow Documentation](https://www.tensorflow.org/)
- [Jupyter Documentation](https://jupyter.org/documentation)
- [NumPy Documentation](https://numpy.org/doc/)



*Proyecto desarrollado como parte de un estudio académico sobre algoritmos de Machine Learning y clasificación de imágenes.*