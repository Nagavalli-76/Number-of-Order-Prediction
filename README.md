# 🛒 Number of Orders Prediction

A machine learning project that predicts the **number of orders** a store will receive, based on store location, region, holiday and discount information. The model is built with **LightGBM** and trained on supplement store sales data.

---

## 📌 Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Tech Stack](#tech-stack)
- [Project Workflow](#project-workflow)
- [Features Used](#features-used)
- [Installation](#installation)
- [How to Run](#how-to-run)
- [Results](#results)
- [Future Improvements](#future-improvements)
- [Author](#author)

---

## Overview

Store owners need to forecast demand to plan stock and staffing. This project uses historical store data (June–July 2019) to predict daily orders using a gradient boosting regression model.

---

## Dataset

**File:** `supplement.csv`

| Column | Description |
|---|---|
| `ID` | Unique record identifier |
| `Store_id` | Unique store identifier |
| `Store_Type` | Type of store (S1–S4) |
| `Location_Type` | Type of location (L1–L5) |
| `Region_Code` | Region of the store (R1–R4) |
| `Date` | Date of the record |
| `Holiday` | 1 if the day is a holiday, else 0 |
| `Discount` | Whether a discount was running (Yes / No) |
| `Orders` | **Target**: number of orders received |

- **Records:** 22,265 rows × 9 columns
- **Missing values:** None

---

## Tech Stack

- **Language:** Python 3
- **Data handling:** Pandas, NumPy
- **Visualization:** Plotly Express
- **Machine learning:** Scikit-learn, LightGBM
- **Environment:** Jupyter Notebook

---

## Project Workflow

1. **Import Dataset**: load `supplement.csv` with Pandas.
2. **Data Inspection**: check `info()`, null values and descriptive statistics.
3. **Data Visualization**: pie charts for Store Type, Location Type, Region Code, Discount and Holiday.
4. **Data Preprocessing**: encode categorical columns into numbers:
   - `Discount`: No → 0, Yes → 1
   - `Store_Type`: S1–S4 → 1–4
   - `Location_Type`: L1–L5 → 1–5
   - `Region_Code`: R1–R5 → 1–5
5. **Train/Test Split**: 80% training (17,812 rows) and 20% testing (4,453 rows), `random_state=42`.
6. **Model Building**: train an `LGBMRegressor`.
7. **Prediction**: predict orders on the test set and store them in a DataFrame.

---

## Features Used

| Feature | Type |
|---|---|
| `Location_Type` | Encoded categorical |
| `Holiday` | Binary |
| `Discount` | Binary |
| `Region_Code` | Encoded categorical |

**Target:** `Orders`

---

## Installation

```bash
# Clone the repository
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>

# (Optional) create a virtual environment
python -m venv venv
venv\Scripts\activate        # Windows
# source venv/bin/activate   # Linux / macOS

# Install dependencies
pip install pandas numpy plotly scikit-learn lightgbm jupyter
```

---

## How to Run

```bash
jupyter notebook No_of_Order_Prediction.ipynb
```

Make sure `supplement.csv` is in the same folder as the notebook, then run all cells from top to bottom.

---

## Results

- The LightGBM model is trained on 17,812 samples with 4 input features.
- Predictions are generated for 4,453 test samples.
- Average order count in the training data is about **333**.

> 📝 Evaluation metrics (MAE, RMSE, R²) are not yet included in the notebook. See *Future Improvements*.

---

## Future Improvements

- Add evaluation metrics: MAE, RMSE and R² score.
- Use `Store_Type`, `Store_id` and date features (day of week, month) as inputs.
- Replace manual mapping with One-Hot Encoding for categorical columns.
- Hyperparameter tuning with GridSearchCV or Optuna.
- Compare against Random Forest, XGBoost and Linear Regression.
- Plot actual vs predicted orders.
- Save the trained model with `joblib` and deploy it with Streamlit or Flask.

---

## Author

**Kodidasu Veera Venkata Nagavalli**
B.Tech AI & ML, Aditya College of Engineering and Technology
🔗 GitHub: [Nagavalli-76](https://github.com/Nagavalli-76)

---

⭐ If you found this project useful, consider giving it a star!
