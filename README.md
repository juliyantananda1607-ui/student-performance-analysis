# Student Performance Analysis

## Project Overview

This project analyzes student performance data using Python to identify factors associated with students' final grades.

The project covers data cleaning, exploratory data analysis (EDA), data visualization, correlation analysis, and machine learning classification.

The main objective is to understand which student characteristics and study behaviors are most useful for predicting final grades.

---

## Dataset

The dataset contains 25,000 student records and includes information about:

- Age
- Gender
- School type
- Parent education
- Study hours
- Attendance percentage
- Internet access
- Travel time
- Extra activities
- Study method
- Math score
- Science score
- English score
- Overall score
- Final grade

---

## Data Cleaning

The following data preprocessing steps were performed:

- Checked the dataset structure and data types
- Checked for missing values
- Checked for duplicate student IDs
- Removed duplicate records
- Encoded categorical variables into numerical values
- Prepared the dataset for machine learning

---

## Exploratory Data Analysis

Data visualization was performed to understand:

- Age distribution
- Study hours distribution
- Attendance percentage distribution
- Average Math score
- Average Science score
- Average English score
- Average Overall score

These visualizations helped identify the general characteristics and academic performance of the students.

---

## Correlation Analysis

Correlation analysis was performed to identify relationships between numerical variables.

The main findings were:

- `study_hours` had a very strong positive correlation with `overall_score` (**0.906**).
- `attendance_percentage` had a moderate positive correlation with `overall_score` (**0.288**).
- Math, Science, and English scores showed strong positive correlations with each other.
- `age` showed almost no correlation with academic scores.

These results suggest that study hours are strongly associated with academic performance in this dataset.

---

# Machine Learning

The target variable for the classification task was:

`final_grade`

Two different modeling scenarios were tested.

---

## Model 1 – Including Subject Scores

The first model used student demographic information, study behavior, attendance, and subject scores.

### Logistic Regression

- Accuracy: **65.39%**
- Macro F1-score: **0.56**

### Random Forest

- Accuracy: **77.00%**
- Macro F1-score: **0.74**

Random Forest performed significantly better than Logistic Regression in this scenario.

---

## Model 2 – Without Subject Scores

To create a more realistic prediction scenario, the following features were removed:

- `math_score`
- `science_score`
- `english_score`
- `overall_score`

The model then predicted `final_grade` using demographic characteristics, attendance, and study behavior.

### Logistic Regression

- Accuracy: **67.74%**
- Macro F1-score: **0.590**

### Random Forest

- Accuracy: **65.13%**
- Macro F1-score: **0.574**

In this scenario, Logistic Regression performed slightly better than Random Forest.

---

## 📊 Model Comparison

| Model | Subject Scores | Accuracy | Macro F1 |
|---|---|---:|---:|
| Logistic Regression | Yes | 65.39% | 0.56 |
| Random Forest | Yes | **77.00%** | **0.74** |
| Logistic Regression | No | **67.74%** | **0.590** |
| Random Forest | No | 65.13% | 0.574 |

---

## Feature Importance

### Random Forest Model 2

When subject scores were excluded, the most important features were:

| Rank | Feature | Importance |
|---:|---|---:|
| 1 | `study_hours` | **44.89%** |
| 2 | `attendance_percentage` | **19.60%** |
| 3 | `age` | 7.05% |
| 4 | `parent_education` | 6.81% |
| 5 | `travel_time` | 5.18% |

The results show that `study_hours` was the most important predictor, followed by `attendance_percentage`.

Together, these two features accounted for approximately **64.49%** of the total feature importance.

---

## Key Findings

### 1. Study hours are highly important

`study_hours` was consistently identified as an important predictor.

It had a correlation of **0.906** with `overall_score` and accounted for **44.89%** of Random Forest feature importance in Model 2.

### 2. Attendance is also an important factor

`attendance_percentage` was the second most important feature in Model 2, with **19.60%** feature importance.

### 3. Subject scores improve prediction performance

When Math, Science, and English scores were included, Random Forest achieved **77.00% accuracy**.

Removing these scores reduced Random Forest performance to **65.13%**.

### 4. Logistic Regression performs better without subject scores

In Model 2, Logistic Regression achieved **67.74% accuracy**, slightly outperforming Random Forest.

This suggests that the relationship between demographic and behavioral variables and final grade can be reasonably modeled using a linear classification approach.

---

## Conclusion

The analysis shows that study behavior, particularly study hours and attendance, provides meaningful information for predicting students' final grades.

Random Forest achieved the best overall performance with **77.00% accuracy and a 0.74 Macro F1-score** when subject scores were included.

However, when academic scores were excluded, Logistic Regression achieved the best performance with **67.74% accuracy and a 0.590 Macro F1-score**.

Overall, the findings suggest that study hours and attendance are the most important behavioral indicators associated with student final grades in this dataset.

These results represent predictive relationships and should not be interpreted as proof of causal relationships.

---

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook

---

## Project Structure

```text
student-performance-analysis/
│
├── README.md
├── dataviz1.ipynb
└── .gitignore
