# # Credit_Risk: Quantitative Probability of Default (PD) Modeling

## 1. Executive Summary
This project develops a robust **Credit Scoring Engine** designed to predict the likelihood of a borrower failing to meet loan obligations. Using the LendingClub dataset, I developed a **Random Forest Ensemble** pipeline that incorporates advanced data balancing techniques and discriminatory analytics to assist in institutional risk decision-making.



## 2. Theoretical Framework
In institutional banking (e.g., JPMorgan, Goldman Sachs), risk is measured through three core components that determine the **Expected Loss (EL)**:

* **PD (Probability of Default):** The likelihood a borrower stops paying (The focus of this model).
* **LGD (Loss Given Default):** The percentage of exposure lost if a default occurs.
* **EAD (Exposure at Default):** The total amount owed at the time of default.

The relationship is formally expressed as:
$$Expected Loss = PD \times LGD \times EAD$$

## 3. Methodology & Governance

### A. Data Integrity
To maintain institutional standards, I implemented automated cleaning protocols to handle missingness in critical financial features like `int.rate` and `installment`. This ensures the model does not derive biased estimators from incomplete or low-quality data records.

### B. Class Imbalance Mitigation (SMOTE)
Credit datasets are inherently imbalanced as defaults are "rare events." To prevent the model from becoming biased toward the majority "Safe" class, I utilized **SMOTE** (Synthetic Minority Over-sampling Technique). This creates synthetic examples of the minority class, allowing the model to learn the specific "Red Flags" associated with high-risk profiles.



### C. Feature Engineering
Categorical data, such as **Loan Purpose**, was transformed using **One-Hot Encoding**. This allows the mathematical engine to quantify qualitative risks, such as the statistical difference in risk between debt consolidation and small business ventures.

---

## 4. Performance Diagnostics & Analytics

### The ROC Curve (Discriminatory Power)
The model achieves an **AUC (Area Under the Curve) of 0.66**. This metric represents the model's ability to distinguish between "Safe" and "Default" profiles. In the context of unsecured consumer lending, an AUC > 0.60 is considered a statistically significant baseline for risk separation.



### Feature Importance (Risk Drivers)
The model identified **Interest Rate**, **FICO Score**, and **Debt-to-Income (DTI)** as the primary predictors of risk. This validates the model against economic theory: higher risk is priced with higher interest rates as a risk-mitigation premium.



### Operational Impact (Confusion Matrix)
The output provides the foundation for **Threshold Tuning**. By analyzing **False Negatives** (missed defaults), a financial institution can calibrate its **Risk Appetite**. A conservative institution would adjust the decision threshold to prioritize catching more defaults, thereby minimizing potential capital loss.



## 5. Future Roadmap
* **Hyperparameter Optimization:** Implementing `GridSearchCV` to optimize tree depth and prevent overfitting.
* **Explainable AI (XAI):** Integrating **SHAP values** to provide "Reason Codes" for loan rejections, ensuring compliance with Fair Lending regulations (e.g., ECOA).
* **Alternative Data Integration:** Incorporating non-traditional data (utility/rent payment history) to break the current discriminatory power ceiling.

---
