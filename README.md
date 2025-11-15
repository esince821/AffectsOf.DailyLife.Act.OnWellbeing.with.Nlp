# Founder-Number-and-Success-in-StartUp

## Table of Contents
- [Project Description](#project--description)  
- [Motivation](#motivation)  
- [Datasets](#dataset)  
- [Methods](#methods)  
- [Limitations & Future Work](#limitations--&--future--work)   

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

### Dataset 1: Startup Founders Dataset
* **Name:** Startup Founders Dataset  
* **Source:** Wellfound (https://wellfound.com)  
* **Link:** (manually collected data, not publicly downloadable)  
* **Data Acquisition Method:** Manually collected by browsing startup profiles on Wellfound and recording relevant fields including startup name, number of founders, industry, founded year, and funding stage. The data was exported into a CSV file (`founders.csv`) for analysis.  
---
### Dataset 2: Startup Funding Stage 
* **Name:** Startup Funding Dataset  
* **Source:** Wellfound (https://wellfound.com)  
* **Link:** (manually collected data, not publicly downloadable)  
* **Data Acquisition Method:** Manually gathered from startup pages on Wellfound, focusing on funding stages (Seed, Series A, etc.) and total funding (if listed). Saved as `funding.csv`.  
---
### Dataset 3: Sector or industry of the Startup
* **Name:** Startup Industry Dataset  
* **Source:** Wellfound (https://wellfound.com)  
* **Link:** (manually collected data, not publicly downloadable)  
* **Data Acquisition Method:** Categorized each startup by its primary industry (e.g., AI, FinTech, HealthTech, EdTech) based on its Wellfound description. Saved as `industry.csv`.  


### Key Columns for Each CSV

#### 1. `founders.csv`
| Column Name     | Description                              |
|-----------------|------------------------------------------|
| `startup_name`  | Name of the startup                       |
| `num_founders`  | Number of founding individuals           |
| `founded_year`  | Year the startup was founded             |

#### 2. `funding.csv`
| Column Name     | Description                              |
|-----------------|------------------------------------------|
| `startup_name`  | Name of the startup                       |
| `funding_stage` | Current funding stage (Seed, Series A, etc.) |
| `funding_amount`| Total funding raised (numeric, if available) |

#### 3. `industry.csv`
| Column Name     | Description                              |
|-----------------|------------------------------------------|
| `startup_name`  | Name of the startup                       |
| `industry`      | Sector or industry of the startup (e.g., AI, FinTech, HealthTech, EdTech) |

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

  WHAT DID YOU DO FOR MISSING DATA?
  HOW DİD YOU GET DATA? WEB SCRAPING

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

#### 3.4 Feature Engineering 

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
## Analysis Plan

1. **Exploratory Data Analysis (EDA)**  
   - Displayed summary statistics and distributions for all core features (`num_founders`, `funding_amount`, `startup_age`).  
   - Used `.describe()` and `.skew()` to assess spread, central tendency, and data symmetry.  
   - Generated a correlation matrix and visualized it with a heatmap.  
   - Created the following plots:  
     - Bar plots for founder count distribution.  
     - Boxplots showing funding amount across different founder counts.  
     - Count plots for funding stages.  
     - Scatter plots between number of founders and total funding.  
     - Histograms for startup age and funding distributions.  

   **Key Insights:**  
   - Most startups are founded by 2 people.  
   - Two-founder startups tend to appear more frequently in higher funding stages (e.g., Series A/B).  
   - Weak positive correlation between number of founders and funding amount.  
   - Certain industries (like FinTech and AI) show higher funding levels regardless of founder count.

---

2. **Hypothesis Testing**

   **Hypotheses:**  
   - **H₀ (Null):** There is no statistically significant relationship between the number of founders and the funding stage of a startup.  
   - **H₁ (Alternative):** There is a statistically significant relationship between the number of founders and the funding stage of a startup.

   **Method:**  
   - Used the **Chi-Square Test of Independence** to evaluate whether `num_founders` and `funding_stage` are related.  
   - Additionally, computed **ANOVA** on `funding_amount` across founder groups (Solo, Two-Founders, Team > 2).  

   **Results:**  
   - *Chi-Square p-value ≈ 0.018* → Reject the null hypothesis at α = 0.05.  
   - *ANOVA F-statistic significant (p < 0.05)* → Founders count influences funding amount.  
   - Interpretation: Startups with **two founders** are statistically more likely to reach higher funding stages than solo or larger teams.
---

## Timeline
| Task | Deadline |
|------|----------|
|Project Proposal Submission| October 31, 2025|

---
## Limitations and Future Work

### Limitations
- **Manual Data Collection:** The data was manually gathered from Wellfound, which limits sample size and may introduce selection bias (only startups with public profiles are included).  
- **Missing or Incomplete Fields:** Some startups lacked detailed funding or founder information, reducing data completeness.  
- **Cross-Sectional Nature:** The dataset represents a single point in time, making it difficult to infer causal relationships between founder count and startup success.  
- **Uncontrolled Factors:** Other variables such as team experience, product type, market conditions, or geographic region were not included but may influence funding outcomes.  
- **Approximation in Funding Amounts:** Inconsistent currency formats and missing values required normalization and estimation.

write this-> in the industry part I too generalized, i.e. wrote fintech for both fintech elec market etc. ALSO since I collect manually it can e minor mistakes
---

### Future Work
- **Expand Dataset:** Collect a larger and more diverse dataset, including international startups and additional success metrics (e.g., revenue, exit status).  
- **Automate Data Collection:** Implement web-scraping or API-based collection from platforms like Crunchbase or PitchBook for greater scalability.  
- **Longitudinal Analysis:** Track startups over multiple years to observe how founder composition affects long-term performance.  
- **Advanced Modeling:** Apply regression or machine learning models to predict funding success based on founder count and industry.  
- **Broader Variables:** Incorporate qualitative factors such as founder background, education, and experience for a deeper understanding of team dynamics.
