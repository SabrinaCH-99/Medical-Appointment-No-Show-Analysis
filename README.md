# Medical Appointment No-Show Analysis (Brazil)

## Overview
**No-shows**—missed medical appointments—pose a significant challenge to healthcare systems worldwide. They lead to the underutilization of medical resources, increased operational costs, and, most importantly, delayed patient care.

As a **Clinical Pharmacist** with an interest in data science, I conducted this Exploratory Data Analysis (EDA) on a dataset of 110k medical appointments in Brazil. My goal was to leverage data to bridge the gap between clinical observation and actionable insights. This project investigates how the following factors influence patient adherence:
* Demographics: Identifying patterns across age groups and genders.
* Waiting Intervals: Analyzing the impact of the lead time between scheduling and the actual visit.
* Comorbidities: Exploring how chronic conditions (e.g., hypertension, diabetes) affect attendance.
* Clinical Communication: Evaluating the effectiveness of SMS reminders in reducing no-show rates.

Through this analysis, I aim to uncover data-driven patterns that can help healthcare providers optimize scheduling strategies and improve patient outcomes.


## Key Insights
* **Waiting Duration:** A strong positive correlation exists between waiting duration and no-show rates. Adherence is highest for same-day appointments but declines significantly as the lead-time increases.
* **SMS Reminders:** SMS notifications effectively improve attendance, with the most pronounced impact seen in appointments scheduled over a week in advance.
* **Age Groups:** Attendance patterns vary by life stage; seniors (65+) exhibit the highest reliability, whereas adolescents and young adults (12-40) are the most likely to miss appointments.
* Gender: Analysis indicates no significant disparity in no-show rates between male and female patients, suggesting that gender is not a primary predictor of adherence in this dataset.


## Analysis Highlights
### 1. Data Cleaning & Preprocessing
* **Data Integrity Check:** Identified and resolved anomalies, such as negative age entries.
* **Temporal Conversion:** Transformed raw date strings into `datetime` objects to enable time-series analysis.
* **Feature Engineering:** Derived a `Waiting_Duration` feature to quantify the gap between the scheduling date and the actual appointment.
    * Developed a custom function to categorize waiting times into logical intervals (e.g., Same-day, Short-term, Long-term).

### 2. Exploratory Data Analysis (EDA)
* **Bivariate & Multivariate Analysis:** Analyzed the relationship between individual clinical factors (Comorbidities, SMS reminders) and patient adherence.
* **Trend Identification:** Conducted group-based comparisons to isolate significant predictors of no-show behavior, moving beyond simple correlations to understand situational impacts.

### 3. Data Visualization
* **Multi-variable Plotting:** Developed visualizations to illustrate the interplay between patient adherence (No-show rates) and key predictors, including Age, Waiting Duration, and SMS status.

### 4. Predictive Modeling & Machine Learning
* **Feature Engineering & Selection:** Processed categorical features using One-Hot Encoding and scaled numerical variables to optimize model performance. Managed class imbalance (as show-ups heavily outweigh no-shows 8:2) using class-weight adjustments.
* **Model Evaluation:** Implemented and compared multiple algorithms, utilizing Logistic Regression, alongside K-Nearest Neighbors, Decision Trees, and Random Forests to maximize predictive power.
* **Best Performing Model**: **KNN (with an adjusted classification threshold of 0.2)** achieved the best overall balance for this imbalanced dataset.
* **Performance Metrics**: Achieved an **AUC-ROC score of 0.72** and a **recall of 0.80** for the no-show class. While lowering the threshold to 0.2 successfully captured 80% of actual no-shows (High Recall), it decreased the precision to **0.31**. 

## Future Work & Development 
**1. Behavioral Segmentation (New vs. Frequent Patients):** Driven by exploratory insights showing significant behavioral variance within the frequent-visitor cohort, future iterations will test dataset segmentation to construct tailored, predictive models for both sub-populations.

**2. Refining Time-Based Features:** Further optimize temporal variables by analyzing the impact of specific days of the week (e.g., Mondays vs. Saturdays) on no-show behaviors, capturing potential weekly clinical patterns.

**3. Feature Isolation for Baseline Patient Behavior:** Conduct an ablation study by **removing intervention features like SMS_received** to evaluate the predictive power of a patient’s intrinsic behavioral characteristics alone.

**4. Try More Powerful Algorithms:** (XGBoost and LightGBM)

**5. Better Ways to Handle Class Imbalance:** Although class weights were already adjusted during training to help the model learn from the minority class, the dataset remains highly imbalanced. In the next step, experiment with advanced resampling techniques like SMOTE (generating synthetic data for no-show cases) to see if it further boosts performance.


## Tech Stack
* **Language:** Python 3.x
* **Libraries:** Pandas, NumPy, Matplotlib, Scikit-learn


## Data Source
The dataset is sourced from [Kaggle: Medical Appointment No Shows](https://www.kaggle.com/datasets/joniarroba/noshowappointments/data)
