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
6. [Example Code Explained](#example-code-explained)

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
import matplotlib.pyplot as plt
import pandas as pd
```

### 2. **Import Dataset**:
Use Pandas to read datasets:
```python
dataset = pd.read_csv("Data.csv")
```

### 3. **Handle Missing Data**:
- Replace missing values using techniques like mean, median, or mode.
- Use `SimpleImputer` to fill missing values.

### 4. **Encode Categorical Data**:
- Encode independent variables with `OneHotEncoder`.
- Encode dependent variables with `LabelEncoder`.

### 5. **Encode Independent Variable**:
Use `OneHotEncoder` to handle categorical data in features.

### 6. **Encode Dependent Variable**:
Use `LabelEncoder` for categorical target variables.

### 7. **Split the Dataset**:
- Divide data into training and testing sets (validation is optional).

### 8. **Feature Scaling**:
- Normalize or standardize data to ensure consistency and comparability.

---

## Detailed Steps

### 1. **Import Python Libraries**
To preprocess data effectively, the following libraries are essential:
- **NumPy**: For efficient numerical computations.
- **Matplotlib**: For data visualization.
- **Pandas**: For handling and analyzing tabular data.

Code:
```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
```

### 2. **Importing the Dataset**
Using `Pandas`, the dataset can be loaded into a DataFrame for easy manipulation. In this example:
```python
dataset = pd.read_csv("Data.csv")
X = dataset.iloc[:, :-1].values  # Independent variables
y = dataset.iloc[:, -1].values  # Dependent variable
```
- `X` contains all columns except the last one (features).
- `y` contains the last column (target variable).

### 3. **Handling Missing Data**
Missing data can disrupt analysis. Use `SimpleImputer` to handle missing values efficiently:
```python
from sklearn.impute import SimpleImputer
imputer = SimpleImputer(missing_values=np.nan, strategy='mean')
imputer.fit(X[:, 1:3])
X[:, 1:3] = imputer.transform(X[:, 1:3])
```
- **Strategy**: Replace missing values with the mean.
- **Fit and Transform**: Apply the imputer to specific columns (1 and 2).

### 4. **Encoding Categorical Data**
#### Encoding the Independent Variable
Categorical variables in `X` are converted using `OneHotEncoder`:
```python
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder
ct = ColumnTransformer(transformers=[('encoder', OneHotEncoder(), [0])], remainder='passthrough')
X = np.array(ct.fit_transform(X))
```
- **OneHotEncoder**: Converts categorical data into a binary matrix.
- **ColumnTransformer**: Applies the encoder to column 0.

#### Encoding the Dependent Variable
For the dependent variable, use `LabelEncoder`:
```python
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
y = le.fit_transform(y)
```
- **LabelEncoder**: Converts categorical labels into integers.

### 5. **Encoding Independent Variable**
One-hot encoding ensures no ordinal relationships between categorical values:
```python
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder
ct = ColumnTransformer(transformers=[('encoder', OneHotEncoder(), [0])], remainder='passthrough')
X = np.array(ct.fit_transform(X))
```
- This step is critical for machine learning models that rely on numerical input.

### 6. **Encoding Dependent Variable**
For classification tasks, categorical target variables need encoding:
```python
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
y = le.fit_transform(y)
```
- Encodes the dependent variable `y` into numerical values.

### 7. **Splitting the Dataset into Training and Test Sets**
To evaluate models, data is divided into training and testing subsets:
```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=1)
```
- **Training Set**: Used to train the model.
- **Test Set**: Used to test the model's performance.
- **`test_size=0.2`**: 20% of the data is allocated to the test set.

### 8. **Feature Scaling**
Scaling ensures that all features contribute equally to the model:
```python
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
X_train[:, 3:] = sc.fit_transform(X_train[:, 3:])
X_test[:, 3:] = sc.transform(X_test[:, 3:])
```
- **`StandardScaler`**: Scales data to have a mean of 0 and a standard deviation of 1.
- **Fit and Transform**: Applied to the training set; only transform is applied to the test set.

---

## Example Code Explained
```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

dataset = pd.read_csv("Data.csv")
X = dataset.iloc[:, :-1].values
y = dataset.iloc[:, -1].values

from sklearn.impute import SimpleImputer
imputer = SimpleImputer(missing_values=np.nan, strategy='mean')
imputer.fit(X[:, 1:3])
X[:, 1:3] = imputer.transform(X[:, 1:3])

from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder
ct = ColumnTransformer(transformers=[('encoder', OneHotEncoder(), [0])], remainder='passthrough')
X = np.array(ct.fit_transform(X))

from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
y = le.fit_transform(y)

from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=1)

from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
X_train[:, 3:] = sc.fit_transform(X_train[:, 3:])
X_test[:, 3:] = sc.transform(X_test[:, 3:])
```
- **Import Libraries**: Essential for computations and preprocessing.
- **Dataset Loading**: Access and store data into variables `X` and `y`.
- **Missing Data**: Impute missing values with column-wise mean.
- **Encoding**: Transform categorical variables into numerical representations.
- **Splitting**: Separate data into training and testing sets.
- **Scaling**: Normalize feature values for improved model performance.

---

**Note**: Proper data preprocessing improves the accuracy and efficiency of machine learning models. Always validate each preprocessing step to ensure data integrity and consistency.
