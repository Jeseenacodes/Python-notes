## Data Gathering

The goal of **data gathering** is to **find, read, and store** data in a format ready for analysis — typically a **Pandas DataFrame**. Python is ideal for this because it can handle data from a wide range of sources: local files, databases, and web-based APIs.

---

### Data Gathering Process

| Step | Description |
|------|--------------|
| **1️⃣ Find** | Locate data from local files, databases, or web sources. |
| **2️⃣ Read** | Load the data into Python using Pandas. |
| **3️⃣ Store** | Save it as a DataFrame for analysis and transformation. |

---

### Data Sources

| Type | Examples | Description |
|------|-----------|-------------|
| **Structured** | Excel, SQL | Already in table format (rows & columns). |
| **Semi-Structured** | CSV, JSON | Easily converted into tabular form. |
| **Unstructured** | PDF, JPG | Requires transformation before analysis. |

>  To perform analysis, data must be **structured as rows and columns**.

---

### 🧾 Reading Files into Python

Use **Pandas** to read different file types into a DataFrame (`df`):

```python
import pandas as pd

# CSV file
df = pd.read_csv("data.csv", sep=",", header="infer")

# Excel file
df = pd.read_excel("data.xlsx", sheet_name=0)

# JSON file
df = pd.read_json("data.json")
```
---

### 🧾 Common File Types & Functions

| File Type | Pandas Function | Example |
|------------|----------------|----------|
| **CSV (Comma-Separated Values)** | `pd.read_csv()` | `df = pd.read_csv("data.csv")` |
| **Excel (XLSX / XLS)** | `pd.read_excel()` | `df = pd.read_excel("data.xlsx", sheet_name="Sheet1")` |
| **JSON (JavaScript Object Notation)** | `pd.read_json()` | `df = pd.read_json("data.json")` |
| **Text Files (Delimited)** | `pd.read_csv()` | `df = pd.read_csv("data.txt", sep="\t")` |
| **SQL Databases** | `pd.read_sql()` | `df = pd.read_sql("SELECT * FROM table", conn)` |
| **HTML Tables** | `pd.read_html()` | `df_list = pd.read_html("https://example.com/table.html")` |
| **Parquet Files** | `pd.read_parquet()` | `df = pd.read_parquet("data.parquet")` |
| **Pickle Files** | `pd.read_pickle()` | `df = pd.read_pickle("data.pkl")` |
| **Clipboard (copy-paste)** | `pd.read_clipboard()` | `df = pd.read_clipboard()` |

---

### ⚙️ Key Parameters for `pd.read_csv()`

```python
pd.read_csv(
    filepath_or_buffer,   # File path or URL
    sep=',',              # Field separator (e.g., '\t' for tab)
    header='infer',       # Row number to use as column names
    names=None,           # Custom column names
    index_col=None,       # Set a column as index
    usecols=None,         # Read specific columns
    dtype=None,           # Set column data types
    na_values=None,       # Define missing value markers
    parse_dates=False     # Automatically parse dates
)
``` 
