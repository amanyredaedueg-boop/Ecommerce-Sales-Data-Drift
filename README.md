# E-commerce Sales Data Drift Detection

## 📌 Project Overview

This project analyzes an e-commerce sales dataset to build a simple machine learning model for sales prediction and detect **Data Drift** that affects model performance.

The main goal is to understand why the model's predictions become inaccurate when customer behavior and sales patterns change, especially during the holiday season.

---

## 🎯 Objectives

* Analyze the raw e-commerce sales data.
* Train a **Linear Regression** model using the first three weeks as historical data.
* Test the model on the remaining period.
* Evaluate model performance using:

  * MAE
  * RMSE
  * R²
* Calculate **Weekly MAE** to monitor model performance.
* Identify when the model performance starts to deteriorate.
* Determine whether the problem is caused by a software bug or **Data Drift**.
* Propose a practical retraining and monitoring strategy.

---

## 📊 Dataset

The dataset contains raw e-commerce sales information from November to January.

### Main Features

| Feature             | Description              |
| ------------------- | ------------------------ |
| `date`              | Sales date               |
| `day`               | Day information          |
| `product_category`  | Product category         |
| `price`             | Product price            |
| `discount_pct`      | Discount percentage      |
| `is_holiday_season` | Indicates holiday season |
| `units_sold`        | Number of units sold     |

The `units_sold` column is used as the target variable for sales prediction.

---

## 🤖 Machine Learning Model

A **Linear Regression** model is used for sales prediction.

### Training Strategy

The first **3 weeks** of the dataset are treated as the historical/old data and used for model training.

The remaining data is used for testing the model and monitoring its performance.

### Features Used

* `price`
* `discount_pct`
* `is_holiday_season`

### Target

* `units_sold`

---

## 📈 Model Evaluation

The model is evaluated using:

### MAE — Mean Absolute Error

Measures the average absolute difference between actual and predicted sales.

### RMSE — Root Mean Squared Error

Measures prediction error while giving more weight to larger errors.

### R² — R-squared

Measures how well the model explains the variation in the target variable.

---

## 🚨 Data Drift Detection

Model performance is monitored using **Weekly MAE**.

The model initially performs relatively well, with low prediction error. During the holiday period, the prediction error increases significantly.

This indicates that the underlying sales behavior has changed and the old model is no longer representative of the current data.

The analysis also compares changes in:

* Average units sold
* Average price
* Discount percentage
* Holiday-season behavior

This helps distinguish **Data Drift** from a normal software bug.

---

## 🔍 Data Drift vs. Software Bug

### Software Bug

A bug is an error in the code or data-processing pipeline that causes incorrect results.

### Data Drift

Data Drift occurs when the characteristics or distribution of incoming data change compared with the data used to train the model.

In this project, the deterioration in model performance is associated with changes in customer behavior, prices, and the holiday season.

---

## 🔄 Retraining Strategy

Retraining the model using only the old data is not recommended because the old data does not represent the new sales behavior.

The proposed workflow is:

```text
Validate Pipeline
       ↓
Detect Data Drift
       ↓
Analyze Model Performance
       ↓
Retrain Using Recent Data
       ↓
Validate New Model
       ↓
Gradual Deployment
       ↓
Continuous Monitoring
```

---

## 💡 Final Decision

The model should not simply continue making automated decisions after its performance deteriorates.

Instead:

1. Verify that the pipeline and code are working correctly.
2. Confirm the presence of Data Drift using performance and data comparisons.
3. Retrain the model using recent representative data.
4. Validate the new model on unseen data.
5. Deploy the improved model gradually.
6. Continuously monitor MAE to detect future performance degradation.

---

## 📁 Project Structure

```text
Ecommerce-Sales-Data-Drift/
│
├── ecommerce_sales_raw.csv
├── Data_Drift_Analysis.ipynb
└── README.md
```

---

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Jupyter Notebook / Google Colab

---

## 👩‍💻 Project Purpose

This project demonstrates a real-world **Machine Learning Model Monitoring and Data Drift Detection** scenario in an e-commerce environment.

The focus is not only on building a prediction model, but also on understanding how model performance changes when real-world data changes.
