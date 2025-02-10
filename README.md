# 🛒 Customer Purchase Prediction  

## 📌 Project Overview  
Understanding online shopper behavior is crucial for businesses looking to improve conversions. This project explores **user interactions**—such as page visits, time spent on site, and traffic sources—to predict whether a visitor will make a purchase.  

Using **data preprocessing, exploratory data analysis (EDA), feature engineering, and machine learning models**, I uncover key patterns that influence buying decisions. The goal is to provide actionable insights that can help businesses **optimize user experience, reduce bounce rates, and boost sales.**  

---

## 📂 Table of Contents  
- [🛠 Data Preprocessing](#-data-preprocessing)  
- [📊 Exploratory Data Analysis (EDA)](#-exploratory-data-analysis-eda)  
- [🔧 Feature Engineering](#-feature-engineering)  
- [🤖 Model Development](#-model-development)  
- [📈 Model Comparison & Performance](#-model-comparison--performance)  
- [🔍 Key Business Insights](#-key-business-insights)  
- [🎯 Recommendations](#-recommendations)  
- [✅ Conclusion](#-conclusion)  
- [👤 Author](#-author)  

---

## 🛠 Data Preprocessing  

### 1️⃣ Data Loading & Exploration  
- **Loaded dataset:** `online_shoppers_intention.csv` (12,330 rows, 18 columns)  
- **Data types:** Numerical, categorical, and boolean  
- **Basic exploration:** `.head()`, `.info()`, `.describe()`  

### 2️⃣ Handling Missing Values  
- Checked using `.isnull().sum()`  
- **No missing values found**  

### 3️⃣ Encoding Categorical Variables  
One-hot encoding applied to:  
- `Month`  
- `OperatingSystems`  
- `Browser`  
- `Region`  
- `TrafficType`  
- `VisitorType`  
- `Weekend`  

### 4️⃣ Feature Engineering  
New Features Created:  
- **`TimeSpentOnSite`** = Sum of all time-related features  
- **`VisitorType_New`** = Simplified visitor classification  

Normalization:  
- Scaled `Administrative`, `ProductRelated`, `BounceRates` using **MinMaxScaler**  

---

## 📊 Exploratory Data Analysis (EDA)  

### 1️⃣ Distribution Insights  
**Numerical Features:**  
- **Right-skewed:** Administrative Page Visits  
- **Low bounce rates:** Majority of users have low bounce & exit rates  

**Categorical Features:**  
- **Most traffic:** May & November (seasonal trend)  
- **Most users:** OS 2 and Browser 2  
- **Visitor Types:** 49.8% Returning vs. 49.8% New visitors  
- **Visit Timing:** 76.7% visits on weekdays vs. 23.3% on weekends  

### 2️⃣ Correlation Analysis   
Below is the **correlation heatmap** of numerical variables, highlighting strong relationships between features:
<img src="https://github.com/MilenaBaldeva/Codes/blob/main/Correlation%20Heatmap%20of%20Numerical%20Variables.png" alt="Correlation Heatmap" width="600">

**Strong Positive Correlations:**  
- `ProductRelated` & `ProductRelated_Duration` **(+0.86)**  
- `Administrative` & `Administrative_Duration` **(+0.60)**  

**Negative Correlations:**  
- `Administrative` & `ExitRates` **(-0.32)**  
- `ExitRates` & `ProductRelated` **(-0.26)**  

### 3️⃣ Purchase Rates: Weekend vs. Non-Weekend  

| Time Period | Purchase Rate |
|------------|--------------|
| **Weekend** | **17.5%** |
| **Weekday** | **15%** |

➡️ **Insight:** Weekend visitors have a slightly higher conversion rate.  

---

## 🔧 Feature Engineering  

New Features:  
- `TimeSpentOnSite`: Total engagement time  
- `VisitorType_New`: Simplified visitor segmentation  

Target Variable:  
- Created **`Revenue`** as a binary target (1 = Purchase, 0 = No Purchase).  

---

## 🤖 Model Development  

- **Train-Test Split:** 80% train / 20% test (Stratified sampling)  
- **Class Distribution:**  

| Dataset | Non-Buyers (%) | Buyers (%) |
|---------|--------------|-----------|
| **Train** | 84.53% | 15.47% |
| **Test** | 84.51% | 15.49% |

**Models Evaluated:**  
- Logistic Regression  
- Random Forest  
- XGBoost (Best Model
