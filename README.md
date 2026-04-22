# Youth Drug Analysis

A machine learning project that analyzes factors associated with youth substance use using **decision trees** and **ensemble methods** in **R**.

## Overview

This project explores the **Youth Drug Analysis** dataset, a pre-cleaned subset of the **NSDUH 2023** data, to identify patterns associated with substance use among youth under 18. The analysis focuses on how demographic, social, and behavioral factors relate to alcohol and marijuana use.

The project applies three predictive tasks:

- **Binary classification**: predict whether a youth has ever consumed alcohol
- **Multi-class classification**: predict marijuana use frequency over the past year
- **Regression**: predict how many days a youth consumed alcohol in the past month

## Dataset

The dataset used in this project is a cleaned subset of the **National Survey on Drug Use and Health (NSDUH) 2023** youth data.

- Approximately **2,900** youth respondents
- **79 selected variables**
- Includes demographics, youth experiences, peer influences, and drug-use-related variables
- Variable definitions were referenced from the **NSDUH codebook**

## Methods

The modeling workflow was completed in **R / RStudio**.

### Models Used

- **Decision Tree**
- **Bagging**
- **Random Forest**
- **Boosting**

### Data Preparation

- Reviewed the NSDUH codebook for variable definitions and valid ranges
- Preserved special survey codes such as unknown/refused when appropriate
- Recoded categories into more descriptive labels
- Removed rows with remaining missing values after cleaning
- Replaced special numeric codes with the mean of valid responses where needed

## Project Goals

This project answers three main questions:

1. **Can we predict whether a youth has ever consumed alcohol?**
2. **Can we predict marijuana use frequency over the past year?**
3. **Can we predict the number of days a youth consumed alcohol in the past month?**

## Model Summary

### 1. Binary Classification

**Target:** Whether a youth has ever consumed alcohol

- A decision tree was trained and pruned to **three splits** using cross-validation
- Ensemble models were tuned for performance:
  - **Bagging**: all predictors, 500 trees
  - **Random Forest**: `mtry = 5`, 500 trees
  - **Boosting**: 1,000 trees, shrinkage = 0.01, depth = 3

**Key predictors:**

- Friends who drink daily
- Friends who use marijuana monthly

**Results:**

- **Boosting accuracy:** 80.7%
- **Random Forest accuracy:** 79.9%
- **Bagging accuracy:** 79.1%
- **Random Forest sensitivity:** 94.4%
- **Random Forest specificity:** 36.5%
- **Random Forest balanced accuracy:** 65.5%

### 2. Multi-Class Classification

**Target:** Marijuana use frequency over the past year

- Predicted across **six usage categories**
- A decision tree was trained and pruned to **three splits** using cross-validation
- Random Forest was tuned with `mtry = 5`

**Key predictors:**

- Peer marijuana use
- Peer smoking behavior
- Whether the youth was offered marijuana

### 3. Regression

**Target:** Number of days a youth consumed alcohol in the past month

- A regression tree was trained and pruned to **four nodes**
- Performance was evaluated using **MSE** and **R-squared**

**Results:**

- **Pruned tree MSE:** 1.43
- **Pruned tree R²:** 6.4%
- **Bagging with 500 trees reduced test MSE to:** 1.28

**Key predictors:**

- Friends' daily drinking
- Youth involvement in selling drugs
- Frequent family arguments

## Key Findings

- **Peer behavior** was the strongest predictor across models
- Friends’ daily drinking and monthly marijuana use were especially influential
- Ensemble methods generally performed better than a single decision tree
- The findings show **associations**, not causation

## Ethical Considerations

This project should be interpreted carefully.

- The results should **not** be used to label or stereotype young people
- The data is **self-reported**, which may introduce bias
- The youth subset may not fully represent all regions or populations
- Findings should be communicated as patterns in the data, not proof of cause and effect

## Conclusion

This study shows that decision trees and ensemble methods can be useful for understanding youth substance use patterns. The analysis suggests that **peer influences** and aspects of the **social environment** are highly associated with youth alcohol and marijuana use.

These results may help inform prevention strategies, especially those focused on peer norms, support systems, and communication around substance use risk.

## Tools

- **Language:** R
- **Environment:** RStudio
- **Methods:** Decision Trees, Bagging, Random Forest, Boosting

## Suggested Repository Structure

```bash
.
├── data/
│   └── youth_data.csv
├── scripts/
│   ├── binary_classification.R
│   ├── multiclass_classification.R
│   └── regression_model.R
├── outputs/
│   ├── plots/
│   └── model_results/
└── README.md   
```

## How to Run

1. Open the project in **RStudio**
2. Load the required packages
3. Place the cleaned dataset in the `data/` folder
4. Run the scripts for:
   - **binary classification**
   - **multi-class classification**
   - **regression**
5. Review model outputs, plots, and evaluation metrics

## Acknowledgments

- **NSDUH 2023** dataset and codebook
