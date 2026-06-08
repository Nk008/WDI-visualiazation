# LDS7004M Data Visualisation Portfolio
## Wealth, Health and Growth: A Visual Analysis of the World Bank WDI Dataset (1990–2022)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/NK008/LDS7004M-DataViz-WDI/blob/main/LDS7004M_Advanced_Notebook.ipynb)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**York St John University | London Campus | MSc Data Science | LDS7004M Data Visualisation**
**Student:** Nareshkumar Shanmugathas | **ID:** 250274615 | **Deadline:** 9 June 2026

---

## Research Question

> *Does national wealth, measured as GDP per capita, predict how long people live and how fast populations grow — and has this relationship changed between 1990 and 2022?*

---

## Key Findings

| Finding | Evidence |
|---|---|
| Income strongly predicts life expectancy | Pearson r = +0.792, p < 0.001, n = 209 |
| Relationship is log-linear not linear | log(GDP) r = +0.79 vs raw GDP r = +0.55 |
| Preston Curve shifted upward 1990–2022 | OLS intercept increased ~5 years |
| COVID-19 reversed a decade of health progress | Global life expectancy fell 1.6 years (2019–2021) |
| 18.4-year gap between income group extremes | Low income 61.2 yrs vs High income 79.6 yrs |
| Population growth inversely linked to income | r(life exp, pop growth) = −0.71 |
| South Asia made the largest regional gains | +12 years median life expectancy 1995–2022 |

---

## Dataset

