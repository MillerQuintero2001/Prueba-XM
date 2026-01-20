# Prueba-XM

> ⚠️ **Nota:** Este README fue generado con asistencia de IA (GitHub Copilot).

## Descripción

Prueba Técnica Misión XM - Análisis de datos del mercado eléctrico colombiano utilizando la API pública de SIMEM (Sistema de Información del Mercado de Energía Mayorista).

---

## Estructura del Proyecto

Prueba-XM/
├── main.py
├── pyproject.toml
├── README.md
├── data/
│   ├── exercise_1/
│   │   ├── datos_tx1.csv         # Datos filtrados versión TX1
│   │   ├── top_3_max.csv         # Top 3 precios de bolsa más altos
│   │   └── bottom_3_min.csv      # Top 3 precios de bolsa más bajos
│   ├── exercise_2/
│   │   └── raw/
│   │       ├── Lecturas_parte1.csv
│   │       ├── Lecturas_parte2.csv
│   │       ├── Mapeo.csv
│   │       └── Ofertas.csv
│   └── raw/
├── Notebook/
│   ├── extract_api_data.ipynb    # Ejercicio 1
│   ├── exercise_2.ipynb          # Ejercicio 2
│   └── extract_data.py
└── visuals/                       # Gráficos generados

---

## Ejercicio 1: Extracción y Análisis de Precios de Bolsa

### Descripción

Este ejercicio consiste en la extracción de datos del **Precio de Bolsa** del mercado eléctrico colombiano mediante la API pública de SIMEM, utilizando el dataset `EC6945`.

### Notebook

📓 [`Notebook/extract_api_data.ipynb`](Notebook/extract_api_data.ipynb)

### Proceso

1. **Extracción de datos**: Conexión a la API de SIMEM con streaming de datos para el período de diciembre 2025.
2. **Filtrado**: Se filtran los datos para obtener únicamente la versión `TX1`.
3. **Análisis exploratorio**:
   - Estadísticas descriptivas (máximo, mínimo, promedio)
   - Identificación de valores únicos por columna
4. **Visualización**:
   - Serie de tiempo del Precio de Bolsa
   - Gráfico de barras con estadísticas principales
5. **Identificación de extremos**:
   - Top 3 horas con mayor precio de bolsa
   - Top 3 horas con menor precio de bolsa

### Datos Generados

| Archivo                              | Descripción                                    |
| ------------------------------------ | ----------------------------------------------- |
| `data/exercise_1/datos_tx1.csv`    | Dataset completo filtrado por versión TX1      |
| `data/exercise_1/top_3_max.csv`    | Las 3 horas con los precios de bolsa más altos |
| `data/exercise_1/bottom_3_min.csv` | Las 3 horas con los precios de bolsa más bajos |

### Visualizaciones

Los gráficos generados se encuentran en la carpeta [`visuals/`](visuals/), incluyendo:

- Serie de tiempo del Precio de Bolsa (Versión TX1)
- Gráfico de barras con valores máximo, mínimo y promedio

---

## Ejercicio 2: Análisis de Desconexión Verificada

### Descripción

Este ejercicio analiza lecturas de fronteras comerciales para calcular la **Desconexión Verificada** por agente.

### Notebook

📓 [`Notebook/exercise_2.ipynb`](Notebook/exercise_2.ipynb)

### Proceso

1. **Carga de datos**: Lectura de archivos CSV (`Lecturas_parte1.csv`, `Lecturas_parte2.csv`)
2. **Concatenación**: Unión de los dataframes de lecturas
3. **Mapeo**: Asociación de fronteras con su valor LBC (Línea Base de Consumo) usando `Mapeo.csv`
4. **Cálculo de CE**: Suma de lecturas por día y frontera
5. **Cálculo de Desconexión Verificada**: `MAX(0, LBC - CE)`
6. **Agregación**: Resultados agrupados por mes y agente

---

## Tecnologías Utilizadas

- **Python 3.x**
- **Pandas**: Manipulación y análisis de datos
- **Matplotlib/Seaborn**: Visualización de datos
- **Requests**: Consumo de API REST
- **Jupyter Notebook**: Desarrollo interactivo

---

## Fuente de Datos

- **SIMEM** (Sistema de Información del Mercado de Energía Mayorista)
- API pública: `https://www.simem.co/backend-files/api/`
- Dataset ID: `EC6945` (Precio de Bolsa)

---

## Autor

Prueba técnica desarrollada para **XM S.A. E.S.P.**
