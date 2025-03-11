# Air Quality in Durban - Part 3: AutoRegressive Model with Time Series Data from MongoDB

## Project Overview
This project is part of a multi-part series analyzing and forecasting air quality in Durban. In **Part 3**, we implement an **AutoRegressive (AR) Model** to predict **PM2.5 values**, leveraging temporal dependencies in the dataset. The analysis builds upon previous parts where we explored data preprocessing and a **Linear Regression model**.

- **Dataset Source:** [Open Africa - Sensors.Africa Air Quality Archive (Durban)](https://open.africa/dataset/sensorsafrica-airquality-archive-durban)  
- **Tools Used:** Python, Pandas, MongoDB, Scikit-learn, Statsmodels, Matplotlib, Seaborn, Plotly  
- **Author:** Dumisani Maxwell Mukuchura  
- **Contact:** dumisanimukuchura@gmail.com | [LinkedIn](https://www.linkedin.com/in/dumisani-maxwell-mukuchura-4859b7170/)  

## Tools and Technologies
- **MongoDB**: A NoSQL database used to store and query the dataset.
- **MongoDB Compass**: A GUI for MongoDB to visualize and interact with the data.
- **MongoDB Shell (`mongosh`)**: A command-line interface for MongoDB.
- **Python**: Used for data analysis, modeling, and visualization.
- **Pandas**: A Python library for data manipulation and analysis.
- **Statsmodels**: A Python library for statistical modeling, used to build the AutoRegressive model.
- **Matplotlib and Plotly**: Libraries for data visualization.

## Goals of This Project
1. **Retrieve historical air quality data** from a **MongoDB database**.
2. **Clean and preprocess the data** to make it suitable for time series analysis.
3. **Perform Exploratory Data Analysis (EDA)** to visualize trends, patterns, and anomalies.
4. **Implement an AutoRegressive (AR) Model** for forecasting PM2.5 values.
5. **Evaluate the model's performance** and compare it with the Linear Regression model from Part 2.
6. **Visualize predictions** and understand residuals through diagnostic analysis.
7. **Implement Walk-Forward Validation** to improve model performance.

## Folder Structure
Air-Quality-in-Durban-Part-3-AutoRegressive-Model-with-TimeSeries-Data-from-MongoDB/ 
│── data/ # Contains the dataset 
│── notebook/ # Jupyter Notebook with the analysis 
│── README.md # Project documentation


## Key Steps in the Analysis

### 1. Data Preparation
- **Connect to MongoDB** and retrieve the air quality data.
- **Resample the data to hourly intervals** for smooth time series processing.
- **Create a single time-dependent variable (`P2`)** instead of a feature-target split.

### 2. Exploratory Data Analysis (EDA)
- **Autocorrelation Function (ACF) Plot** to check relationships between PM2.5 values over time.
- **Partial Autocorrelation Function (PACF) Plot** to determine the optimal number of lags for the AR model.

### 3. Model Building
- **Baseline Model:** Uses the mean of the training data as a naive predictor.
- **AutoRegressive (AR) Model:** Uses the past PM2.5 value (`P2.L1`) to predict the next PM2.5 value.

### 4. Model Evaluation
- **Training Mean Absolute Error (MAE):** **0.66**  
- **Test MAE (Out-of-Sample Prediction):** **2.99**  
- **Residual Analysis:** Residuals appear normally distributed, indicating a well-fitted model.

### 5. Walk-Forward Validation
- **Walk-Forward Validation (WFV):** A rolling window approach retraining the model at each time step.
- **Improved Test MAE (WFV):** **0.74** (significant improvement from 2.99)

## Results & Insights
- The **AutoRegressive Model (AR(1)) performed better than the Linear Regression model** from Part 2.
- Residuals show **no strong autocorrelation**, confirming a well-behaved model.
- **Walk-Forward Validation significantly improved** forecasting accuracy.
- The final model equation is:  
  **P2 = 0.563 + (0.950 * P2.L1)**

## Next Steps
- Extend the AR model to **higher-order lags (AR(p))** for better long-term predictions.
- Implement **advanced models (ARIMA, LSTMs, XGBoost)** for comparison.
- Incorporate **additional features like weather conditions** to enhance forecasting accuracy.

