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


## Future Work & Development 
* Statistical Modeling (Logistic Regression): Beyond exploratory analysis, I plan to develop a Logistic Regression model to quantify the odds ratio of no-shows for each risk factor, allowing for more precise predictions of patient behavior.
* Predictive Analysis: Implementing machine learning algorithms to build a predictive tool that flags high-risk appointments in real-time, enabling proactive interventions.

## Tech Stack
* **Language:** Python 3.x
* **Libraries:** Pandas, NumPy, Matplotlib


## Data Source
The dataset is sourced from [Kaggle: Medical Appointment No Shows](https://www.kaggle.com/datasets/joniarroba/noshowappointments/data)
