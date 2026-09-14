# sprint7-final-project_telecom-analysis
Proyecto final Sprint 7
# 📞 ConnectaTel: Análisis Estadístico y Segmentación de Clientes

## 🎯 Objetivo del Proyecto
El objetivo de este proyecto es analizar el comportamiento de uso de los clientes de **ConnectaTel** en Latinoamérica para identificar patrones de consumo de llamadas y mensajes, detectar valores atípicos (*outliers*) y segmentar a los usuarios por edad y nivel de uso. Estos hallazgos permiten evaluar la efectividad de la oferta comercial y sugerir oportunidades de optimización de planes y retención de usuarios.

---

## 📊 Datasets Utilizados
* **`plans.csv`**: Información de los planes comerciales (Básico y Premium) con precios, minutos, mensajes y GB incluidos, además de los costos por exceso.
* **`users_latam.csv`**: Datos demográficos y contractuales de los usuarios (id, edad, ciudad, fecha de registro, tipo de plan y *churn*).
* **`usage.csv`**: Registro detallado de la actividad real consumida por cada usuario (llamadas, mensajes, duración y longitud).

---

## 🛠️ Etapas del Análisis
* **1. Carga y Exploración Inicial:** Inspección de la estructura, cantidad de filas/columnas (`shape`) y tipos de datos (`info`).
* **2. Calidad de Datos:** Detección de nulos, identificación de valores *sentinels* (`-999` en edad y `'?'` en ciudad) y fechas fuera del periodo válido (`2026`).
* **3. Limpieza y Tratamiento:** Reemplazo de *sentinels* por la mediana en `age`, etiquetado de valores de ciudad, corrección de inconsistencias temporales y justificación de nulos de tipo MAR en consumo.
* **4. Resumen Estadístico por Usuario:** Consolidación de la tabla `user_profile` sumando `cant_mensajes`, `cant_llamadas` y `cant_minutos_llamada` por cada `user_id`.
* **5. Análisis Exploratorio y Outliers:** Generación de histogramas con KDE y boxplots. Cálculo de límites superiores mediante el método **IQR** (Rango Intercuartílico).
* **6. Segmentación:** Clasificación por niveles de uso (`grupo_uso`: Bajo, Medio, Alto) y demografía (`grupo_edad`: Joven, Adulto, Adulto Mayor).
* **7. Insight Ejecutivo:** Diagnóstico final sobre los patrones detectados y recomendaciones comerciales.

---

## 🚀 Cómo Ejecutar el Proyecto

### Opción 1: Ejecutar en Google Colab
1. Sube el archivo del notebook (`S7 Version-Estudiante-Project-ConnectaTel.ipynb`) a Google Colab.
2. Carga los datasets (`plans.csv`, `users_latam.csv`, `usage.csv`) en la ruta `/datasets/`.
3. Ejecuta todas las celdas en orden (`Entorno de ejecución → Ejecutar todo`).

### Opción 2: Entorno Local (Jupyter Notebook)
1. Clona el repositorio desde la terminal:
   ```bash
   git clone https://github.com/darlingsaavedra/sprint7-final-project_telecom-analysis.git 
```
2.	Instala las librerías necesarias:
```bash
pip install pandas numpy matplotlib seaborn
```
3.	Ejecuta Jupyter Notebook para abrir el proyecto:
```bash
jupyter notebook "S7 Version-Estudiante-Project-ConnectaTel.ipynb"
```
________________________________________
📌 Guía de Reproducción
1.	Estructura del Proyecto: Asegúrate de mantener los archivos estructurados de la siguiente manera dentro de tu directorio de trabajo:   
```text
├── datasets/
│   ├── plans.csv
│   ├── users_latam.csv
│   └── usage.csv
├── S7 Version-Estudiante-Project-ConnectaTel.ipynb
└── README.md
```
2.	Ejecución Secuencial:
o	Paso 1 a 3 (Limpieza): Ejecuta en orden para procesar los sentinels de edad (-999), ciudad ('?'), fechas futuras (2026) y nulos estructurales.
o	Paso 4 y 5 (Métricas y Outliers): Ejecuta el cálculo de user_profile e IQR para generar los boxplots de llamadas y mensajes.
o	Paso 6 y 7 (Segmentación e Insights): Genera las nuevas variables categóricas (grupo_uso y grupo_edad) y visualiza sus respectivas distribuciones.
________________________________________
💡 Principales Conclusiones y Recomendaciones
  
•	Tratamiento de Outliers: Los valores extremos en minutos y mensajes corresponden a heavy users reales del servicio, por lo que se decidió conservarlos para no alterar el perfil de consumo.
•	Estrategia Comercial: Se sugiere evaluar la creación de un paquete intermedio ("Básico Plus") para capturar a usuarios que exceden el plan Básico pero no migran a Premium, así como diseñar promociones orientadas por edad y nivel de consumo.

