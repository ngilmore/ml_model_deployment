# Deploying Machine Learning Models
Repo of repeatable ML model pipeline development and deployment.

## Machine Learning Pipeline: Overview

### Basic Architecture Design
High level overview of the architecture and tools being used for each phase / environment.
![Basic Architecture Design](/images/basic_architecture.png)

### Steps:
1. **Data Gathering**
2. **Data Analysis**
3. **Feature Engineering** - deal with missing data, convert categorical variables (i.e. cardinality, rare labels, strings, etc.), assess data distributions (i.e. deal with skewed data), and deal with outliers (outliers may throw off algorithms affected by their presence which may cause overfitting), feature scaling (ML may be sensitive to feature scales - see NOTES below)
4. **Feature Selection** - algorithms/procedures to identify the most predictive features and limit models to only those features that add value, provide greatest interpretability, and easier to implement into Production (reduced risk of data errors, reduced data redundancy (constant variables, quasi-constant variables, duplication, correlation), less code, smaller JSON messages, etc.)
5. **ML Model Building** - [A] regression, classification, or clustering; [B] linear, tree, neural network, etc; [C] supervised, unsupervised, or reinforcement learning (all choices are dependent on the business problem to be solved). Can often include Meta-Ensembing (model of models)
6. **ML Model Assessment** - evaluate **uplift in business value** in addition to ROC-AUC, Accuracy, MSE, RMSE, MAE, etc. metrics
7. **Model Deployment** - includes Feature Engineering, Feature Selection, and ML Model components (not just the ML Model)

#### NOTES:
ML models sensitive to feature scales:
- Linear & Logistic Regression
- Neural Networks
- Support Vector Machines
- K-Nearest Neighbours
- K-Means Clustering
- Linear Discriminant Analysis (LDA)
- Principal Component Analysis (PCA)

Tree-based ML models insensitive to feature scales:
- Classification & Regression Trees
- Random Forests
- Gradient Boosted Trees

### Example Models:
1. Predicting the Sale Price of Houses (dataset from [Kaggle](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data))
