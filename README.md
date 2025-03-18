# Descripción del Proyecto: Predicción de la Pérdida de Clientes para Interconnect

## Introducción

Este proyecto tiene como objetivo predecir la pérdida de clientes para Interconnect, una empresa de telecomunicaciones, utilizando técnicas de aprendizaje automático. La predicción de la pérdida de clientes es crucial para las empresas en industrias competitivas, ya que les permite identificar a los clientes con alto riesgo de abandonar y tomar medidas proactivas para retenerlos. El objetivo de este proyecto fue construir un modelo predictivo capaz de prever la pérdida de clientes con precisión, basado en varias fuentes de datos relacionadas con el comportamiento de los clientes, contratos y uso de servicios.

## Resumen de los Procedimientos

El proyecto involucró varios pasos clave: recopilación de datos, preprocesamiento, análisis exploratorio de datos (EDA), selección y evaluación del modelo. A continuación se presenta un resumen de los pasos tomados durante el proyecto.

### 1. Recopilación de Datos

El proyecto comenzó con la recopilación de cuatro conjuntos de datos principales, los cuales fueron necesarios para comprender los diversos aspectos del comportamiento de los clientes:
- **contract.csv**: Contiene información sobre el contrato del cliente, incluyendo tipo de facturación, método de pago, cargos y fechas de inicio/fin del contrato.
- **personal.csv**: Contiene datos personales sobre los clientes, como género, grupo de edad, estado civil y si tienen dependientes.
- **internet.csv**: Proporciona detalles sobre el servicio de internet del cliente, incluyendo el tipo de servicio y complementos como seguridad en línea, copia de seguridad, protección de dispositivos y servicios de transmisión.
- **phone.csv**: Incluye información sobre si un cliente tiene varias líneas telefónicas conectadas a su servicio.
Cada conjunto de datos contiene un ID único de cliente, lo que facilita la integración y el seguimiento a través de diferentes fuentes de datos.

### 2. Preprocesamiento de Datos

Se limpiaron y transformaron los datos para asegurar que fueran adecuados para el aprendizaje automático. Los principales pasos de preprocesamiento fueron:
- **Manejo de Valores Faltantes**: Se verificó si los conjuntos de datos tenían datos faltantes o incompletos, y se aplicaron estrategias adecuadas para abordarlos.
- **Ingeniería de Características**: Las variables categóricas se transformaron en numéricas mediante técnicas como "One-Hot Encoding" para hacerlas adecuadas para los modelos de aprendizaje automático.
- **Balanceo de Datos**: El conjunto de datos original presentaba un desequilibrio entre clientes activos e inactivos, lo que podría generar predicciones sesgadas en el modelo. Se aplicaron técnicas como sobremuestreo y submuestreo para equilibrar los datos y evitar sesgos en el modelo.

### 3. Análisis Exploratorio de Datos (EDA)

Se realizó un análisis exploratorio de datos para descubrir patrones e información oculta en los datos. Los principales objetivos del EDA fueron:
- **Identificar Patrones y Relaciones**: El análisis tenía como objetivo descubrir correlaciones entre las diferentes características, como el comportamiento de los clientes, el tipo de contrato y el uso de servicios, y su impacto en la pérdida de clientes.
- **Detectar Valores Atípicos e Inconsistencias**: Se identificaron y corrigieron cualquier inconsistencia en los datos, como valores atípicos o entradas erróneas.
- **Selección de Características**: Se identificaron las características clave que contribuían significativamente a la pérdida de clientes mediante visualizaciones y matrices de correlación, lo que guió la selección de variables para el entrenamiento del modelo.

### 4. Selección y Entrenamiento del Modelo

Se probaron y compararon varios modelos de aprendizaje automático para determinar el más eficaz para predecir la pérdida de clientes. Los modelos probados incluyeron:
- **Regresión Logística**
- **K-Vecinos Más Cercanos (KNN)**
- **Bosque Aleatorio (Random Forest)**
- **Búsqueda en Cuadrícula + Bosque Aleatorio**
- **Máquina de Refuerzo de Gradiente (GBM)**
- **XGBoost**
- **LightGBM**
Se utilizaron técnicas de búsqueda en cuadrícula para optimizar los hiperparámetros y mejorar el rendimiento de los modelos.

