#Chick Weight Feed Recommendation System using Similarity-Based Analysis

## Project Overview

This project develops a feed recommendation system that identifies alternative feeds types based on their observed chicken-weight performance.

The system uses historical chicken weight data to create performance profiles for different feed types. Principal Component Analysis (PCA) was used to create a composite performance dimension and cosine similarity to identify feeds with similar profiles.

The goal of this project is to answer:

 **Given a feed currently being used, which other feed types have a similar observed performance profile and could be considered as alternatives?**


## Dataset

The project uses the **Chick Weight (`chickwts.csv`) dataset**.

### Dataset characteristics

* **71 observations**
* **6 feed categories**
* **3 columns, feed,weight and rownames**

The six feed types are:

* Casein
* Horsebean
* Linseed
* Meatmeal
* Soybean
* Sunflower

The dataset contains **no missing values and no duplicate rows**.


The project follows these main steps:

### 1. Data Understanding

The dataset was loaded and inspected for:

* Shape and structure
* Data types
* Missing values
* Duplicate records
* Feed distribution

### 2. Exploratory Data Analysis

The relationship between feed type and chicken weight was explored using statistical summaries and visualizations, histogram and boxplots.

### 3. Feed Performance Profiling

The chicken weights were standardized and summarized for each feed using:

* Mean
* Standard deviation
* Minimum
* Maximum

Each feed was therefore represented by a four-variable performance profile.

### 4. Principal Component Analysis

PCA was applied to the four feed-profile variables to create a single composite performance score.

PC1 explained approximately 97.2% of the variation, meaning that the first component captured most of the information contained in the four profile variables.

### 5. Cosine Similarity

Cosine similarity was used to measure how similar the feed profiles were.

A score closer to **1** indicates greater similarity, while values closer to **0** indicate less similarity.

### 6. Feed Recommendation

For each primary feed, the system identifies the three most similar alternative feeds.

## PCA Results

The PC1 scores ranked the feeds as follows:

| Feed      | PC1 Score |
| --------- | --------: |
|=======================|
| Sunflower |     1.534 |
| Casein    |     1.285 |
| Meatmeal  |     0.378 |
| Soybean   |    -0.290 |
| Linseed   |    -0.773 |
| Horsebean |    -2.134 |

Sunflower had the highest PC1 score, while horsebean had the lowest.

## Key Findings

* **Casein and sunflower** have the strongest similarity at **0.99**.
* **Linseed and soybean** have a very high similarity of **0.97**.
* **Soybean and meatmeal** have a similarity of **0.95**.
* **Horsebean** has relatively low similarity with several other feeds.

## Recommendations

The recommendation system produced the following alternatives:

| Primary Feed | Best Alternative |    Score | Second Alternative | Score | Third Alternative | Score |
| ------------ | ---------------- | -------: | ------------------ | ----: | ----------------- | ----: |
| Casein       | **Sunflower**    | **0.99** | Meatmeal           |  0.89 | Soybean           |  0.71 |
| Horsebean    | **Linseed**      | **0.83** | Soybean            |  0.66 | Meatmeal          |  0.41 |
| Linseed      | **Soybean**      | **0.97** | Meatmeal           |  0.84 | Horsebean         |  0.83 |
| Meatmeal     | **Soybean**      | **0.95** | Casein             |  0.89 | Linseed           |  0.84 |
| Soybean      | **Linseed**      | **0.97** | Meatmeal           |  0.95 | Casein            |  0.71 |
| Sunflower    | **Casein**       | **0.99** | Meatmeal           |  0.85 | Soybean           |  0.65 |

## 🛠️ Technologies Used

* **Python 3.11**
* **Pandas** – Data manipulation
* **NumPy** – Numerical computation
* **Scikit-learn** – StandardScaler, PCA and cosine similarity
* **Matplotlib** – Visualization
* **Seaborn** – Statistical visualization
* **VS Code**

## Conclusion

The project demonstrates how historical chicken-weight data can be transformed into a **data-driven feed recommendation system**.

By combining **feed performance profiling, PCA, and cosine similarity**, the system can identify feed types with similar observed performance profiles and provide alternative recommendations.

## Project Structure
Recommendation_System/
│
├── Chickwts.ipynb
├── chickwts.csv
└── README.md
