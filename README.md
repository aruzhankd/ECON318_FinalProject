# ECON318_FinalProject
# The Causal Effect of High vs. Low Interest Rates on Loan Default Probability

![Interest Rate Analysis](https://img.shields.io/badge/Analysis-Propensity%20Score%20Matching-blue)
![Language](https://img.shields.io/badge/Language-R-blueviolet)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📊 Project Overview

This research project investigates the causal relationship between interest rates and loan default probability, with a focus on implications for Kazakhstan's microlending sector. Using propensity score matching to address selection bias, we analyze a large dataset of over 2.2 million loans to determine whether high interest rates directly cause higher default rates.

**Key Finding:** Contrary to conventional wisdom, after controlling for selection bias, high interest rates (>20%) are associated with a **28.6% reduction in the odds of default** compared to similar loans with lower interest rates. This surprising result has significant implications for interest rate regulation.

## 🔍 Research Question

> "What is the causal effect of high interest rates (above 20%) versus low interest rates (20% and below) on borrowers' probability of loan default?"

## 📚 Repository Contents

- `econ318-finalproject-reportcode.ipynb` - Jupyter notebook containing all analysis code (developed in Kaggle)
- `README.md` - This file documenting the project
- `accepted_2007_to_2018Q4.csv` - Dataset used for the analysis (large file - stored using Git LFS)
- `/figures` - Directory containing generated visualizations:
  - Interest rate distribution
  - Default rate by interest rate range
  - Interest rate by loan grade
  - Covariate balance
  - Treatment effect estimation

## 🛠️ Methodology

This project employs a two-stage approach to establish causality:

1. **Propensity Score Matching (PSM)**: Addresses selection bias by matching loans with similar characteristics but different interest rates
2. **Logistic Regression**: Estimates the effect of high interest rates on default probability using the matched sample

### Variables Used for Matching

- Loan amount
- Loan grade (risk assessment)
- Annual income
- Term (loan duration)
- Employment length
- Home ownership status
- Verification status

## 📈 Key Visualizations

Our analysis includes five major visualizations:

1. **Interest Rate Distribution**: Shows the spread of interest rates across the dataset with a 20% threshold marker
2. **Default Rate by Interest Rate Range**: Demonstrates the raw relationship between interest rates and default rates
3. **Interest Rate Distribution by Loan Grade**: Illustrates selection bias in interest rate assignment
4. **Covariate Balance Plot**: Shows improved balance between treatment and control groups after matching
5. **Treatment Effect Visualization**: Displays the causal effect with confidence intervals

## 🔬 Results Summary

- **Raw data** shows a positive correlation between interest rates and default rates
- **After PSM**, high interest rates are associated with **lower** default probabilities (OR = 0.714, 95% CI: 0.628-0.811)
- **Key control variables**: Loan grade is the strongest predictor of default, with higher-risk grades showing 1.8-3.9 times higher odds of default
- The counterintuitive finding suggests selection bias in interest rate assignment is substantial and that high rates may serve as a screening mechanism

## 🏃‍♀ Running the Code

### Option 1: Run on Kaggle (Recommended)

1. Go to [Kaggle](https://www.kaggle.com) and log in
2. Click "Create" → "Notebook"
3. Select "File" → "Upload Notebook" and choose `econ318-finalproject-reportcode.ipynb`
4. Add the dataset:
   - Click the "Data" tab in the right sidebar
   - Click "+ Add data"
   - Search for "accepted_2007_to_2018Q4" or upload the CSV directly
5. Ensure the path matches: `/kaggle/input/accepted-2007-to-2018q4-csv/accepted_2007_to_2018Q4.csv`
6. Click the "Run All" button (▶▶) to execute all cells
7. Results and visualizations will be generated automatically

### Option 2: Run Locally

1. Install R and Jupyter Notebook with R kernel
2. Install required R packages:
   ```r
   install.packages(c("tidyverse", "MatchIt", "cobalt", "broom", "viridis", "scales"))
