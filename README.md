# 🫀 Heart Disease Prediction & Analysis — End-to-End Data Science Project

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![SQL](https://img.shields.io/badge/MySQL-8.0-orange?logo=mysql)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-red?logo=scikitlearn)
![License](https://img.shields.io/badge/License-MIT-green)

> A complete end-to-end data science pipeline for predicting heart disease using **Python**, **SQL**, **Machine Learning**, and **Power BI** — covering data exploration, preprocessing, model building, and interactive dashboarding.

---

## 📌 Project Overview

Heart disease is one of the leading causes of mortality worldwide. This project builds a full analytics and prediction pipeline on a real-world clinical dataset of **918 patients**, aiming to:

- Understand patterns and risk factors through **Exploratory Data Analysis (EDA)**
- Clean and preprocess the data for modeling
- Predict heart disease using a **K-Nearest Neighbors (KNN) classifier**
- Run analytical queries using **SQL**
- Visualize key insights through an interactive **Power BI dashboard**

---

## 🗂️ Project Structure

```
heart-disease-project/
│
├── heart.csv                    # Raw dataset (918 records, 12 features)
├── HeartdiseaseFinal.ipynb      # Main Jupyter Notebook (EDA + ML pipeline)
├── heart_sql1.sql               # SQL queries for data analysis
├── heart_dashboard.pbix         # Power BI dashboard file
└── README.md                    # Project documentation
```

---

## 📊 Dataset Description

**Source:** [Kaggle — Heart Failure Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction)

| Feature | Description |
|---|---|
| `Age` | Patient's age in years |
| `Sex` | Gender (M / F) |
| `ChestPainType` | Type of chest pain (ATA, NAP, ASY, TA) |
| `RestingBP` | Resting blood pressure (mm Hg) |
| `Cholesterol` | Serum cholesterol (mg/dL) |
| `FastingBS` | Fasting blood sugar > 120 mg/dL (1 = True) |
| `RestingECG` | Resting ECG result (Normal, ST, LVH) |
| `MaxHR` | Maximum heart rate achieved |
| `ExerciseAngina` | Exercise-induced angina (Y / N) |
| `Oldpeak` | ST depression induced by exercise |
| `ST_Slope` | Slope of peak exercise ST segment (Up, Flat, Down) |
| `HeartDisease` | Target variable — 1 = Disease, 0 = No Disease |

- **Total Records:** 918  
- **Target Distribution:** ~55% with heart disease, ~45% without

---

## ⚙️ Tech Stack

| Layer | Tools Used |
|---|---|
| **Language** | Python 3.10+ |
| **Data Manipulation** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **Machine Learning** | Scikit-learn |
| **Database & Queries** | MySQL / SQL |
| **BI Dashboard** | Power BI |
| **Notebook** | Jupyter Notebook |

---

## 🔍 Project Pipeline

### 1. 📥 Data Loading & EDA
- Loaded `heart.csv` using Pandas
- Checked shape, data types, null values, and duplicates
- Analyzed distribution of Age, Cholesterol, RestingBP, MaxHR using histograms
- Visualized heart disease distribution across Sex, ChestPainType, FastingBS
- Generated a **correlation heatmap** to identify feature relationships
- Used box plots and violin plots for outlier detection and spread analysis

### 2. 🧹 Data Preprocessing & Cleaning
- Detected biologically invalid **zero values** in `Cholesterol` and `RestingBP`
- **Imputed zeros** with the mean of non-zero values (domain-aware approach)
- Applied **One-Hot Encoding** (`pd.get_dummies`) on categorical columns: `Sex`, `ChestPainType`, `RestingECG`, `ExerciseAngina`, `ST_Slope`
- Converted all encoded columns to integer type for model compatibility
- **Train-Test Split:** 80% train / 20% test (stratified to preserve class ratio)
- Applied **StandardScaler** for feature normalization

### 3. 🤖 Machine Learning Model — KNN Classifier
- Model: `KNeighborsClassifier(n_neighbors=5)` from Scikit-learn
- Trained on scaled features using `StandardScaler`

**Model Performance:**

| Metric | Score |
|---|---|
| **Accuracy** | **88.58%** |
| Precision (Class 0) | 0.89 |
| Precision (Class 1) | 0.89 |
| Recall (Class 0) | 0.85 |
| Recall (Class 1) | 0.91 |
| F1-Score (Macro Avg) | 0.88 |

**Confusion Matrix:**
```
[[70  12]
 [ 9  93]]
```

### 4. 🗃️ SQL Analysis
Executed structured queries in MySQL on the same dataset for analytical insights:

- Total patient count and disease vs. no-disease split
- Heart disease rate **by gender** and **by chest pain type**
- Age group bucketing: Under 40 / 40–50 / 51–60 / Above 60
- Average Cholesterol, BP, MaxHR, and Oldpeak **by disease status**
- High-risk patient identification (BP > 140, Cholesterol > 240)
- ECG type distribution and ST_Slope correlation with disease
- Exercise angina vs. heart disease rate analysis

### 5. 📈 Power BI Dashboard
Interactive dashboard featuring:
- **KPI Cards:** Total patients, disease count, disease rate %
- **Bar Charts:** Disease by gender, chest pain type, ECG type
- **Age Group Analysis:** Disease distribution across age buckets
- **Slicers:** Filter by Sex, ChestPainType, ST_Slope for drill-down

---

## 🚀 How to Run This Project

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### Steps
```bash
# 1. Clone the repository
git clone https://github.com/your-username/heart-disease-prediction.git
cd heart-disease-prediction

# 2. Launch the Jupyter Notebook
jupyter notebook HeartdiseaseFinal.ipynb

# 3. For SQL — import heart.csv into MySQL and run
mysql -u root -p heart_db < heart_sql1.sql

# 4. For Power BI — open heart_dashboard.pbix in Power BI Desktop
```

---

## 📌 Key Findings

- **Males** had a significantly higher heart disease rate (~63%) compared to females (~26%)
- **ASY (Asymptomatic) chest pain** was the strongest predictor — over 79% of ASY patients had heart disease
- Patients with **exercise-induced angina** showed ~85% heart disease rate
- **Flat ST_Slope** was strongly associated with heart disease compared to Up slope
- Heart disease patients had notably **lower MaxHR** and **higher Oldpeak** values on average
- The **51–60 age group** had the highest disease count across all age buckets

---

## 📄 License

This project is licensed under the **MIT License** — feel free to use and build upon it.

---

## 🙋‍♂️ Author

**[Your Name]**  
Data Analyst | Aspiring Data Scientist  
📧 your.email@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/yourprofile) | [GitHub](https://github.com/your-username)

---

> ⭐ If you found this project helpful, consider giving it a star on GitHub!
