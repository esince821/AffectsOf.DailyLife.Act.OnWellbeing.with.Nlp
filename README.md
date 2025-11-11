# Founder-Amount-and-Success-in-StartUp
# Startup Founder Analysis: Number of Founders vs. Success

## Table of Contents
- [Overview](#overview)  
- [Motivation](#motivation)  
- [Dataset](#dataset)  
- [Methods](#methods)  
- [Results & Discussion](#results--discussion)   

---

## Overview
This project investigates how the number of founders of a startup correlates with success indicators such as funding stage and longevity.  
Although many startups are founded by two people (often hypothesized as one with technical skills and one with business skills), this analysis aims to validate that pattern using real‑world data.

---

## Motivation
Understanding team structures in early‑stage ventures is valuable for both entrepreneurs and investors.  
Questions we address include:  
- What is the typical number of founders in startups?  
- Do startups with two founders outperform those with one or more than two founders?  
- Is there an industry‑specific pattern in founder count?

---

## Dataset
Dataset 1: Startup Founders Dataset

Dataset 2: Startup Funding Stage 

 
- Manual collection via AngelList 

**Key Columns:**
| Column Name     | Description                                  |
|------------------|----------------------------------------------|
| `startup_name`   | Name of the company                           |
| `num_founders`   | Number of founding individuals                |
| `industry`       | Sector or industry of the startup             |
| `founded_year`   | Year the startup was founded                  |
| `funding_stage`  | Current or highest funding stage (Seed, A, B…) |
| `funding_amount` | Total funding raised (if available)           |
| `country`        | Country or region where the startup is based |

**Notes:**  
Data cleaning was performed to remove duplicates, standardize industry names, and convert funding figures into numeric format.

---

## Methods
The following steps outline the methodology:
1. **Data collection:** Selected startups, extracted founder count and success metrics.  
2. **Data cleaning & preparation:** Handled missing values, normalized categories, formatted data.  
3. **Exploratory data analysis:**  
   - Calculated descriptive statistics for `num_founders`.  
   - Plotted distribution of founder counts (histogram/bar chart).  
   - Examined relationship between `num_founders` and `funding_amount`, and `funding_stage` (scatter plots, boxplots).  
4. **Interpretation:** Discussed findings in terms of probable business/technical alignment, team size dynamics, and industry context.

---

## Timeline


## Results & Discussion
- Expectation: Two‑founder teams are the most common in the dataset.  
- Preliminary observation: Startups with two founders may show higher average funding or longer survival time compared to solo‑founder or larger teams.  
- Potential explanations: Complementary skills in two‑person teams, simpler decision making, balanced division of labor.  
- Limitations: Data may be biased by publicly visible startups (survivorship bias), missing funding data, regional differences.

