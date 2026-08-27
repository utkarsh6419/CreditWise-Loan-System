# 💳 CreditWise Loan Approval System

> Machine Learning-based Loan Approval Prediction and Pre-Screening

CreditWise is an ML-assisted loan pre-screening project designed to predict whether a loan application is likely to be **Approved or Rejected** using historical applicant, financial, credit, employment, and loan information.

The project addresses the problem of slow and inconsistent manual screening by providing a fast, data-driven first-level prediction while keeping **human verification in the final decision loop**.

## 🎯 Problem

SecureTrust Bank's existing process requires loan officers to manually evaluate income, employment, credit history, and other application details. The supplied problem statement identifies this process as time-consuming, biased, and inconsistent. Incorrect screening can cause good customers to be rejected or high-risk customers to be approved.

CreditWise aims to learn patterns from historical applications and provide an initial **Approved / Rejected** prediction before final human verification.

## 🚀 Objectives

- Inspect and clean historical loan data.
- Handle missing values and inconsistent records.
- Encode categorical variables for ML models.
- Split data into training and testing sets.
- Scale features where appropriate.
- Train and compare multiple classification algorithms.
- Evaluate models using Accuracy, Precision, Recall, F1-score, and Confusion Matrix.
- Select a suitable model based on the project's evaluation objective.

## 📊 Dataset

The provided dataset contains **1,000 records and 20 original columns** representing loan applicants. The target is `Loan_Approved` (`1 = Approved`, `0 = Rejected`).

Key attributes include applicant/co-applicant income, employment status, age, marital status, dependents, credit score, existing loans, DTI ratio, savings, collateral value, requested loan amount, loan term, loan purpose, property area, education level, gender, and employer category.

## 🧠 ML Pipeline

```text
Historical Loan Data
        ↓
Data Inspection & Cleaning
        ↓
Missing Value Handling
        ↓
Categorical Encoding
        ↓
80/20 Train-Test Split
        ↓
Feature Scaling
        ↓
┌───────────────┬───────────────┬───────────────┐
│ Logistic      │ K-Nearest     │ Gaussian      │
│ Regression    │ Neighbors     │ Naive Bayes   │
└───────┬───────┴───────┬───────┴───────┬───────┘
        └───────────────┼───────────────┘
                        ↓
              Model Evaluation
                        ↓
              Approved / Rejected
```

## 🔧 Current Implementation

The notebook uses OneHotEncoder with `drop="first"` and `handle_unknown="ignore"`, followed by an 80/20 train-test split with `random_state=42`. Numerical/model inputs are standardized using `StandardScaler`.

Three classifiers are currently evaluated:

1. **Logistic Regression**
2. **K-Nearest Neighbors (KNN)** with `n_neighbors=5`
3. **Gaussian Naive Bayes**

## 📈 Current Results

Results reported by the executed notebook:

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---:|---:|---:|---:|
| Logistic Regression | **86.5%** | 78.33% | **77.05%** | **77.69%** |
| KNN | 76.0% | 62.75% | 52.46% | 57.14% |
| Naive Bayes | **86.5%** | **80.36%** | 73.77% | 76.92% |

The current notebook selects **Naive Bayes based on Precision**. In a real lending environment, final model selection should consider business costs, calibration, fairness, false approvals, false rejections, and regulatory requirements rather than one metric alone.

## 🧪 Evaluation

CreditWise evaluates:

- **Accuracy:** overall proportion of correct predictions.
- **Precision:** correctness of positive/approval predictions.
- **Recall:** proportion of actual approvals correctly identified.
- **F1-score:** balance between precision and recall.
- **Confusion Matrix:** breakdown of true/false positives and negatives.

## 📁 Repository Structure

```text
CreditWise-Loan-System/
├── README.md
├── PROBLEM_STATEMENT.md
├── credit_wise.ipynb
├── loan_approval_data.csv
├── requirements.txt
├── .gitignore
├── src/
│   └── README.md
├── app/
│   └── README.md
└── models/
    └── README.md
```

## 🛠️ Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## ▶️ Run Locally

```bash
git clone https://github.com/utkarsh6419/CreditWise-Loan-System.git
cd CreditWise-Loan-System
pip install -r requirements.txt
jupyter notebook
```

Open `credit_wise.ipynb` and run the notebook with `loan_approval_data.csv` in the repository root.

## 🔐 Responsible AI & Limitations

Credit decisions have significant financial consequences. This repository represents a machine-learning experiment and pre-screening prototype, not a production credit-decision engine.

A production system would require robust validation, cross-validation, fairness and bias testing, explainability, probability calibration, threshold analysis, privacy/security controls, model-drift monitoring, auditability, and appropriate human oversight and regulatory compliance.

## 🔮 Roadmap

- [ ] Build a reusable preprocessing pipeline
- [ ] Add cross-validation and hyperparameter tuning
- [ ] Compare additional classifiers
- [ ] Add explainability and feature analysis
- [ ] Add probability/risk scoring
- [ ] Add fairness evaluation
- [ ] Build a Streamlit interface
- [ ] Serialize and version production models
- [ ] Add API support
- [ ] Add automated tests and CI/CD
- [ ] Add model monitoring

## 👨‍💻 Project

**CreditWise Loan Approval System**  
**Repository:** `utkarsh6419/CreditWise-Loan-System`  
**Primary notebook:** `credit_wise.ipynb`

---

*Built as an ML-assisted loan pre-screening prototype with human verification retained for final decisions.*
