# Caso-de-Negocios---Venta-Multicanal---LATAM

# Multichannel Sales Analysis – LATAM Retail Business Case

![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/GloriaTP/Caso-de-Negocios---Venta-Multicanal---LATAM/blob/main/Copia_de_Sprint07_Webinar11_students_version.ipynb)

## Business Problem
A multichannel retailer sells through **Web, App, Physical store and WhatsApp** across several Latin American countries. Leadership needs to know:
- Which countries, channels and categories generate the most revenue?
- Where is the margin concentrated?
- What sales segments exist?
- Are there atypical sales that could distort the analysis?

## Data
- **Source file:** `sprint07_proyecto_ventas_multicanal_latam.csv`
- **Size:** 180 sales records · 19 columns
- **Period:** January–April 2026
- **Coverage:** multiple LATAM countries (including Colombia, Chile, Peru and Mexico), 5 product categories (Fashion, Sports, Home, Beauty, Technology)
- **Key fields:** country, city, channel, category, payment method, customer type, units, unit price, discount, revenue, cost, margin, customer age, satisfaction, delivery days and returns

## Cleaning & Transformations
| Issue / Step | Action |
|---|---|
| Missing values | `metodo_pago` (6.1%), `satisfaccion` (5.0%), `dias_entrega` (3.9%), `edad_cliente` (2.8%) |
| Data safety | Worked on a copy (`df_limpio`) to preserve the original dataset |
| Dates | `fecha` converted to `datetime`; monthly period column created |
| Text consistency | Whitespace and capitalization standardized in 8 categorical columns |
| Payment method | Nulls filled with **"No informado"** |
| Numeric nulls | Filled with the **median** (delivery days, customer age, satisfaction) |
| Outliers | Detected with the **IQR rule** on revenue |
| Segmentation | `segmento_venta` created with a custom function and `.apply()` |
| Validation | Confirmed 0 nulls after cleaning |

## Key KPIs
| KPI | Value |
|---|---|
| Total revenue | 235,680,980 |
| Total margin | 82,220,991 (**34.89%**) |
| Average ticket | 1,309,338 |
| Return rate | 7.22% |
| Average satisfaction | 7.43 / 10 |

## Patterns & Segments
**Sales segments** (by revenue per sale)

| Segment | Rule | Sales |
|---|---|---|
| High | ≥ 4,000,000 | 11 |
| Medium | ≥ 150,000 | 151 |
| Low | < 150,000 | 18 |

**Top 5 country–channel–category combinations by revenue**

| Country | Channel | Category | Revenue | Margin % |
|---|---|---|---|---|
| Peru | App | Technology | 26.96M | 38% |
| Chile | Physical store | Technology | 22.77M | 36% |
| Chile | App | Technology | 20.59M | 32% |
| Colombia | Web | Technology | 15.84M | 32% |
| Colombia | App | Home | 10.54M | 33% |

**Outliers**
- The IQR rule flagged **14 atypical sales** (revenue above 3,554,200).
- **12 of the 14** are in Technology, mostly through App and Physical store.
- These 14 sales (about 8% of all sales) account for roughly **38% of total revenue**.
- The average revenue per sale is almost double the median (1.31M vs. 0.69M), which confirms a right-skewed distribution.

## Conclusions & Recommendations
1. **Technology drives the business:** 8 of the top 10 combinations are Technology, led by Peru (App) and Chile (App and Physical store).
2. **Revenue is concentrated in few, high-value sales:** a small group of large orders carries a big share of revenue, so results can swing easily with a handful of transactions.
3. **Review outliers before deciding:** they are not errors, but they should be validated (bulk orders, corporate buyers) before they are used for forecasts or targets.
4. **Margin is healthy but uneven:** the overall margin is 34.89%, with Mexico–Web–Technology showing the highest margin among the top combinations, so there is room to optimize discounts in lower-margin channels.
5. **Next steps:** compare sales with and without returns, build a profitability metric, and test alternative segment thresholds.

> Note: some country–channel–category combinations have few sales (3 to 9), so rankings should be confirmed with a larger sample.

## Tools
Python · pandas · Matplotlib · Seaborn · Jupyter Notebook · Google Colab

## How to Reproduce
1. Click the **Open In Colab** badge above.
2. Run the cells in order. The notebook loads the dataset directly from a public URL.
3. Exports generated: `ventas_multicanal_limpio.csv` and `Ranking_final_ventas.csv`.
