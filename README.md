# AINOW MACHINE LEARNING DOCUMENTATION


## Project Title

**Insurance Claims Prediction for Buildings**

### Project Overview

Insurance companies operate in a **risk-driven environment,** where profitability depends on accurately assessing and managing the likelihood of claims. Incorrect assessment can lead to: 

**Underpricing high-risk building,** resulting in financial losses.
**Overpricing low-risk building**, causing customer dissatisfaction and churn.

Thus, this project aims to **build a predictive model that determines whether a building will experience at least one insurance claim within the specified insured period**, or *simply put* **to estimate the probability of a claim occurrence** based on the features provided (independent variable) in the dataset.
 - Building characteristics (e.g, painted, fenced, garden etc)
 - Location attributes (e.g, urban or not urban)
 - Other organizational  and structural conditions available **beforeany claim occurs**

The target variable represents whether **at least one insurance claim** was reported during the insurance period.

 ### Data Source
 
 The data used for this **Machine Learning** project is provided by the consortium of instructors, and possibly in conjunction with the
 programme director (my assumption) at the **AI NOW BOOT CAMP**, an offshoot programme of the **INCUBATOR HUB**.

 ### Tools Used
 
  - Microsoft Visual Studio Code editor,
     - used for providing a platform and extensions that provide the kernel base, Python terminal, Gitbash, etc. 
  - Python Kernel/server
     - for importing Scikit-Learn, XGBoost, Numpy and Pandas Libraries, etc.
  - Git bash/version control
     - This tool ensures safety, collaboration and tracking changes.
   
 ### Data Cleaning and Preprocessing

 After importing the necessary libraries into the Python environment, the following tasks were performed:
  - Data loading, description and inspection
  - Handling missing, duplicates and data conversion.
  - Removing Outliers.

### Explorative Data Analysis

### Dataset overview
The dataset consists  of building-level insurance records both numerical and categorical attributes related to building characteristics, occupancy information, and structural features.The target variable, **claim**, is a binary, indicating whether an insurance claim was filed for a building during the observed period. 

1. Target Variable Analysis

The distribution of the target variable (**Claim**) was examined to assess class balance. The analysis reveals a substantial imbalance between claim and non-claim observations, with non-claim instances significantly outnumbering claim cases.
This imbalance suggests that accuracy alone would be an inadequate evaluation metric. Consequently, additional evaluation measures such as **ROC-AUC, recall, precision, and F1-score** were more appropriate for evaluating model performance. The observed class imbalance motivates the use of class-weighted models and robust tree-based models.

 2. Numerical Feature Analysis

 Descriptive  statistics and distribution plots were used to analyse numerical variables. Several features exhibited skewed distribution and the presence of extreme values in building age and insured duration. These findings suggest that numerical variables contain valuable information and may exhibit a non-linear relationship with the target variable, and tree-based models were considered suitable. 
 
 3. Categorical Feature Analysis

 Categorical variables were analyzed using the  necessary statistical method  and claim rate comparison. The analysis revealed differences in claim occurrence across several cataegories  e.g, buildings without fencing exhibited higher claim frequencies than  fenced buildings, and the presence or absence of a garden and building painting status showed varying claim tendencies. These patterns indicates cataegorical play a significant role in differentiating claim risk, which are vitals for predictive models.

4. Temporal and Derived Feature Analysis

The dataset includes time-related variables such as **Year of Observation** and **Date of Occupancy**. Exploratory analysis shows these variables are strongly related, enabling the derivation of a new feature representing **building age at the time of observation**.
The derived *building age* feature provided a more interpretable and risk-relevant measure compared to raw date variables. The transformation improved model interpretability and reduced redundancy among correlated temporal variables.

5. Correlation and Feature Relationships

Correlation analysis among numerical variables identified moderate to strong relationships between certain predictors, those derived from temporal features. while Multicolinearity is less problematic for tree-based models, this analysis informed feature selection decisions and helped avoid redundant information.
The result of this analysis supported the choice of ensemble learning methods capable of capturing complex interactions among features.

### Model Evaluation and Results

### 1. Evaluation Strategy

To ensure reliable and unbiased performance assessment, the dataset was divided into **training and test sets** using a stratified split to preserve the original class distribution of insurance claims.

Given the **class imbalance** typically observed in insurance claim data and the **asymmetric business costs of misclassification**, model performance was evaluated using **cost-sensitive and probability-based metrics** rather than accuracy alone.

The following models were trained and evaluated:

* **Random Forest Classifier**
* **XGBoost Classifier**

Both models were trained using identical training and test splits to ensure a fair comparison.

### 2. Evaluation Metrics

The evaluation focused on the following metrics:

* **Recall (Claim Class)**
  Measures the ability of the model to correctly identify buildings that experienced at least one insurance claim. This metric is critical, as false negatives (missed claims) represent a high financial risk to the insurer.

* **ROC-AUC (Area Under the Receiver Operating Characteristic Curve)**
  Assesses the model’s overall ability to distinguish between claim and non-claim buildings across all classification thresholds. ROC-AUC is threshold-independent and robust to class imbalance.

* **Precision (Claim Class)**
  Used as a supporting metric to evaluate how many predicted claim cases were correct.

Accuracy was reported for completeness but was **not used as a primary decision metric** due to its limitations in imbalanced and cost-sensitive contexts.

### 3. Model Performance Results

The table below summarizes the performance of the evaluated models on the test dataset:

| Model         | ROC-AUC  | Recall (Claim) | Precision (Claim) | Accuracy       |
| ------------- | -------- | -------------- | ----------------- | -------------- |
| Random Forest | Moderate | Moderate       | Higher            | Higher         |
| XGBoost       | Higher   | Higher         | Moderate          | Slightly Lower |

### 4. Comparative Analysis

The **XGBoost classifier** demonstrated superior performance in terms of **ROC-AUC and recall for the claim class**, indicating a stronger ability to:

* Capture complex, non-linear relationships in the data
* Correctly identify high-risk buildings
* Minimize costly false negatives

While the Random Forest model achieved slightly higher precision and overall accuracy, this came at the expense of **lower recall**, implying a higher number of missed claim cases — an undesirable outcome from an insurance risk perspective.

### 5. Business Interpretation of Results

From a business standpoint:

* **Missing a claim-prone building (false negative)** can lead to underpricing and unexpected payouts.
* **Flagging a low-risk building as high-risk (false positive)** typically results in minor premium adjustments and manageable customer impact.

Given this imbalance in cost, the **XGBoost model’s higher recall** makes it more suitable for operational deployment, as it prioritizes risk detection over conservative accuracy measures.

### 6. Final Model Selection

Based on both **statistical performance** and **business relevance**, the **XGBoost classifier** was selected as the final model.

The selection was driven by:

* Strong discriminatory power (high ROC-AUC)
* Superior recall for claim prediction
* Better alignment with insurance risk management objectives

The final model provides a robust foundation for:

* Risk-based underwriting
* Premium optimization
* Preventive risk intervention strategies

### 7. Limitations and Future Improvements

Despite strong performance, several limitations remain:

* The model does not account for **claim severity**, only claim occurrence
* External risk factors (e.g., weather, crime rates) were not included
* Threshold optimization could further improve cost-efficiency
 
 
