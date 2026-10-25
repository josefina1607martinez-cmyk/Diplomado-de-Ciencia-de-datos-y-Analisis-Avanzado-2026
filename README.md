# Detección de fraude en transacciones financieras móviles (PaySim)

Proyecto Final Integrador de la Diplomatura en Ciencia de Datos y Análisis Avanzado (UTN.BA). Equipo N.º 21: Axel Bojko, Joaquín Bousono, Rocío Esposito, Josefina Martínez y Romina Obregón.

## Qué hace

Modelo de clasificación que asigna un puntaje de riesgo a cada transacción para priorizar cuáles revisar manualmente. El objetivo operativo es detectar al menos el 80 % de los fraudes reales revisando como máximo el 5 % de las transacciones.

Metodología CRISP-DM, partición temporal 60/20/20 por `step`, comparación de regresión logística, Random Forest y XGBoost con ponderación de clases y con submuestreo (sin SMOTE), selección por PR-AUC en validación con una regla fijada de antemano, y evaluación única en test.

Resultado principal en el test temporal: XGBoost con ponderación de clases obtiene PR-AUC de 0,9909 y captura el 100 % de los fraudes revisando el 5 % de las transacciones; para llegar al 80 % necesita revisar el 1,07 %. Los datos son sintéticos, por lo que es una prueba de concepto. El detalle está en el informe final.

## Contenido

- `Proyecto_Final_Integrador.ipynb`: notebook completo, con las salidas de la última ejecución.
- `requirements.txt`: librerías necesarias.

## Datos

PaySim, "Synthetic Financial Datasets For Fraud Detection" (Lopez-Rojas, Elmir y Axelsson, 2016): https://www.kaggle.com/datasets/ealaxi/paysim1

El archivo (`PS_20174392719_1491204439457_log.csv`, 6.362.620 filas) no se incluye en el repositorio por su tamaño. El notebook lo descarga automáticamente de Kaggle. Para eso necesita un usuario y una API key de Kaggle (Kaggle > Settings > API > Create New Token); el notebook las pide al ejecutarse. Las condiciones de uso del dataset están en la página de Kaggle.

## Cómo ejecutarlo

**En Google Colab:** abrir el notebook, elegir "Entorno de ejecución > Ejecutar todas" y cargar las credenciales de Kaggle cuando las pida. Las dependencias que faltan se instalan solas.

**En local** (Python 3.10 o superior):

```
git clone <URL-DEL-REPOSITORIO>
cd <carpeta-del-repositorio>
pip install -r requirements.txt
jupyter notebook Proyecto_Final_Integrador.ipynb
```

Ejecutar todas las celdas en orden. Las salidas se guardan en la carpeta `results/`.

## Reproducibilidad

Semilla fija (`random_state = 42`). Ejecutar el notebook completo demora entre 20 y 30 minutos, casi todo en el entrenamiento de los seis modelos. Los números del informe provienen de esa misma ejecución.
