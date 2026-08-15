# US Crime Pattern Analysis Using K-Means and GMM

## Project Overview

This project applies unsupervised machine learning techniques to identify patterns in crime statistics across 50 US states.

The analysis uses the **USArrests dataset** and applies **K-Means clustering** and **Gaussian Mixture Models (GMM)** to discover natural groupings of states based on their crime characteristics.

**Murder, Assault, and Rape** are selected as the primary crime variables, while **Principal Component Analysis (PCA)** is used for dimensionality reduction and visualization.

The objective is to provide a data-driven approach that can support public policy research, targeted crime-prevention strategies, and resource allocation.

> **Important:** The clusters identify statistical similarities between states. They do not establish that a particular policy, demographic factor, or socioeconomic condition caused higher or lower crime levels.

## Public Policy Problem

A public policy research firm requires a data-driven approach to identify patterns in crime statistics across different regions.

Crime levels can vary considerably between states, and treating all states as having the same crime profile may result in less targeted interventions.

Clustering can help:

- Identify states with similar crime patterns.
- Distinguish groups with relatively lower and higher crime levels.
- Identify specific combinations of Murder, Assault, and Rape that characterize different groups.
- Support targeted crime-prevention strategies.
- Inform resource allocation and regional policy planning.

## Objectives

1. Explore and understand the USArrests dataset.
2. Assess the quality and characteristics of the crime data.
3. Identify the most relevant variables for clustering.
4. Standardize the selected crime variables.
5. Apply PCA for dimensionality reduction and visualization.
6. Apply K-Means clustering to identify groups of states.
7. Apply Gaussian Mixture Model (GMM) clustering.
8. Evaluate and compare the clustering solutions.
9. Interpret the characteristics of each crime-pattern cluster.
10. Develop public policy implications and recommendations based on the findings.

## Dataset

The project uses the **USArrests dataset**, which contains crime statistics for **50 US states**.

The dataset contains:

- **50 observations**
- **5 variables**
- **4 analytical variables**
- **1 state identifier**

| Variable | Description |
|---|---|
| Murder | Murder arrest rate |
| Assault | Assault arrest rate |
| UrbanPop | Percentage of the population living in urban areas |
| Rape | Rape arrest rate |
| State | Name of the US state |

The notebook's data-quality checks show that the dataset contains **no missing values or duplicate records**, and all 50 states are uniquely represented.

## Feature Selection

The analysis initially considers **Murder, Assault, UrbanPop, and Rape**.

Based on the correlation analysis and the project's objective, **Murder, Assault, and Rape** are selected for the clustering analysis because they directly represent crime patterns.

**UrbanPop** is excluded because it has relatively weak relationships with the crime variables, particularly Murder and Assault.

The selected variables are therefore:

- **Murder**
- **Assault**
- **Rape**

## Project Workflow

The notebook follows this workflow:

1. Load and inspect the dataset.
2. Perform exploratory data analysis.
3. Check data quality.
4. Examine descriptive statistics and distributions.
5. Analyze correlations between variables.
6. Select the relevant crime features.
7. Standardize the selected features.
8. Apply PCA for dimensionality reduction.
9. Determine the number of K-Means clusters using the Elbow Method.
10. Determine the number of GMM components using BIC.
11. Apply K-Means and GMM clustering.
12. Visualize the clusters using PCA.
13. Evaluate the clustering results using the Silhouette Score.
14. Examine cluster sizes and characteristics.
15. Identify states within each cluster.
16. Interpret the results from a public policy perspective.

## Exploratory Data Analysis

The analysis examines:

- Dataset structure and dimensions.
- Data types.
- Missing values.
- Duplicate observations.
- Descriptive statistics.
- Variable distributions.
- Correlations between crime variables.

The dataset contains substantial variation across states. **Assault** has the highest average value at **170.76**, while **Murder** averages **7.79** and **Rape** averages **21.23**.

The differences in scale between the variables support the need for standardization before applying clustering algorithms.

