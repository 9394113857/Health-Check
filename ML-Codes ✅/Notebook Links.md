# ML Codes / Notebook Links

> **Status Legend:**  
> 🟢 **WORKING NOW** — Confirmed working  
> 🟠 **NEEDS UPDATES** — Changes/editing are still required  
> 🔴 **NOT YET CHECKED** — Not yet verified/confirmed  

---

# 1. Malaria Flow

**Malaria Predictor / Prediction:**  
![WORKING NOW](https://img.shields.io/badge/STATUS-WORKING%20NOW-brightgreen)

<strong>Malaria Code / Colab Notebook:</strong><br>

<a href="https://colab.research.google.com/drive/1EdgGBI-s_cyNwJiftYerqVPzLbzI1Dup?usp=sharing" target="_blank" rel="noopener noreferrer">
  <img src="https://img.shields.io/badge/STATUS-NEEDS%20UPDATES-orange" alt="NEEDS UPDATES">
</a>

**Note:** Some changes/edits are still required in the Colab notebook.

**Google Colab Notebook:**  
[Open Malaria Colab Notebook](https://colab.research.google.com/drive/1EdgGBI-s_cyNwJiftYerqVPzLbzI1Dup?usp=sharing)

### Current Focus

- [ ] Review the existing Malaria notebook
- [ ] Complete required changes/edits
- [ ] Check preprocessing
- [ ] Check model loading
- [ ] Check prediction flow
- [ ] Verify the final prediction result
- [ ] Confirm the complete deployment flow

### Interview Focus

- Overall Malaria prediction workflow
- Dataset and preprocessing
- Model used
- Model input and prediction
- Connection between model and application

**Interview Priority:** ⭐⭐⭐

---

# 2. Diabetes Flow

**Diabetes Prediction Result:**  
![WORKING NOW](https://img.shields.io/badge/STATUS-WORKING%20NOW-brightgreen)

### 🌐 Live Diabetes Prediction

[Open Diabetes Prediction](https://healthcheck-udoy.onrender.com/diabetes)

### Current Status

The Diabetes prediction flow is currently working on the live website.

---

## 🏆 Main Diabetes Notebook

**Notebook:** `Diabetes_prediction_with proper_analysis.ipynb`

**Role:** 🥇 **MAIN NOTEBOOK**

This is the **primary Diabetes notebook** to study, understand deeply, and use as the main project/interview reference.

### Main Notebook Topics

- [ ] Dataset understanding
- [ ] Understanding the Diabetes dataset
- [ ] Understanding the 8 input features
- [ ] Data cleaning
- [ ] Data preprocessing
- [ ] Exploratory Data Analysis (EDA)
- [ ] Feature selection
- [ ] Target variable
- [ ] Train-test split
- [ ] Classification
- [ ] Gradient Boosting
- [ ] Model training
- [ ] Model evaluation
- [ ] Accuracy
- [ ] Precision
- [ ] Recall
- [ ] F1-score
- [ ] Confusion Matrix
- [ ] Cross-validation
- [ ] Hyperparameter tuning
- [ ] GridSearchCV
- [ ] Final model selection
- [ ] Saving the trained model
- [ ] Model deployment
- [ ] Connecting the trained model with Flask

### Main Notebook Priority

**⭐⭐⭐⭐⭐ — HIGHEST PRIORITY**

---

## 🥈 Reference Diabetes Notebook

**Notebook:** `DiabetesNotebook.ipynb`

**Role:** 🥈 **REFERENCE NOTEBOOK**

This notebook is mainly used as a reference for different classification algorithms and model comparison.

### Reference Notebook Topics

- [ ] Decision Tree
- [ ] Random Forest
- [ ] Naive Bayes
- [ ] Training different classifiers
- [ ] Comparing multiple models
- [ ] Model performance comparison
- [ ] Classification algorithms
- [ ] Feature importance
- [ ] Alternative approaches
- [ ] Model selection

### Reference Notebook Priority

**⭐⭐⭐ — MEDIUM PRIORITY**

### Main Interview Questions to Understand

> What other models were tried?

> Why were multiple models compared?

> How were the models evaluated?

> What is a Decision Tree?

> What is Random Forest?

> What is Naive Bayes?

> Why can one model perform better than another?

---

## 🌐 Diabetes Website Inputs

The live Diabetes prediction page accepts these **8 inputs**:

1. Pregnancies
2. Glucose
3. Blood Pressure
4. Skin Thickness
5. Insulin Level
6. Body Mass Index (BMI)
7. Diabetes Pedigree Function
8. Age

---

## 🔗 Diabetes Deployment Flow

```text
Diabetes Dataset
        ↓
Data Cleaning
        ↓
Data Preprocessing
        ↓
Exploratory Data Analysis
        ↓
Feature / Target Selection
        ↓
Train-Test Split
        ↓
Model Training
        ↓
Model Evaluation
        ↓
Cross-Validation
        ↓
Hyperparameter Tuning
        ↓
Final Model
        ↓
Save Trained Model
        ↓
diabetes-model.pkl
        ↓
Flask / run.py
        ↓
User Enters 8 Inputs
        ↓
classifier.predict(data)
        ↓
Diabetes Prediction
        ↓
Live Website Result
