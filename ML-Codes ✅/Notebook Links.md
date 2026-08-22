# ML Codes / Notebook Links

> **Status Legend:**  
> 🟢 **WORKING NOW** — Confirmed working  
> 🟠 **NEEDS UPDATES** — Changes/editing are still required  
> 🔴 **NOT YET CHECKED** — Not yet verified/confirmed  

---

# 1. Malaria Flow

**Malaria Predictor / Prediction:**  
![WORKING NOW](https://img.shields.io/badge/STATUS-WORKING%20NOW-brightgreen)

### 🌐 Live Malaria Prediction

[Open Live Malaria Predictor](https://healthcheck-udoy.onrender.com/malaria)


### Current Status

The Malaria prediction flow is currently working on the live website.

The application accepts a **cell image upload** for prediction.

**Website Input:**

- Cell image
- JPG format

---

## 🏆 Main Malaria Notebook

**Notebook:** `Malaria_Detecion_Code.ipynb`

**Role:** 🥇 **MAIN NOTEBOOK**

This is the **primary Malaria notebook** to study, understand, and use as the main project/interview reference.

### Why This Is the Main Notebook

This notebook contains the more complete end-to-end Malaria CNN workflow, including:

- Dataset setup
- Kaggle dataset download
- Dataset verification
- Dataset extraction
- Image loading
- Image preprocessing
- Image resizing
- Label creation
- Training/testing split
- CNN model development
- Model training
- Training accuracy/loss analysis
- Final model evaluation
- Classification report
- Confusion matrix
- Sample predictions
- Model saving
- Additional test-image prediction
- Batch prediction and evaluation

### Main Notebook Topics

- [ ] Dataset understanding
- [ ] Parasitized vs Uninfected classes
- [ ] Image loading
- [ ] Image preprocessing
- [ ] Image resizing to 50 × 50
- [ ] RGB image handling
- [ ] Label creation
- [ ] Train-test split
- [ ] One-hot encoding
- [ ] CNN architecture
- [ ] Convolution layers
- [ ] MaxPooling
- [ ] Batch Normalization
- [ ] Dropout
- [ ] Flatten layer
- [ ] Dense layers
- [ ] Softmax output
- [ ] Model compilation
- [ ] Model training
- [ ] Training accuracy
- [ ] Validation accuracy
- [ ] Training loss
- [ ] Validation loss
- [ ] Final test evaluation
- [ ] Classification report
- [ ] Precision
- [ ] Recall
- [ ] F1-score
- [ ] Confusion Matrix
- [ ] Sample predictions
- [ ] Model saving
- [ ] Model loading
- [ ] Batch prediction
- [ ] Deployment connection

### 🎯 Main Notebook Priority

**⭐⭐⭐⭐⭐ — HIGHEST PRIORITY**

---

## 🥈 Reference Malaria Notebook

**Notebook:** `malariadetection (1).ipynb`

**Role:** 🥈 **REFERENCE NOTEBOOK**

This is the earlier/simpler Malaria notebook.

It should be kept as a reference for understanding the original CNN implementation and basic training workflow.

### Reference Notebook Topics

- [ ] Basic dataset loading
- [ ] Parasitized images
- [ ] Uninfected images
- [ ] Image resizing
- [ ] Train-test split
- [ ] One-hot encoding
- [ ] CNN architecture
- [ ] Model compilation
- [ ] Model training
- [ ] Model evaluation
- [ ] Accuracy
- [ ] Training/validation curves
- [ ] Confusion Matrix
- [ ] Basic prediction
- [ ] Saving `malaria-model.h5`

### 🎯 Reference Notebook Priority

**⭐⭐⭐ — MEDIUM PRIORITY**

### Purpose of Reference Notebook

Use this notebook mainly to:

> Understand the original/simple CNN implementation.

> Compare it with the more complete Malaria notebook.

> Review the basic model-building flow if needed.

---

## 🦠 Malaria Classification

The model performs **cell image classification** between two classes:

```text
0 → Parasitized / Infected
1 → Uninfected

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

---

# 3. Fetal Health Flow

---

# 4. Stroke Prediction Flow

---

# 5. Continue
