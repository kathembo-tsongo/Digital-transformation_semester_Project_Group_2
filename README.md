# Digital-transformation_semester_Project_Group_2

Digital technologies have transformed education, commerce, healthcare, government services, and financial inclusion. However, digital access remains uneven across East Africa. As a team, we were engaged by the **East African Communications Organisation (EACO)** to evaluate the progress of digital transformation within East Africa, using World Bank Open Data to answer six research questions and produce evidence-based policy recommendations.

## Project Overview

This project retrieves, cleans, and analyzes World Bank indicator data (2010–2024) for East African countries to assess digital inclusion progress and give EACO actionable, evidence-backed recommendations.

**Countries covered:** Kenya, Tanzania, Uganda, Rwanda, Burundi, Ethiopia, South Sudan, Somalia

**Indicators used:**
| World Bank Code | Indicator |
|---|---|
| `IT.NET.USER.ZS` | Internet users (% of population) |
| `IT.CEL.SETS.P2` | Mobile cellular subscriptions (per 100 people) |
| `EG.ELC.ACCS.ZS` | Access to electricity (% of population) |

## Research Questions

1. Which East African country has experienced the highest growth in internet users between 2010 and 2024?
2. How does internet penetration compare with mobile-phone subscriptions across the selected countries?
3. Is access to electricity associated with higher internet usage?
4. Which country has the largest gap between mobile-phone ownership and internet usage?
5. How does Kenya compare with the other East African countries in terms of digital transformation?
6. Which three policy interventions would accelerate digital inclusion within the East African region?

## Repository Structure
├── Digital_Transformation.ipynb # Main analysis notebook (data retrieval → EDA → stats → viz → recommendations)
├── raw_data.json # Raw API response, saved before cleaning
├── panel_clean.csv # Cleaned, wide-format dataset (dashboard data source)
├── raw_world_bank_data.zip # Archived raw pull from the World Bank API
├── clean_data/ # Supporting cleaned data files
├── raw_data/ # Supporting raw data files
├── LICENSE
└── README.md
## Methodology

- **Data retrieval:** World Bank API v2 (`https://api.worldbank.org/v2`), fetched programmatically via Python `requests`
- **Data Quality Assessment:** missing values, duplicate records, outlier detection (1.5×IQR), completeness, and consistency checks
- **Cleaning:** deduplication on `(country, year, indicator)`, dropped missing values, range-clipped percentage indicators to [0, 100]
- **Statistical techniques:**
  - Pearson & Spearman correlation (electricity vs. internet access)
  - OLS regression with clustered standard errors (electricity + mobile → internet)
  - Trend analysis (CAGR and absolute growth, 2010–2024)
  - Forecasting (Holt's linear trend method, projected to 2028)
- **Visualizations:** bar charts, grouped/horizontal bar charts, scatter plots, correlation heatmap, small multiples, historical + forecast line chart — each with a written justification for chart choice

## Dashboard

*(In progress)* An interactive dashboard (Streamlit) will provide KPI cards, filterable charts, a geographic map, and drill-down views built on `panel_clean.csv`, for EACO to explore the data directly.

## Deliverables

- [x] Python Notebook (`Digital_Transformation.ipynb`)
- [x] Raw JSON data (`raw_data.json`)
- [x] Cleaned CSV dataset (`panel_clean.csv`)
- [ ] Interactive dashboard
- [x] Presentation slides(`Group 2 Capstone-Digital Transformation.pptx`)
- [ ] Group member contributions

## Group Members

| Name | Contribution |
|---|---|
| _Kathembo Tsongo 112721_ | _Repos creation, Set the working Environment, Data Preparation from the WB API_ |
| _Sarah Mongare 133834_ | _Questions 1 and 2, Powerpoint_ |
| _David Gathage 223405_ | DQA, cleaning, and exploratory data analysis |
| _Mark_ | _Questions 5 and 6_ |
| _Neville Masheti_ | _Interactive Dashboard_ |

## How to Run

1. Open `Digital_Transformation.ipynb` in Google Colab or Jupyter
2. Run all cells top to bottom (installs dependencies automatically via `!pip install`)
3. Outputs (`raw_data.json`, `panel_clean.csv`) are regenerated in the working directory
