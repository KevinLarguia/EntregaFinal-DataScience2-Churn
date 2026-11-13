# Entrega Final — Data Science II (Coderhouse)

**Alumno:** Kevin Larguia

Predicción de abandono (churn) de estudiantes de una plataforma de cursos online (Platzi), planteado como un problema de **clasificación binaria**. Retoma el proyecto de la entrega anterior y suma validación cruzada, optimización de hiperparámetros, modelos de ensamble e interpretación con SHAP.

## Contenido

- `EntregaFinal_Larguia.ipynb`: notebook con abstracto, problema, EDA, ingeniería de atributos, entrenamiento con validación cruzada, optimización (GridSearchCV / RandomizedSearchCV), selección de modelo, ajuste de umbral, SHAP y conclusiones.
- `platzi_churn.csv`, `platzi_courses.csv`, `platzi_interactions.csv`: datos utilizados.
- `Presentacion_Churn_Larguia.pptx` / `.pdf`: presentación ejecutiva (12 diapositivas).
- `requirements.txt`: librerías necesarias.

## Resumen de resultados

| Modelo (optimizado) | AUC validación cruzada (5 folds) | AUC test |
|---|---|---|
| **Random Forest (seleccionado)** | **0.662** | **0.655** |
| KNN | 0.659 | 0.657 |
| XGBoost | 0.659 | 0.663 |
| Árbol de Decisión | 0.633 | 0.635 |

- Con el umbral ajustado (≈0.30), el modelo detecta el **78%** de los estudiantes que abandonan.
- El 10% de estudiantes con mayor riesgo concentra el 20% de los abandonos (el doble que eligiendo al azar).
- Variables más importantes (SHAP): días sin entrar a la plataforma o a un curso, plan Basic / pago mensual, ranking en la comunidad y nivel de uso.

## Cómo ejecutarlo

```bash
pip install -r requirements.txt
jupyter notebook EntregaFinal_Larguia.ipynb
```

En Google Colab: subir el notebook y los 3 CSV, e instalar `shap` y `xgboost` si no están disponibles. La ejecución completa tarda unos 5 minutos (la búsqueda de hiperparámetros es la parte más lenta).
