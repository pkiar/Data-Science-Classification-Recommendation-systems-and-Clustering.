# ## K-NN wine classification model using PCA

## Project Overview

This project develops a machine learning solution for a wine distributor that needs to classify wines based on their measurable chemical properties.

The solution uses **k-Nearest Neighbors (k-NN)** for classification and **Principal Component Analysis (PCA)** for dimensionality reduction. The objective is to support wine classification, quality control, inventory management, and the identification of unusual chemical profiles.

> **Important:** The model's 100% test accuracy is based on the provided dataset and test split. It should not be interpreted as proof that the model will achieve 100% accuracy on new wines in production.

## Business Problem

The distributor handles wines from different regions and suppliers. Manual classification and verification can be time-consuming and inconsistent.

A machine learning model can help:

- Classify wines automatically according to their chemical properties.
- Support quality-control activities.
- Identify unusual chemical profiles that may require further investigation.
- Improve inventory organization.
- Reduce manual classification effort.

## Business Objectives

1. Ensure customer safety by identifying potentially unsafe or poor-quality wines.
2. Maintain wine quality through chemical-based classification and proper storage.
3. Detect potentially counterfeit wines through unusual chemical profiles.
4. Improve inventory management by automatically classifying wines.
5. Increase operational efficiency through faster classification and quality control.

## Dataset

The project uses a wine dataset containing:

- **178 observations**
- **14 variables**
- **13 chemical features**
- **1 target variable (`Wine`)**
- **3 wine classes**

Class distribution:

| Wine Class | Observations |
|---|---:|
| Class 1 | 59 |
| Class 2 | 71 |
| Class 3 | 48 |

The dataset contains no missing values or duplicate observations according to the notebook's data-quality checks.

### Target

`Wine` is the target variable, with classes **1, 2, and 3**.

### Chemical Features

The 13 chemical measurements are used as predictors for classification. The notebook does not apply label encoding to `Wine` because the target is already represented numerically as 1, 2, and 3.

## Project Workflow

The notebook follows this workflow:

1. Load and inspect the dataset.
2. Perform exploratory data analysis.
3. Check data quality.
4. Separate features and target.
5. Split the data into training and testing sets.
6. Standardize the chemical features.
7. Apply PCA.
8. Train a baseline k-NN classifier.
9. Tune PCA and k-NN hyperparameters using `GridSearchCV`.
10. Evaluate the optimized model.
11. Compare the baseline and tuned models.
12. Interpret the results from a business perspective.

## Exploratory Data Analysis

The analysis examines:

- Wine class distribution.
- Correlations between chemical features.
- Feature distributions.
- Mean chemical measurements by wine class.

Several chemical variables are correlated. For example, the notebook reports a strong positive correlation between **Phenols and Flavanoids (r = 0.86)**. This supports the use of PCA to reduce overlapping information in the feature space.

## Data Preparation

The dataset is divided using an **80:20 train-test split** with stratification to preserve the proportions of the three wine classes.

`StandardScaler` is used because k-NN is distance-based and the chemical variables have different numerical scales.

The scaler is fitted only on the training data and then applied to the test data to avoid data leakage.

## PCA

PCA is used to reduce the dimensionality of the standardized chemical features.

The notebook reports that:

- Original features: **13**
- Components required to retain at least 95% variance: **10**
- The first 10 components explain approximately **96.24%** of the variance.

During model tuning, however, PCA component count is treated as a hyperparameter, and the best-performing pipeline selected **8 components** based on cross-validation accuracy.

## Modeling

### Baseline Model

A baseline k-NN classifier was trained using:

- `k = 5`
- All 13 standardized features
- No PCA

Baseline test accuracy:

**97.22%**

### Hyperparameter Tuning

The optimized pipeline combines:

`StandardScaler → PCA → k-NN`

`GridSearchCV` was used with:

- 5-fold stratified cross-validation
- Accuracy as the scoring metric
- PCA components: 2, 3, 4, 5, 6, 8, 10
- `k`: 1–20
- Weights: `uniform`, `distance`
- Metrics: `euclidean`, `manhattan`, `minkowski`

This resulted in **840 parameter combinations** and **4,200 cross-validation fits**.

### Best Parameters

| Parameter | Best Value |
|---|---|
| PCA components | 8 |
| Number of neighbors (`k`) | 10 |
| Weights | `uniform` |
| Distance metric | `euclidean` |

Best cross-validation accuracy:

**97.88%**

## Final Results

The optimized k-NN + PCA model achieved:

**Test accuracy: 100.00%**

Classification performance:

| Class | Precision | Recall | F1-score | Support |
|---|---:|---:|---:|---:|
| 1 | 1.00 | 1.00 | 1.00 | 12 |
| 2 | 1.00 | 1.00 | 1.00 | 14 |
| 3 | 1.00 | 1.00 | 1.00 | 10 |
| **Overall** | **1.00** | **1.00** | **1.00** | **36** |

The confusion matrix contains no misclassifications:

- Class 1: **12/12** correctly classified
- Class 2: **14/14** correctly classified
- Class 3: **10/10** correctly classified
- Total errors: **0**

### Model Comparison

| Model | Test Accuracy |
|---|---:|
| Baseline k-NN, k=5, 13 features | 97.22% |
| Tuned k-NN + PCA | **100.00%** |

## Technologies Used

- Python
- pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
- Jupyter Notebook

## Required Python Libraries

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
```

## How to Run

### 1. Clone or download the project

Place the notebook and dataset in the same project directory.

### 2. Ensure the dataset is available

The notebook expects a file named:

```text
wine.csv
```

The dataset should be in the same directory as the notebook.

### 3. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 4. Start Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
wine.ipynb
```

Run the notebook cells from top to bottom.

## Project Files

Recommended project structure:

```text
wine-classification/
├── wine.ipynb
├── wine.csv
└── README.md
```

## Business Recommendations

The model can initially be used as a **decision-support tool** for automated wine classification and inventory management.

For production deployment, the model should first be validated using a larger and more diverse dataset containing new wine samples from different suppliers, regions, and conditions.

The distributor should also continuously monitor model performance and periodically retrain the model as verified new data becomes available.

## Conclusion

The project demonstrates that a tuned **k-NN classifier combined with PCA** can effectively classify the three wine classes in the provided dataset.
