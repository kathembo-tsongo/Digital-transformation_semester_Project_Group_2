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

## Link to Recording

View the group explanation of the project on the short link - http://tiny.cc/grp2-analytics

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
├── Group2_Digital_Transformation_Dashboard.twbx # Packaged Tableau dashboard (workbook + data bundled)
├── Group2_Digital_Transformation_Dashboard.pdf # Static PDF snapshot of the dashboard
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

An interactive Tableau dashboard built on `panel_clean.csv` gives EACO a self-service view of the analysis: 3 KPI cards, 5 interactive charts, a Country filter, and a geographic map with drill-down.

**How to access it:**

- **Interactive version (recommended):** open `Group2_Digital_Transformation_Dashboard.twbx` in [Tableau Desktop](https://www.tableau.com/products/desktop) or the free [Tableau Reader](https://www.tableau.com/products/reader). The file is self-contained — the data is bundled inside, so no extra setup is required.
- **Quick preview (no software needed):** open `Group2_Digital_Transformation_Dashboard.pdf` for a static snapshot of the dashboard.

**Using the dashboard:**

- Use the **Country filter** to focus on one or more countries across all charts at once.
- **To drill down, click on a country on the map view** — this filters every other chart on the dashboard to that country. Click empty space on the map to reset back to all countries.

## Deliverables

- [x] Python Notebook (`Digital_Transformation.ipynb`)
- [x] Raw JSON data (`raw_data.json`)
- [x] Cleaned CSV dataset (`panel_clean.csv`)
- [x] Interactive dashboard (`Group2_Digital_Transformation_Dashboard.twbx`, snapshot in `Group2_Digital_Transformation_Dashboard.pdf`)
- [x] Presentation slides(`Group 2 Capstone-Digital Transformation.pptx`)
- [x] Group member contributions

## Group Members

| Name | Contribution |
|---|---|
| _Kathembo Tsongo 112721_ | _Repos creation, Set the working Environment, Data Preparation from the WB API_ |
| _Sarah Mongare 133834_ | _Questions 1 and 2, Powerpoint_ |
| _David Gathage 223405_ | DQA, cleaning, and exploratory data analysis |
| _Mark Murungi 98283_ | _Questions 5 and 6_ |
| _Neville Masheti 138133_ | _Interactive Dashboard_ |

## How to Run

1. Open `Digital_Transformation.ipynb` in Google Colab or Jupyter
2. Run all cells top to bottom (installs dependencies automatically via `!pip install`)
3. Outputs (`raw_data.json`, `panel_clean.csv`) are regenerated in the working directory
