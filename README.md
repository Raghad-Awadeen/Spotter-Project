# Spotter-Project

# Spotter ML Assessment — Freight Rate Prediction

Machine learning solution for predicting freight rates based on shipment, route, equipment, market, and date-related features.

## Project Overview

This project was developed as part of the Spotter Machine Learning assessment.

The objective is to train a regression model using historical freight data and predict the `posted_rate` for unseen loads in the validation dataset.

The project includes:

- Data cleaning and preprocessing
- Exploratory Data Analysis (EDA)
- Feature analysis and engineering
- Comparison of multiple regression models
- Model evaluation using MAE, RMSE, and R²
- Final model selection and training
- Predictions for the provided validation dataset

## Project Structure

```text
Spotter-ML-Assessment/
│
├── data/
│   ├── train_test.csv
│   ├── validation.csv
│   ├── december_predictions.csv
│   └── december_chart_inputs.csv
│
├── notebooks/
│   ├── 01_data_cleaning_and_eda.ipynb
│   ├── 02_model_training_and_evaluation.ipynb
│   └── 03_final_model_and_validation.ipynb
│
├── validation_predictions.csv
├── score.py
├── requirements.txt
└── README.md
```

## Dataset

The project uses the datasets provided as part of the assessment.

### `train_test.csv`

Historical labeled data used for data exploration, preprocessing, model training, and evaluation.

The target variable is:

```text
posted_rate
```

### `validation.csv`

Unseen loads used to generate the final predictions.

Each load contains a unique:

```text
load_id
```

### `december_chart_inputs.csv`

December input data provided for evaluating the model's predictions for a fixed route and shipment configuration.

### `december_predictions.csv`

Contains the model predictions generated for the December chart inputs.

## Data Preparation

The data preparation process included:

- Reviewing data types and column structures
- Handling missing values
- Investigating invalid values
- Handling negative values in the `weight` feature
- Converting date information into useful features
- Reviewing numerical and categorical features
- Checking feature distributions and relationships
- Investigating potential outliers and unusual observations
- Preparing the data for machine learning models

Missing values were handled based on the nature of each feature rather than simply removing affected rows.

Negative values in the `weight` feature were investigated and treated as invalid observations during preprocessing.

## Exploratory Data Analysis

EDA was performed to understand:

- Target variable distribution
- Numerical feature distributions
- Categorical feature frequencies
- Relationships between features and freight rates
- Route-related patterns
- Equipment type differences
- Distance and weight relationships
- Market-related patterns
- Date-related patterns
- Potential outliers and unusual observations

The data cleaning and EDA process is available in:

```text
notebooks/01_data_cleaning_and_eda.ipynb
```

## Modeling Approach

Multiple regression models were trained and evaluated using the prepared training data.

The evaluated models were:

- CatBoost
- Ridge
- LightGBM
- XGBoost

Models were evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

The model comparison and evaluation process is available in:

```text
notebooks/02_model_training_and_evaluation.ipynb
```

## Model Results

The evaluated models achieved the following results:

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| **CatBoost** | **103.85** | **646.65** | **0.8210** |
| Ridge | 166.62 | 655.27 | 0.8162 |
| LightGBM | 246.38 | 694.77 | 0.7934 |
| XGBoost | 292.57 | 743.17 | 0.7636 |

### Model Selection

**CatBoost was selected as the final model** because it achieved:

- The lowest MAE: **103.85**
- The lowest RMSE: **646.65**
- The highest R²: **0.8210**

This indicates that CatBoost provided the best overall performance among the evaluated models on the evaluation data.

## Evaluation Metrics

### MAE

Mean Absolute Error measures the average absolute difference between the actual and predicted freight rates.

**Lower values indicate better performance.**

### RMSE

Root Mean Squared Error gives a higher penalty to large prediction errors.

**Lower values indicate better performance.**

### R²

R² measures the proportion of variance in the target variable explained by the model.

**Higher values generally indicate better performance.**

## Final Model

The final model is a **CatBoost Regressor**.

The final model training and validation workflow is available in:

```text
notebooks/03_final_model_and_validation.ipynb
```

This notebook contains the final model training process and generation of predictions for the validation dataset.

## Predictions

The final predictions for the provided validation dataset are stored in:

```text
validation_predictions.csv
```

The file contains:

```text
load_id,predicted_rate
```

Each `load_id` corresponds to one load in the validation dataset.

## Scoring

The provided:

```text
score.py
```

script can be used to evaluate the generated predictions according to the assessment requirements.

## Installation

Create a Python environment and install the required dependencies:

```bash
pip install -r requirements.txt
```

## Running the Project

### 1. Data Preparation and EDA

Open:

```text
notebooks/01_data_cleaning_and_eda.ipynb
```

Run the notebook to review the data cleaning and exploratory analysis process.

### 2. Model Training and Evaluation

Open:

```text
notebooks/02_model_training_and_evaluation.ipynb
```

Run the notebook to train and compare the evaluated regression models.

### 3. Final Model and Validation

Open:

```text
notebooks/03_final_model_and_validation.ipynb
```

Run the notebook to train the final CatBoost model and generate predictions for the validation dataset.

## Requirements

The required Python packages and versions are listed in:

```text
requirements.txt
```

## Output

The main submission output is:

```text
validation_predictions.csv
```

with the required columns:

```text
load_id
predicted_rate
```
