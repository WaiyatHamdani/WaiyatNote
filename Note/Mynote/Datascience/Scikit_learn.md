# Introduction to scikit-learn

**scikit-learn** (also called `sklearn`) is a Python library for machine learning. It provides tools for classification, regression, clustering, dimensionality reduction, model selection, and preprocessing.

## Table Content
- [Key Features](#key-features)
- [Common Algorithms](#common-algorithms)
- [Example Workflow](#example-workflow)
- [Preprocessing](#preprocessing-in-scikit-learn)

## Key Features

1. **Classification**: Used for categorizing objects (e.g., spam detection).
2. **Regression**: Predicting continuous values (e.g., stock prices).
3. **Clustering**: Grouping similar objects (e.g., customer segmentation).
4. **Dimensionality Reduction**: Reducing input variables (e.g., PCA).
5. **Model Selection**: Choosing between models using cross-validation.

## Common Algorithms

- **Linear Regression**:
  - `LinearRegression()` is used for predicting continuous values.
- **Classification Algorithms**:
  - `LogisticRegression()`: For binary classification tasks.
  - `DecisionTreeClassifier()`: A tree-based model for classification.
- **Clustering**:
  - `KMeans()`: A clustering algorithm for grouping similar data points.



## Example Workflow
1) Here's a typical machine learning workflow using **scikit-learn**:
```python
# Import necessary libraries
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Sample dataset (X: features, y: target)
X = np.array([[1, 1], [2, 2], [3, 3], [4, 4], [5, 5]])
y = np.array([2, 4, 6, 8, 10])

# Split data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Initialize the model
model = LinearRegression()

# Train the model
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Evaluate the model
mse = mean_squared_error(y_test, y_pred)
print(f'Mean Squared Error: {mse}')
```
2) Explanation of Workflow:
- Data Splitting: We use train_test_split() to divide the dataset into training and testing sets.
- Model Creation: LinearRegression() initializes the linear regression model.
- Model Training: The model is trained using fit() on the training data.
- Predictions: We make predictions on the test data using predict().
- Evaluation: We use mean_squared_error() to calculate the accuracy of our model.

## Preprocessing in scikit-learn
1) Scaling the Data:
```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
```
2) Handling Missing Data:
```python
from sklearn.impute import SimpleImputer

imputer = SimpleImputer(strategy='mean')
X_imputed = imputer.fit_transform(X)
```