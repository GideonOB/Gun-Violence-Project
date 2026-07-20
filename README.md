# Spatial and Temporal Patterns of U.S. Gun Violence: A Population-Adjusted Analysis

A reproducible R/Quarto data analysis project examining U.S. gun violence incident patterns, county-level socioeconomic conditions, geographic concentration, temporal trends, and population-adjusted incident rates.

## View Project

- [View rendered report](https://yourusername.github.io/repo-name/)
- [View source code](./Gun%20Violence.qmd)
---

## Project Overview

This project analyzes U.S. gun violence incident data alongside county/county-equivalent Census socioeconomic data to better understand where incidents are concentrated, how incident rates change over time, and how population-adjusted firearm incident rates relate to county-level poverty.

The analysis began as a classroom final project and is currently presented as a recruiter-facing portfolio project. It may later serve as the foundation for a broader research and dashboard project focused on firearm violence analytics, socioeconomic context, geographic concentration, and reproducible public-safety data reporting.

The project uses R and Quarto to clean, join, analyze, visualize, and report the data in a transparent and reproducible format.

---

## Research Questions

This project is organized around six core questions:

1. Where are gun violence incidents geographically concentrated?
2. Which states have the highest population-adjusted incident rates over time?
3. Are incidents more common in certain months or days of the week?
4. Is county poverty rate related to population-adjusted gun violence incident rates?
5. Do victim counts differ between weekday and weekend incidents?
6. What do the patterns look like in Michigan specifically?

---

## Tools and Technologies

- **R**
- **Quarto**
- **tidyverse**
- **lubridate**
- **stringr**
- **skimr**
- **naniar**
- **gt**
- **gtExtras**
- **plotly**
- **calendR**
- **readr**

---

## Data Sources

The analysis uses two main datasets:

1. **Gun Violence Archive incident data**  
   Used to analyze incident-level patterns, including date, state, city, county/county-equivalent identifier, victim counts, incident characteristics, and location fields.

2. **U.S. Census county/county-equivalent data, 2009–2023**  
   Used to recover county/county-equivalent names, join population and socioeconomic variables, and calculate population-adjusted incident rates.

Required input files:

```text
gun_violence_geo.csv
census_data_county_2009-2023.csv
```

Depending on data size and redistribution permissions, these files may not be included directly in the repository. If they are not included, place the required CSV files in the project root before rendering the Quarto report.

---

## Methodology

The project follows a full data analysis workflow:

### 1. Data Loading and Inspection

The raw gun violence incident file is loaded, inspected with `glimpse()` and `skim()`, and reviewed for variable types, missingness, and structure.

### 2. Data Cleaning

The cleaning process includes:

- converting dates into date-only format;
- extracting year, month, quarter, weekday, and weekend status;
- standardizing text fields;
- converting identifiers to character fields;
- creating total victim counts;
- creating incident severity categories;
- separating primary incident outcomes from additional incident context.

### 3. Missingness Analysis

The project examines missingness across key fields, including geographic fields, address information, business/school names, and incident characteristics. Missingness is treated as an important data-quality issue rather than ignored.

### 4. Census Join and Rate Construction

The gun violence data is joined to Census county/county-equivalent data using GEOID and year. This allows the analysis to calculate:

- incident rates per 100,000 residents;
- victim rates per 100,000 residents;
- victim-fatal incident rates per 100,000 residents.

### 5. Connecticut Geography Harmonization

Connecticut required additional handling because the Census file uses planning-region county-equivalent GEOIDs for 2022 and 2023, while the gun violence incident data still stores those records under older county GEOIDs. The project maps Connecticut city/town names to planning regions where needed to preserve usable records in the population-adjusted analysis.

### 6. Exploratory Data Analysis

The report includes summary tables and visualizations for:

- state-level incident rate trends;
- month and weekday incident patterns;
- weekday vs. weekend victim severity;
- poverty rate and incident rate relationships;
- state/jurisdiction incident rates by poverty group;
- additional incident contexts;
- Michigan area concentration;
- interactive incident mapping.

### 7. Permutation Test

A permutation/randomization test evaluates whether higher-poverty counties/county-equivalents have higher mean population-adjusted gun violence incident rates than lower-poverty counties/county-equivalents in the most recent analysis year.

---

## Key Findings

The main findings from the analysis are:

- Several high-rate states/jurisdictions show persistently elevated population-adjusted gun violence incident rates over time.
- Incidents are more concentrated on weekends and in warmer months, suggesting both weekday/weekend and seasonal patterns.
- Weekend incidents have higher average victim counts than weekday incidents.
- County/county-equivalent poverty rate has a positive but limited relationship with population-adjusted gun violence incident rates.
- Higher-poverty state/jurisdiction groups show higher distributions of average incident rates.
- Michigan incidents are strongly concentrated in Detroit, Flint, and Grand Rapids relative to their share of the state's 2020 population.
- Interactive mapping is useful for spatial exploration, but population-adjusted state and county/county-equivalent rates are more appropriate for formal geographic comparison.

---

## Project Outputs

The project currently includes:

- a full Quarto analysis report;
- data dictionary and summary tables;
- static and interactive visualizations;
- missingness and join-quality checks;
- population-adjusted rate calculations;
- a Michigan-focused concentration analysis;
- a permutation/randomization test.

This repository represents the current portfolio version of the project. The work may later be used as a stepping stone for a broader research and dashboard project, but the materials in this repository should be read as the completed current-stage analysis.

---

## Suggested Repository Structure

```text
gun-violence-socioeconomic-analysis/
├── README.md
├── FinalProject_Gideon_GunViolence.qmd
├── docs/
│   └── index.html
├── Images/
├── data/
│   └── README.md
├── outputs/
│   ├── figures/
│   └── tables/
├── .gitignore
└── LICENSE
```

---

## How to Reproduce

1. Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY-NAME.git
cd YOUR-REPOSITORY-NAME
```

2. Place the required data files in the project root:

```text
gun_violence_geo.csv
census_data_county_2009-2023.csv
```

3. Open the Quarto file in RStudio or another compatible editor.

4. Install the required R packages if needed:

```r
install.packages(c(
  "tidyverse",
  "lubridate",
  "stringr",
  "skimr",
  "naniar",
  "gt",
  "plotly",
  "gtExtras",
  "calendR",
  "readr"
))
```

5. Render the Quarto report:

```bash
quarto render FinalProject_Gideon_GunViolence.qmd
```

---

## Limitations

This project is observational and should not be interpreted as proving that poverty causes gun violence. The results show associations and descriptive patterns, not causal effects.

Additional limitations include:

- possible missing or incomplete incident records;
- dependence on the accuracy of geographic fields such as city, county, and GEOID;
- differences between incident-level geography and Census county/county-equivalent geography;
- exclusion or adjustment of records that could not be joined to population data;
- use of 2020 city population context in the Michigan-focused analysis rather than full city-year denominators.

---

## Possible Future Direction

This current repository is intended to present the completed portfolio version of the analysis. The project may later serve as a stepping stone for a broader research and dashboard project, but this README focuses on the current R/Quarto analysis rather than future deliverables.

---

## Author

**Gideon Osei Bonsu**  
Master's Student, Data Science and Analytics  
Grand Valley State University

Professional website: `Add your website link here`  
GitHub: `Add your GitHub profile link here`

---

## Notes

This project is intended for educational, portfolio, and research-development purposes. It uses publicly available data sources to demonstrate reproducible data cleaning, population-adjusted analysis, visualization, and statistical reasoning in a public-safety context.
