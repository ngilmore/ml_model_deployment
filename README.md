# Deploying Machine Learning Models

Repo of repeatable ML model pipeline development and deployment.

[![made-with-python](https://img.shields.io/badge/Built%20with-Python-1f425f.svg)](https://www.python.org/)
[![made-with-sklearn](https://img.shields.io/badge/Built%20with-sklearn-1f425f.svg)](https://www.python.org/)
[![made-with-jupyter](https://img.shields.io/badge/Built%20with-Jupyter-1f425f.svg)](https://www.python.org/)
[![made-with-vscode](https://img.shields.io/badge/Built%20with-VS%20Code-1f425f.svg)](https://www.python.org/)
[![made-with-docker](https://img.shields.io/badge/Built%20with-Docker-1f425f.svg)](https://www.python.org/)
[![deployed-on-heroku](https://img.shields.io/badge/Deployed%20on-Heroku-1f425f.svg)](https://www.python.org/)
[![deployed-on-aws](https://img.shields.io/badge/Deployed%20on-AWS-1f425f.svg)](https://www.python.org/)

[![GitHub license](https://img.shields.io/github/license/Naereen/StrapDown.js.svg)](https://github.com/Naereen/StrapDown.js/blob/master/LICENSE)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)

[![CircleCI](https://circleci.com/gh/ngilmore/ml_model_deployment.svg?style=svg)](https://circleci.com/gh/ngilmore/ml_model_deployment)
[![Heroku App Status](https://heroku-shields.herokuapp.com/lasso-reg-model)](https://lasso-reg-model.herokuapp.com/version)

## Projects

1. Predict the sale price of houses using Lasso regression (dataset from [Kaggle](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data)).
   - Initial data gathering/analysis, feature engineering/selection, model building/evaluation done locally in Jupyter notebooks.
   - Development of deployable/scaleable model then moved to .py (VS Code) files. Wrapped model in a Flask application with testing, versioning, and packaging for deployment and re-use. Added CI/CD through the inclusion of GitHub (source code control), GemFury (packaging), and Circleci (automated testing and deployment).
   - Deployed to Production on [Heroku](https://lasso-reg-model.herokuapp.com/version) (PaaS) without containers automatically once CI/CD pipeline runs successfully.
   - Dockerized the model and app for deployment to Production.
     - TODO: Deploy model as Docker container to Heroku - requires a plan upgrade on Heroku to allow for Docker Layer caching.
   - TODO: Deploy model as Docker container to AWS (IaaS).
2. Differentiate weeds from crop seedlings using a convolutional neural network (CNN).
   - TODO: Build and deploy this model.

## Machine Learning Pipeline: Overview

### Basic Architecture Design

High level overview of the architecture and tools used for each phase / environment.

![Basic Architecture Design](/images/basic_architecture.png)

### Steps

1. **Data Gathering**
2. **Data Analysis**
3. **Feature Engineering** - deal with missing data, convert categorical variables (i.e. cardinality, rare labels, strings, etc.), assess data distributions (i.e. deal with skewed data), and deal with outliers (outliers may throw off algorithms affected by their presence which may cause overfitting), feature scaling (ML may be sensitive to feature scales - see NOTES below)
4. **Feature Selection** - algorithms/procedures to identify the most predictive features and limit models to only those features that add value, provide greatest interpretability, and easier to implement into Production (reduced risk of data errors, reduced data redundancy (constant variables, quasi-constant variables, duplication, correlation), less code, smaller JSON messages, etc.)
5. **ML Model Building** - [A] regression, classification, or clustering; [B] linear, tree, neural network, etc; [C] supervised, unsupervised, or reinforcement learning (all choices are dependent on the business problem to be solved). Can often include Meta-Ensembing (model of models)
6. **ML Model Assessment** - evaluate **uplift in business value** in addition to ROC-AUC, Accuracy, MSE, RMSE, MAE, etc. metrics
7. **Model Deployment** - includes Feature Engineering, Feature Selection, and ML Model components (not just the ML Model)

#### NOTES

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