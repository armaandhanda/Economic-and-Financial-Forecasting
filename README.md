# **Time Series Forecasting for Retail Sales**

## **Authors**
- Armaan Dhanda 
- Georgy Jacob 
- Nithin Srivatsa 

---

## **Executive Summary**
This time series forecasting project focuses on predicting future sales across three product categories: **Furniture**, **Technology**, and **Office Supplies** using three different models: **SARIMA**, **Prophet**, and **LSTM**.

### **Key Highlights**
1. **Dataset**: Derived from a fictional Superstore with rich transactional and categorical details, capturing:
   - Orders, shipping methods, and products.
   - Customer segmentation and geographic distribution.
   - Sales metrics such as sales, discounts, and profit margins.
2. **Models**:
   - **SARIMA**: Effective for linear data with seasonality and trends.
   - **Prophet**: Flexible, modern model for non-linear trends and changepoints.
   - **LSTM**: Deep learning approach for complex patterns and long-term dependencies.
3. **Performance**:
   - **Prophet**: Best overall performance with low RMSE across categories.
   - **LSTM**: Best in the **Technology** category due to its ability to capture non-linear relationships.
   - **SARIMA**: Best in the **Office Supplies** category, where sales were more stable and linear.

---

## **Dataset Overview**
The dataset provides detailed sales transactions across multiple dimensions:
- **Transactional Data**: Unique order IDs and order dates.
- **Logistics Information**: Shipping details and methods.
- **Customer Insights**: Segmentation and geographic distribution.
- **Product Portfolio**: Categories and subcategories of products.
- **Financial Metrics**: Sales, discounts, and profit margins.

The dataset's **granular temporal structure** allowed us to:
1. Analyze distinct sales patterns across categories:
   - **Furniture**: High variance with strong seasonality.
   - **Office Supplies**: Stable and predictable trends.
   - **Technology**: Complex patterns with trends and seasonality.
2. Aggregate data weekly to reduce noise and capture business cycles.

---

## **Modeling Approach**

### **1. SARIMA (Seasonal ARIMA)**
- **Strengths**:
  - Captures linear trends and seasonal patterns effectively.
  - Works well for stable and predictable data.
- **Limitations**:
  - Assumes linearity, struggles with non-linear patterns.
- **Performance**:
  - Best suited for **Office Supplies** due to its stable and linear nature.

### **2. Prophet**
- Developed by Facebook for flexible time series forecasting.
- **Features**:
  - Automatic changepoint detection.
  - Handles missing data and sudden trend changes.
  - Models multiple seasonality patterns and holiday effects.
- **Performance**:
  - Best overall model, excelling in capturing non-linear trends and seasonality.

### **3. LSTM (Long Short-Term Memory)**
- A deep learning model for sequence modeling.
- **Strengths**:
  - Captures complex, non-linear patterns.
  - Learns long-term dependencies in data.
- **Performance**:
  - Best for the **Technology** category, where long-term dependencies dominate.

---

## **Implementation Details**

### **1. Data Preprocessing**
- **Datetime Conversion**: Transformed date strings into datetime objects.
- **Weekly Aggregation**:
  - Captured weekly business cycles while reducing daily noise.
  - Preserved meaningful patterns like month-end spikes.

### **2. Model Training**
#### **SARIMA**:
- Parameter selection using grid search and information criteria (AIC/BIC).
- Diagnostic checks using ACF/PACF plots and residual analysis.
#### **Prophet**:
- Tuned changepoint flexibility with `changepoint_prior_scale`.
- Added holiday effects and custom seasonality settings.
#### **LSTM**:
- Optimized sequence length and scaled features with `MinMaxScaler`.
- Architecture:
  - Multiple LSTM layers with dropout for regularization.
  - Dense output layer for predictions.

---

## **Performance Analysis**

### **Key Results**:
| **Model**   | **Furniture RMSE** | **Technology RMSE** | **Office Supplies RMSE** |
|-------------|---------------------|----------------------|---------------------------|
| **SARIMA**  | 598.95              | 1003.17             | **264.45**               |
| **Prophet** | **428.04**          | 432.57              | 495.77                   |
| **LSTM**    | 822.67              | **301.47**          | 716.81                   |

- **Furniture**:
  - Prophet outperformed with the lowest RMSE due to its ability to handle seasonal variations.
  - LSTM captured non-linear patterns effectively but had a higher error rate.
- **Technology**:
  - LSTM was the best performer, excelling in capturing long-term dependencies.
  - Prophet closely followed with competitive RMSE.
- **Office Supplies**:
  - SARIMA excelled, proving its strength in linear and stable datasets.

---

## **Critical Evaluation and Recommendations**
### **Strengths**:
- Comprehensive model comparison across categories.
- Robust weekly aggregation strategy to balance noise and data granularity.

### **Improvements**:
1. **External Features**:
   - Incorporate macroeconomic indicators, competitor pricing, marketing campaigns, or weather data.
2. **Model Enhancements**:
   - Use ensemble methods combining SARIMA, Prophet, and LSTM.
   - Explore advanced models like NeuralProphet or XGBoost with time-based features.
3. **Production Considerations**:
   - Automate anomaly detection and model retraining.
   - Implement quantile forecasting for uncertainty estimation.

---

## **Conclusion**
This project highlights the importance of tailoring models to data characteristics:
1. **Prophet**: Best overall due to its flexibility and ability to model complex patterns.
2. **LSTM**: Most effective for categories with non-linear trends and dependencies (e.g., Technology).
3. **SARIMA**: Ideal for stable and linear datasets (e.g., Office Supplies).

By leveraging the strengths of statistical, machine learning, and deep learning models, the project successfully delivered accurate forecasts, providing actionable insights for retail sales planning.

---

## **How to Run**
1. Clone this repository:
   ```bash
   git clone https://github.com/<username>/<repo_name>.git
   cd <repo_name>
