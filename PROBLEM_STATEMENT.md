# CreditWise Loan System - Problem Statement

## Overview

A mid-sized financial company, SecureTrust Bank, provides personal and home loans across urban and rural regions of India. The current manual verification process requires loan officers to evaluate income proofs, employment details, credit history, and other application information.

The supplied problem statement identifies the process as time-consuming, biased, and inconsistent. Incorrect decisions can cause good customers to be rejected or high-risk customers to be approved.

## Proposed Need

CreditWise introduces an intelligent Machine Learning-powered pre-screening system that analyses applicant details and predicts whether a loan should be **Approved** or **Rejected** before final human verification.

## Dataset

Each row represents a loan applicant and contains personal, financial, employment, credit, and loan information. The target variable is `Loan_Approved`, where `1 = Approved` and `0 = Rejected`.

## Key Fields

- Applicant income and co-applicant income
- Employment status
- Age and marital status
- Dependents
- Credit score
- Existing loans
- DTI ratio
- Savings and collateral value
- Loan amount and loan term
- Loan purpose
- Property area
- Education level
- Gender
- Employer category
- Loan approval target

## Expected Outcome

The system should learn hidden patterns from historical customer records and provide accurate, fast, and consistent loan approval pre-screening before final human verification.
