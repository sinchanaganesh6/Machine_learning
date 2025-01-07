# Data Preprocessing in Python

---

## Author & Attribution
**Author**: [Sinchana Ganesh]  
**Original Repository**: [GitHub Link](https://github.com/sinchanaganesh6/Machine_learning.git)  
**License**: Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)  

---

## Table of Contents
1. [Introduction](#introduction)
2. [Tools for Data Preprocessing](#tools-for-data-preprocessing)
3. [Steps in Data Preprocessing](#steps-in-data-preprocessing)
4. [Detailed Steps](#detailed-steps)
5. [Code Exercise](#code-exercise-handling-missing-data)

---

## Introduction
Data preprocessing is a critical step in preparing raw data for analysis. It includes cleaning, transforming, and organizing data to make it suitable for machine learning or statistical models.

---

## Tools for Data Preprocessing
- **NumPy**: For numerical computations and handling arrays.
- **Pandas**: For handling tabular data such as CSV files.
- **Matplotlib**: For data visualization.
- **Scikit-learn**: For machine learning models and preprocessing utilities.

---

## Steps in Data Preprocessing
### 1. **Import Python Libraries**:
```python
import numpy as np
import pandas as pd
```

### 2. **Import Dataset**:
Use Pandas to read datasets:
```python
dataset = pd.read_csv("filename.csv")
```

### 3. **Handle Missing Data**:
- Replace missing values using techniques like mean, median, or mode.
- Drop missing data if necessary.

### 4. **Encode Categorical Data**:
- Encode independent and dependent variables using label encoding or one-hot encoding.

### 5. **Split the Dataset**:
- Divide data into training and testing sets (validation is optional).

### 6. **Feature Scaling**:
- Normalize or standardize data to ensure consistency and comparability.

---

## Detailed Steps
### 1. **Import Dataset**
- Use Pandas to create a variable that holds the table data as a DataFrame:
```python
dataset = pd.read_csv("filename.csv")
```

### 2. **Create New Entities**:
- **Matrix of Features**: Columns used as inputs.
- **Dependent Variable Vector**: Column used as the output.

---

## Code Exercise: Handling Missing Data

### Steps
#### 1. **Import Necessary Libraries**
```python
import numpy as np
import pandas as pd
from sklearn.impute import SimpleImputer
```

#### 2. **Load the Dataset**
```python
dataset = pd.read_csv("filename.csv")
```

#### 3. **Identify Missing Data**
- Check for missing values in the dataset:
```python
print(dataset.isnull().sum())
```

#### 4. **Print Missing Data in Matrix of Features**
```python
X = dataset.iloc[:, :-1].values
print(pd.DataFrame(X).isnull().sum())
```

#### 5. **Configure an Instance of SimpleImputer**
```python
imputer = SimpleImputer(missing_values=np.nan, strategy="mean")
```

#### 6. **Fit and Transform Data**
- Apply imputation:
```python
imputer.fit(X)
X = imputer.transform(X)
```

#### 7. **Print Updated Matrix of Features**
```python
print(X)
```

---

**Note**: Always ensure to validate the preprocessing steps to avoid introducing biases or errors in the analysis.
