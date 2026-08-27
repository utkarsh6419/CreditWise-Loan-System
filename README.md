# 💳 CreditWise Loan Approval System

### Machine Learning-based Loan Approval Prediction & Pre-Screening

[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/) [![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?logo=scikit-learn)](https://scikit-learn.org/) [![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://jupyter.org/)

CreditWise is a machine learning project that predicts whether a loan application is likely to be **Approved or Rejected** using historical applicant, financial, employment, credit, and loan information.

The project addresses the manual screening problem described in the provided problem statement by creating a fast, consistent **first-level pre-screening aid** before final human verification. The system is intended to support loan officers, not replace responsible human decision-making.

---

## 🎯 Problem Statement

SecureTrust Bank serves customers across urban and rural regions of India. Its existing manual verification process requires loan officers to evaluate income, employment details, credit history, and other application information.

This process can be **time-consuming, biased, and inconsistent**, creating two major risks:

- Good customers may be rejected, resulting in lost business.
- High-risk customers may be approved, resulting in financial losses.

CreditWise uses historical loan application data to learn patterns and provide an initial **Approved / Rejected** prediction before final human verification.

📄 Full source problem statement: [`PROBLEM_STATEMENT.md`](./PROBLEM_STATEMENT.md)

---

## 🚀 Project Objectives

- Analyze historical loan applications.
- Handle missing and inconsistent data.
- Encode categorical variables for machine learning.
- Split the data into training and testing sets.
- Scale features where appropriate.
- Train multiple classification models.
- Compare models using multiple evaluation metrics.
- Provide a foundation for a future interactive loan pre-screening application.

---

## 📊 Dataset

The provided dataset contains **1,000 loan application records and 20 original columns**.

### Major Features

| Feature | Description |
|---|---|
| `Applicant_ID` | Unique applicant identifier |
| `Applicant_Income` | Monthly applicant income |
| `Coapplicant_Income` | Monthly co-applicant income |
| `Employment_Status` | Salaried / Self-Employed / Business |
| `Age` | Applicant age |
| `Marital_Status` | Married / Single |
| `Dependents` | Number of dependents |
| `Credit_Score` | Credit bureau score |
| `Existing_Loans` | Number of existing loans |
| `DTI_Ratio` | Debt-to-income ratio |
| `Savings` | Savings balance |
| `Collateral_Value` | Value of collateral provided |
| `Loan_Amount` | Requested loan amount |
| `Loan_Term` | Loan duration in months |
| `Loan_Purpose` | Home / Education / Personal / Business |
| `Property_Area` | Urban / Semi-Urban / Rural |
| `Education_Level` | Graduate / Postgraduate / Undergraduate |
| `Gender` | Applicant gender |
| `Employer_Category` | Govt / Private / Self |
| `Loan_Approved` | Target: `1 = Approved`, `0 = Rejected` |

---

## 🧠 Machine Learning Workflow

```text
                  ┌────────────────────────┐
                  │ Historical Loan Data   │
                  └────────────┬───────────┘
                               ↓
                  ┌────────────────────────┐
                  │ Data Inspection & EDA  │
                  └────────────┬───────────┘
                               ↓
                  ┌────────────────────────┐
                  │ Missing Value Handling │
                  └────────────┬───────────┘
                               ↓
                  ┌────────────────────────┐
                  │ Feature Preprocessing  │
                  │ Encoding + Scaling     │
                  └────────────┬───────────┘
                               ↓
                  ┌────────────────────────┐
                  │ Train / Test Split     │
                  │       80% / 20%        │
                  └────────────┬───────────┘
                               ↓
            ┌──────────────────┼──────────────────┐
            ↓                  ↓                  ↓
      ┌────────────┐     ┌────────────┐     ┌────────────┐
      │ Logistic   │     │    KNN     │     │  Gaussian  │
      │ Regression │     │            │     │ Naive Bayes│
      └──────┬─────┘     └──────┬─────┘     └──────┬─────┘
             └───────────────────┼──────────────────┘
                                 ↓
                     ┌──────────────────────┐
                     │ Model Evaluation     │
                     │ Accuracy / Precision │
                     │ Recall / F1 / Matrix │
                     └──────────┬───────────┘
                                ↓
                     ┌──────────────────────┐
                     │ Approved / Rejected  │
                     └──────────────────────┘
```

---

## 🔧 Current Implementation

The primary implementation is contained in [`credit_wise.ipynb`](./credit_wise.ipynb).

The notebook currently includes:

- Dataset loading and inspection
- Missing-value handling
- Categorical encoding
- Train/test splitting
- Feature scaling using `StandardScaler`
- Exploratory data analysis and visualizations
- Classification model training
- Model comparison
- Confusion matrices

### Models Tested

**1. Logistic Regression**  
A linear classification baseline suitable for interpreting relationships between features and the binary approval target.

**2. K-Nearest Neighbors (KNN)**  
A distance-based classifier using `n_neighbors=5` in the current notebook.

**3. Gaussian Naive Bayes**  
A probabilistic classification approach based on Bayes' theorem with Gaussian assumptions for continuous inputs.

---

## 📈 Current Model Results

Results reported by the executed notebook:

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---:|---:|---:|---:|
| Logistic Regression | **86.5%** | 78.33% | **77.05%** | **77.69%** |
| KNN | 76.0% | 62.75% | 52.46% | 57.14% |
| Naive Bayes | **86.5%** | **80.36%** | 73.77% | 76.92% |

The current notebook selects **Naive Bayes based on Precision**.

> **Important:** These are experimental results from the current notebook and should not be interpreted as production-level credit-decision performance.

---

## 🧪 Evaluation Metrics

CreditWise evaluates models using:

- **Accuracy**: overall percentage of correct predictions.
- **Precision**: how many predicted approvals are actually approvals.
- **Recall**: how many actual approvals are correctly identified.
- **F1 Score**: balance between precision and recall.
- **Confusion Matrix**: shows true/false positives and negatives.

For a real lending system, model selection should consider the different costs of false approvals and false rejections rather than relying on a single metric.

---

## 📁 Repository Structure

```text
CreditWise-Loan-System/
│
├── README.md
├── PROBLEM_STATEMENT.md
├── credit_wise.ipynb
├── loan_approval_data.csv
├── requirements.txt
├── .gitignore
│
├── src/
│   └── README.md
│
├── app/
│   └── README.md
│
└── models/
    └── README.md
```

The `src`, `app`, and `models` directories currently document the planned project structure. The notebook remains the primary implementation for this first version.

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| **Python** | Core programming language |
| **Pandas** | Data loading and manipulation |
| **NumPy** | Numerical operations |
| **Matplotlib** | Visualization |
| **Seaborn** | Statistical visualization |
| **Scikit-learn** | Preprocessing, ML models and evaluation |
| **Jupyter Notebook** | Development and experimentation |

---

## ▶️ Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/utkarsh6419/CreditWise-Loan-System.git
cd CreditWise-Loan-System
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Launch Jupyter

```bash
jupyter notebook
```

Open:

```text
credit_wise.ipynb
```

Make sure `loan_approval_data.csv` remains in the repository root so the notebook can load the dataset.

---

## 🔐 Responsible AI & Limitations

Loan approval is a high-impact financial decision. CreditWise is currently an **educational ML prototype and pre-screening concept**, not a production credit-decision engine.

A production-ready system would require additional work including:

- Fairness and bias evaluation
- Stronger validation and cross-validation
- Model explainability
- Probability calibration
- Threshold and cost analysis
- Data privacy and security
- Model drift monitoring
- Auditability
- Human oversight
- Appropriate regulatory compliance

The purpose of the current project is to demonstrate the machine-learning workflow and provide a foundation for further development.

---

## 🔮 Future Roadmap

- [ ] Improve preprocessing with reusable pipelines
- [ ] Add cross-validation
- [ ] Perform hyperparameter tuning
- [ ] Compare additional ML algorithms
- [ ] Add feature importance / explainability
- [ ] Add approval probability or risk score
- [ ] Build an interactive Streamlit application
- [ ] Save and version trained models
- [ ] Add prediction API
- [ ] Add automated tests
- [ ] Add GitHub Actions CI/CD
- [ ] Add model monitoring

---

## 👨‍💻 Project Information

**Project:** CreditWise Loan Approval System  
**Repository:** `utkarsh6419/CreditWise-Loan-System`  
**Primary implementation:** `credit_wise.ipynb`  
**Dataset:** `loan_approval_data.csv`

---

### ⭐ About This Version

This is the **first version of CreditWise**, focused on learning, experimentation, model comparison, and establishing a clean GitHub project foundation. Future versions can evolve the notebook into a complete deployable ML application.
