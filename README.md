# Customer Attrition Risk Prediction | Graduate Predictive Modeling Project

## Project Status

**Phase:** Final Models — Complete ✅

**Timeline:**
- **Analytic Plan:** Submitted to `reports/01 analytic plan/`
- **Preliminary Results:** Submitted to `reports/02 preliminary results/` with feedback addressed
- **Final Models & Report:** Completed in `reports/03 final report and appendices/`

**Deliverable:** [DSE6111_FinalPresentation_JMLemieux.pdf](reports/03%20final%20report%20and%20appendices/DSE6111_FinalPresentation_JMLemieux.pdf)

---

## Project Overview

This project investigates the risk determination and feature identification of customer attrition using supervised classification modeling. The client company faces customer attrition (churn) that impacts revenue and growth. This analysis aims to **identify high-risk customers most likely to leave** so the company can proactively intervene with targeted retention efforts, optimize marketing spend, and improve customer lifetime value.

## Purpose & Business Impact

### Primary Objective
Develop a reliable predictive model to identify at-risk customers and enable data-driven retention strategies.

### Business Outcomes
The client company will use the developed predictive model to:
- **Customer Targeting:** Identify and prioritize high-risk customers most likely to churn for immediate intervention
- **Retention Strategy:** Focus limited retention resources on customers with highest churn probability for maximum ROI
- **Marketing Efficiency:** Efficiently target retention and engagement efforts based on attrition risk scores
- **Feature Insights:** Understand key drivers and customer behaviors that signal imminent attrition
- **Segmentation:** Develop personalized retention offers tailored to different customer risk segments
- **Resource Allocation:** Optimize budget and staffing allocation based on predicted churn volumes

## Key Findings

**Best Performing Model:** XGBoost (Full Feature Set)
- See [SummarizedMetrics.xlsx](testing%20and%20output/SummarizedMetrics.xlsx) for detailed performance comparison across all models
- Outperforms baseline and alternative approaches (Logistic Regression, kNN, Naive Bayes, Random Forest)

**Top Features Influencing Attrition:**
- See Feature Importance analysis in final report and individual model appendices
- Key drivers include customer engagement metrics, account tenure, and transaction patterns

**Business Recommendations:**
- See [DSE6111_FinalPresentation_JMLemieux.pdf](reports/03%20final%20report%20and%20appendices/DSE6111_FinalPresentation_JMLemieux.pdf) for strategic recommendations and deployment guidance
- Includes implementation roadmap, risk scoring strategy, and actionable retention tactics

---

## Data & Problem Scope

**Dataset:** Client-provided customer database
- **Size:** 10,000 customer records
- **Features:** 21 customer attributes including demographics, account information, and engagement metrics
- **Target Variable:** Binary classification (Customer Attrition vs. Retention)
- **Business Context:** Supervised learning problem to support proactive customer retention strategy

## Project Phases

This project addresses three sequential phases:

### Phase 1: Develop an Analytic Plan
* Propose a supervised classification problem (binary target: customer attrition vs. retention)
* Identify the target variable and feature set
* Determine necessary data processing steps
* Identify and engineer features as needed
* Document expected analytic and informational outcomes

### Phase 2: Perform Preliminary Analysis
* Execute data processing steps
* Create additional engineered features
* Train initial logistic regression and kNN models
* Evaluate models and determine refinements
* Identify additional data processing and feature engineering needs

### Phase 3: Conclude and Present Final Results
* Revise preliminary models as needed
* Compare performance of **6 candidate models** + baseline:
  - Null Model (baseline for comparison)
  - Logistic Regression
  - k-Nearest Neighbors (kNN)
  - Naive Bayes
  - Random Forest
  - XGBoost
* Select model most appropriate for this business need
* Determine most important features influencing customer attrition
* Discuss practical deployment and future research directions

---

## Project Structure

