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

























