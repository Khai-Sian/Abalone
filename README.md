# Regression with Abalone Dataset
### Playground Series - Season 4, Episode 4

## Project Overview
This project focuses on **regression modeling** to predict the **Rings** attribute of abalones, which serves as an indicator of their age. The dataset was generated using **deep learning models**, maintaining distributions close to the original Abalone dataset while introducing slight variations.

## Dataset Description
The dataset consists of **train.csv** (training data) and **test.csv** (test data), along with a **sample_submission.csv** file for submission formatting. The target variable for regression is **Rings**, an integer representing the estimated age of each abalone.

### Features:
- **id** – Unique identifier for each sample.
- **Sex** – Gender category (**M, F, I**).
- **Length** – Longest shell diameter (continuous variable).
- **Diameter** – Perpendicular diameter to length.
- **Height** – Shell height excluding outer layers.
- **Whole weight** – Total weight including the shell.
- **Shucked weight** – Weight of the abalone meat after removal from the shell.
- **Viscera weight** – Weight of the internal organs.
- **Shell weight** – Weight of the shell after drying.
- **Rings** – Target variable indicating the age (integer).

## Data Processing Steps
### 1. Data Cleaning
- Renamed **Whole weight.1** → **Shucked weight** and **Whole weight.2** → **Viscera weight**.
- Handled missing values by filtering out rows with empty or zero values.
- Converted **Sex** into numerical format using one-hot encoding.

### 2. Exploratory Data Analysis (EDA)
- Boxplots and histograms revealed **no significant differences** between male and female abalones, but **infant abalones exhibited distinct patterns** due to their smaller size.
- Hexbin plots demonstrated **exponential growth** in weight as abalones aged, while **length, diameter, and height** followed a more **logarithmic trend**.
- **Correlation analysis** confirmed strong relationships between **weight variables and age**.

### 3. Feature Engineering
- Applied **MinMaxScaler** for normalization.
- Encoded categorical variables using **StringIndexer** and **OneHotEncoder**.
- Constructed final feature vectors using **VectorAssembler**.

## Model Training & Evaluation
### 1. Linear Regression
- Used **one-hot encoded Sex + scaled numerical features**.
- **Coefficients:** Weight attributes had the highest influence on prediction.
- **Intercept:** Adjusted baseline prediction for the model.
- **Performance:** Mean Absolute Error (MAE) and Mean Squared Error (MSE) indicated decent model accuracy but room for improvement.

### 2. Polynomial Regression
- Expanded features to **second-degree polynomial terms**.
- **Performance:** Showed slight improvement over linear regression.

### 3. Decision Tree Regression
- Implemented **DecisionTreeRegressor** for non-linear predictions.
- **Performance:** Captured intricate relationships in the dataset but suffered from overfitting.

### 4. Random Forest Regression
- Used **RandomForestRegressor** for ensemble learning.
- **Performance:** Provided better generalization with **lower prediction errors** than Decision Tree.

### Model Comparison:
| Algorithm | Min Predicted Rings | Max Predicted Rings |
|-----------|---------------------|---------------------|
| **Linear Regression** | **1** | **29.18** |
| **Polynomial Regression** | **1.99** | **29.53** |
| **Decision Tree Regression** | **4.37** | **17.77** |
| **Random Forest Regression** | **4.41** | **15.52** |

## Key Findings
- **Abalones grow heavier with age** while their physical dimensions change minimally.
- **Weights (Shucked, Viscera, and Whole) are the strongest predictors** for age estimation.
- **Polynomial expansion enhances accuracy**, capturing non-linear growth trends.
- **Random Forest performs best for generalization**, avoiding overfitting compared to Decision Tree.

## Conclusion
This analysis provides valuable insights into **abalone growth patterns** and the efficiency of different regression models for age prediction. Further improvements could be explored through **deep learning models**, advanced feature selection techniques, or incorporating the original dataset.

---
