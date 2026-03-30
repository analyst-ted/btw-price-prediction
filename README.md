# BMW Price Prediction Analysis 🚗

This project implements a machine learning pipeline to predict the resale price of BMW vehicles. By applying strategic data cleaning and target transformations, the model achieves a **Mean Absolute Percentage Error (MAPE) of 18.35%**.

## 📊 Project Highlights
* **Baseline Model:** Linear Regression ($R^2$: 0.75, MAPE: 20.89%)
* **Champion Model:** Random Forest Regressor (**MAPE: 18.35%**)
* **Key Challenge:** High target skewness (3.31) and non-physical outliers (Log 56.30 "glitches").

## 🛠️ Data Engineering & Preprocessing
To stabilize the model and improve percentage accuracy, the following engineering steps were taken:

1.  **Outlier Handling:** Applied a 2%–98% quantile cap on prices. This removed "junk" listings ($<800) and ultra-luxury outliers that disproportionately skewed the regression gradient.
2.  **Target Transformation:** Switched from a Cube Root to a **Log1p Transformation**. This shifted the model's objective from minimizing absolute dollar error to minimizing relative percentage error, which is more representative of real-world car depreciation.
3.  **Feature Engineering:** * Derived `car_age` from registration dates to capture temporal depreciation.
    * Utilized One-Hot Encoding for categorical variables (`car_type`, `paint_color`).

## 📈 Model Evaluation
The final Random Forest model was evaluated using a 33% hold-out test set. 

| Metric | Linear Regression | Random Forest |
| :--- | :--- | :--- |
| **MAE (Avg $ Error)** | $2,344.93 | **$2,083.74** |
| **MAPE (Avg % Error)** | 20.89% | **18.35%** |

### Residual Analysis
The residual distribution confirmed that the model is highly accurate for mid-range vehicles ($10k–$25k). Expected heteroscedasticity (fanning) appears in the luxury segment ($35k+), indicating that at higher price points, unobserved features like "Vehicle Condition" or "Service History" carry more weight than mileage or age alone.

## 🚀 How to Run
1.  **Clone the repo:**
    ```bash
    git clone [https://github.com/analyst-ted/bmw-price-prediction.git](https://github.com/analyst-ted/bmw-price-prediction.git)
    ```
2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
3.  **Run the Analysis:**
    Open `car_prediction.ipynb` in Jupyter Notebook or VS Code to see the full pipeline.

---
*Developed by Arup Roy (analyst-ted) as part of a Data Science study intensive.*