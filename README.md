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
- **Dataset Source:** [UCI Online Shoppers Intention](https://archive.ics.uci.edu/dataset/468/online+shoppers+purchasing+intention+dataset)
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
- XGBoost (Best Model)  

---

## 📈 Model Comparison & Performance  

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|-------|----------|----------|--------|----------|---------|
| Logistic Regression | 0.8812 | 0.7380 | 0.3613 | 0.4851 | 0.8810 |
| Random Forest | 0.8978 | 0.7407 | 0.5236 | 0.6135 | 0.9168 |
| **XGBoost (Best)** | **0.8950** | **0.6804** | **0.6073** | **0.6418** | **0.9213** |

### 🏆 Best Model: XGBoost  
- ✅ **Highest Recall (0.6073)** → Identifies most buyers  
- ✅ **Best F1-Score (0.6418)** → Balance between precision & recall  
- ✅ **Best ROC-AUC (0.9213)** → Strong classification ability  

---

## 🔍 Key Business Insights  

### **SHAP Analysis: Top Predictors of Purchase**  
<img src="https://github.com/MilenaBaldeva/Codes/blob/main/Shap.png" alt="Correlation Heatmap" width="600">

1. **PageValues** → Strongest predictor  
2. **TimeSpentOnSite** → Higher engagement = Higher conversion  
3. **ProductRelated_Duration** → More time on product pages = More purchases  
4. **ExitRates** → Lower exit rates = Higher purchase probability  
5. **VisitorType_Returning_Visitor** → Returning visitors convert more often  
6. **Weekend** → Weekends positively impact purchases  

---

## 🎯 Recommendations  

### **Improve Customer Retention & Sales**  
- **Enhance Page Value** → Implement personalized recommendations.  
- **Target Seasonal Trends** → Boost marketing efforts in **May, March, December**.  
- **Reduce Exit & Bounce Rates** → Improve website usability, content relevance.  
- **Engage Visitors** → Optimize product pages for clarity and engagement.  
- **Retain Returning Customers** → Implement loyalty programs & personalized offers.  
- **Weekend Promotions** → Offer discounts & flash sales on weekends.  

### **For Marketing & Sales Teams**  
- **Target High-Value Users** → Use the **XGBoost model** to identify engaged users.  
- **Personalized Marketing** → Use **SHAP insights** to tailor promotions.  
- **Optimize Website** → Monitor & improve bounce and exit rates via A/B testing.  

---

## ✅ Conclusion  

✅ **XGBoost is the best-performing model for predicting purchases.**  
✅ **PageValues, TimeSpentOnSite, and ProductRelated_Duration are the strongest predictors.**  
✅ **Optimizing engagement, reducing bounce rates, and seasonal marketing can drive higher revenue.**  

---

## 👤 Author  

📌 **Milena Baldeva**  
📧 [milena.baldeva@gmail.com](mailto:milena.baldeva@gmail.com)  
🔗 [LinkedIn Profile](https://www.linkedin.com/in/milena-baldeva-051b01100/)  


