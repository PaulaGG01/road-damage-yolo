# Governance Checklist – Proyecto de Detección de Daños en Pavimentos

## 1. Privacidad y consentimiento

El proyecto utiliza imágenes de pavimentos y carreteras obtenidas de datasets públicos y recursos abiertos disponibles para investigación en visión computacional.

No se utilizan imágenes que contengan información personal identificable, rostros de personas o matrículas de vehículos.

Por lo tanto, el riesgo de afectación a la privacidad es considerado bajo.

---

## 2. Minimización de datos

El dataset utilizado contiene únicamente las imágenes necesarias para entrenar el modelo de detección de daños en pavimentos.

No se almacenan metadatos personales ni información adicional que no sea necesaria para el entrenamiento del modelo.

---

## 3. Declaración de limitaciones (Cuándo no usar el modelo)

El modelo desarrollado corresponde a un **prototipo académico** y no debe utilizarse como único sistema de evaluación para decisiones críticas de mantenimiento de infraestructura.

Limitaciones conocidas:

- dataset de tamaño reducido
- una única clase de daño
- variabilidad en iluminación y condiciones del pavimento
- detección limitada en grietas muy delgadas

Por estas razones, el sistema debe utilizarse únicamente como **herramienta de apoyo a inspección humana**.

---

## 4. Nota de riesgos (Falsos positivos y falsos negativos)

El sistema puede generar dos tipos de errores:

**Falsos positivos (FP)**  
El modelo identifica daño donde no existe deterioro real.

Impacto:
- inspecciones innecesarias
- sobreestimación de deterioro

**Falsos negativos (FN)**  
El modelo no detecta daño existente.

Impacto:
- omisión de deterioro real
- retraso en intervenciones de mantenimiento

En aplicaciones reales se recomienda combinar el modelo con inspección humana.

---

## 5. Derechos del dataset

El dataset utilizado fue preparado mediante la plataforma **Roboflow** y se basa en imágenes disponibles públicamente para fines de investigación en visión computacional.

Las imágenes se utilizan exclusivamente con fines académicos y de investigación.

---

## 6. Licencia del proyecto

Este proyecto se publica bajo licencia **MIT**, permitiendo su uso, modificación y distribución con fines académicos o de investigación, siempre manteniendo la atribución correspondiente.

Licencia MIT:

Copyright (c) 2026

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files to deal in the software without restriction.
