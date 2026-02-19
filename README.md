**Optimización de Predicción Diaria en Retail**

Este repositorio contiene un análisis e implementación de un modelo de Machine Learning para predecir ventas diarias. A través de ingeniería de variables y optimización de hiperparámetros, logramos explicar la variabilidad de los datos, alcanzando un **R² de 0.30**.  

Dataset: [E-commerce Business Transaction](https://www.kaggle.com/datasets/gabrielramos87/an-online-shop-business/data) de [Gabriel Ramos](https://www.kaggle.com/gabrielramos87)  
Fuente: [Kaggle](https://www.kaggle.com/)

## Resumen del Proyecto
El objetivo principal fue predecir el volumen de ventas en un dataset con alta volatilidad (con más de 500,000 registros). El reto principal radicaba en capturar los picos de demanda estacionales dentro de cada mes.

### Resultados Clave:
| Métrica | Valor |
| :--- | :--- |
| **Modelo Final** | RandomForestRegressor (n_estimators=100, min_samples_leaf=3, random_state=42) |
| **MAE** | 64,965 |
| **R² Score** | **0.3032** |
| **Precisión Relativa** | ~76.41% |

---

## Innovaciones Tecnológicas y de Negocio

### 1. Ingeniería de Variables: `DayStrength`
Se identificó que el modelo base ignoraba comportamientos cíclicos clave. Mediante un análisis de estacionalidad, se creó la característica **`DayStrength`**, la cual pondera la fuerza de ventas de días específicos del mes (especialmente los días 5, 9 y 20). Esta variable fue el motor que impulsó el R² de 0.24 a 0.30.

### 2. Optimización de Modelos
Se realizaron múltiples experimentos documentados en el notebook:
* **Random Forest vs. XGBoost:** Se determinó que RF gestionaba mejor el ruido de este dataset específico.
* **Transformación Logarítmica:** Fue evaluada y descartada, ya que suavizaba los picos de demanda que eran críticos para el negocio.
* **Ajuste:** Uso de `RandomizedSearchCV` con `TimeSeriesSplit` para garantizar una validación temporal real (evitando el data leakage).

---

## Diagnóstico del Modelo
El análisis de residuos confirma que un buen comportamiento en el modelo:
* **Distribución Normal de Errores:** Los errores están centrados en cero

---

## Librerías utilizadas
```bash
pandas
numpy
scikit-learn
matplotlib
seaborn
xgboost
