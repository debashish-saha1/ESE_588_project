# ESE 588 Project - Fetal Heart Rate Classification

## 📌 Objective

The goal of this project is to develop machine learning models to classify fetal health status (Healthy vs Compromised) based on time-series derived features from fetal heart rate (FHR) signals. The focus is on:
- Maximizing true positive (TP) detection for compromised cases.
- Minimizing false negatives (FN), which could lead to missed diagnoses.
- Comparing model performance with and without data augmentation.

---

## 📁 Dataset

- **Training Data:** 185 samples (171 healthy, 14 compromised)  
- **Test Data:** 4 separate groups of 100 samples each (unlabeled)  
- **Features:** 21 numerical features extracted from FHR signals  
- **Label:** Binary — `0` (Healthy), `1` (Compromised)

---

## 🧠 Models Trained

We trained and evaluated the following models:
- Logistic Regression
- Random Forest
- Gradient Boosting
- XGBoost

Each model was evaluated using 5 randomized stratified splits (80% train, 20% validation) to report **average performance**.

---

## 🔄 Data Augmentation Techniques Tested

We explored four training set variations:
1. **Original** — No augmentation
2. **SMOTE** — Synthetic Minority Oversampling
3. **ADASYN** — Adaptive Synthetic Sampling
4. **Gaussian Noise Injection** — Minor noise added to positive-class examples

---

## 📊 Evaluation Metrics

Each model was evaluated on:
- **Accuracy**
- **AUC (Area Under ROC Curve)**
- **True Positives (TP)**
- **False Negatives (FN)**

### 📋 Full Results (Average over 5 randomized validation splits)

| Augmentation      | Model              | Accuracy | AUC   | TP  | FN  |
| ----------------- | ------------------ | -------- | ----- | --- | --- |
| **Original**      | LogisticRegression | 98.4%    | 1.000 | 2.6 | 0.4 |
|                   | RandomForest       | 98.9%    | 1.000 | 2.6 | 0.4 |
|                   | GradientBoosting   | 98.9%    | 0.964 | 2.8 | 0.2 |
|                   | XGBoost            | 98.9%    | 0.994 | 2.8 | 0.2 |
| **SMOTE**         | LogisticRegression | 97.8%    | 1.000 | 2.4 | 0.6 |
|                   | RandomForest       | 98.9%    | 1.000 | 2.6 | 0.4 |
|                   | GradientBoosting   | 98.4%    | 0.961 | 2.8 | 0.2 |
|                   | XGBoost            | 98.4%    | 0.990 | 2.8 | 0.2 |
| **ADASYN**        | LogisticRegression | 97.8%    | 1.000 | 2.4 | 0.6 |
|                   | RandomForest       | 98.9%    | 0.999 | 2.6 | 0.4 |
|                   | GradientBoosting   | 98.4%    | 0.953 | 2.6 | 0.4 |
|                   | XGBoost            | 98.4%    | 0.988 | 2.8 | 0.2 |
| **GaussianNoise** | LogisticRegression | 98.4%    | 0.998 | 2.6 | 0.4 |
|                   | RandomForest       | 98.9%    | 1.000 | 2.6 | 0.4 |
|                   | GradientBoosting   | 98.9%    | 0.964 | 2.8 | 0.2 |
|                   | XGBoost            | 98.9%    | 0.990 | 2.8 | 0.2 |

---

## 🏁 Final Model

- **Model Selected:** `XGBoost`
- **Data Used:** Original training data (no augmentation)
- **Why:** Consistently high accuracy and AUC with the lowest false negative rate (0.2)

---

## 📝 Files Included

| File | Description |
|------|-------------|
| `Training_Data_588_Project_Spring2025.xlsx` | Original training data |
| `Test_Data_588_Project_Spring2025.xlsx` | Unlabeled test groups |
| `Myresults_XGBoost.xlsx` | Final predictions |
| `augmentation_analysis.ipynb` | Model training, augmentation, and evaluation |
| `README.md` | This file |

---

## 🚀 How to Reproduce

1. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

2. Run the notebook:
    ```bash
    jupyter notebook augmentation_analysis.ipynb
    ```

3. Check results and output files.

---

## 👤 Author

Ashish — ESE 588, Spring 2025
