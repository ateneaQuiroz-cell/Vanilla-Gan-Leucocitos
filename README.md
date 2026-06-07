# Generación de imágenes de Leucocitos con Vanilla GAN

Implementación de una Vanilla GAN en TensorFlow/Keras para generar imágenes sintéticas de leucocitos entrenada sobre el dataset BCCD. Este proyecto se enfoca exclusivamente en la **generación de imágenes**, no en la clasificación.

## Justificación

El conteo manual de glóbulos blancos es un proceso lento, costoso y propenso a errores humanos. Los modelos de deep learning pueden automatizar esta tarea, pero requieren grandes volúmenes de datos etiquetados. El dataset BCCD cuenta con apenas **364 imágenes** y un desbalance de hasta **10:1** entre clases, lo que dificulta el entrenamiento de clasificadores robustos.

Este proyecto propone el uso de una **Generative Adversarial Network (GAN)** para generar imágenes sintéticas de leucocitos que puedan utilizarse como datos de augmentación, sentando la base para futuros clasificadores automáticos.

---

## Dataset

Se utilizó el **BCCD Dataset** (Blood Cell Count and Detection), un dataset público de imágenes de frotis sanguíneo.

| Tipo | Imágenes |
|------|----------|
| Neutrófilos | 215 |
| Eosinófilos | 94 |
| Linfocitos | 37 |
| Monocitos | 23 |
| **Total** | **373** |

Para este proyecto se trabajó con leucocitos como clase general (WBC), sin distinguir subtipos.

**Fuentes:**
- https://github.com/Shenggan/BCCD_Dataset
- https://www.kaggle.com/datasets/paultimothymooney/blood-cells

---

## Arquitectura
## Preprocesamiento

1. Organización de imágenes por clase usando `bccd_labels.csv`
2. Conversión a RGB (3 canales)
3. Redimensionado a 64×64 px
4. Normalización: `(pixel - 127.5) / 127.5` → rango [-1, 1]

### Generador
Transforma un vector de ruido aleatorio en una imagen de 64×64×3.

### Discriminador
Clasificador binario que distingue imágenes reales de generadas.

