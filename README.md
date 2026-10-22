# Caso-de-Negocios---Venta-Multicanal---LATAM

Vamos a trabajar como analistas de datos de una tienda multicanal LATAM. El objetivo es aprender flujo de trabajo práctico: 
-¬ cargar datos 
-¬ explorarlos  
-limpiarlos 
-automatizar tareas simples 
-graficar 
-detectar outliers 
-segmentar ventas 
-> cerrar con conclusiones accionables.

## Problem
Is there a relationship between urban mobility (congestion and travel delays) and economic productivity (GDP per capita)? The goal is to help the EverPeak strategy team decide where transport infrastructure investment could matter most.

## Dataset
- **Coverage:** 2024 · 15 cities · 7 countries
- `jams_delay`: traffic congestion indicator (mobility)
- `city_gdp_capita`: GDP per capita (productivity)

## Analysis
- **Cleaning:** `datetime` and `float` conversions, `snake_case` column names across both datasets
- **Integration:** aggregation at city–year level and an `INNER` join of traffic and economic data
- **Exploration:** box plots (outliers), histograms (distributions), bar charts (city comparison)

## Results
- **No clear relationship** between traffic and GDP per capita.
- Box plots show unusually high values that look like anomalies, concentrated mostly in Brazil.

## Recommendations
1. Prioritize **Mexico City** and **São Paulo**, which have the highest congestion.
2. Validate Brazil's data sources before drawing conclusions.
3. Invest in transport infrastructure in **Bogotá** (top priority) and **Santiago**.
4. Extend the analysis to more years and run formal correlations per city.
---
# DataSet

Filas
Columnas

