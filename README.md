# Video Games Sales Prediction

## Project Overview
This project aims to predict global sales of video games using machine learning techniques. It involves analyzing a dataset containing various features of video games, preprocessing the data, and training regression models to predict sales. The best results were achieved using a Polynomial Regression model applied to ordinal-encoded and normalized data.

---

## Table of Contents
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Data Preprocessing](#data-preprocessing)
- [Machine Learning Models](#machine-learning-models)
- [Results](#results)
- [Conclusion](#conclusion)
- [Technologies Used](#technologies-used)
- [How to Use](#how-to-use)
- [Future Work](#future-work)

---

## Dataset
The dataset contains 16,598 rows and includes the following columns:
- `Rank`: Overall sales ranking
- `Name`: Name of the video game
- `Platform`: System used for playing (e.g., PC, PS4)
- `Year`: Year of release
- `Genre`: Category of the game (e.g., Action, Sports)
- `Publisher`: Publishing company
- `NA_Sales`, `JP_Sales`, `Other_Sales`, `Global_Sales`: Sales data in millions of units

Key decisions for data preparation:
- Dropped irrelevant columns (`Name`, `NA_Sales`, `JP_Sales`, `Other_Sales`)
- Used `Platform`, `Publisher`, `Genre`, and `Year` as features
- `Global_Sales` as the target variable

---

## Methodology
1. **Data Cleaning**: 
   - Removed rows with missing `Publisher` values.
   - Replaced missing `Year` values with the mode.
   - Converted `Year` from float to integer.
   - Handled rare categories in `Publisher` by grouping them into "Other."
   - Removed outliers from `Global_Sales`.

2. **Data Encoding**:
   - Experimented with One Hot Encoding and Ordinal Encoding for categorical variables (`Platform`, `Publisher`, `Genre`).
   - Normalized ordinal-encoded data for additional experiments.

3. **Model Training**:
   - Split data into training (80%) and testing (20%) sets.
   - Evaluated models using Root Mean Squared Error (RMSE).

---

## Machine Learning Models
The following regression models were trained on different versions of the dataset:
1. **Linear Regression**
2. **Polynomial Regression** (varied degrees)
3. **Support Vector Machine (SVM)** with Linear and RBF kernels

---

## Results
- **One Hot Encoded Data**:
  - Linear Regression and SVM performed similarly (RMSE: ~0.52).
  - Polynomial Regression overfitted (RMSE: ~29 million on test data).

- **Ordinal Encoded Data**:
  - Linear Regression and Polynomial Regression performed well (RMSE: ~0.56).
  - SVM performed worse (RMSE: ~0.77).

- **Ordinal Encoded and Normalized Data**:
  - Polynomial Regression (degree 4) achieved the best results (Train RMSE: 0.0061, Test RMSE: 0.0064).

---

## Conclusion
- The project demonstrates how encoding and normalization impact model performance.
- Polynomial Regression on ordinal-encoded and normalized data outperformed other models, providing accurate predictions with minimal error.
- One Hot Encoding introduced too many features, leading to suboptimal performance.

---

## Technologies Used
- **Programming Language**: Python
- **Libraries**: Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn

---

## How to Use
1. Clone the repository.
2. Ensure the required libraries are installed.
3. Run the preprocessing and training scripts to replicate the results.

---

## Future Work
- Experiment with additional regression models (e.g., Random Forest, XGBoost).
- Explore feature engineering for better representation of categorical variables.
- Increase dataset size for improved model generalization.
