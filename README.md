# 💳 Predictive Credit Risk Modeling

**Can we predict which borrowers will default before it happens?**

This ML system analyzes 1.35 million loans to flag high-risk borrowers early, enabling banks to intervene proactively and avoid millions in losses.

**Bottom line:** Achieves 72% accuracy and catches 53% of defaults while only rejecting 24% of good applicants.

---

## 🎯 Key Results

| Metric | Value | What It Means |
|--------|-------|---------------|
| **AUC-ROC** | 0.72 | Strong predictive accuracy |
| **Default Detection** | 53% | Catches half of all defaults proactively |
| **Precision** | 36% | 1 in 3 flagged loans actually defaults |
| **False Positive Rate** | 24% | Minimizes rejection of creditworthy applicants |

---

## 💰 Business Impact: $500M Portfolio Example

**Without Model:**
- 100,000 defaults × $15K avg loan = **$1.5B in losses**

**With Model:**
- Flag 53,000 high-risk loans for intervention
- 30% intervention success rate = 15,900 defaults prevented
- **$238.5M in avoided losses annually**

---

## 💡 The Problem

Traditional credit scores are **static snapshots** of the past. They can't predict who's about to experience financial distress.

**The gap:** Banks need to identify at-risk borrowers 6-12 months in advance to offer interventions (counseling, restructuring) before default.

---

## 🔍 Key Findings

### What Actually Predicts Default?

Tested everything. Here's what matters most:

1. **Loan Grade** (validates existing underwriting)
2. **Interest Rate** (lender's risk perception)
3. **Loan Term** (longer = more risk exposure)
4. **Loan-to-Income Ratio** (borrowing beyond means)
5. **Debt-to-Income Ratio** (existing financial strain)

**Surprising insight:** Annual income barely matters (-0.04 correlation). It's not what you earn—it's how stretched you already are.

---

## 🛠️ How It Works

### 1. Data Engineering
- Started with 2.26M raw loans
- Cleaned to 1.35M completed loans (removed in-progress loans)
- Created 9 financial risk features

### 2. Model Selection
Tested three algorithms:
- Logistic Regression: 0.53 AUC ❌
- Random Forest: 0.71 AUC
- **XGBoost: 0.72 AUC** ✅

### 3. The Critical Decision: Threshold Optimization

**Standard approach (50% threshold):** Caught only 7% of defaults—unusable.

**Business-driven approach (25% threshold):** Caught 53% of defaults—deployment-ready.

**Why this matters:** This is where technical modeling meets business reality. The threshold choice balances:
- **False negatives** (missed defaults) = direct financial loss
- **False positives** (rejected good loans) = opportunity cost

---

## 📊 Model Validation

**The model learned real risk factors, not noise.**

Top predictors align perfectly with financial domain knowledge:
- Loan grade (existing business logic) ✅
- Interest rates (price reflects risk) ✅  
- Debt ratios (financial strain) ✅

This proves the model would generalize to new borrowers, not just memorize training data.

---

## 🚀 Tech Stack

**Python** | **XGBoost** | **Scikit-learn** | **Pandas** | **Matplotlib**

---

## 📁 Project Structure
```
credit-risk-modeling/
├── data/
│   ├── raw/              # Download from Kaggle (too large for GitHub)
│   └── processed/
├── notebooks/
│   └── 01_eda_modeling.ipynb
├── models/
│   └── credit_risk_xgb.pkl
└── README.md
```

---

## 💻 Running the Project

1. **Clone repo:**
```bash
   git clone https://github.com/jasonodom44/credit-risk-modeling.git
```

2. **Download data:** [Lending Club Dataset on Kaggle](https://www.kaggle.com/datasets/wordsforthewise/lending-club)

3. **Place file:** `data/raw/accepted_2007_to_2018Q4.csv.gz`

4. **Install dependencies:**
```bash
   pip install pandas numpy scikit-learn xgboost matplotlib seaborn jupyter
```

5. **Run notebook:** `notebooks/01_eda_modeling.ipynb`

---

## 🎓 What I Learned

✅ **Threshold optimization is a business decision**, not just a technical one  
✅ **Feature importance validates model quality** - top predictors should make sense  
✅ **Class imbalance requires strategy** - standard metrics can mislead with 20% default rates  
✅ **Domain knowledge matters** - model must learn actual risk factors, not correlations

---

## 👤 About

**Jason Odom**  
Data Analytics Student | California State University, Fresno  
Risk Analytics Intern @ DaVita Dialysis

This project demonstrates end-to-end ML capability: from business problem definition → data engineering → model selection → deployment-ready calibration.

**Connect:** [LinkedIn](https://www.linkedin.com/in/jasonmodom) | [Portfolio](https://jasonodom44.github.io) | [Email](mailto:jasonodom44@gmail.com)

---

## 📄 Data Attribution

Dataset: [Lending Club (2007-2018)](https://www.kaggle.com/datasets/wordsforthewise/lending-club)  
Note: Educational project using historical data. Not financial advice.
