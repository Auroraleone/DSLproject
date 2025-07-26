# Real Estate Price Prediction

**Author**: Aurora Leone  
**University**: Politecnico di Torino  
**Student ID**: 334258  
**Course**: Data Science Lab: Process and Methods (Summer Call, A.Y. 2024/2025)

---

## Abstract

This project presents a comprehensive machine learning pipeline to predict real estate rental prices using LightGBM, combined with extensive feature engineering and preprocessing techniques. The final model achieves a **Mean Absolute Error (MAE) of 174.812**, demonstrating strong generalization and predictive performance across different property types and geographic locations.

---

## Problem Overview

Rental price prediction is a complex task due to:

- **Heterogeneous data types**: numeric, categorical, unstructured text, and geographic coordinates.
- **Right-skewed target distribution** (skewness = 9.13).
- **Strong spatial and contextual variability** (urban/suburban/coastal dynamics).
- **Non-linear relationships** between size, location, amenities, and price.

The challenge is to build a robust and interpretable model that handles:
- Missing values  
- Outliers  
- High-dimensional feature space  
- Mixed data types  
- Non-linearity and spatial dependencies

---

## Proposed Approach

The pipeline is composed of 3 main stages:

### 1. 🔍 Preprocessing & Feature Engineering

- **Outlier removal** using a conservative IQR-based threshold (15th–85th percentile, 2.5× IQR).
- **Hierarchical missing value imputation** using grouped medians by architectural logic.
- **Log transformation** of the target variable to reduce skewness.
- **Feature engineering** across:
  - Spatial clustering (K-means on lat/lon)
  - Structural ratios (e.g., rooms per square foot)
  - Text analysis (TF-IDF on titles/descriptions)
  - Amenities normalization
  - Temporal patterns
- **Categorical encoding** with smoothed target encoding (α=25) and one-hot encoding.
- **Dimensionality reduction**: removed low-variance features and selected top 111 via Pearson correlation.

### 2. 🌲 Model Selection: LightGBM

- Selected due to its:
  - Native handling of categorical data
  - Regularization capabilities
  - Fast training time
  - Interpretability
- Compared against XGBoost and neural networks (excluded for interpretability or inefficiency on this task).

### 3. ⚙️ Hyperparameter Tuning

- L1 = 0.2, L2 = 1.5 regularization  
- Learning rate = 0.04, max 2500 rounds, early stopping  
- Max depth = 16, num_leaves = 180  
- Feature fraction = 0.8, Bagging fraction = 0.7  

---

## Results

- **Mean Absolute Error (MAE)**: **174.812**
- **Test mean prediction**: 1,492.43  
- **Test median prediction**: 1,352  
- **Training mean**: 1,494.64  
- **Training median**: 1,350  
- Strong alignment between predicted and actual distributions.
- Spatial and engineered features had the highest importance.

---

## 📂 Repository Structure

| File | Description |
|------|-------------|
| [`DSLproject334258.ipynb`](./DSLproject334258.ipynb) | Jupyter notebook with the full implementation pipeline |
| [`Report334258.pdf`](./Report334258.pdf) | Full technical report explaining methodology, modeling, results and discussion |
| [`Data_Science_Lab__Project_Assignment_Summer_2025-3 (1).pdf`](./Data_Science_Lab__Project_Assignment_Summer_2025-3%20(1).pdf) | Official project assignment with dataset sources and requirements |
| [`README.md`](./README.md) | This documentation file you're reading now |


---

## Dataset

The dataset was provided as part of the **Data Science Lab Summer Call 2025**. Dataset download links and description are available in:

📄 `Data_Science_Lab__Project_Assignment_Summer_2025-3 (1).pdf`(./Data_Science_Lab__Project_Assignment_Summer_2025-3%20(1).pdf)

---

