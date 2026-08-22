# ML Codes / Notebook Links

> **Status Legend:**  
> 🟢 **WORKING NOW** — Confirmed working  
> 🟠 **NEEDS UPDATES** — Changes/editing are still required  
> 🔴 **NOT YET CHECKED** — Not yet verified/confirmed  

---

## 1. Malaria Flow

**Malaria Predictor / Prediction:**  
![WORKING NOW](https://img.shields.io/badge/STATUS-WORKING%20NOW-brightgreen)

<strong>Malaria Code / Colab Notebook:</strong><br>

<a href="https://colab.research.google.com/drive/1EdgGBI-s_cyNwJiftYerqVPzLbzI1Dup?usp=sharing" target="_blank" rel="noopener noreferrer">
  <img src="https://img.shields.io/badge/STATUS-NEEDS%20UPDATES-orange" alt="NEEDS UPDATES">
</a>

**Note:** Some changes/edits are still required in the Colab notebook.

**Google Colab Notebook:**  
[Open Malaria Colab Notebook](https://colab.research.google.com/drive/1EdgGBI-s_cyNwJiftYerqVPzLbzI1Dup?usp=sharing)

---

## 2. Diabetes Flow

**Diabetes Prediction Result:**  
![WORKING NOW](https://img.shields.io/badge/STATUS-WORKING%20NOW-brightgreen)

**Live Diabetes Prediction:**  
[Open Diabetes Prediction](https://healthcheck-udoy.onrender.com/diabetes)

### 🏆 Main Diabetes Notebook

**`Diabetes_prediction_with proper_analysis.ipynb`**

This is the **MAIN notebook** for the current Diabetes Prediction project.

**Focus Areas:**
- Dataset understanding
- Data cleaning and preprocessing
- Exploratory Data Analysis (EDA)
- 8 diabetes input features
- Feature and target selection
- Train-test split
- Classification
- Model evaluation
- Accuracy, Precision, Recall and F1-score
- Confusion Matrix
- Cross-validation
- Hyperparameter tuning
- GridSearchCV
- Final model selection
- Saving the trained model
- Connecting the model with Flask

### 🥈 Reference Diabetes Notebook

**`DiabetesNotebook.ipynb`**

This is the **REFERENCE notebook**.

Use it mainly for:
- Decision Tree
- Random Forest
- Naive Bayes
- Comparing different classifiers
- Understanding model performance
- Model selection concepts
- Feature importance
- Alternative approaches

> **Study Priority:**  
> 🥇 `Diabetes_prediction_with proper_analysis.ipynb` → **MASTER / MAIN NOTEBOOK**  
> 🥈 `DiabetesNotebook.ipynb` → **REFERENCE / MODEL COMPARISON**

### 🌐 Diabetes Deployment Flow

```text
Diabetes Dataset
        ↓
Data Analysis & Preprocessing
        ↓
Model Training
        ↓
Model Evaluation
        ↓
Model Selection & Tuning
        ↓
Save Trained Model
        ↓
diabetes-model.pkl
        ↓
Flask / run.py
        ↓
User enters 8 inputs
        ↓
classifier.predict(data)
        ↓
Diabetes Prediction Result
        ↓
Live Website