### 5. Evaluación del Modelo

Cada modelo fue evaluado utilizando varias métricas clave para determinar su precisión y efectividad:
- **AUC-ROC**: Mide la capacidad del modelo para distinguir entre clientes que se darán de baja y los que no. Un AUC más alto indica un mejor rendimiento.
- **Precisión (Accuracy)**: La proporción de casos correctamente clasificados (tanto clientes que se dan de baja como los que no).
- **Precisión (Precision)**: La proporción de verdaderos positivos entre todos los predichos como positivos, lo que indica la exactitud de predecir la pérdida de clientes.
- **Recuperación (Recall)**: La proporción de verdaderos positivos entre todos los casos reales positivos, lo que mide la capacidad del modelo para identificar correctamente a los clientes que se irán.
- **Puntuación F1**: Un balance entre precisión y recuperación, proporcionando una medida más completa del rendimiento del modelo, especialmente importante en casos de desequilibrio de clases.

### 6. Selección del Modelo Final

Después de probar varios modelos, se seleccionó **Random Forest** como el modelo final debido a su rendimiento robusto en diversas métricas. El rendimiento del modelo se evaluó en el conjunto de prueba, y los resultados se resumen a continuación.

## Hallazgos

### Métricas de Rendimiento del Modelo

- **AUC-ROC**: **0.86** – Esto indica que el modelo funciona bien para distinguir entre clientes que se darán de baja y aquellos que no.
- **Precisión (Accuracy)**: **76%** – El modelo clasificó correctamente el 76% de los casos, lo que es positivo. Sin embargo, en problemas de desequilibrio de clases como este, es fundamental evaluar también otras métricas como precisión, recuperación y puntuación F1.
- **Precisión (Precision)**: **0.91** – La precisión indica que, cuando el modelo predice que un cliente se irá, tiene un 91% de probabilidad de ser correcto.
- **Recuperación (Recall)**: **0.74** – El modelo identifica correctamente el 74% de los clientes que realmente se irán. Sin embargo, este valor sugiere que aún hay margen para mejorar la detección de la pérdida de clientes.
- **Puntuación F1**: **0.81** – El modelo logra un buen equilibrio entre precisión y recuperación, lo que lo hace eficaz para identificar a los clientes que se irán sin ser demasiado sensible a falsos positivos o negativos.

### Matriz de Confusión

- **Verdaderos Positivos (VP)**: **751** – Clientes que fueron correctamente predichos para darse de baja y lo hicieron.
- **Verdaderos Negativos (VN)**: **313** – Clientes que fueron correctamente predichos como no se darían de baja y no lo hicieron.
- **Falsos Positivos (FP)**: **76** – Clientes que fueron incorrectamente predichos para darse de baja, pero no lo hicieron.
- **Falsos Negativos (FN)**: **267** – Clientes que fueron incorrectamente predichos como no se darían de baja, pero lo hicieron.

La capacidad del modelo para captar la mayoría de los clientes que realmente se dan de baja es evidente, aunque algunas predicciones falsas podrían generar acciones de retención innecesarias o, por el contrario, la pérdida de oportunidades para retener a los clientes que realmente quieren irse.

## Conclusión

El proyecto logró desarrollar un modelo de aprendizaje automático para predecir la pérdida de clientes para Interconnect. El modelo **Random Forest** demostró un rendimiento sólido, logrando un **AUC-ROC de 0.86**, **precisión de 0.91** y **puntuación F1 de 0.81**. Estos resultados sugieren que el modelo es eficaz para predecir la pérdida de clientes y puede respaldar las estrategias de retención de Interconnect.

Sin embargo, existen áreas de mejora. El **índice de recuperación** de **0.74** indica que algunos clientes que se darían de baja no fueron detectados por el modelo, lo que podría generar oportunidades perdidas para la retención. El trabajo futuro debería centrarse en mejorar la recuperación, posiblemente mediante el uso de técnicas avanzadas como SMOTE para equilibrar las clases o refinando los hiperparámetros del modelo.

En general, el modelo proporciona una base sólida para identificar a los clientes con alto riesgo de pérdida y facilitar esfuerzos de retención dirigidos, pero se necesita un monitoreo continuo y optimización para mantener y mejorar su rendimiento.
