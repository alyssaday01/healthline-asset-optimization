# From Random to Relevant: A Predictive Asset Targeting Study
**📊 Optimizing Asset Strategy for Healthline**

---

This repository contains a data science case study focused on improving Healthline's content asset strategy. Historically, assets were randomly assigned to users at the end of article pages. This project demonstrates how predictive modeling can shift the strategy **from random assignment to relevance-driven targeting**, maximizing both user engagement and revenue.

---

## 🎯 Objective

Healthline’s business team sought a data-driven method to determine which content assets should be shown to users based on session context. The dataset includes one month of page views and conversion behavior for a subset of page categories.

> The goal: **Increase revenue per page view** by showing users the right asset, at the right time, based on behavioral and contextual signals.

---

## 📁 Project Structure

```plaintext
healthline-asset-optimization/
├── data/ │
└── Case_Material.xlsx # Provided dataset
├── notebooks/ │
└── healthline_analysis.ipynb # Full analysis notebook
├── README.md # This file
```

---

## 🧪 Methodology Overview

### 1. Exploratory Data Analysis (EDA)
- Grouped bar chart by **Asset** and **Diagnosis**
- Identified that **Asset C** and **users with unknown diagnoses** consistently converted at higher rates
  
### 2. Feature Engineering
- `time_to_asset_sec`: Time on page before asset is shown
- Session hour bins (`is_morning`, `is_evening`)
- Page category encoding
- Return visitor flags

### 3. Modeling Approaches
Two models were developed to predict user conversion:

- **Logistic Regression**  
  A baseline model that offers strong performance and interpretability

- **Random Forest Classifier (calibrated)**  
  A more expressive model for capturing non-linear interactions

### 4. Model Evaluation
- ROC-AUC and classification reports
- Feature importance and coefficient interpretation
- Both models simulated in a business context using real conversion probabilities

---

## 💰 Simulated Business Impact

Simulations used predicted conversion probabilities to assign the asset most likely to convert per session.

| Strategy | Simulated Revenue | % Uplift vs. Baseline |
|----------|-------------------|------------------------|
| Random (Current) | \$7,166 | — |
| Logistic Regression | \$37,762 | +427.85% |
| Random Forest | \$15,062 | +110.24% |

> **Note**: Simulations are illustrative, and actual impact may vary. These results emphasize the value of using predictive targeting over randomness.

---

## 📈 Key Takeaways

- Conversion signals are detectable and actionable, even for incomplete user profiles (**e.g., unknown diagnoses**)
- Lightweight models like Logistic Regression can outperform baselines with strong, clean features
- Feature-driven targeting supports both revenue growth and user personalization
- Model outputs can be used to operationalize **real-time asset matching**

---

## 🧭 Recommendations for Deployment

- **Real-Time Integration**: Deploy the trained model behind a lightweight API to serve asset recommendations during the session
- **A/B Testing Framework**: Run controlled experiments to compare predictive targeting vs. current random logic
- **Iterative Improvement**: Monitor feature drift and retrain periodically using fresh engagement data
- **Edge Case Handling**: Include fallback logic for extremely short sessions or missing data

---

## 🔧 Tech Stack

- Python (Pandas, NumPy, Scikit-learn, Seaborn, Matplotlib)
- Jupyter Notebook
- Git & GitHub for version control and collaboration

---

## 📓 Notebook

The full analysis notebook can be found here: ```notebooks/healthline_analysis.ipynb```

--

## 🖥️ Presentation Deck

View the 4-slide executive summary here: [Optimizing Asset Strategy - Slide Deck]([link_here](https://www.canva.com/design/DAGssqJldq4/cCYKavNmBDyKxfZ1Yn9vLA/edit?ui=eyJBIjp7fX0))

---

## 👤 Author

**Alyssa Day**
Data Science | Artificial Intelligence | Strategy & Impact
[Github](https://github.com/alyssaday01) * [LinkedIn](https://www.linkedin.com/in/alyssaday01/)
