# Data Cleaning Overview (Pandas)

###  Goal  
The goal of **data cleaning** is to prepare raw data for accurate and efficient analysis.  
This involves ensuring consistency, correcting errors, and transforming data into usable formats.

---

##  Key Steps in Data Cleaning

1. **Overview** – Understand your dataset and its structure.  
2. **Data Types** – Verify and correct the data types of each column.  
3. **Data Issues** – Identify and fix errors, inconsistencies, and missing values.  
4. **Creating New Columns** – Derive meaningful features from existing data to enhance analysis.

>  The order of these tasks can vary depending on your dataset, but this sequence provides a reliable starting point.

---

## 1️⃣ Data Types

When using Pandas to read data, each column is automatically assigned a data type.  
However, sometimes Pandas misinterprets numeric or datetime columns as text (`object`), so always verify types before analysis.

### Checking Data Types
```python
df.dtypes        # View data types of each column
df.info()        # Get data types plus non-null counts
```
###  Common Pandas Data Types
| Data Type    | Description                       |
| ------------ | --------------------------------- |
| `bool`       | Boolean (True/False)              |
| `int64`      | Integer values                    |
| `float64`    | Decimal or floating-point numbers |
| `object`     | Text or mixed data                |
| `datetime64` | Date and time values              |

---

## 2️⃣ Converting Data Types
### Converting to Datetime
```python
# Use pd.to_datetime() to convert object columns into datetime format.
df['Date'] = pd.to_datetime(df['Date'])

df['Date'] = pd.to_datetime(df['Date'], format='%Y-%m-%d') # Specify format if needed

```
Pandas usually detects standard date formats automatically, but specifying the format can prevent errors.

### Converting to Numeric
```python

# Use pd.to_numeric() to convert text-based columns into numeric types.
df['Price'] = pd.to_numeric(df['Price'], errors='coerce')
``` 

```python
# To clean non-numeric characters (like $ or %), use string replacement first:
df['Price'] = df['Price'].str.replace('$', '', regex=False)

df['Price'] = pd.to_numeric(df['Price'])
# pd.to_numeric() handles missing values (NaN), while Series.astype() does not.
``` 

### Alternative: Using astype(), when you’re confident there are no missing or invalid values.
```python
df['Quantity'] = df['Quantity'].astype(int) # Convert a column to a specific type (int, float, object, bool):
```

## Best Practices
- Always check column types after loading data.
- Use pd.to_datetime() and pd.to_numeric() for safe conversions.
- Clean formatting issues (like symbols or text) before converting.
- Verify conversions using df.info() or df.head().

---

## Handling Missing Data in Python (Pandas)

## 1️⃣ Representations of Missing Data

| Type | Description | Notes |
|------|--------------|-------|
| `np.nan` | NumPy’s “Not a Number” | Most common; stored as float |
| `pd.NA` | Pandas’ dedicated missing value | Supports integers and other data types |
| `None` | Base Python null value | Cannot be used in numerical operations |

---

## 2️⃣ Finding Missing Data

Use these methods to detect missing values in your DataFrame:

```python
df.isna()                        # Boolean DataFrame showing missing values
df.isna().sum()                  # Count of missing values per column
df.info()                        # Summary of non-null counts and data types
df.value_counts(dropna=False)    # Includes NaN in value counts
df[df.isna().any(axis=1)]        # Select rows with any missing values
```
---

##  3️⃣ Handling Missing Data

Different situations call for different strategies:

a. Keep Missing Data
- Retain missing values if they convey information or uncertainty.
- Proceed without removal or imputation.

b. Remove Missing Data
```python
df.dropna()                          # Remove rows with any NaNs
df.dropna(how='all')                 # Remove rows entirely made of NaNs
df.dropna(thresh=2)                  # Keep rows with at least 2 non-NaN values
df.dropna(subset=['City'])           # Remove rows with NaN in specific column
df.dropna().reset_index(drop=True)   # Reset index after removal
```
Use inplace=True or reassign (df = df.dropna()) to make changes permanent.

c. Keep only Non_missing data
```python
df[df['State'].notna()]   # Keep rows where 'State' is not missing
```
---

## 4️⃣ Imputing (Replacing) Missing Data
Replace missing values with appropriate substitutes based on data type and context.
```python
df.fillna(0)                              # Replace all NaNs with 0
df['Grade'].fillna(df['Grade'].mean())    # Replace with mean
df['Grade'].fillna(df['Grade'].mode()[0]) # Replace with mode
df['Grade'].fillna(df['Grade'].median())  # Replace with median
```
Use inplace=True to modify the DataFrame directly.

---
## 5️⃣ Resolving Missing Data Manually

```python
df.loc[10, 'State'] = 'NY' # Update specific values

import numpy as np                  #Update multiple values conditionally:
df['Year'] = np.where(df['Year'].isna(), 'Freshman', df['Year'])

```
---
## Best Practices
- Use .info() first to assess data completeness.
- Understand why data is missing before deciding how to handle it.
- Choose methods based on data type, context, and domain expertise.
- Always document your cleaning steps for reproducibility and transparency.

---

##  Quick Reference Table

| **Function / Method** |  **Description** |  **Example** |
|---------------------------|--------------------|----------------|
| `df.isna()` | Returns `True` for missing values | `df.isna()` |
| `df.isna().sum()` | Counts missing values per column | `df.isna().sum()` |
| `df.info()` | Displays non-null count per column | `df.info()` |
| `df.value_counts(dropna=False)` | Includes `NaN` in frequency counts | `df.col.value_counts(dropna=False)` |
| `df.dropna()` | Drops rows with any missing values | `df.dropna()` |
| `df.dropna(how='all')` | Drops rows entirely made of `NaN`s | `df.dropna(how='all')` |
| `df.dropna(thresh=n)` | Keeps rows with ≥ *n* non-missing values | `df.dropna(thresh=2)` |
| `df.dropna(subset=['col'])` | Drops rows with `NaN` in a specific column | `df.dropna(subset=['City'])` |
| `df.notna()` | Returns `True` for non-missing values | `df['City'].notna()` |
| `df.fillna(value)` | Fills missing values with a given value | `df.fillna(0)` |
| `df['col'].fillna(df['col'].mean())` | Fills missing with mean | `df['Grade'].fillna(df['Grade'].mean())` |
| `df.loc[row, col] = value` | Updates a specific missing value | `df.loc[10, 'State'] = 'FL'` |
| `np.where(condition, value_if_true, value_if_false)` | Replace conditionally | `df['Year'] = np.where(df['Year'].isna(), 'Freshman', df['Year'])` |






