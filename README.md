#  From Data to Insight: Automated Epitope Prediction Pipeline

## Table of Contents

- [Project Overview]( #Project-Overview)
- [WHY ](WHY?)
- [Data Sources](#Data-Sources)
- [Issue ](#Issue)
- [Tools for Overcoming the Issue](#Tools-for-Overcoming-the-Issue)
- [Analysis ](#Analysis)
- [Before & After](#Before-&-After)
- [Results ](#Results)
- [Limitations ](#Limitations)
- [REFERENCES](REFERENCES)
  
### Project Overview
This project is intended for researchers, data scientists, and immunology teams working on pathogen analysis, vaccine research, or epitope discovery.

A complete machine-learning pipeline was developed to predict Linear B-cell epitopes in Trypanosoma cruzi, the parasite responsible for Chagas disease.
The dataset contains 49,606 samples and 1,291 features, requiring advanced preprocessing and dimensionality reduction.
 <img width="986" alt="Variable Imbalance" src="https://github.com/user-attachments/assets/fcc468b4-aa59-4c4b-a335-d8ee0bd56d04">

### WHY
Accurate epitope prediction is essential for:
        . Vaccine candidate identification
        . Diagnostic development
        . Understanding immune response mechanisms

However, B-cell epitopes are extremely rare, and the dataset is high-dimensional and imbalanced, making prediction challenging without a structured data-mining approach.
 
### Data Sources

The primary dataset used for this analysis is the 'df.csv' file, which includes detailed information about each sample's epitopes associated with the parasite Trypanosoma cruzi.


### Issue

The raw dataset presented major obstacles:
High dimensionality (1,291 features)
Severe class imbalance (epitope-positive samples are very rare)
Missing values and noise
Risk of information loss when reducing features (PCA)
Difficulty building an interpretable, stable model

### Tools for Overcoming the Issue
Several strategies were applied:

Data Preparation

  - Cleaning and formatting
  - Handling missing values
  - Scaling and normalization

Dimensionality Reduction

  - Applying PCA to manage high dimensionality
  - Testing different numbers of components

Modeling

  - Building a full Scikit-learn pipeline for repeatable processing
  - Training and evaluating models on unseen data
  - Exploring techniques to manage class imbalance (e.g., weighting)


###  Analysis
code/features worked with
```python

# Create full pipeline
pipeline_lr = Pipeline([
    ('preprocessing', preprocessing_pipeline),
    ('classifier', classifier1)
```

### Before & After
Before (Raw Data)

  1,291 unfiltered features
  Highly imbalanced classes
  Slow training and high risk of overfitting
  Limited interpretability

After (Processed Data)

  Dimensionality significantly reduced through PCA
  Clean, normalized dataset
  End-to-end pipeline implemented
  Faster model training

Clearer understanding of epitope distribution
### Results/Findings
Predictions on the unseen dataset showed:

  - 98.82% predicted as −1 → No Linear B-cell epitope
  - 1.18% predicted as 1 → Presence of epitope

This reflects the biological reality: epitopes are rare in this parasite.
The pipeline handled the complexity well but may have lost some biological signal due to the use of Principal Component Analysis (PCA) for feature reduction.

### Limitations

- PCA may remove important biological features
- Severe class imbalance can bias predictions
- Model generalizability depends on additional datasets

### REFERENCES
1.[Epitope Mapping](https://doi.org/10.1155/2016/6760830)

2.Predictive Data Mining Models by David and Desheng.





