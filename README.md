# Opioid Mortality Risk in Georgia Counties

An interactive dashboard exploring county-level opioid mortality risk across Georgia's 159 counties using Bayesian spatial modeling.

🔗 **[View Live Dashboard](https://feiran924.github.io/opioid-dashboard/)**

---

## About This Project

This dashboard presents results from a **BYM2 (Besag-York-Mollié 2) spatial model** fitted via INLA, examining how distance to substance use treatment facilities and county demographic composition relate to opioid mortality risk in Georgia (2022). The analysis includes two focal variables and nine confounders, revealing a **suppression effect**: neither focal variable is statistically significant in simple models, but both emerge as significant under full multivariate adjustment.

## Visualizations

| Widget | Type | Description |
|--------|------|-------------|
| Widget 1 | Interactive Leaflet Map | Geographic distribution of county-level posterior mean relative risk (RR); hover/click for county statistics |
| Widget 2 | Interactive Plotly Scatter | Poverty rate vs. opioid mortality risk, colored by risk category; point size encodes distance to nearest SU facility |

## Data Sources

- **Opioid mortality:** Georgia Department of Public Health (2022 vital statistics)
- **Socioeconomic covariates:** U.S. Census Bureau ACS 5-year estimates (2018–2022)
- **Treatment facility distances:** [SAMHSA Treatment Locator](https://www.samhsa.gov) and [HRSA Data Warehouse](https://data.hrsa.gov)

## Repository Contents

```
├── interactive_widgets_dashboard.Rmd   # Source code (flexdashboard)
├── index.html                          # Knitted dashboard (GitHub Pages)
└── README.md
```

> **Note:** Source data (`ga_opioid_data_updated_final.rds`) is not included in this repository as it contains county-level health data. Contact the author for data access inquiries.

## Impact

Opioid overdose remains a leading cause of preventable death in the United States, claiming over 80,000 lives annually, with rural and underserved communities facing disproportionate burden due to limited access to treatment. This dashboard enables public health officials and policymakers to identify high-risk Georgia counties and understand how treatment facility access compounds socioeconomic disadvantage, supporting more equitable and data-driven resource allocation.

## Methods

- **Model:** BYM2 spatial Poisson model via INLA
- **Software:** R (`flexdashboard`, `leaflet`, `plotly`, `INLA`, `sf`, `spdep`)
- **Spatial structure:** Queen contiguity adjacency matrix across 159 Georgia counties
- **Prior:** Uniform(0,1) [logitbeta(1,1)] for spatial mixing parameter φ; PC prior for precision

## Author

Feiran Zhang — Department of Biostatistics and Bioinformatics, Emory University
