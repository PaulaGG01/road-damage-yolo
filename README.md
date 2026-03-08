# Detección automática de daños en pavimentos con YOLO

![Detección del modelo](images/detección_modelo.jpg)

## 1. Introducción

El deterioro de pavimentos urbanos representa uno de los principales desafíos para la gestión de infraestructura vial en ciudades y redes de transporte. Problemas como grietas, baches y deformaciones del asfalto afectan la seguridad vial, aumentan los costos de mantenimiento y reducen la vida útil de la infraestructura.

Actualmente, muchas inspecciones de pavimentos se realizan mediante evaluaciones visuales manuales realizadas por técnicos en terreno. Este proceso puede ser lento, costoso y susceptible a variaciones en los criterios de evaluación.

En este contexto, la **visión por computador** y el **aprendizaje profundo** permiten desarrollar sistemas automatizados capaces de detectar daños en pavimentos a partir de imágenes, facilitando procesos de monitoreo, inspección y priorización de mantenimiento.

Este proyecto desarrolla un **prototipo de detección automática de daños en pavimentos utilizando el modelo YOLO**, aplicado a imágenes de carreteras y vías urbanas.

---

# 2. Definición del problema AECO

El proyecto aborda el siguiente problema dentro del sector **AECO (Architecture, Engineering, Construction & Operations)**:

**Problema**

Identificar automáticamente daños visibles en pavimentos mediante análisis de imágenes utilizando modelos de visión computacional.

**Contexto**

La detección temprana de deterioro en carreteras permite mejorar la planificación de mantenimiento, optimizar recursos y aumentar la seguridad vial.

**Usuario potencial**

- Municipios
- Departamentos de infraestructura
- Empresas de mantenimiento vial
- Concesionarias de carreteras

**Clases detectadas**

El modelo identifica daños en pavimentos agrupados en la clase:

- `damage`

La categoría incluye ejemplos de:

- grietas longitudinales  
- grietas transversales  
- baches  
- desprendimiento del pavimento  
- deformaciones del asfalto  

**Valor práctico**

El sistema podría integrarse en plataformas de inspección automática utilizando cámaras montadas en vehículos, drones o dispositivos móviles, permitiendo generar inventarios de deterioro de infraestructura vial.

---

# 3. Dataset

El dataset fue gestionado utilizando **Roboflow**, plataforma especializada en preparación de datasets para visión computacional.

Características principales del dataset:

- Total de imágenes: **387**
- Tipo de anotación: **Bounding Boxes**
- Número de clases: **1**
- Clase: `damage`

División del dataset:

- Entrenamiento: 80%
- Validación: 10%
- Test: 10%

Las imágenes incluyen diferentes tipos de pavimentos, condiciones de iluminación y niveles de deterioro.

---

# 4. Entrenamiento del modelo

El modelo fue entrenado utilizando **YOLOv8**, un algoritmo de detección de objetos basado en redes neuronales convolucionales optimizado para detección en tiempo real.

Configuración de entrenamiento:

- Modelo: **YOLOv8n**
- Tamaño de imagen: **640 × 640**
- Número de épocas: **30**
- Batch size: **16**
- Entorno de entrenamiento: **Google Colab (GPU Tesla T4)**

YOLO fue seleccionado por su equilibrio entre velocidad de inferencia y precisión en tareas de detección de objetos.

---

# 5. Resultados del entrenamiento

Los gráficos de entrenamiento muestran la evolución de las funciones de pérdida y métricas del modelo durante el proceso de entrenamiento.

![Gráficos de entrenamiento](images/graficos_entrenamiento.jpg)

Observaciones:

- Las funciones de pérdida disminuyen progresivamente durante el entrenamiento.
- El modelo comienza a estabilizar su aprendizaje después de aproximadamente 20 épocas.
- La métrica mAP muestra una tendencia creciente durante el proceso.

---

# 6. Métricas del modelo

Las métricas obtenidas para el modelo fueron:

- **mAP@50:** 25.4%
- **Precision:** 45.1%
- **Recall:** 31.4%

![Métricas del modelo](images/metricas_modelo.jpg)

Interpretación:

- El modelo logra detectar correctamente daños en una proporción significativa de imágenes.
- El recall indica que todavía existen casos de daño que no son detectados.
- El desempeño podría mejorar con un dataset más grande y una clasificación más detallada de daños.

---

# 7. Matriz de confusión

La matriz de confusión permite analizar el comportamiento del modelo en términos de predicciones correctas y errores.

![Matriz de confusión](images/matriz_de_confusión.png)

Interpretación:

- 12 detecciones correctas de daño
- 17 falsos positivos
- 23 falsos negativos

Esto indica que el modelo tiene margen de mejora para identificar ciertos tipos de deterioro menos evidentes.

---

# 8. Ejemplos de detección

A continuación se muestran ejemplos de inferencia utilizando el modelo entrenado.

### Ejemplo 1

![Detección 1](images/detección_01.jfif)

### Ejemplo 2

![Detección 2](images/detección_02.jfif)

### Ejemplo 3

![Detección 3](images/detección_03.jfif)

Estos ejemplos muestran la capacidad del modelo para identificar grietas y deterioro en pavimentos mediante bounding boxes.

---

# 9. Ejemplo de funcionamiento del modelo

![Detección del modelo](images/detección_modelo.jpg)

El modelo identifica automáticamente regiones deterioradas del pavimento y asigna un nivel de confianza a cada detección.

---

# 10. Análisis del umbral de confianza

El nivel de confianza determina qué detecciones son consideradas válidas.

### Umbral de confianza 70%

![Umbral 70](images/umbral_confianza_70.jpg)

### Umbral de confianza 80%

![Umbral 80](images/umbral_confianza_80.jpg)

Un umbral más alto reduce falsos positivos, pero puede disminuir el número de detecciones.

---

# 11. Limitaciones del modelo

Las principales limitaciones del sistema actual son:

- tamaño reducido del dataset
- variabilidad en iluminación y tipos de pavimento
- presencia de una única clase de daño
- detección limitada de grietas muy delgadas

Estas limitaciones son habituales en prototipos iniciales de visión por computador.

---

# 12. Posibles mejoras futuras

Para mejorar el desempeño del modelo se podrían implementar las siguientes mejoras:

- aumentar el tamaño del dataset
- crear múltiples clases de daño (grietas, baches, deformaciones)
- utilizar modelos YOLO de mayor capacidad
- aplicar técnicas de data augmentation
- incorporar imágenes capturadas en condiciones locales reales

---

# 13. Tecnologías utilizadas

- Python  
- YOLOv8 (Ultralytics)  
- Roboflow  
- Google Colab  
- Visión por Computador  
- Deep Learning  

---

# 14. Conclusión

Este proyecto demuestra la viabilidad de utilizar **modelos de detección de objetos basados en deep learning para identificar daños en pavimentos**. Aunque se trata de un prototipo inicial, los resultados muestran el potencial de estas tecnologías para apoyar sistemas de inspección automatizada en infraestructura vial dentro del sector AECO.

El desarrollo futuro de datasets más amplios y modelos más robustos podría permitir implementar soluciones reales para monitoreo inteligente de carreteras.
