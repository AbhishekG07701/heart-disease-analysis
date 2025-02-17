# Heart Disease Data Analysis & Prediction

## 📌 Overview  

Heart disease is the **leading cause of death worldwide**, responsible for **17.9 million deaths per year**. This project leverages **data analysis and machine learning** to identify patterns and build a predictive model for **early detection of heart disease**.  

### **Dataset**  

The dataset, sourced from **Kaggle**, contains various medical and diagnostic information for patients, including those diagnosed with heart disease and those without.  

📂 **Key Features in the Dataset:**  

- **age**: Age of the patient (years)  
- **sex**: Gender (1 = Male, 0 = Female)  
- **chest_pain_type**: Type of chest pain experienced:  
  - 0: Typical Angina  
  - 1: Atypical Angina  
  - 2: Non-Anginal Pain  
  - 3: Asymptomatic  
- **resting_blood_pressure**: Resting blood pressure (mm Hg)  
- **cholesterol**: Serum cholesterol level (mg/dL)  
- **fasting_blood_sugar**: Whether fasting blood sugar > 120 mg/dL (1 = Yes, 0 = No)  
- **resting_ecg**: Resting electrocardiographic results:  
  - 0: Normal  
  - 1: ST-T wave abnormality  
  - 2: Left ventricular hypertrophy  
- **max_heart_rate**: Maximum heart rate achieved during exercise  
- **exercise_induced_angina**: Chest pain caused by exercise (1 = Yes, 0 = No)  
- **oldpeak**: ST depression induced by exercise relative to rest  
- **st_slope**: Slope of the ST segment:  
  - 0: Upsloping  
  - 1: Flat  
  - 2: Downsloping  
- **target**: Diagnosis result (1 = Heart Disease, 0 = No Heart Disease)  

---

## 📊 **Exploratory Data Analysis (EDA)**  

🔎 **Key Insights from Data Visualization:**  

- **Heart disease is more common in males** but increases for both genders with age.  
- **Higher cholesterol and blood pressure levels** strongly correlate with heart disease.  
- **Patients with typical angina and higher ST depression values (oldpeak)** are at higher risk.  
- **Exercise-induced angina is a strong predictor** of heart disease.  

Visualizations included **histograms, box plots, and correlation heatmaps** to explore these relationships.  

---

## 🛠 **Data Preparation & Feature Engineering**  

To improve the model’s performance, I cleaned and transformed the data with the following steps:  

- **Fixed Outliers**: Used **Z-score filtering** to remove extreme values. 
- **Feature Engineering**: Created new meaningful features, including:  
   - **Cholesterol-to-Age Ratio**: Normalizes cholesterol values based on age.  
   - **Blood Pressure Categories**: Binned blood pressure into normal, elevated, and hypertension groups.  
   - **Heart Rate Fitness Indicator**: Compared actual max heart rate with the expected max heart rate (220 - age).  
   - **Oldpeak Analysis**: Examined ST depression values in relation to diagnosis outcomes.
- **Scaled Data**: Used **MixMaxScaler** to scale the data. 
---

## 🤖 **Machine Learning Model Comparison**  

I tested multiple **classification models** to find the best one for predicting heart disease.  

| Model | Accuracy | Precision | Recall | F1-Score | ROC AUC |
|--------|----------|----------|--------|----------|---------|
| Logistic Regression | 87.80% | 86.82% | 85.50% | 86.15% | 93.83% |
| SGD Classifier | 76.95% | 66.67% | 96.18% | 78.75% | 93.69% |
| Decision Tree | 89.15% | 90.91% | 83.97% | 87.30% | 88.63% |
| SVC | 86.78% | 84.33% | 86.26% | 85.28% | 94.64% |
| K-Nearest Neighbors | 84.75% | 79.45% | 88.55% | 83.75% | 89.94% |
| Random Forest | 92.88% | 91.04% | 93.13% | 92.08% | 96.99% |
| AdaBoost | 84.75% | 81.62% | 84.73% | 83.15% | 93.69% |
| Gradient Boosting | 93.22% | 90.51% | 94.66% | 92.54% | 96.18% |
| XGBoost | 92.88% | 89.85% | 94.66% | 92.19% | 96.02% |
| **Stacking Ensemble (Final Model)** | **92.88%** | **89.85%** | **94.66%** | **92.19%** | **96.02%** |  


### **How I Built the Final Model** 🏆  

After testing individual models, I used **Stacking Ensemble Learning**, which combines multiple models to **maximize performance**.  

✔ **Base Models Used:**  
   - **Decision Trees** (for rule-based learning)  
   - **Random Forest** (for feature importance analysis)  
   - **XGBoost** (for boosting weak predictions)  
   - **Gradient Boosting** (to refine decision boundaries)  

✔ **Final Meta-Model:** **Logistic Regression**, which learns from the base models’ predictions to improve overall accuracy.  

The final model correctly **predicted heart disease in over 92% of cases**, making it highly reliable. 🚀  

---

## 🏁 **Project Structure**  

- 📂 `data/`: Contains the dataset files
- 📜 `Analysis_heart_disease_dataset`: Jupyter notebook for analysis & visualization 
- 📜 `README.md`: Project details and documentation  