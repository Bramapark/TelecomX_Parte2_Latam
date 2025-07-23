# Proyecto Telecom X - Parte 2: Predicción de Cancelación de Clientes (Churn)

## 🎯 Propósito del Análisis

El propósito principal de este proyecto es construir un modelo que permita **predecir si un cliente cancelará el servicio (churn)**, utilizando variables demográficas, contractuales y de facturación. Esto ayuda a la empresa a desarrollar estrategias de retención basadas en datos reales.

---

## 📁 Estructura del Proyecto

```
TelecomX_Parte2/
│
├── data/
│   ├── telecomx_limpio.csv       # Datos preprocesados listos para análisis y modelado
│
├── notebooks/
│   ├── TelecomX_Analisis.ipynb   # Notebook con todo el flujo: ETL, EDA y modelos
│
├── visualizaciones/              # Carpeta opcional para guardar gráficos exportados
│
└── README.md                     # Este archivo con descripción del proyecto
```

---

## 🧹 Preparación de los Datos

### ✅ Clasificación de Variables

- **Categóricas**:
  - `Gender`, `Partner`, `Dependents`, `Contract`, `PaperlessBilling`, `PaymentMethod`
- **Numéricas**:
  - `Tenure` (meses de permanencia), `MonthlyCharges`, `TotalCharges`

### 🔄 Codificación y Normalización

- **One-Hot Encoding**: aplicado a todas las variables categóricas nominales.
- **Label Encoding**: para convertir la variable objetivo `Churn` a valores binarios.
- **Estandarización**: `StandardScaler` aplicado a variables numéricas antes de entrenamiento con KNN y otros modelos sensibles a escala.

### 🔀 División de Datos

- **80%** para entrenamiento (`X_train`, `y_train`)
- **20%** para prueba (`X_test`, `y_test`)
- Separación estratificada para mantener proporción de la clase `Churn`.

---

## 🧠 Justificaciones en el Modelado

- Se probaron múltiples modelos: **Logistic Regression**, **Random Forest**, **Decision Tree** y **KNN**.
- Se utilizó `GridSearchCV` para ajustar hiperparámetros.
- La métrica principal fue el **f1-score**, adecuada para datos desbalanceados.
- `RandomForestClassifier` obtuvo el mejor equilibrio entre precisión y recall.

---

## 📊 Ejemplos de Gráficos e Insights (EDA)

- **Clientes con contrato "Month-to-month" tienen mayor tasa de churn.**
- **Los cargos mensuales más altos están correlacionados con cancelaciones.**
- **Clientes que usan “Electronic check” como medio de pago presentan mayor tasa de churn.**
- **La permanencia (`Tenure`) baja (menos de 12 meses) está fuertemente asociada a cancelaciones.**

Gráficos generados:

- `countplot` de distribución de churn.
- `boxplot` de cargos mensuales por tipo de contrato y churn.
- `histplot` de `Tenure` por churn.
- `heatmap` de correlaciones.
- `stacked barplot` de churn por forma de pago y tipo de contrato.

---

## 🚀 Instrucciones para Ejecutar el Cuaderno

1. Abrir Google Colab y cargar el archivo `TelecomX_Analisis.ipynb`.
2. Subir el archivo `telecomx_limpio.csv` al entorno de ejecución.
3. Instalar dependencias si es necesario:

```python
!pip install pandas scikit-learn matplotlib seaborn
```

4. Ejecutar las celdas en orden para realizar el análisis completo: EDA → Preprocesamiento → Modelado → Evaluación.

---

📌 **Este proyecto es parte de una estrategia de analítica predictiva aplicada a la fidelización de clientes.**
