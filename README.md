**Data Science Classification, Recommendation Systems, and Clustering Project**

Welcome to our **Machine Learning Projects Portfolio**. This repository contains a collection of practical data science and machine learning projects covering **classification, clustering, recommendation systems, dimensionality reduction, exploratory data analysis, and model evaluation**.

The projects demonstrate how machine learning techniques can be applied to real-world problems, from automatically classifying products to identifying patterns in crime statistics and recommending alternative chicken feeds based on observed performance.

---

## Projects Overview

# 1. Chicken Weight Feed Recommendation System

This project develops a **feed recommendation system** that identifies alternative chicken feed types based on their observed chicken-weight performance.

Historical chicken-weight data is used to create performance profiles for different feeds. PCA is then used to create a composite performance dimension, while **cosine similarity** identifies feeds with similar performance profiles.

### Key Techniques

* Data exploration and visualization
* Feature standardization
* Performance profiling
* Principal Component Analysis (PCA)
* Cosine similarity
* Similarity-based recommendations

### Dataset

The project uses the **Chick Weight (****`chickwts.csv`****) dataset**, containing:

* 71 observations
* 6 feed categories
* Chicken weight measurements

The feed types include:

* Casein
* Horsebean
* Linseed
* Meatmeal
* Soybean
* Sunflower

### Key Results

Some of the strongest similarities identified were:

* **Casein → Sunflower:** 0.99
* **Sunflower → Casein:** 0.99
* **Linseed → Soybean:** 0.97
* **Soybean → Linseed:** 0.97
* **Soybean → Meatmeal:** 0.95

The project demonstrates how similarity-based machine learning techniques can be used to identify potential alternatives based on historical performance.

**Project folder:** `Recommendation_System/`

---

# 2. US Crime Pattern Analysis

This project applies **unsupervised machine learning** to identify patterns in crime statistics across the 50 US states.

The analysis uses the **USArrests dataset** and applies **K-Means clustering** and **Gaussian Mixture Models (GMM)** to discover groups of states with similar crime characteristics. PCA is used for dimensionality reduction and visualization.

### Key Techniques

* Exploratory Data Analysis
* Feature selection
* Standardization
* Principal Component Analysis (PCA)
* K-Means clustering
* Gaussian Mixture Models (GMM)
* Elbow Method
* Bayesian Information Criterion (BIC)
* Silhouette Score

### Dataset

The USArrests dataset contains:

* 50 US states
* Murder arrest rates
* Assault arrest rates
* Rape arrest rates
* Urban population percentage

The analysis selects **Murder, Assault, and Rape** as the primary clustering variables.

### Key Results

Two clustering approaches were compared:

| Model   | Clusters | Silhouette Score |
| ------- | -------: | ---------------: |
| K-Means |        4 |           0.4643 |
| **GMM** |    **2** |       **0.5610** |

GMM produced the better-defined clustering solution based on the Silhouette Score.

### Policy Application

The results can support:

* Targeted crime-prevention strategies
* Evidence-based resource allocation
* Cross-state policy comparisons
* Regional monitoring
* Further public-policy research

The clusters represent **statistical similarities**, not evidence that a particular policy or socioeconomic factor causes crime levels.

**Project folder:** `Clustering/`

---

# 3. Wine Classification Model

This project develops a machine learning model for a wine distributor that needs to classify wines based on their measurable chemical properties.

The solution combines **k-Nearest Neighbors (k-NN)** with **Principal Component Analysis (PCA)** to classify wines into three classes.

### Key Techniques

* Exploratory Data Analysis
* Data preprocessing
* Feature standardization
* Principal Component Analysis
* k-Nearest Neighbors
* GridSearchCV
* Cross-validation
* Model evaluation
* Confusion matrix

### Dataset

The dataset contains:

* 178 observations
* 13 chemical features
* 3 wine classes

Class distribution:

| Wine Class | Observations |
| ---------- | -----------: |
| Class 1    |           59 |
| Class 2    |           71 |
| Class 3    |           48 |

### Model Development

The project compares a baseline k-NN model with an optimized **PCA + k-NN pipeline**.

The best parameters were:

| Parameter           | Best Value |
| ------------------- | ---------- |
| PCA Components      | 8          |
| Number of Neighbors | 10         |
| Weights             | Uniform    |
| Distance Metric     | Euclidean  |

The optimized model achieved:

**100% test accuracy**

compared with **97.22%** for the baseline k-NN model.

> **Note:** The 100% test accuracy applies to the provided dataset and test split. It should not be interpreted as a guarantee of 100% accuracy on new production data.

### Potential Applications

* Automated wine classification
* Quality-control support
* Inventory management
* Identification of unusual chemical profiles
* Reduction of manual classification effort

**Project folder:** `Classification_model/`

---
# Technologies Used

The projects primarily use **Python** and the following data science and machine learning libraries:

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn
* Jupyter Notebook

## These technologies are used across the individual projects for data manipulation, visualization, dimensionality reduction, machine learning, and model evaluation.

# Repository Structure

```text
Data Science Classification, Recommendation Systems, and Clustering Project/
│
├── Recommendation_Systems/
│   ├── Chickwts.ipynb
│   ├── chickwts.csv
│   └── README.md
│
├── Clustering/
│   ├── USArrests.ipynb
│   ├── USArrests.csv
│   └── README.md
│
├── Classification_Model/
│   ├── wine.ipynb
│   ├── wine.csv
│   └── README.md
│
└── README.md
```
# Getting Started

## 1. Clone the Repository
## 2. Install the Required Libraries
## 3. Launch Jupyter Notebook

# Project Goals

The overall goal of this portfolio is to demonstrate practical applications of machine learning across different problem types:

**Recommendation**

Identify similar feed types using performance profiles and similarity measures.

**Clustering**

Discover natural groups within crime statistics without predefined labels.

**Classification**

Automatically classify wines using measurable chemical characteristics.

Together, these projects demonstrate the application of machine learning to **real-world analytical and decision-support problems**.

---

# Learning Outcomes

Through these projects, the following skills are demonstrated:

* Data preprocessing
* Exploratory data analysis
* Feature engineering and selection
* Data standardization
* Dimensionality reduction
* Supervised machine learning
* Unsupervised machine learning
* Similarity-based analysis
* Hyperparameter tuning
* Model evaluation
* Data visualization
* Business and policy interpretation

--

# About This Portfolio

This repository brings together practical machine learning projects that demonstrate the ability to move from **raw data → analysis → modeling → evaluation → actionable insights**.

The projects cover different machine learning approaches and application areas while emphasizing reproducible analysis, appropriate model evaluation, and practical interpretation of results.

---

## Project Summary

| Project                        | Problem Type   | Main Model/Method       | Main Result                          |
| ------------------------------ | -------------- | ----------------------- | ------------------------------------ |
|  Feed Recommendation | Recommendation | PCA + Cosine Similarity | Identified similar feed alternatives |
| US Crime Analysis           | Clustering     | K-Means + GMM           | GMM achieved 0.5610 Silhouette Score |
| Wine Classification         | Classification | PCA + k-NN              | 100% test accuracy on provided split |

---

## Conclusion

This portfolio demonstrates how machine learning can be applied to different real-world problems using a combination of **data analysis, dimensionality reduction, similarity measurement, classification, and clustering**.

The projects provide practical examples of how data-driven methods can support **recommendations, classification, pattern discovery, resource planning, and decision-making**.