- **Source:** [World Bank World Development Indicators (WDI)](https://databank.worldbank.org/source/world-development-indicators)
- **Coverage:** 217 sovereign countries, 1990–2022 (33 years)
- **Observations:** 7,161 country-year rows
- **Indicators used:**

| WDI Code | Variable | Unit | Completeness |
|---|---|---|---|
| NY.GDP.PCAP.CD | GDP per capita | Current USD | 95.1% |
| SP.DYN.LE00.IN | Life expectancy at birth | Years | 100.0% |
| SP.POP.TOTL | Total population | Persons | 100.0% |

> **Note:** The raw WDI CSV files are not included in this repository due to file size (~25 MB). Download them free from the World Bank DataBank link above. See `data/README_data.md` for full instructions.

---

## Repository Structure
LDS7004M-DataViz-WDI/
├── LDS7004M_Advanced_Notebook.ipynb       ← Main notebook (run this)
├── LDS7004M_Advanced_Notebook_Executed.ipynb  ← Executed version with all outputs
├── src/
│   └── wdi_analysis.py                    ← Standalone Python script
├── figures/
│   ├── fig01_missing_heatmap.png
│   ├── fig02_histogram_kde.png
│   ├── fig03_kde_plots.png
│   ├── fig04_ecdf.png
│   ├── fig05_preston_curve.png
│   └── ... (all 23 static + 8 interactive figures)
├── data/
│   └── README_data.md                     ← Where to download the WDI data
├── report/
│   └── LDS7004M_Final_Report.docx
├── requirements.txt
└── README.md

---

## Visualisations (31 total)

### Static Charts — Seaborn and Matplotlib (Figures 1–23)

| Figure | Chart Type | Section | Key Insight |
|---|---|---|---|
| 1 | Missing value heatmap | Data cleaning | GDP missingness concentrated 1990–1995 |
| 2 | Histogram + KDE + normal fit | Univariate EDA | GDP extreme positive skew confirms log transform needed |
| 3 | KDE plots — filled, multi-group, bimodal | Univariate EDA | Clear income group separation in life expectancy |
| 4 | ECDF plots | Univariate EDA | 100% of Low income countries below 70 years |
| 5 | Preston Curve — scatter + LOESS + OLS + 95% CI | Bivariate | r = +0.792, slope = 13.3 yrs per log-unit |
| 6 | Joint plot with marginal distributions | Bivariate | Confirms log-linear relationship shape |
| 7 | Line chart — regional trends + moving average + CI | Temporal | COVID-19 dip 2020–2021 clearly visible |
| 8 | Box plot — all structural lines annotated | Categorical | 18.4-year income group gap |
| 9 | Boxen + violin + swarm plots | Categorical | Within-group distributional heterogeneity |
| 10 | Point plot with 95% CI error bars | Categorical | Uncertainty around group means |
| 11 | Bar chart + count plot + Pareto chart | Categorical | North America + Europe = 80% of global GDP |
| 12 | lmplot — separate OLS per income group | Regression | Steepest gradient in Low income group |
| 13 | Logistic regression curve | Regression | Decision boundary at ~$15–20K GDP per capita |
| 14 | Residual plot + Q-Q plot | Regression diagnostics | Moderate heteroscedasticity at mid-income |
| 15 | Correlation heatmap + Preston Curve temporal shift | Matrix | Curve shifted upward ~5 years 1990–2022 |
| 16 | Pair plot | Multi-variable | Complete bivariate relationship structure |
| 17 | PairGrid — custom diagonal/upper/lower | Multi-variable | Three plot types in one figure |
| 18 | FacetGrid col=Income Group | Small multiples | Within-group income-health gradient |
| 19 | FacetGrid col=Region col_wrap=2 | Small multiples | South Asia +12 years since 1990 |
| 20 | Bubble chart + quadrant lines + threshold fills | Advanced overlays | Cuba over-performer, Nigeria under-performer |
| 21 | All 5 Seaborn styles | Styling showcase | whitegrid selected as default |
| 22 | All 4 Seaborn contexts | Styling showcase | notebook context used throughout |
| 23 | All 6 Seaborn colour palettes | Styling showcase | colorblind-safe palette recommended |

### Interactive Charts — Plotly (Figures P1–P8)

| Figure | Chart Type | Key Interactive Feature |
|---|---|---|
| P1 | Animated scatter — Preston Curve 1990–2022 | Play button + year slider + hover tooltips |
| P2 | Choropleth world map — life expectancy | Hover tooltips per country + zoom/pan |
| P3 | Choropleth world map — GDP per capita | Log-scale colour + hover tooltips |
| P4 | Sunburst diagram — Region → Income → Country | Click to zoom into any region or income group |
| P5 | Treemap — population by region/income | Area = population, colour = health, hover tooltips |
| P6 | Bubble chart — GDP, health, population by region | Click legend to show/hide regions |
| P7 | Stacked area chart — regional trends | Hover to see all regional values at any year |
| P8 | Parallel coordinates — income group profiles | Drag on any axis to create a brush filter |

---

## How to Run

### Option 1 — Google Colab from GitHub (Recommended — no installation needed)

Click the **Open in Colab** badge at the top of this README, or use this URL:https://colab.research.google.com/github/NK008/LDS7004M-DataViz-WDI/blob/main/LDS7004M_Advanced_Notebook.ipynb

Once open in Colab:
1. Upload the 6 WDI CSV files using the Files panel (folder icon in the left sidebar)
2. In Section 1 cell, change `DATA_DIR = '/mnt/user-data/uploads'` to `DATA_DIR = '/content'`
3. Click **Runtime → Run all** (Ctrl+F9)
4. All 23 static figures generate in approximately 4–6 minutes
5. Run the final Section 14 cell to download all 31 figures as a zip file

### Option 2 — Google Colab with Azure Blob Storage (Persistent — no re-upload needed)

If you have the WDI files stored in Azure Blob Storage, add this cell at the top of the notebook:

```python
!pip install azure-storage-blob -q
from azure.storage.blob import BlobServiceClient
import os

CONN_STR = "YOUR_AZURE_CONNECTION_STRING"
CONTAINER = "wdi-data"
LOCAL_DIR = "/content/wdi_data"

os.makedirs(LOCAL_DIR, exist_ok=True)
client = BlobServiceClient.from_connection_string(CONN_STR)
cc = client.get_container_client(CONTAINER)

for blob in cc.list_blobs():
    with open(os.path.join(LOCAL_DIR, blob.name), "wb") as f:
        f.write(cc.download_blob(blob.name).readall())
    print(f"Downloaded: {blob.name}")

DATA_DIR = LOCAL_DIR
```

### Option 3 — Local Installation

```bash
git clone https://github.com/YOUR_GITHUB_USERNAME/LDS7004M-DataViz-WDI.git
cd LDS7004M-DataViz-WDI
pip install -r requirements.txt
jupyter notebook LDS7004M_Advanced_Notebook.ipynb
```

---

## Requirements
pandas>=2.0.0
numpy>=1.24.0
matplotlib>=3.7.0
seaborn>=0.13.0
scipy>=1.10.0
statsmodels>=0.14.0
plotly>=5.15.0
kaleido>=0.2.1
azure-storage-blob>=12.0.0
jupyter>=1.0.0

---

## Cloud Infrastructure

| Service | Purpose | Details |
|---|---|---|
| Azure Blob Storage | Persistent dataset storage | Container: wdi-data, Region: UK South |
| Google Colab | Notebook execution environment | Python 3, T4 GPU runtime |
| Power BI Online | Interactive business dashboard | 6 visuals + year slicer |
| GitHub | Version control and portfolio hosting | Public repo, Colab integration |

---

## Academic References

- Preston, S.H. (1975) 'The changing relationship between mortality and level of economic development', *Population Studies*, 29(2), pp. 231–248.
- Cairo, A. (2016) *The Truthful Art: Data, Charts, and Maps for Communication*. San Francisco: New Riders.
- Tufte, E.R. (2001) *The Visual Display of Quantitative Information*. 2nd edn. Cheshire, CT: Graphics Press.
- Wilke, C.O. (2019) *Fundamentals of Data Visualisation*. Sebastopol: O'Reilly Media.
- Waskom, M.L. (2021) 'Seaborn: statistical data visualization', *Journal of Open Source Software*, 6(60).
- World Bank (2024) *World Development Indicators*. Available at: https://databank.worldbank.org [Accessed: April 2026].

---

## Licence

This project is licensed under the MIT Licence. See `LICENSE` for details.

---

*York St John University — London Campus — MSc Data Science 2025/26*
