
---

# Querying Census Data for Socio-Ecological Research

---

## Overview


This project was developed to enable **reproducible, efficient access to detailed census block group and tract-level data** for environmental and socio-demographic research. It supports analyses that examine the **human and environmental consequences of structural inequality**, particularly through the lens of **race, income, housing**, and related social indicators. Although the current version does not include ecological outcome layers (such as tree canopy density or pollution exposure), it establishes a scalable infrastructure for linking those datasets in future analyses.


## Designed for Reproducible Research

Conducting socio-ecological research in the United States remains unnecessarily difficult. While rich public datasets exist—from the U.S. Census Bureau, EPA, and other agencies—few clear examples demonstrate how to join spatial and social data at meaningful geographic scales for statistical analysis. Many official tools are either built for casual exploration or lack compatibility with spatial workflows. Tools like data.census.gov remain overcomplicated to use and does not allow for a reproducible data flow. This project emerged from the need to develop transparent, scalable workflow for accessing census data, particularly when linking it to environmental indicators like facility location, pollution burden, or climate risk.

---

```{r acs-variable-table, message=FALSE, warning=FALSE}

library(tibble)

# Defined ACS variables with code and description
acs_variable_rationale <- tribble(
  ~`Variable Name`, ~`ACS Code`, ~`Description`,
  "pop",           "B03002_001", "Total population",
  "pop_nhwhite",   "B03002_003", "Non-Hispanic White",
  "pop_nhblack",   "B03002_004", "Non-Hispanic Black",
  "popx_nhamind",  "B03002_005", "Non-Hispanic American Indian/Alaska Native",
  "popx_nhasian",  "B03002_006", "Non-Hispanic Asian",
  "popx_nhhwnpi",  "B03002_007", "Non-Hispanic Hawaiian or Pacific Islander",
  "popx_nhother",  "B03002_008", "Non-Hispanic Other Race",
  "popx_nhtwomr",  "B03002_009", "Non-Hispanic Two or More Races",
  "pop_hispltx",   "B03002_012", "Hispanic or Latinx (any race)",
  "hu_total",      "B25001_001", "Total housing units",
  "hu_totocc",     "B25003_001", "Occupied housing units",
  "hu_totown",     "B25003_002", "Owner-occupied housing units",
  "hu_totrnt",     "B25003_003", "Renter-occupied housing units",
  "hh_total",      "B19001_001", "Total number of households",
  "hh_medinc",     "B19013_001", "Median household income"
)

print(acs_variable_rationale)

```
Each variable listed above can be used to calculate proportions of racial/ethnic groups or housing conditions at the block group level. These metrics form the core of spatial demographic analysis and can be joined with environmental data to conduct environmental justice assessments.

This repository does not contain environmental or health outcome data, however it establishes the demographic and spatial infrastructure necessary to:
- Link to environmental exposure datasets (e.g., EPA GHGRP, FRS, TRI)
- Assess social vulnerability and racialized exposure to environmental risks
- Conduct spatial inequality or environmental justice analyses

The dataset can be easily extended to integrate additional spatial layers such as:
- Pollution exposure data (e.g., PM2.5 models, regulatory emissions)
- Climate vulnerability indices (e.g., CDC SVI, CalEnviroScreen)
- EPA facility databases (e.g., FRS, CAMD, ECHO)

Users can edit the script to adjust data by the census block, census tract, county, or state level. The data is designed to be used with the `sf` package in R, which allows for easy manipulation and visualization of spatial data.

---

Citation

Walker, K. (2023). tidycensus: Load US Census Boundary and Attribute Data as ‘tidyverse’ and ‘sf’-Ready Data Frames. R package version 1.4.4. https://walker-data.com/tidycensus/

U.S. Census Bureau. American Community Survey 5-Year Data (2016–2020). https://www.census.gov/data/developers/data-sets/acs-5year.html

---
