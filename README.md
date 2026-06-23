# 🏦 Personal Loan Acceptance Prediction Bank Marketing Analysis

> Predicting which bank customers are likely to accept a personal loan offer using classification models on the UCI Bank Marketing Dataset.

---

## 📌 Task Objective

Banks run telemarketing campaigns to promote financial products such as term deposits and personal loans. Contacting every customer is costly and inefficient. The goal of this task is to **predict which customers are likely to accept a personal loan offer**, so the bank can focus its marketing resources on high-potential customers and reduce unnecessary contact with those unlikely to subscribe.

**Target Variable:** `deposit` whether a customer subscribed to a term deposit (`yes` / `no`)

---

## 📂 Repository Structure

```
personal-loan-acceptance-prediction/
│
├── Task5_PersonalLoanAcceptance.ipynb   # Main Jupyter Notebook (fully executed)
├── bank.csv                             # Dataset (UCI Bank Marketing Repository)
├── README.md                            # Project overview (this file)
└── Images/
├── ├── ├── ├── ├── ├── ├── ├── ├── ├── ├── ├── ├── ├── ├── ├──
```

---

## 🗂️ Dataset

| Property | Detail |
|---|---|
| Source | UCI Machine Learning Repository Bank Marketing Dataset |
| Records | 11,162 customer entries |
| Features | 16 (demographic + campaign-related) |
| Target | `deposit`: yes/no |

**Key features used:** `age`, `job`, `marital`, `education`, `balance`, `duration`, `campaign`, `pdays`, `previous`, `poutcome`, `contact`, `housing`, `loan`, `default`

---

## 🔧 Approach

### 1. Data Cleaning & Preparation
- Checked for missing values → none found
- Removed duplicate rows
- Relabelled `'unknown'` in `poutcome` to `'not_contacted'` for clarity
- Engineered two new features:
  - `age_group` customers binned into 6 age bands (18–25, 26–35, …, 65+)
  - `prev_contacted` binary flag: 1 if customer was contacted in a prior campaign
- Encoded target variable: `yes` → 1, `no` → 0
- Label-encoded all categorical features for model input

### 2. Exploratory Data Analysis (EDA)
Performed 9 visualisations to understand patterns before modelling:

| Plot | Insight |
|---|---|
| Target Distribution | Dataset is nearly balanced: 47.4% accepted vs 52.6% declined |
| Age Distribution | Customers aged 18–25 and 65+ accept more often |
| Job Type Analysis | Students and retired customers show the highest acceptance rates |
| Marital Status | Single customers accept slightly more than married/divorced |
| Education Level | Tertiary-educated customers accept at a higher rate |
| Bank Balance | Customers with higher balances are more likely to subscribe |
| Correlation Heatmap | `duration` has the strongest positive correlation with acceptance |
| Campaign Contacts | Acceptance drops sharply after 3 contacts, over-calling hurts conversion |
| Previous Outcome | Prior campaign `success` leads to 60%+ acceptance rate |

### 3. Model Training
Both models were trained on an **80/20 stratified train-test split**:

- **Logistic Regression:** max_iter=1000`, linear probabilistic classifier
- **Decision Tree:** max_depth=6`, `min_samples_split=20` to prevent overfitting

### 4. Evaluation
Models were evaluated using: Accuracy, Precision, Recall, F1-Score, ROC-AUC, Confusion Matrix, and ROC Curve comparison.

---

## 📊 Results

| Metric | Logistic Regression | Decision Tree |
|---|---|---|
| **Accuracy** | ~80% | ~82% |
| **Precision** | ~79% | ~81% |
| **Recall** | ~78% | ~80% |
| **F1-Score** | ~78% | ~80% |
| **ROC-AUC** | ~0.85 | ~0.83 |

- The **Decision Tree** achieved slightly higher accuracy and is more interpretable for business stakeholders
- **Logistic Regression** produced smoother probability estimates (higher ROC-AUC), making it better for risk scoring

### 🏆 Top Predictors (Decision Tree Feature Importance)
1. **`duration:`** Call length is the single most powerful predictor
2. **`poutcome:`** Previous campaign outcome strongly influences current acceptance
3. **`balance:`** A higher account balance correlates with acceptance
4. **`age:`** Younger and older customers are more receptive
5. **`campaign:`** Number of contacts has a negative relationship with acceptance

---

## 💡 Key Business Insights

1. **Call duration matters most:** Longer, meaningful calls strongly predict acceptance. Train agents to maintain quality conversations rather than rushing.

2. **Re-target past successes:** Customers from previous successful campaigns convert at 60%+. Always prioritise this group in the next campaign.

3. **Age targeting:** Focus marketing on **18–25 year olds** (early savers) and **65+ retirees** (investment-focused), as they show the highest acceptance rates.

4. **Job-based segmentation:** **Students** and **retired** customers are the most receptive groups. Blue-collar and service workers respond least.

5. **Stop over-calling:** Acceptance rates drop sharply after 3 contacts per customer. Limit each customer to 3 calls per campaign.

6. **Higher-balance customers:** are better prospects, they have financial capacity and are more interested in savings/investment products.

7. **Single customers:** show slightly higher acceptance than married or divorced possible indicator of greater financial flexibility.

---

## 🚀 How to Run

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/Data-Science-Internship-Task5--LoanAcceptancePrediction.git
cd personal-loan-acceptance-prediction

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn

# 3. Launch Jupyter
jupyter notebook Task5_PersonalLoanAcceptance.ipynb
```

> **Note:** Make sure `bank.csv` is in the same directory as the notebook before running.

---

## 🛠️ Technologies Used

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-EDA-green)
![Scikit--learn](https://img.shields.io/badge/Scikit--learn-Models-orange)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualisation-red)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualisation-purple)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-yellow)

---
