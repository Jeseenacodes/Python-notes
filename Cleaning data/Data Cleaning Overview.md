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

## 🧾 Data Cleaning — Quick Reference Guide

This quick reference provides the most common **Pandas methods** for detecting and handling missing data, fixing incorrect data types, and cleaning text or inconsistent values.

---

### 🧭 1. Detecting & Summarizing Missing Data

| Task | Command | Description |
|------|----------|-------------|
| Check missing values (boolean) | `df.isna()` | Returns `True` for missing entries |
| Count missing values per column | `df.isna().sum()` | Summarizes total NaNs by column |
| View dataset info | `df.info()` | Shows data types, non-null counts |
| Count all values (incl. NaN) | `df['col'].value_counts(dropna=False)` | Detects missing or rare values |
| Select rows with missing data | `df[df.isna().any(axis=1)]` | Filters only incomplete rows |

---

### 🧹 2. Handling Missing Data

| Task | Command | Description |
|------|----------|-------------|
| Drop rows with missing values | `df.dropna()` | Removes rows with any NaN |
| Drop only if all values are NaN | `df.dropna(how='all')` | Keeps partially filled rows |
| Drop rows missing specific column | `df.dropna(subset=['City'])` | Removes rows missing “City” |
| Keep rows without missing values | `df[df['City'].notna()]` | Filters complete data only |
| Fill missing values (impute) | `df['Grade'].fillna(df['Grade'].mean(), inplace=True)` | Replaces NaN with mean (or 0, median, etc.) |

---

### 🧠 3. Converting Data Types

| Task | Command | Description |
|------|----------|-------------|
| View data types | `df.dtypes` | Displays data type of each column |
| Convert to numeric | `pd.to_numeric(df['col'], errors='coerce')` | Converts to numeric, sets invalids to NaN |
| Convert to datetime | `pd.to_datetime(df['col'], format='%Y-%m-%d')` | Converts string dates to datetime |
| Convert data type explicitly | `df['col'].astype('float')` | Changes column to specific type |

---

### 🔡 4. Cleaning & Standardizing Text

| Task | Command | Description |
|------|----------|-------------|
| Convert to lowercase | `df['col'].str.lower()` | Standardizes text case |
| Remove extra spaces | `df['col'].str.strip()` | Cleans leading/trailing spaces |
| Replace substrings | `df['col'].str.replace('old', 'new', regex=False)` | Replaces incorrect values |
| Find inconsistent text | `df['col'].value_counts()` | Lists unique variations |
| Replace multiple values | `df['col'] = df['col'].map(mapping_dict)` | Maps incorrect to correct values |
| Conditional updates | `df['col'] = np.where(df['col'] == 'x', 'y', df['col'])` | Fix based on condition |

---

### 🧩 5. String & Pattern Utilities (Pandas `.str`)

| Task | Command | Description |
|------|----------|-------------|
| Get string length | `df['col'].str.len()` | Returns length of each string |
| Extract pattern | `df['col'].str.extract(r'(\d+)')` | Extracts digits (regex) |
| Check pattern presence | `df['col'].str.contains('pattern', case=False)` | Boolean mask for matching |
| Split into multiple columns | `df['col'].str.split('-', expand=True)` | Breaks strings by delimiter |
| Concatenate values | `df['col'].str.cat(sep=', ')` | Joins multiple string values |

---
























