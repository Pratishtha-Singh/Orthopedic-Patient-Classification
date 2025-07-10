# Orthopedic-Patient-Classification

---

## Project Overview

This project focuses on classifying orthopedic patients into Normal (NO) and Abnormal (AB) categories using six biomechanical features of the spine and pelvis. The goal is to provide a reliable diagnostic aid for healthcare professionals by leveraging machine learning techniques. We have implemented one Supervised Learning method (KNN) and one Unsupervised Learning we utilized a Gaussian Mixture Model(GMM) with Expectation-Maximization(EM) algorithm on a reduced feature set using PCA for better interpretability.

---

## Contents

- [Data](#data)  
- [Preprocessing & Cleaning](#preprocessing--cleaning)  
- [Feature Engineering](#feature-engineering)  
- [Exploratory Data Analysis](#exploratory-data-analysis)  
- [Modeling](#modeling)  
- [Results & Evaluation](#results--evaluation)  
- [Project Structure](#project-structure)  
- [Dependencies](#dependencies)  

---

## Data

The dataset consists of:
- 310 patient records
- Biomechanical attributes:
    Pelvic Incidence
    Pelvic Tilt
    Lumbar Lordosis Angle
    Sacral Slope
    Pelvic Radius
    Grade of Spondylolisthesis
- Class label: Normal or Abnormal

---

## Preprocessing & Cleaning

- Added column headers based on metadata.
- Converted all feature columns to numeric types (float64).
- Checked for and confirmed no missing values.
- Balanced class distribution using SMOTE, increasing total samples to 398.

---

## Feature Engineering

- **Skew Adjustment:** Shifted and log‑transformed the grade_of_spondylolisthesis to correct skewness and handle negative values.
- **Scaling:** Applied MinMax scaling to normalize all features between 0 and 1.
- **Dimensionality Reduction:** Performed PCA and retained the first three principal components, capturing ~85–90% of variance.

---

## Exploratory Data Analysis

- Visualized feature distributions with histograms.
- Generated pair plots to inspect relationships and class separability.
- Examined feature correlations with a heatmap.
- Created scree and 3D PCA projection plots to guide dimensionality reductio
 
 ---

## Modeling

### Model Selection  
**Supervised: K-Nearest Neighbors (KNN)**
- Distance metric: Euclidean
- Hyperparameter tuning via GridSearchCV to select optimal k.

**Unsupervised: Gaussian Mixture Model (GMM) with Expectation-Maximization (EM)**
- Applied on PCA-reduced data for soft clustering.  


### Train–Validation Split  
- **Training set:** 80% of the data  
- **Validation set:** 20% of the data  
- **Random state:** 42 (for reproducibility)
- **PCA:** 3 PCs were chosen explaining approximately 85–90% of the variance

---

## Results & Evaluation

**KNN:** 87% accuracy; F1-scores: AB = 0.90, NO = 0.82

**PCA+GMM+EM:** 82% accuracy; F1-scores: AB = 0.85, NO = 0.78

The comparison reveals that the supervised KNN model generally offered more balanced and slightly superior predictive performance, making it particularly suitable for clinical diagnostics. In contrast, the unsupervised PCA+GMM+EM approach demonstrated significant advantages in exploratory contexts, particularly in accurately identifying normal cases, highlighting its potential value in initial analyses.

---

## Project Structure

| Path                                  | Description                                  |
|---------------------------------------|----------------------------------------------|
| `README.md`                           | Main project overview                        |
| `Project_File.ipynb`                  | Original analysis & modeling notebook        |
| `Dataset.csv`                        | Directory containing data files              |



---

## Dependencies
- Python 3.8+
- pandas
- numpy
- scikit-learn
- imbalanced-learn
- matplotlib
- seaborn
- jupyter

---


