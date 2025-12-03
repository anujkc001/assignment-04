# Global Pollution Severity Classification Project

##  Project Objective
The goal of this project was to classify countries into three distinct **Pollution Severity** categories—**Low, Medium, and High**—based on various environmental, industrial, and economic factors. This classification is intended to provide a clear framework for targeted environmental policy and resource allocation.

***

##  Methodology: Key Phases

### Phase 1: Data Preprocessing & Feature Engineering
* **Data Cleaning:** Handled missing values using **median** imputation for numerical features (e.g., CO2, Industrial Waste) to ensure robustness against outliers.
* **Target Creation:** The multi-class target (`Pollution_Severity`) was created based on the **Air Pollution Index**, using **tertiles** (33.3% and 66.6% quantiles) to define the Low, Medium, and High classes.
* **Scaling & Encoding:** Features were **standardized** (StandardScaler) and categorical features (`Country`, `Year`) were **Label Encoded**.
* **Engineered Feature:** The **Years\_Since\_Start** feature was created to capture underlying pollution trends over time.

### Phase 2: Classification Modeling
Three comparative classifiers were implemented and tuned using **Cross-Validation** (`GridSearchCV`):

1.  **Multinomial Naive Bayes (MNB):** Used primarily as a baseline model (data was scaled to the $[0, 1]$ range for compatibility).
2.  **K-Nearest Neighbors (KNN):** Tuned for optimal **K** neighbors, leveraging the strength of distance metrics on the standardized data.
3.  **Decision Tree (DT):** Tuned using `max_depth` and `min_samples_split` to prevent overfitting and enhance interpretability.

***

##  Phase 3: Reporting and Insights

### Model Comparison Summary

| Model | Optimal Tuning Parameter | Overall Accuracy | Recall (High Class) | F1-Score (Weighted) |
| :--- | :--- | :--- | :--- | :--- |
| **MNB** | N/A | [Insert MNB Accuracy] | [Insert MNB Recall] | [Insert MNB F1-Score] |
| **KNN** | K = [Insert Optimal K] | [Insert KNN Accuracy] | [Insert KNN Recall] | [Insert KNN F1-Score] |
| **Decision Tree** | Depth = [Insert DT Max Depth] | [Insert DT Accuracy] | [Insert DT Recall] | [Insert DT F1-Score] |

**Conclusion:** The **Tuned Decision Tree** is the recommended model for deployment due to its high performance and superior **Interpretability**, allowing policymakers to easily trace the cause-and-effect rules for any severity classification.

### Actionable Insights and Policy Recommendations

#### 1. Drivers of Pollution Severity (Feature Importance)

Analysis of the Decision Tree's **Feature Importance** highlights the critical factors for classification:

| Feature | Importance Score | Policy Implication |
| :--- | :--- | :--- |
| **[Insert Top Feature, e.g., CO2\_Emissions\_Scaled]** | **[Insert Score]** | Confirms industrial output as the dominant factor; must be the target of emissions controls. |
| **[Insert 2nd Feature, e.g., Industrial\_Waste (in tons)]** | **[Insert Score]** | Highlights waste management as a core environmental failure point. |
| **[Insert 3rd Feature, e.g., GDP\_Per\_Capita]** | **[Insert Score]** | Suggests economic ability is tied to environmental failure, requiring strict "Green GDP" enforcement. |

#### 2. Strategic Policy Recommendations

* **Targeted Regulation:** Implement mandatory regulatory audits and oversight in all countries classified in the **"High" Pollution Severity** category by the model.
* **Waste-to-Energy (WtE) Incentive:** Given the high importance of **Industrial Waste**, incentivize the expansion of WtE and advanced recycling facilities to convert a pollution driver into a resource (Energy Recovered).
* **Energy Transition:** Mandate ambitious targets for **Renewable Energy (%)** adoption in high-severity countries to address the root source of $\text{CO}_2$ emissions.

***
