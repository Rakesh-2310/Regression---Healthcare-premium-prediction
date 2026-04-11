# 🏥 Healthcare Premium Price Prediction

A production-ready Machine Learning project that predicts health insurance premiums using demographic, lifestyle, and medical data. This project demonstrates a complete end-to-end ML lifecycle, including preprocessing, feature engineering, model optimization, error-driven improvements, and deployment.

---

## 🚀 Project Overview

The goal of this project is to estimate healthcare insurance premiums based on user inputs such as age, income, BMI, smoking status, and medical history.

Key highlight:
👉 Implemented a **segmented modeling strategy** driven by residual error analysis to improve prediction performance across different age groups.

---

## 🎯 Key Features

* 🔍 Accurate premium prediction (~98% R² score)
* 🧠 Segmented ML models (age-based)
* ⚙️ Advanced preprocessing & feature engineering
* 📊 Error-driven model improvement strategy
* 🖥️ Interactive Streamlit web application

---

## 🏗️ Tech Stack

* **Language**: Python
* **ML Libraries**: Scikit-learn, XGBoost
* **Data Processing**: Pandas, NumPy
* **Visualization**: Matplotlib, Seaborn
* **Deployment**: Streamlit
* **Model Storage**: Joblib

---

## 📂 Project Structure

```bash
├── artifacts/
│   ├── model_rest.joblib
│   ├── model_young.joblib
│   ├── scaler_rest.joblib
│   ├── scaler_young.joblib
│
├── model_training/
│   ├── data_segmentation.ipynb
│   ├── HPP_data_preprocessing_1.ipynb
│   ├── HPP_data_preprocessing_rest.ipynb
│   ├── HPP_data_preprocessing_young.ipynb
│   ├── ml_premium_prediction_rest_with_gr.ipynb
│
├── resource/
│   └── premiums.xlsx
│
├── main.py                    # Streamlit UI
├── prediction_helper.py      # Preprocessing + prediction logic
├── requirements.txt
├── runtime.txt
└── README.md
```

---

## ⚙️ ML Pipeline

### 🔹 1. Data Ingestion

* Loaded dataset from Excel (`premiums.xlsx`)
* Performed schema validation and initial inspection

---

### 🔹 2. Data Preprocessing

* Handled missing values based on mechanism (MCAR, MAR, MNAR)
* Fixed inconsistent values:

  * Negative dependents
  * Redundant categorical values
* Removed outliers in **Age** using IQR method

---

### 🔹 3. Exploratory Data Analysis (EDA)

* Univariate and bivariate analysis on:

  * Gender, Region, Income Level, Medical History
* Identified key relationships influencing premium

---

### 🔹 4. Feature Engineering

* Created **Normalized Risk Score** from medical history

---

### 🔹 5. Encoding

* **Target Encoding**:

  * income_level, insurance_plan
* **One-Hot Encoding**:

  * gender, region, marital_status
  * bmi_category, smoking_status, employment_status

---

### 🔹 6. Feature Scaling

* Applied **MinMaxScaler** on numerical features

---

### 🔹 7. Feature Selection

* Correlation analysis
* VIF (Variance Inflation Factor) to remove multicollinearity

---

### 🔹 8. Model Training

* Linear Regression
* Ridge Regression
* XGBoost Regressor

---

### 🔹 9. Hyperparameter Tuning

* RandomizedSearchCV for model optimization

---

### 🔹 10. Model Evaluation

* Metrics:

  * MSE, RMSE, R² (~98%)
* Residual-based error analysis across categories

---

### 🔹 11. Iterative Improvement (Core Insight 🚀)

* Identified performance variation across **age groups**
* Implemented **segmented modeling strategy**:

| Age Group | Model Used        | Reason                                    |
| --------- | ----------------- | ----------------------------------------- |
| ≤ 25      | Linear Regression | Better interpretability, simpler patterns |
| > 25      | XGBoost           | Handles complex relationships             |

> Note: XGBoost performed well across all segments, but Linear Regression was chosen for younger users to maintain explainability.

---

### 🔹 12. Deployment

* Built using **Streamlit**
* Real-time prediction pipeline:

  ```
  User Input → Preprocessing → Scaling → Model → Prediction
  ```
* Loaded models and scalers using Joblib

---

## ▶️ How to Run Locally

```bash
# Clone the repository
git clone

# Install dependencies
pip install -r requirements.txt

# Run Streamlit app
streamlit run main.py
```

---

## 📊 Model Performance

* Achieved **~98% R² score**
* Improved generalization using:

  * Feature engineering
  * Hyperparameter tuning
  * Segmented modeling

---

## ⚠️ Limitations

* Manual preprocessing pipeline (not fully automated)
* Sensitive to unseen categories
* No API layer (UI-based deployment only)

---

## 🔮 Future Improvements

* Implement **sklearn Pipeline** for automation
* Add **SHAP for model explainability**
* Build **FastAPI backend**
* Dockerize for production

