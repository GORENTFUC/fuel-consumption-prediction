# Modelamiento y Predicción del Consumo de Combustible Marítimo

Regresión Lineal Múltiple y Análisis Diagnóstico de Residuos.

## Integrantes (Grupo F)

- Diego Fernando Anacona Perez
- Juan David Mora Rayo
- Juan Sebastian Lizcano Quevedo

## Información del proyecto

| Campo | Detalle |
|---|---|
| Facultad | Facultad de Ingeniería |
| Programa académico | BigData y Analítica de datos |
| Semestre | 1 |
| Área de conocimiento | Análisis de Datos / Big Data |
| Fecha de inicio | 5/10/2026 |
| Fecha de cierre | 10/10/2026 |

## Resumen

El proyecto analiza el consumo de combustible (`fuel_consumption`) de embarcaciones operativas mediante un modelo de Regresión Lineal Múltiple. Con un conjunto de datos de 1,440 observaciones, se evalúa la influencia de la distancia recorrida (`distance`) y el tipo de barco (`ship_type`). El trabajo cubre la preparación de datos, el análisis exploratorio, el ajuste del modelo y la validación de supuestos estadísticos (linealidad, normalidad, homocedasticidad, independencia y multicolinealidad).

**Pregunta de investigación:** ¿En qué medida la distancia recorrida y el tipo de barco explican la variación en el consumo de combustible de las embarcaciones mediante un modelo de regresión lineal múltiple?

## Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `SolucionTrabajoGrupalUnidad_4.ipynb` | Cuaderno con el análisis exploratorio, el modelo y el diagnóstico de residuos. |
| `ship_fuel_efficiency.csv` | Base de datos de embarcaciones (1,440 registros). |
| `FO-IV-159-GRUPO-F.xlsx` | Formato institucional con la ficha del proyecto. |

## Algoritmo y metodología

Metodología cuantitativa, de alcance correlacional y diseño no experimental, desarrollada en Python (Google Colab):

1. **Preparación de datos:** revisión de variables, tipos y valores faltantes.
2. **Análisis exploratorio:** estadísticas descriptivas, gráficos de dispersión y matriz de correlación.
3. **Selección de variables:** `fuel_consumption` como variable dependiente; `distance` y `ship_type` como independientes.
4. **Ajuste del modelo:** Regresión Lineal Múltiple por Mínimos Cuadrados Ordinarios (OLS).
5. **Diagnóstico:**
   - Normalidad: gráfico Q-Q y prueba de Shapiro-Wilk.
   - Homocedasticidad: prueba de Breusch-Pagan.
   - Independencia: estadístico de Durbin-Watson.
   - Multicolinealidad: factor de inflación de la varianza (VIF).
6. **Ajustes:** transformación logarítmica (`log(fuel_consumption) ~ log(distance) + C(ship_type)`) y errores estándar robustos HC3 ante la heterocedasticidad.

**Librerías:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `statsmodels`, `scipy`.

## Resultados principales

- El modelo logarítmico explica el **97.4 %** de la variación del consumo (R² ajustado de 0.943 a 0.974).
- **Distancia:** coeficiente ≈ 1.00, el consumo es proporcional a la distancia (10 % más de millas implica cerca de 10 % más de combustible).
- **Tipo de barco** (frente a un Fishing Trawler, a igual distancia): Tanker Ship ≈ +59 %, Oil Service Boat ≈ +20 %, Surfer Boat ≈ −41 %.
- Clima, ruta, mes y eficiencia del motor no resultaron significativos; el tipo de combustible casi no mejora el modelo.
- Durbin-Watson ≈ 2.06, por lo que los residuos son independientes.

Una asociación estadística no demuestra por sí sola una relación causal.

## Cómo ejecutar

1. Abrir `SolucionTrabajoGrupalUnidad_4.ipynb` en Google Colab o Jupyter.
2. Ubicar `ship_fuel_efficiency.csv` en el mismo directorio del cuaderno.
3. Instalar dependencias si es necesario:

   ```bash
   pip install pandas numpy matplotlib seaborn statsmodels scipy
   ```

4. Ejecutar todas las celdas.
