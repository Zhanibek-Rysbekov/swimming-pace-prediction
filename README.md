# Olympic Swimming Performance Prediction (End-to-End ML Pipeline)

## Overview
This repository contains an end-to-end Machine Learning pipeline designed to predict an athlete's 100m swimming pace based on biological indicators and race parameters. Utilizing raw scraped data from the **Paris 2024 Olympic Games**, the project demonstrates data collection, automated preprocessing, model benchmarking, and web deployment.

## Key Technical Features

### 1. Web Scraping & Data Engineering
* **Data Collection:** Automated extraction of **2,787 elite athlete records** from official web sources using `BeautifulSoup`.
* **Feature Scope:** Engineered a clean dataset consisting of 10 primary dimensional features including `sex`, `nationality`, `height`, `weight`, `age_2024`, and `distance_m`.
* **Data Quality:** Conducted strict data validation ensuring 0 duplicates and handling missing values to prevent downstream training bias.

### 2. Robust Preprocessing Pipeline
* Implemented a repeatable `Scikit-learn` pipeline for production-level data transformation.
* Seamlessly handles numerical features via scaling and categorical features (`sex`, `nationality`) via automated encoding layers.

### 3. Model Benchmarking & Evaluation
Evaluated 5 distinct regression algorithms under identical validation splits. **Gradient Boosting** emerged as the champion architecture:

| Model | MAE (sec) | RMSE | R² Score |
| :--- | :---: | :---: | :---: |
| **Gradient Boosting** | **1.30** | **1.62** | **0.86** |
| Random Forest | 1.34 | 1.67 | 0.85 |
| XGBoost | 1.38 | 1.72 | 0.84 |
| Linear Regression | 1.41 | 1.77 | 0.83 |
| Decision Tree | 1.69 | 2.11 | 0.76 |

* *Insight:* The final Gradient Boosting model achieves an $R^2$ of **0.86**, meaning it explains 86% of the variance in swimming speeds, with a Mean Absolute Error of just **1.30 seconds** per 100m.

### 4. Interactive Web Deployment
* Built and deployed a web interface using **Gradio** for real-time inference.
* Users can input an athlete's biometric profile (age, physical proportions) and race distance to instantly forecast their competitive pace.

## Tech Stack
* **Data Pipelines:** Python, Pandas, NumPy, BeautifulSoup
* **Machine Learning:** Scikit-learn, Gradient Boosting, XGBoost, Random Forest
* **Interface & Deployment:** Gradio Web UI