## Data Preparation

The selected crime variables are standardized before clustering because the variables have different numerical scales.

Standardization places the selected features on a comparable scale so that no single crime variable disproportionately influences the clustering results.

## PCA

**Principal Component Analysis (PCA)** is applied after standardization.

The purpose of PCA in this analysis is to reduce the dimensionality of the selected crime features and provide a two-dimensional representation that can be used to visualize the resulting clusters.

The PCA representation is used to visualize how states are grouped by K-Means and GMM.

## Modeling

Two clustering approaches are applied:

### K-Means Clustering

The **Elbow Method** is used to determine a suitable number of clusters for K-Means.

The analysis identifies **4 clusters** as the selected K-Means solution.

The resulting clusters provide a more detailed segmentation of states according to their crime patterns.

### Gaussian Mixture Model

A **Gaussian Mixture Model (GMM)** is also applied.

The **Bayesian Information Criterion (BIC)** is used to determine the optimal number of components.

The analysis identifies **2 GMM clusters** as the selected solution.

The two clusters provide a broader distinction between states with relatively lower and higher levels across the selected crime variables.

## Model Evaluation

The clustering solutions are evaluated using the **Silhouette Score**.

| Model | Number of Clusters | Silhouette Score |
|---|---:|---:|
| K-Means | 4 | 0.4643 |
| GMM | 2 | **0.5610** |

The **GMM model achieved the higher Silhouette Score of 0.5610**, compared with 0.4643 for K-Means.

A higher Silhouette Score indicates better-defined and more separated clusters. Therefore, **GMM produced the better-defined clustering solution for this dataset**.

## Cluster Sizes

The models produced the following cluster sizes:

| Model | Cluster Sizes |
|---|---|
| K-Means | 14, 12, 7, 17 |
| GMM | 31, 19 |

K-Means provides a more detailed segmentation through four clusters, while GMM groups the states into two broader crime-pattern groups.

## Cluster Characteristics

### K-Means

The K-Means clusters show different combinations of Murder, Assault, and Rape levels.

- **Cluster 0** has the lowest overall crime levels.
- **Cluster 1** has high Murder and Assault levels.
- **Cluster 2** has high Murder and Assault levels and the highest average Rape level.
- **Cluster 3** represents a moderate crime pattern.

### GMM

The GMM clusters provide a broader distinction:

- **Cluster 0** has lower average Murder, Assault, and Rape levels.
- **Cluster 1** has substantially higher average levels across all three crime measures.

The GMM results therefore provide a simpler distinction between lower- and higher-crime patterns.

## Public Policy Implications

The clustering analysis provides the public policy research firm with a **data-driven way to identify states with similar crime patterns**.

Potential applications include:

- **Targeted crime-prevention strategies:** States with similar crime profiles can be considered together when designing interventions.
- **Resource allocation:** Higher-crime groups may require greater attention when allocating crime-prevention and public safety resources.
- **Policy comparison:** States within the same cluster can be compared to identify differences in policies, prevention strategies, and resource allocation.
- **Avoiding a one-size-fits-all approach:** Different clusters demonstrate that states can have different combinations of Murder, Assault, and Rape levels.
- **Regional monitoring:** The clustering approach can be repeated with updated data to monitor changes in crime-pattern groups over time.

## Public Policy Recommendations

Based on the clustering results, the public policy research firm can use the analysis to support:

1. **Targeted interventions** for states with similar crime profiles.
2. **Evidence-based resource allocation** toward areas with greater or specific crime burdens.
3. **Cross-state comparisons** between states within the same crime-pattern cluster.
4. **Ongoing monitoring** of changes in regional crime patterns.
5. **Further research** combining crime statistics with socioeconomic, demographic, and policy variables.

The clustering results should be used as a **decision-support tool rather than evidence of causality**. Further socioeconomic, demographic, and policy data would be required to investigate the underlying causes of the identified crime patterns.

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
