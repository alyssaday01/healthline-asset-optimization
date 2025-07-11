# 📊 ***From Random to Relevant:* A Predictive Asset Targeting Study**
**Optimizing Conversion and Revenue**

---

## Problem Statement

Healthline currently uses a **random asset assignment strategy** for visitors. While this ensures broad exposure across content, it ignores available user signals — potentially limiting both **conversion rate** and **total revenue**.

This project explores whether **predictive modeling** can improve outcomes by recommending the asset most likely to convert for each user session.

---

## 📁 Project Structure

```plaintext
healthline-asset-optimization/
├── data/
│   └── Case_Material.xlsx            # Provided dataset
├── notebooks/
│   └── healthline_analysis.ipynb     # Full analysis notebook
├── README.md                         # This file
```

---

## 🧪 Methodology Overview

### 1. Exploratory Data Analysis (EDA)
Initial exploration revealed conversion rates vary by:
- **Asset Shown**: Asset C had the highest conversion rate (~17%)
- **Diagnosis Group**: Known diagnoses like Ulcerative Colitis outperform unknowns — but unknown users still convert well
- **Device Type**: Mobile users converted more often than desktop users
> 📌 These patterns suggest that personalization has potential — even when user profiles are incomplete.

### 2. Asset Value Analysis *(Business Impact)*
Even though Asset C had the highest conversion rate, it drove the lowest revenue. Why?
- **Asset A** had the highest **total revenue** due to more overall conversions (despite a lower $5 average per-conversion value)
- **Asset B** offered the **highest value** per conversion at $7 but lagged in volume
- **Asset C**'s $2.50 per-conversion value limits its overall impact
> 💡 Conversion rate alone is insufficient — asset evaluation must also consider **revenue per conversion** to guide optimization strategies.

### 2. Feature Engineering
Several features were engineered to capture relevant engagement behavior and contextual cues:
- `time_to_asset_sec`: Seconds from session to start to asset load
- `is_morning`, `is_evening`: Flags based on time-of-day hour
- `time of day`: Raw hour data used for time-window analysis
- One-hot encoding of categorical variables (e.g., device type, diagnosis)

#### Additional Analysis
- **Conversion Rate by Asset & Time of Day**
  Afternoon sessions had the highest average conversion rates overall.
  - Asset A and C performed best in the **afternoon**
  - Asset B peaked in the **evening**
 > ⏰ **Timing matters** — asset performance varies by time of day, suggesting value in time-aware targeting.

### 3. Modeling Approaches
Two models were trained to predict the **probability of conversion**, using behavioral and contextual features (e.g., diagnosis, device, time-to-asset, time of day):
- **Logistic Regression**  
  A baseline model that offers strong performance and interpretability
- **Random Forest Classifier (calibrated)**  
  A more expressive model for capturing non-linear interactions
> Both models were trained on balanced class samples and tested on held-out data.

### 4. Model Evaluation
Models were evaluated using:
- **ROC-AUC Scores**: Random Forest slightly outperformed Logistic Regression
- **Feature Importances**: Return Visitor, time before asset display, and time of day were top drivers
- **Business Simulations**: Used predicted probabilities to assign the optimal asset per session
  > Logistic Regression tended to produce **higher simulated revenue**, while Random Forest offered **more conservative, but realistic performance**.

---

## 💰 Simulated Business Impact

Simulations used predicted conversion probabilities to assign the asset most likely to convert per session.

| Strategy | Simulated Revenue | % Uplift vs. Baseline |
|----------|-------------------|------------------------|
| Random (Current) | \$7,166 | — |
| Logistic Regression | \$37,762 | +427.85% |
| Random Forest | \$15,062 | +44.56% |

> **Note**: Simulations are illustrative, and actual impact may vary. These results emphasize the value of using predictive targeting over randomness.

---

## 🔑 Key Takeaways

- **User signals are actionable** — even sessions with missing diagnosis can be targeted effectively
- **Conversion ≠ Revenue** — a high conversion rate doesn’t guarantee high value
- **Feature-engineered inputs**, such as time-to-asset and known diagnosis, drive strong performance
- Predictive targeting outperforms random assignment across all tested strategies
- Even simple models like Logistic Regression can unlock major gains in personalization
> Decided to keep the '`Unknown Diagnosis` value to preserve data purity and avoid losing useful information

---

## ✅ Final Analysis & Recommendation
This analysis addresses the core challenge from the case study: **random asset assignment leaves conversion and revenue on the table**.

To test predictive targeting:
- A **Logistic Regression** model established the baseline and demonstrated the largest simulated revenue gain (+427%)
- A **Random Forest** model captured more complex behavior and still outperformed random logic (+110%)
> While Logistic Regression had the highest simulated uplift, the **Random Forest** model offers a **realistic deployment choice** — balancing performance and robustness without overconfidence in predictions.

---

## 🚀 Deployment Recommendations
- **Real-Time Integration**: Serve asset recommendations through an API during the session
- **A/B Testing Framework**: Compare predictive targeting vs. current assignment logic in live experiments
- **Monitoring & Iteration**: Track feature drift, retrain periodically, and refine based on updated behavior
- **Fallback Logic**: Implement edge-case handling for sessions with incomplete or short engagement data

---

## 🔧 Tech Stack

- Python (Pandas, NumPy, Scikit-learn, Seaborn, Matplotlib)
- Jupyter Notebook
- Git & GitHub for version control and collaboration

---

## 📓 Notebook

The full analysis notebook can be found here: ```notebooks/healthline_analysis.ipynb```

---

## 🖥️ Presentation Deck

View the 4-slide executive summary here: [Optimizing Asset Strategy - Slide Deck](https://www.canva.com/design/DAGssqJldq4/cCYKavNmBDyKxfZ1Yn9vLA/edit?ui=eyJBIjp7fX0)

---

## 👤 Author

**Alyssa Day**  
Data Science | Artificial Intelligence | Strategy & Impact  
[GitHub](https://github.com/alyssaday01) • [LinkedIn](https://www.linkedin.com/in/alyssaday01/)