```
predictive-modeling/
├── code/                                # R Markdown notebooks for analysis
│   ├── 02 preliminary results/          # Initial findings and exploratory analysis
│   │   └── DSE6111_PrelimResults_receiped_JLemieux.Rmd
│   └── 03 final models/                 # Final model iterations and deliverables
│       ├── DSE6111_FullNull.Rmd
│       ├── DSE6111_FullLogistic.Rmd
│       ├── DSE6111_FullKNN.Rmd
│       ├── DSE6111_FullnaiveBayes.Rmd
│       ├── DSE6111_FullRandomForest.Rmd
│       ├── DSE6111_FullXGBoost.Rmd
│       ├── DSE6111_JustLogistic.Rmd
│       ├── DSE6111_JustKNN.Rmd
│       ├── DSE6111_JustnaiveBayes.Rmd
│       ├── DSE6111_JustRandomForest.Rmd
│       └── DSE6111_JustXGBoost.Rmd
├── data/                                # Project datasets
│   └── customer_data_1.csv              # Main customer dataset
├── images/                              # Visualizations for reports
├── reports/                             # Formal report deliverables
│   ├── 01 analytic plan/
│   ├── 02 preliminary results/
│   └── 03 final report and appendices/
├── instructions and feedback/           # Project requirements and feedback
└── testing and output/                  # Metrics comparison and model outputs
    ├── SummarizedMetrics.xlsx
    └── xgBoost_test_results.xlsx
```

---

## Model Comparison Methodology

**Null Model Baseline:**
All models are compared against a null model (always predicting the most common class). This ensures we validate that each model provides genuine predictive value over the baseline and understand the performance gain from each approach.

**Evaluation Metrics:**
- **Accuracy** — Overall classification correctness
- **ROC Curve & AUC** — Sensitivity/specificity trade-offs across classification thresholds
- **Cross-Validation** — 10-fold cross-validation for robust performance estimates

**Model Variants:**
- **Full Models:** Use all available customer features for maximum information
- **Selected Feature Models ("Just"):** Use engineered features identified as most predictive (feature engineering validation)

All models include:
- Data preprocessing (dummy variable encoding, centering, scaling)
- Hyperparameter tuning via cross-validation
- Feature importance analysis

---

## Quick Start: How to Run the Models

### Prerequisites
Ensure R and RStudio are installed, and required packages are loaded (see [R Dependencies](#r-dependencies)).

### Running a Single Model
1. Open an R Markdown file from `code/03 final models/` (e.g., `DSE6111_FullXGBoost.Rmd`)
2. In RStudio, click **Knit** or use `Ctrl+Shift+K`
3. The HTML report will be generated with:
   - Data preprocessing steps
   - Model training and cross-validation results
   - Performance metrics and ROC curves
   - Feature importance rankings

### Comparing All Models
- Open `testing and output/SummarizedMetrics.xlsx` for a side-by-side comparison of all model performance metrics
- See `testing and output/xgBoost_test_results.xlsx` for detailed XGBoost variant testing

### Viewing Final Recommendations
- Open [DSE6111_FinalPresentation_JMLemieux.pdf](reports/03%20final%20report%20and%20appendices/DSE6111_FinalPresentation_JMLemieux.pdf) for:
  - Executive summary and key findings
  - Model selection rationale
  - Feature importance interpretation
  - Business application strategies
  - Future research recommendations

---

## R Dependencies

Key packages used across analyses:
- **Data Wrangling:** `tidyverse`, `dplyr`, `tidyr`, `stringr`
- **Visualization:** `ggplot2`, `gridExtra`
- **Modeling & Evaluation:** `caret`, `glmnet`, `kknn`, `naivebayes`, `ranger`, `xgboost`
- **Model Evaluation:** `pROC`, `yardstick`
- **Reporting:** `rmarkdown`, `knitr`

Install all dependencies:
```r
packages <- c("tidyverse", "dplyr", "tidyr", "stringr", "ggplot2", "gridExtra",
              "caret", "glmnet", "kknn", "naivebayes", "ranger", "xgboost", 
              "pROC", "yardstick", "rmarkdown", "knitr")
install.packages(packages)
```

---

## Tools & Technologies

| Tool | Purpose |
|------|---------|
| **R Studio** | Prototyping, analysis, and documentation |
| **R** | Data wrangling, statistical analysis, plotting (tidyverse, dplyr, ggplot2) |
| **MS Excel** | Dataset review and metrics comparison |
| **GitHub** | Version control and project management |

---

## Attribution

**Student:** J. Lemieux  
**Course:** DSE6111 — Predictive Modeling  
**Date Completed:** December 2024
