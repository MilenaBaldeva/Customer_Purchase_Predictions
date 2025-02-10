# 🛒 Customer Purchase Prediction

## 📌 Project Overview
This project analyzes online shopper behavior to predict purchase likelihood using machine learning. The dataset `online_shoppers_intention.csv` contains user interaction data, including page visits, engagement duration, and traffic source. 

We apply data preprocessing, exploratory data analysis (EDA), feature engineering, and model evaluation to derive actionable business insights.

---

## 📂 Table of Contents
- [Data Preprocessing](#data-preprocessing)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Feature Engineering](#feature-engineering)
- [Model Development](#model-development)
- [Model Comparison & Performance](#model-comparison--performance)
- [Key Business Insights](#key-business-insights)
- [Recommendations](#recommendations)
- [Conclusion](#conclusion)
- [Setup & Installation](#setup--installation)

---

## 🔍 Data Preprocessing
### 1. Data Loading & Exploration
- Loaded `online_shoppers_intention.csv` (12,330 rows, 18 columns).
- Mixed data types: numerical, categorical, boolean.
- Basic exploration: `.head()`, `.info()`, `.describe()`.

### 2. Handling Missing Values
- Checked using `.isnull().sum()`
- **No missing values found**.

### 3. Encoding Categorical Variables
- One-hot encoding applied to:
  - `Month`
  - `OperatingSystems`
  - `Browser`
  - `Region`
  - `TrafficType`
  - `VisitorType`
  - `Weekend`

### 4. Feature Engineering
- **New Features Created**:
  - `TimeSpentOnSite` = Sum of all time-related features.
  - `VisitorType_New` = Simplified visitor classification.
- **Normalization**:
  - Scaled `Administrative`, `ProductRelated`, `BounceRates` using **MinMaxScaler**.

---

## Exploratory Data Analysis (EDA)
### 1. Distribution Insights
- **Numerical Features**:
  - Right-skewed: `Administrative Page Visits`
  - **Low bounce rates**: Majority of users have low bounce & exit rates.
- **Categorical Features**:
  - Most traffic: **May & November** (seasonal trend).
  - Most users on **OS 2** and **Browser 2**.
  - **49.8%** Returning vs **49.8%** New visitors.
  - **76.7% visits** on weekdays vs **23.3% on weekends**.

### 2. Correlation Analysis
- **Strong Positive Correlations**:
  - `ProductRelated` & `ProductRelated_Duration` (+0.86)
  - `Administrative` & `Administrative_Duration` (+0.60)
- **Negative Correlations**:
  - `Administrative` & `ExitRates` (-0.32)
  - `ExitRates` & `ProductRelated` (-0.26)

### 3. Purchase Rates: Weekend vs. Non-Weekend
- **Weekend purchase rate:** 17.5%
- **Weekday purchase rate:** 15%
- ➡️ **Insight**: Weekend visitors have a slightly higher conversion rate.

---

## ⚙️ Feature Engineering
- **New Features**:
  - `TimeSpentOnSite`: Total engagement time.
  - `VisitorType_New`: Simplified visitor segmentation.
- **Target Variable**:
  - Created **Revenue** as a binary target (`1 = Purchase`, `0 = No Purchase`).

---

## 🤖 Model Development
- **Train-Test Split**: 80% train / 20% test (Stratified sampling).
- **Class Distribution**:
  - Training: **Non-Buyers (84.53%)**, Buyers (15.47%).
  - Testing: **Non-Buyers (84.51%)**, Buyers (15.49%).

### 🔥 Models Evaluated
1. **Logistic Regression**
2. **Random Forest**
3. **XGBoost (Gradient Boosting)**

---

## 📊 Model Comparison & Performance

| Model                 | Accuracy | Precision | Recall  | F1-Score | ROC-AUC |
|----------------------|----------|------------|---------|----------|---------|
| Logistic Regression | **0.8812** | 0.7380 | 0.3613 | 0.4851 | 0.8810 |
| Random Forest       | **0.8978** | 0.7407 | 0.5236 | 0.6135 | 0.9168 |
| **XGBoost** (Best)  | **0.8950** | 0.6804 | **0.6073** | **0.6418** | **0.9213** |

### 🏆 Best Model: **XGBoost**
✅ **Highest Recall (0.6073)** → Identifies most buyers  
✅ **Best F1-Score (0.6418)** → Balance between precision & recall  
✅ **Best ROC-AUC (0.9213)** → Strong classification ability  

---

## 🔑 Key Business Insights (SHAP Analysis)
- **Top Predictors of Purchase**:
  - `PageValues`: **Strongest predictor**.
  - `TimeSpentOnSite`: **Higher engagement = Higher conversion**.
  - `ProductRelated_Duration`: **More time on product pages → More purchases**.
  - `ExitRates`: **Lower exit rates → Higher purchase probability**.
  - `VisitorType_Returning_Visitor`: **Returning visitors convert more often**.
  - `Weekend`: **Weekends positively impact purchases**.

---

## 📢 Recommendations
### 🔹 Improve Customer Retention & Sales
1. **Enhance Page Value** → Implement personalized recommendations.
2. **Target Seasonal Trends** → Boost marketing efforts in **May, March, December**.
3. **Reduce Exit & Bounce Rates** → Improve website usability, content relevance.
4. **Engage Visitors** → Optimize product pages for clarity and engagement.
5. **Retain Returning Customers** → Implement loyalty programs & personalized offers.
6. **Weekend Promotions** → Offer discounts & flash sales on weekends.

### 🎯 Marketing & Sales Teams
- **Target High-Value Users**: Use the **XGBoost model** to identify engaged users.
- **Personalized Marketing**: Use **SHAP insights** to tailor promotions.
- **Optimize Website**: Monitor & improve **bounce and exit rates** via **A/B testing**.

---

## 🏁 Conclusion
✅ **XGBoost is the best-performing model for predicting purchases**.  
✅ **PageValues, TimeSpentOnSite, and ProductRelated_Duration are the strongest predictors**.  
✅ **Optimizing engagement, reducing bounce rates, and seasonal marketing can drive higher revenue**.  

---

## 📌 Author
Milena Baldeva
📧 milena.baldeva@gmail.com





