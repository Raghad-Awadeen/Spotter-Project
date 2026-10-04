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
- Final model training
- Predictions for the provided validation dataset

## Project Structure

```text
Spotter-ML-Assessment/
│
├── data/
│   ├── train_test.csv
│   ├── validation.csv
│   └── december_chart_inputs.csv
│
├── notebooks/
│   ├── 01_data_cleaning_and_eda.ipynb
│   ├── 02_model_training_and_evaluation.ipynb
│   └── 03_final_model_and_validation.ipynb
│
│
├── validation_predictions.csv
├── score.py
├── requirements.txt
└── README.md
```

## Dataset

The project uses three datasets provided as part of the assessment:

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

## Data Preparation

The data preparation process included:

- Reviewing data types and column structures
- Handling missing values
- Investigating invalid values
- Handling negative weight values
- Converting date information into useful features
- Reviewing categorical and numerical features
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
- Date and time-related patterns
- Potential outliers and unusual observations

The EDA is available in:

```text
notebooks/data_cleaning_eda.ipynb
```

## Modeling Approach

Several regression models were evaluated using the prepared training data.

The model comparison included tree-based and boosting approaches.

Models were evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

The model comparison and evaluation process can be found in:

```text
notebooks/model_comparison.ipynb
```

## Evaluation Metrics

### MAE

Mean Absolute Error measures the average absolute difference between the actual and predicted freight rates.

Lower values indicate better performance.

### RMSE

Root Mean Squared Error gives a higher penalty to large prediction errors.

Lower values indicate better performance.

### R²

R² measures how much of the variation in the target variable is explained by the model.

Higher values generally indicate better performance.

## Final Model

After comparing the evaluated models, the final model was selected based on validation performance and overall suitability for the dataset.

The final model implementation is available in:

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
notebooks/data_cleaning_eda.ipynb
```

Run the notebook to review the data cleaning and exploratory analysis process.

### 2. Model Comparison

Open:

```text
notebooks/model_comparison.ipynb
```

Run the notebook to train and compare the evaluated models.

### 3. Final Model

Open:

```text
notebooks/final_model.ipynb
```

This notebook contains the final model training and validation prediction workflow.

### 4. Generate Predictions

The final prediction workflow is also available in:

```text
src/final_model.py
```

The resulting predictions are saved as:

```text
validation_predictions.csv
```

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
