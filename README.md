# Diabetes Risk Assessment Engine

An end-to-end Machine Learning system that assesses diabetes risk by classifying individuals as **Healthy**, **Pre-diabetic**, or **Diabetic** using the CDC's BRFSS health survey dataset. Designed as an intelligent screening tool, the system prioritizes identifying high-risk individuals to support earlier intervention.

---

## Problem Statement

Diabetes often progresses silently until serious complications arise. Early identification of individuals at risk—especially those in the **pre-diabetic stage**—can significantly improve preventive healthcare.

This project aims to build a machine learning system capable of assessing diabetes risk from lifestyle and health-related indicators, enabling timely awareness and supporting informed healthcare decisions.

---

## Solution Overview

The system analyzes **21 health-related attributes** such as BMI, blood pressure, physical activity, smoking habits, and general health to classify individuals into one of three categories:

- Healthy
- Pre-diabetic
- Diabetic

To improve reliability, multiple machine learning models were benchmarked and evaluated before selecting the final model based on medical screening performance.

---

## System Workflow

```text
Patient Health Information
            │
            ▼
Data Cleaning & Preprocessing
            │
            ▼
Class Balancing & Feature Engineering
            │
            ▼
Model Benchmarking
(SVM, Random Forest, Logistic Regression,
Decision Tree, XGBoost)
            │
            ▼
Hyperparameter Optimization
            │
            ▼
Best Model Selection
            │
            ▼
Model Serialization (Joblib)
            │
            ▼
Streamlit Web Application
            │
            ▼
Diabetes Risk Assessment
```

---

## Engineering Challenges

### Handling Class Imbalance

The original dataset contained approximately **84% healthy individuals**, making it difficult for the model to learn minority classes.

To address this, strategic undersampling was performed to create a balanced dataset and improve learning across all three risk categories.

### Managing Noisy Survey Data

Survey datasets naturally contain inconsistencies and extreme values.

Outlier clipping and preprocessing were performed to improve data quality without removing valuable information.

### Detecting the Pre-diabetic Stage

Distinguishing pre-diabetic individuals is considerably more challenging than binary classification.

Five different machine learning algorithms were benchmarked to identify the model with the strongest capability for detecting transitional cases.

---

## Model Benchmarking

| Model | Accuracy | Recall (Diabetic) |
|--------|---------:|------------------:|
| **Support Vector Machine (SVM)** | **54%** | **0.64** |
| XGBoost | 53% | 0.62 |
| Logistic Regression | 54% | 0.59 |
| Random Forest | 52% | 0.56 |
| Decision Tree | 43% | 0.41 |

### Why SVM?

Although multiple models achieved similar accuracy, **Support Vector Machine (SVM)** delivered the highest recall for diabetic patients, making it the preferred choice for medical screening where minimizing missed high-risk cases is more important than maximizing overall accuracy.

---

## Key Insights

- High Blood Pressure emerged as a stronger predictor of diabetes than BMI.
- Medical datasets require evaluation beyond accuracy; recall plays a critical role in identifying high-risk patients.
- Lifestyle-based machine learning models can effectively support early screening but should complement—not replace—clinical diagnosis.

---

## Application Preview

The trained model was deployed using **Streamlit**, allowing users to enter health information and receive an instant diabetes risk assessment.

![Diabetes Risk Predictor Interface](D-Risk_Analyser_Result.png)

---

## Tech Stack

**Programming Language**

- Python

**Machine Learning**

- Scikit-learn
- XGBoost

**Data Processing**

- Pandas
- NumPy

**Model Serialization**

- Joblib

**Deployment**

- Streamlit

---

## Project Structure

```text
Diabetes_Risk_Assessment_Engine/
│
├── app.py
├── model.joblib
├── notebook.ipynb
├── requirements.txt
├── D-Risk_Analyser_Result.png
└── README.md
```

---

## Getting Started

### Clone Repository

```bash
git clone <repository-url>
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Launch the Application

```bash
streamlit run app.py
```

---

## Future Improvements

- Deploy the application on a cloud platform.
- Support real-time patient monitoring.
- Improve performance using larger and more diverse clinical datasets.
- Extend the system into a multimodal healthcare screening platform.

---
