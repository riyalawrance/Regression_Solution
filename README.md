# Regression_solution

Solving of polynomial regression using the normal equation α = (X^T X)^(-1) X^T Y

## What it does

- Fits polynomial curves (degree 2 and 3) to data
- Calculates regression coefficients manually using matrix operations
- Evaluates model performance with R² score

## Requirements

```bash
pip install numpy pandas matplotlib scikit-learn
```

## Usage

```python
import numpy as np
import pandas as pd

# Load data
data = pd.read_csv('Data.csv')
X = data.iloc[:,:-1].values
Y = data.iloc[:,-1].values

# Create polynomial features (degree 3)
X_poly = np.column_stack([
    np.ones(len(X)),  # intercept
    X,                # x
    X**2,             # x²
    X**3              # x³
])

# Calculate coefficients: α = (X^T X)^(-1) X^T Y
X_T = X_poly.T
coefficients = np.linalg.inv(X_T @ X_poly) @ X_T @ Y

print("Coefficients:", coefficients)
```

## Formula

**Degree 2**: y = a + bx + cx²  
**Degree 3**: y = a + bx + cx² + dx³

**Normal Equation**: α = (X^T X)^(-1) X^T Y

## Evaluation

- **SSE**: Sum of squared errors
- **SST**: Total sum of squares  
- **R²**: 1 - (SSE/SST)

## Files

- `Solution.ipynb` - Main code
- `Data.csv` - Dataset
- `README.md` - This file
