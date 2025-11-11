# Founder-Amount-and-Success-in-StartUp

## Table of Contents
- [Project Description](#project--description)  
- [Motivation](#motivation)  
- [Dataset](#dataset)  
- [Methods](#methods)  
- [Results & Discussion](#results--discussion)   

---

## Project Description
This project investigates how the number of founders of a startup correlates with success indicators such as funding stage(the level of investment a startup has reached, e.g., Seed, Series A, etc.) and longevity.
Although many startups are founded by two people (often hypothesized as one with technical skills and one with business skills), this analysis aims to validate that pattern using real‑world data.

---

## Motivation
Understanding team structures in early‑stage ventures is valuable for both entrepreneurs and investors.  
Questions we address include:  
- What is the typical number of founders in startups?  
- Do startups with two founders outperform those with one or more than two founders?  
- Is there an industry‑specific pattern in founder count?

---

## Datasets

Dataset 1: Startup Founders Dataset
* **Name:** Startup Founders Dataset  
* **Source:** Wellfound (https://wellfound.com)  
* **Link:** (manually collected data, not publicly downloadable)  
* **Data Acquisition Method:** Manually collected by browsing startup profiles on Wellfound and recording relevant fields including startup name, number of founders, industry, founded year, and funding stage. The data was exported into a CSV file (`founders.csv`) for analysis.  
---
Dataset 2: Startup Funding Stage 
* **Name:** Startup Funding Dataset  
* **Source:** Wellfound (https://wellfound.com)  
* **Link:** (manually collected data, not publicly downloadable)  
* **Data Acquisition Method:** Manually gathered from startup pages on Wellfound, focusing on funding stages (Seed, Series A, etc.) and total funding (if listed). Saved as `funding.csv`.  
---
Dataset 3: Sector or industry of the Startup
* **Name:** Startup Industry Dataset  
* **Source:** Wellfound (https://wellfound.com)  
* **Link:** (manually collected data, not publicly downloadable)  
* **Data Acquisition Method:** Categorized each startup by its primary industry (e.g., AI, FinTech, HealthTech, EdTech) based on its Wellfound description. Saved as `industry.csv`.  
---

**Key Columns:**
| Column Name     | Description                                  |
|------------------|----------------------------------------------|
| `startup_name`   | Name of the company                           |
| `num_founders`   | Number of founding individuals                |
| `industry`       | Sector or industry of the startup             |
| `founded_year`   | Year the startup was founded                  |
| `funding_stage`  | Current or highest funding stage (Seed, A, B…) |
| `funding_amount` | Total funding raised (if available)           |


---

## Methods
### 1. Data Collection

- Extracted data from Wellfound startup pages.

- Manually recorded structured fields (founder count, funding stage, etc.).

- Saved as .csv files for analysis.

### 2. Data Cleaning and Preparation

- Combined datasets (founders.csv, funding.csv, industry.csv) on startup_name.

- Removed duplicates and startups with missing essential fields (e.g., num_founders).

- Standardized funding_stage (e.g., unified “Series-A” and “Series A”).

- Converted funding_amount to numeric (removing $, M, K symbols).

-Created additional columns:

  startup_age = 2025 - founded_year

  funding_log = log(funding_amount + 1) (to normalize skewed data).

### 3. Exploratory Data Analysis (EDA) Pipeline

- A more advanced and reproducible EDA pipeline will include:

#### 3.1 Descriptive Statistics

- Summary statistics for numeric variables (num_founders, funding_amount, startup_age).

- Frequency table for categorical variables (funding_stage, industry).

- Cross-tabulation: num_founders × funding_stage.

#### 3.2 Visualization Suite

| Goal                                             | Visualization Type                      | Tool/Library            |
| ------------------------------------------------ | --------------------------------------- | ----------------------- |
| Founder count distribution                       | Bar plot / Histogram                    | `matplotlib`, `seaborn` |
| Funding stage proportions                        | Pie chart / Count plot                  | `seaborn`               |
| Relationship between founders and funding amount | Boxplot or Violin plot                  | `seaborn`               |
| Correlation heatmap                              | Heatmap (funding_amount, founders, age) | `seaborn`               |
| Industry vs founder count                        | Stacked bar chart                       | `pandas`, `matplotlib`  |
| Funding stage vs age                             | Boxplot                                 | `seaborn`               |

#### 3.3 Statistical Testing

- ANOVA / Kruskal-Wallis Test: To test if funding amounts differ significantly between groups with different founder counts.

- Chi-Square Test: To test if num_founders and funding_stage are independent.

- Correlation Analysis: Between num_founders and funding_amount.

#### 3.4 Feature Engineering (Optional)

- Encode categorical variables (funding_stage, industry) numerically.

- Create founder_group categories: Solo, Two-Founder, Team (>2).

#### 3.5 Reproducibility

- Implement the full EDA in a Jupyter Notebook (eda.ipynb).

- Use modular code blocks:

  data_cleaning.py

  eda_visuals.py

  stat_tests.py

- Export all figures automatically to a /figures directory.

---

## Timeline
| Task | Deadline |
|------|----------|
|Project Proposal Submission| October 31, 2025|
## Results & Discussion
- Expectation: Two‑founder teams are the most common in the dataset.  
- Preliminary observation: Startups with two founders may show higher average funding or longer survival time compared to solo‑founder or larger teams.  
- Potential explanations: Complementary skills in two‑person teams, simpler decision making, balanced division of labor.  
- Limitations: Data may be biased by publicly visible startups (survivorship bias), missing funding data, regional differences.

