# 🏠 California House Price Predictor: A Linear Regression Journey

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Machine_Learning-orange)
![Pandas](https://img.shields.io/badge/Pandas-Data_Manipulation-green)

## 📌 Overview
This project applies Machine Learning to predict real estate prices using the famous California Housing Dataset. Rather than just building a model, this project focuses on the **end-to-end data pipeline**, highlighting the importance of data scaling, debugging, and extracting real-world insights from algorithmic predictions. 

## 🛠️ The Tech Stack
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Machine Learning:** Scikit-Learn (Linear Regression, StandardScaler)
* **Data Visualization:** Seaborn, Matplotlib

## 🧠 The Journey & Key Learnings
Building this model wasn't a straight line. During the development process, I encountered and resolved a massive data pipeline error:

* **The Scaling Trap:** My initial model evaluation returned an R² score of **-1403**. By stepping through the pipeline, I discovered I was passing raw, unscaled test data into a model trained on scaled data. 
* **The Fix:** Implementing a strict scaling protocol (`StandardScaler.fit_transform` on training data, and only `.transform` on testing data) resolved the data leakage and stabilized the model.

## 📊 Key Insights from the Data
After fixing the model, visualizing the predictions revealed some fascinating quirks about both the algorithm and the dataset:

### 1. The "Wall at 5.0"
![Actual vs Predicted](scatter_plot.png)  
*(Add your Actual vs Predicted image here)*

Looking at the predictions, there is a literal vertical wall of data points at the $500,000 mark (represented as 5.0). The original dataset artificially "capped" luxury houses at this price. The model actually attempts to predict their true, higher values, but looks incorrect because reality was capped!

### 2. The Model Guessed "Negative" Money
For a tiny fraction of extremely cheap properties, the model predicted a negative price. A great reminder that algorithms just do math—they don’t inherently understand the real-world constraints of money unless we program them to!

### 3. What Actually Drives Prices?
![Feature Importance](feature_importance.png)  
*(Add your Feature Importance image here)*

By extracting the coefficients from the Linear Regression model, I found that **Median Income** is by far the biggest driver of high house prices in this dataset, while the physical age of the house has surprisingly little impact.

## 🚀 How to Run This Project
1. Clone the repository:
   ```bash
   git clone [https://github.com/SurajM80/california-housing-regression.git](https://github.com/SurajM80/california-housing-regression.git)
