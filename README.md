# Random Forest Analysis in R (DAT 640 Practical R Activity Seven)

![R](https://img.shields.io/badge/R-Programming-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Decision%20Trees%20%26%20Random%20Forest-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

> **Course:** DAT 640 – Practical R  
> **Activity:** Seven (Lab 8.3.1 & Random Forest Exploration)  
> **Deliverable:** Complete analysis with screenshots and findings  

---

## Overview
This lab focused on exploring **Decision Trees** and **Random Forests** in R using the `birthwt` dataset from the **MASS** package. The target variable was **low** (indicator of low birth weight < 2.5 kg). Predictors included **maternal factors** such as age, weight (`lwt`), prior premature labor (`ptl`), smoking status, race, hypertension (`ht`), and uterine irritability (`ui`).  

The assignment had three key steps:  
1. Plotting and interpreting a **Classification Tree** in R.  
2. Building a **Decision Tree model** and analyzing results.  
3. Building a **Random Forest model**, performing variable importance analysis, and comparing results to the Decision Tree.  

---

## Part 1: Classification Tree

The **Classification Tree** was built as an initial exploration of the data. This simple model illustrated how categorical and numeric predictors can be split recursively to classify whether a newborn’s birth weight is low (< 2.5 kg).  

![Figure 1 — Classification Tree](rf-DB1.png)

> *Observation:* Even at this early stage, the tree began splitting on **maternal weight** and **prior premature labor**, reinforcing the intuition that these are critical risk factors for birth outcomes.

---

## Part 2: Decision Tree Model

The **Decision Tree** was trained to predict low birth weight outcomes (`low`).  

### Findings:
- **Accuracy:** **71.05%** — correctly classified ~71% of newborns.  
- **Most important split:** `ptl < 1` (prior premature labor).  
- **Maternal weight (`lwt`)** repeatedly appeared as a key split:
  - `lwt >= 106` reduced likelihood of low birth weight.  
  - `lwt >= 132` was also important in the smaller subgroup (`ptl ≥ 1`).  
- **Age:** Mothers younger than 20 showed higher risk of delivering low birth weight babies.  

### Interpretation:
The Decision Tree clearly highlighted **prior premature labor** and **maternal weight** as the strongest predictors of low birth weight. While interpretable, the single tree structure risks **overfitting** and had only moderate predictive power.  

![Figure 2 — Decision Tree Model](rf-DB2.png)

---

## Part 3: Random Forest Model

The **Random Forest** algorithm was trained using the same predictors, averaging across many decision trees to reduce overfitting.  

### Findings:
- **Accuracy:** **71.05%**, the same as the Decision Tree.  
- **OOB (Out-of-Bag) Error Estimate:** **33.11%**, suggesting misclassification in about one-third of cases.  
- **Variable importance (Mean Decrease in Gini):**  
  - **Maternal weight (`lwt`) = 15.25**  
  - **Age = 12.68**  
  - **Hypertension (`ht`) = 2.45**  
  - **Uterine irritability (`ui`) = 3.41**  
- **Interpretation:** Weight and age were confirmed as the strongest predictors, while hypertension and uterine irritability played a smaller role.  

### Interpretation:
The Random Forest model validated the Decision Tree’s findings but with more stability and less risk of overfitting. Although the **overall accuracy remained the same**, the Random Forest provided richer insights through **variable importance rankings**.  

![Figure 3 — Random Forest](rf-DB3.png)

---

## Comparative Evaluation

| Aspect | Decision Tree | Random Forest |
|--------|---------------|---------------|
| **Accuracy** | 71.05% | 71.05% |
| **OOB Error** | N/A | 33.11% |
| **Interpretability** | High (clear splits, easy to follow) | Medium (ensemble model, less transparent) |
| **Risk of Overfitting** | Higher | Lower |
| **Key Predictors** | `ptl`, `lwt`, `age` | `lwt`, `age`, `ptl` (confirmed with importance scores) |

**Summary:**  
- The Decision Tree is easy to interpret but less stable.  
- The Random Forest improves generalization by averaging trees, reducing overfitting.  
- Both models consistently identified **maternal weight** and **age** as top predictors of birth outcomes, with **prior premature labor** as another major factor.  

---

## Key Skills Demonstrated
- **R Programming:** Used RStudio and R libraries to train and evaluate models.  
- **Machine Learning Fundamentals:** Built and interpreted **Decision Trees** and **Random Forests**.  
- **Data Understanding:** Connected predictors like age, maternal weight, and prior premature labor to medical/real-world implications.  
- **Model Evaluation:** Reported accuracy, OOB error, and variable importance.  
- **Critical Analysis:** Compared models, highlighting interpretability vs robustness trade-offs.  
- **Documentation:** Embedded code results, screenshots, and narrative into a professional README.  

---

## Future Improvements
- Tune Random Forest hyperparameters (e.g., number of trees, mtry) to optimize accuracy.  
- Try cross-validation for a more robust performance estimate.  
- Test alternative models (e.g., logistic regression, gradient boosting) for comparison.  
- Visualize variable importance using bar plots for more intuitive communication.  

---

## Repo Description
Practical R Activity Seven (DAT 640): Decision Tree vs Random Forest analysis on the **MASS birthwt dataset**. Demonstrates classification modeling, accuracy evaluation, variable importance analysis, and comparative discussion of interpretability vs robustness.  

---

## Tags
