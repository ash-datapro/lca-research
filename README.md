# How Do Mental Health and Healthcare Access Shape Diabetes Risk?

*A Study of Understudied Populations Using Latent Class Analysis and Factor Analysis*

Dataset: [https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset)

Research Summary (PDF): [https://github.com/ash-datapro/lca-research/blob/main/ResearchSummary.pdf](https://github.com/ash-datapro/lca-research/blob/main/ResearchSummary.pdf)

---

## Overview

This research investigates how healthcare access, health-related behaviors, and unobserved population traits relate to diabetes risk, with emphasis on a vulnerable subgroup reporting poor mental health and limited access to care. Using data from the 2015 BRFSS, we apply Factor Analysis and Latent Class Analysis (LCA) to uncover latent health profiles and assess their association with diabetes status. 

---

## Objectives

* Identify latent subpopulations that differ systematically in health behaviors and risk factors. 
* Examine how lifestyle patterns within an underrepresented group (≥15 poor-mental-health days/month and no healthcare access) relate to diabetes outcomes. 
* Use model-based evidence to inform targeted interventions for at-risk groups. 

---

## Data

* Source: BRFSS 2015 (441,456 records; 330 variables). Survey uses stratified telephone sampling with weighting to improve representativeness. 
* Study subset: Focus on individuals reporting ≥15 days/month of poor mental health and lacking healthcare access (n = 1,462). 
* Selected variables: 22 features spanning clinical indices (e.g., blood pressure, cholesterol, BMI), behaviors (smoking, physical activity, fruit/vegetable intake), self-reported health, and demographics. Non-categorical variables were binned for model compatibility (e.g., BMI dichotomized; general health recoded). 

---

## Methods

### Preprocessing

* Filtering and feature engineering conducted in R (e.g., *dplyr*).
* Harmonization via binning/recoding to align measurement scales across variables (e.g., reverse-coding to align health implications where appropriate). 

### Factor Analysis

* Suitability checks: Bartlett’s Test χ² = 1897.804 (p ≈ 0), KMO = 0.73 (all variables ≥ 0.5). 
* Parallel analysis indicated **4 factors** as optimal. 
* Interpretable factors included:

  * **General health/physical functioning** (e.g., physical health, difficulty walking, general health).
  * **Dietary habits** (fruits, vegetables).
  * **Cardiovascular indices** (high blood pressure, high cholesterol).
  * **Substance use/weight** (smoking, alcohol; inverse loading for BMI). 

### Latent Class Analysis (LCA)

* Model selection via **BIC**, testing 1–7 classes; **4-class** solution minimized BIC. 
* Variables used aligned with Factor Analysis (binning maintained; reverse coding unnecessary for LCA). 

---

## Results

### Latent Classes (Health Profiles)

* **Class 1 – Relatively Healthy**: Lowest poor general/physical health; highest physical activity.
* **Class 2 – Moderately Healthy with High Awareness**: Highest fruit/vegetable intake; lowest high blood pressure; paradoxically high self-reported poor physical health.
* **Class 3 – Unhealthy with Poor Awareness**: High poor physical health; lowest vegetable intake; minimal fruit intake; low activity.
* **Class 4 – High-Risk**: High unhealthy BMI, poor general health, and high blood pressure. 

### Association with Diabetes Status

* Diabetes status categories: 0 (no diabetes), 1 (pre-diabetes), 2 (diabetes).
* Class-wise “no diabetes” proportions: **C1: 0.914**, **C2: 0.827**, **C3: 0.681**, **C4: 0.557**; pattern aligns with increasing risk from C1→C4. 
* Statistical validation: χ² = **191** (df = 6, p < 2.2e-16); ANOVA **F = 69.23** (p < 2.2e-16), supporting a non-trivial association between latent classes and diabetes risk. 

---

## Key Insights

* Unsupervised methods (Factor Analysis + LCA) reveal coherent, actionable health profiles within an understudied subgroup lacking healthcare access and experiencing poor mental health. 
* Dietary patterns, cardiovascular markers, and physical functioning jointly differentiate risk strata with clear gradients in diabetes prevalence. 
* Findings support tailored intervention design for the most vulnerable classes (e.g., targeted education and preventative care for Classes 3–4). 

---

## Reproducibility & Workflow

1. **Data acquisition** from BRFSS 2015 and subsetting the target population. 
2. **Preprocessing** in R (filtering, binning, selective reverse-coding; feature set = 22 variables). 
3. **Factor Analysis** (Bartlett/KMO checks; parallel analysis → 4 factors; interpretation of loadings). 
4. **LCA** (BIC-based model selection → 4 classes; profiling of each class). 
5. **Validation** (class × diabetes association via χ² and ANOVA). 

---

## Data Access

* **Primary dataset**: BRFSS Diabetes Health Indicators (Kaggle)
  [https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset)

---

## Acknowledgment of AI Usage

AI tools supported preprocessing, grammatical refinement, and visualization optimization; all outputs were reviewed for accuracy and academic integrity compliance. 

---

## References (Selected)

Representative prior work employing LCA for chronic disease and metabolic risk profiling informed the study design and interpretation. See the Research Summary for full citations. 

---

*This README summarizes the project’s scope, design, and findings. For detailed tables, figures (e.g., correlation heat map, parallel analysis scree, class profiles), and complete methodology, refer to the Research Summary PDF.* 
