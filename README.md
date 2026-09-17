# Taller 3 - Python y Machine Learning

Proyecto integrador que abarca carga de datos, modelos de Machine Learning y visión artificial.

---

## Links de Despliegue

### 1. Diagnóstico Clínico con Random Forest (Streamlit)
**https://modelos1.streamlit.app/**

Sistema de diagnóstico médico que utiliza un modelo Random Forest para predecir enfermedades (infarto, neumonía, gripe, ansiedad, gastroenteritis) a partir de 34 variables clínicas.

**Cómo acceder:**
1. Abrir el enlace en el navegador
2. En la pestaña "📊 Signos Vitales" ingresa edad, sexo y constantes vitales
3. En "❤️ Factores Riesgo" marca hipertensión, diabetes, etc.
4. En "🫀 Síntomas Cardiorrespiratorios" selecciona los síntomas presentes
5. En "🧠 Otros Síntomas" completa con náuseas, vómitos, ansiedad, etc.
6. Haz clic en **"🔍 Realizar Diagnóstico Integral"**

**Código fuente:** `Modelos_ML/RandomForest/`

---

### 2. API de Predicción de Precios de Viviendas (FastAPI + Django)
**https://taller3pyml-production-0fce.up.railway.app/**

API REST desarrollada con FastAPI que predice precios de viviendas según su superficie en metros cuadrados usando un modelo de Regresión Lineal.

**Cómo acceder:**
1. Abrir el enlace en el navegador
2. Verificar el estado: `GET /` retorna el health check de la API
3. Para predicciones: `POST /predict` enviando `{ "area_m2": 82.5 }`

**Documentación interactiva (Swagger):**
- Agregar `/docs` al final del enlace: `https://taller3pyml-production-0fce.up.railway.app/docs`

**Código fuente:** `Modelos_ML/RegresionLineal/back/`

---

### 3. Frontend - Predicción de Viviendas (Django)
**https://taller3pyml-production-3d1a.up.railway.app/**

Interfaz web desarrollada con Django que consume la API de predicción de precios y permite al usuario ingresar el área en m² para obtener una estimación del valor de la vivienda.

**Cómo acceder:**
1. Abrir el enlace en el navegador
2. Ingresar los metros cuadrados de la vivienda
3. Hacer clic en el botón de predicción
4. Visualizar el precio estimado

**Código fuente:** `Modelos_ML/RegresionLineal/front/`

---

### 4. Visión Artificial - Detección de Rostros (Flask + OpenCV)
**https://taller3-pyml-liart.vercel.app/**

Aplicación web que detecta rostros en imágenes usando OpenCV y el clasificador Haar Cascade. Permite subir una imagen o usar la cámara web en tiempo real.

**Cómo acceder:**
1. Abrir el enlace en el navegador
2. **Subir imagen:** Arrastrar una imagen al área designada o hacer clic para seleccionar
3. **Cámara web:** Cambiar a la pestaña "Usar Cámara" y encender la cámara
4. Hacer clic en **"Procesar Imagen"** o ver la detección en vivo
5. Visualizar los rostros detectados con recuadros verdes

**Código fuente:** `Modelos_ML/py_img-main/`

---

## Estructura del Proyecto

```
taller3_pyml/
├── Carga_datos/                    # Notebooks de carga de datos
│   ├── 1.csv_carga_datos.ipynb     # Carga con Pandas (CSV)
│   ├── 2.excel_carga_datos.ipynb   # Carga con openpyxl (Excel)
│   ├── 3.api_carga_datos.ipynb     # Carga desde APIs (requests)
│   ├── 4.webscraping_carga_datos.ipynb  # Web scraping (BeautifulSoup)
│   ├── dataset_ventas.csv          # Dataset de ejemplo
│   └── dataset_ventas.xlsx         # Dataset de ejemplo
│
├── Modelos_ML/                     # Modelos de Machine Learning
│   ├── RandomForest/               # Diagnóstico clínico (Streamlit)
│   │   ├── 1.Crear_dataset.py      # Generación del dataset sintético
│   │   ├── 2.Entrenar_modelo.py    # Entrenamiento del modelo
│   │   ├── 3.Predecir_enfermedad.py # App Streamlit (desplegada)
│   │   ├── data/                   # Datos generados
│   │   ├── models/                 # Modelo entrenado (.pkl)
│   │   └── requirements.txt
│   │
│   ├── RegresionLineal/            # Predicción de viviendas
│   │   ├── back/                   # API FastAPI
│   │   │   ├── main.py             # Endpoint /predict
│   │   │   ├── train.py            # Entrenamiento del modelo
│   │   │   ├── models/             # Modelo .joblib
│   │   │   ├── Dockerfile
│   │   │   └── requirements.txt
│   │   └── front/                  # Frontend Django
│   │       ├── app_prediccion/     # App Django
│   │       ├── manage.py
│   │       ├── Dockerfile
│   │       └── requirements.txt
│   │
│   ├── Visionartificial/           # Detección de rostros (notebook)
│   │   ├── index.ipynb
│   │   └── haarcascade_frontalface_default.xml
│   │
│   └── py_img-main/                # Visión artificial (desplegada)
│       ├── api/index.py            # API Flask + OpenCV
│       ├── public/                 # Frontend HTML/CSS/JS
│       ├── haarcascade_frontalface_default.xml
│       ├── vercel.json
│       └── requirements.txt
│
└── README.md
```

---

## Tecnologías Utilizadas

| Componente | Tecnologías |
|------------|-------------|
| **Carga de datos** | Pandas, openpyxl, requests, BeautifulSoup |
| **ML - Random Forest** | scikit-learn, Streamlit, Plotly |
| **ML - Regresión Lineal** | scikit-learn, FastAPI, Django, Joblib |
| **Visión Artificial** | OpenCV, Flask, Haar Cascade |
| **Despliegue** | Streamlit Cloud, Railway, Vercel |

---

## Ejecución en Local

### Random Forest (Streamlit)
```bash
cd Modelos_ML/RandomForest
pip install -r requirements.txt
python 1.Crear_dataset.py
python 2.Entrenar_modelo.py
streamlit run 3.Predecir_enfermedad.py
```

### Regresión Lineal (API + Frontend)
```bash
# Backend
cd Modelos_ML/RegresionLineal/back
pip install -r requirements.txt
python train.py
uvicorn main:app --reload

# Frontend
cd Modelos_ML/RegresionLineal/front
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

### Visión Artificial
```bash
cd Modelos_ML/py_img-main
pip install -r requirements.txt
python api/index.py
```
