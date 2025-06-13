# Clasificación de Radiografías de Tórax con Redes Neuronales

Este repositorio contiene un proyecto de Machine Learning enfocado en la **clasificación automática de radiografías de tórax** utilizando redes neuronales convolucionales (CNN) y modelos de **Transfer Learning** (VGG16 y ResNet50). El objetivo es comparar el rendimiento de tres enfoques distintos en la clasificación de imágenes médicas en cuatro categorías: **COVID-19, pulmones sanos, opacidad pulmonar y neumonía viral**.

> 📄 El proyecto incluye un **paper académico en formato IEEE** (en español), donde se explica el desarrollo completo del proyecto, disponible en este repositorio: [`paper/cnn_transfer_learning_chestxray_ieee.pdf`](./paper/cnn_transfer_learning_chestxray_ieee.pdf)

---

## 📊 Dataset

Se utilizó el [COVID-19 Radiography Dataset](https://www.kaggle.com/datasets/tawsifurrahman/covid19-radiography-database) disponible en Kaggle, que incluye:

- Total de **21,165 imágenes de rayos X**
- 4 clases: COVID-19, pulmones sanos, opacidad pulmonar y neumonía viral
- Imágenes redimensionadas a **64×64 píxeles** para facilitar el procesamiento

---

## ⚙️ Metodología

### 1. División de los datos
- **Entrenamiento:** 80%
- **Validación:** 20%
- División estratificada para balancear clases.

### 2. Preprocesamiento
- **Data augmentation:** rotaciones, desplazamientos, zoom, volteo horizontal
- **Normalización:** escala de los píxeles al rango `[0, 1]`

### 3. Modelos implementados

| Modelo              | Descripción |
|---------------------|-------------|
| CNN Personalizada   | Arquitectura con 3 capas convolucionales, max pooling y average pooling. |
| VGG16 (Transfer Learning) | Se congelaron los últimos 15 pesos; capas superiores adaptadas. |
| ResNet50 (Transfer Learning) | Similar a VGG16, con skip connections para redes profundas. |

### 4. Entrenamiento
- Optimizador: **Adam**
- Learning rate: `0.0001`
- Función de pérdida: `categorical_crossentropy`
- Epochs: `10`
- Batch size: `32`
- Métricas: Accuracy, Precision, Recall y F1-score

---

## 📈 Resultados

| Modelo              | Accuracy | Precision | Recall | F1-score |
|---------------------|----------|-----------|--------|----------|
| **ResNet50**        | 0.91     | 0.90      | 0.91   | 0.91     |
| VGG16               | 0.88     | 0.89      | 0.86   | 0.88     |
| CNN Personalizada   | 0.76     | 0.78      | 0.73   | 0.74     |

- ResNet50 obtuvo el mejor rendimiento general.
- VGG16 fue competitivo, con menor complejidad computacional.
- La CNN personalizada fue menos precisa, pero ofrece una base adaptable para mejoras futuras.

---

## 📘 Paper

El archivo [`paper/cnn_transfer_learning_chestxray_ieee.pdf`](./paper/cnn_transfer_learning_chestxray_ieee.pdf) explica en detalle el problema, la metodología, visualizaciones y análisis comparativo entre modelos.
- **Idioma:** Español
- **Formato:** IEEE

## Conclusiones
- Los modelos preentrenados, como ResNet50 y VGG16, son altamente efectivos para tareas de clasificación médica.
- Aumentar la resolución de entrada o aplicar técnicas de balanceo de clases podría mejorar aún más el rendimiento.
- Este trabajo demuestra la aplicabilidad de la IA en el diagnóstico por imágenes médicas, ofreciendo un punto de partida sólido para futuras investigaciones.

  
## 👥 Autores

Este proyecto fue desarrollado por:

- **Marlon Daniel Mora Restrepo**
- **Martín Correa Valencia**

