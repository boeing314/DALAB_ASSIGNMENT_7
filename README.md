# DA5401 A7 – Multi‑Class Model Selection using ROC & PRC

##  Objective
This project performs **multi‑class land‑cover classification** using the **UCI Landsat Satellite dataset** and evaluates multiple machine learning models using:
- **Weighted F1‑Score**
- **Macro‑Averaged ROC‑AUC**
- **Macro‑Averaged Precision‑Recall (AP) Score**

The primary goal is to determine:
- The best model  
- The worst model  
- Effectiveness of evaluation metrics beyond simple accuracy  

---

## Dataset Summary
- **Dataset:** UCI Statlog (Landsat Satellite)
- **Classes:** 6 land cover types  
- **Features:** Spectral reflectance data from satellite sensors  
- **Challenge:** Moderate class overlap and imbalance

Source:  
https://archive.ics.uci.edu/dataset/146/statlog+landsat+satellite

---

##  Models Trained
| Model | Library | Notes |
|-------|---------|------|
| KNN (k=5) | sklearn | Instance‑based baseline |
| Decision Tree | sklearn | High variance |
| Logistic Regression | sklearn | Linear decision boundaries |
| Gaussian Naive Bayes | sklearn | Independence assumption often invalid |
| Dummy Classifier (Prior) | sklearn | Baseline reference |
| SVC (probability=True) | sklearn | Non‑linear kernel → expected best performance |
| Random Forest | sklearn | Ensemble of decision trees |
| XGBoost | xgboost | Gradient boosting, strong model |

---

##  Methodology

###  Part A – Baseline Metrics
- Standardization using `StandardScaler`
- Train/Test split: **85% / 15%**
- Compute **Weighted F1**

###  Part B – ROC Analysis
- OvR (One‑vs‑Rest) Multi‑Class ROC
- Macro‑averaged AUC
- Single ROC plot with all model curves

###  Part C – PRC Analysis
- Multi‑Class Macro‑Averaged Precision‑Recall curves
- Compute **Average Precision (AP)**

###  Part D – Final Model Selection
Comparison of Rankings (Highest → Lowest):

**Weighted F1 Ranking**
> KNN > SVC > Decision Tree > Logistic Regression > GaussianNB > Dummy Prior

**Macro ROC‑AUC Ranking**
> SVC > KNN > Logistic Regression > GaussianNB > Decision Tree > Dummy Prior

**Macro AP Ranking**
> SVC > KNN > Logistic Regression > GaussianNB > Decision Tree > Dummy Prior

- **SVC consistently top in threshold‑based metrics**  
- Dummy Prior performs like random guessing (AUC ≈ 0.50)  
- **KNN‑1** (Brownie Model) → AUC < 0.50 due to noise sensitivity

---

## Final Recommendation

> **Support Vector Classifier (SVC)** is the best model for this classification task

---

##  Key Plots Included in Notebook
- Macro‑Averaged OvR ROC Curve (All Models)
- Macro‑Averaged Precision‑Recall Curve (All Models)
- Performance Summary Table (F1, AUC, AP)

---

##  Files Included
| File | Description |
|------|------------|
| A7.ipynb | Full implementation with visualizations and analysis |
| README.md | This summary report |

---

