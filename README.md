### Project Title

**Insurance Claims Prediction for Buildings**

### Objective

The objective of this project is to **build a predictive algorithm (model) that determines whether a building will experience at least one insurance claim
within a specified insured period,** or to *simply put,**the model aims to estimate the probability of a claim occurrence** based on:

 - Building characteristics (e.g, painted, fenced, garden)
 - Location attributes (e.g, urban or rural settlement)
 - Other organizational and structural conditions available, before any claim occurs.

The target variable represents whether **at least one insurance claim** was reported during the insured period.

### Problem Type Identification

Before performing any data preprocessing or modeling, it is essential to define clearly, the nature of the problem.

**Is this a classification or regression problem?**

**This is a binary classification problem**  

#### Justification:

The target variable has two _possible outcomes_ 

 - '1' The building experienced **at least one insurance claim**
 - '0' The building experienced ** no insurance claim**

The goal is not to predict the monetary value of claims, but rather **the occurrence of a claim event**

The model output either :

 - A **class label** (claim / no claim) or
 - A **probability of claim occurrence**

Hence, classification algorithms such as **LogisticRegression, RandomForest, XGBoost or CatBoost** are appropriate for this task.

### Modelling Perspective 

From a business and insurance-risk perspective, this problem focuses on :

 - **Risk assessment**
 - **Early identification of high-risk buildings**
 -  **Improve underwriting and pricing decisions**

Predicting claim occurrence enables insurers to:
i. Allocate resources efficiently
ii. Adjust premiums based on risk
iii. Implement preventive measures for high-risk pr;operties.
