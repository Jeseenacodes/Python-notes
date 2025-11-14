
# Seaborn
1. Built on top of Matplotlib which gives clean visuals, built-in themes, charts desgined for statistical analysis.

=> Seaborn = Matplotlib with style & smarter defaults.

| **Step**                 | **Description**                                         | **Example / Notes**                                                      |
| ------------------------ | ------------------------------------------------------- | ------------------------------------------------------------------------ |
| **1. Import**            | Import Seaborn                                          | `import seaborn as sns`                                                  |
| **2. Load Data**         | Use a DataFrame                                         | `df = sns.load_dataset('tips')`                                          |
| **3. Choose Chart Type** | Use seaborn functions                                   | `sns.barplot()`, `sns.lineplot()`, `sns.scatterplot()`, `sns.histplot()` |
| **4. Plot**              | Pass x, y, data                                         | `sns.barplot(x="day", y="total_bill", data=df)`                          |
| **5. Customize**         | Titles with Matplotlib (`plt.title()`), palette, labels | `sns.set_style("whitegrid")`                                             |
| **6. Show**              | Render chart                                            | `plt.show()`                                                             |

## Customizations

### **Titles & Labels**

```python
# Matplotlib controls titles even while using Seaborn:

plt.title("Sales Trend")
plt.xlabel("Month")
plt.ylabel("Revenue ($)")
```

### Colors
```python
# Single color
sns.barplot(x="day", y="total_bill", data=tips, color="skyblue")
```

```python
# Color by category (`hue`)
sns.scatterplot(x="total_bill", y="tip", hue="sex", data=tips)
```

### Style Themes

```python
sns.set_theme(style="whitegrid")      `"darkgrid"`, `"white"`, `"dark"`
```

### Figure Size

Use Matplotlib:

```python
plt.figure(figsize=(8, 5))
sns.barplot(x="day", y="total_bill", data=tips)
plt.show()
```

### Legends

Seaborn automatically creates legends when using `hue`, `style`, or `size`.

```python
# Add or customize:

plt.legend(title="Customer Type")
```
---
# How to Code for Seaborn

| **Chart Type**   | **Seaborn Syntax**                      | **What It Answers**               |
| ---------------- | --------------------------------------- | --------------------------------- |
| **Bar Chart**    | `sns.barplot(x=, y=, data=df)`          | Compare categories                |
| **Line Chart**   | `sns.lineplot(x=, y=, data=df)`         | Trends over time                  |
| **Scatter Plot** | `sns.scatterplot(x=, y=, data=df)`      | Relationship between 2 variables  |
| **Histogram**    | `sns.histplot(values, bins=, kde=True)` | Distribution of one variable      |
| **Box Plot**     | `sns.boxplot(y=, data=df)`              | Spread, outliers                  |
| **Violin Plot**  | `sns.violinplot(y=, data=df)`           | Distribution + density            |
| **Heatmap**      | `sns.heatmap(df, annot=True)`           | Correlation, comparison via color |
| **Pair Plot**    | `sns.pairplot(df)`                      | Multi-variable relationships      |
| **Count Plot**   | `sns.countplot(x=, data=df)`            | Frequency of categories           |
---
## Common Errors 

| **Error**                                                    | **Why It Happens**                     | **Fix**                                           |
| ------------------------------------------------------------ | -------------------------------------- | ------------------------------------------------- |
| Forgetting `plt.show()`                                   | Plot doesn’t appear                    | Always end with `plt.show()`                      |
| Using non-existent column names                            | Spelling or capitalization mismatch    | Check DataFrame columns exactly (`df.columns`)    |
| Passing lists to `data=`                                   | `data=` only accepts DataFrames        | Use `x="colname", y="colname", data=df`           |
| Using numeric `hue` with too many unique values            | Creates unreadable color gradients     | Convert to category or use binning                |
| Using wrong chart type (`countplot` vs `barplot`)         | Confusing count vs aggregation         | `countplot` = counts; `barplot` = mean of numeric |
| Data types not cleaned                                    | Strings in numeric columns, NaN values | Convert types and drop NA                         |
| Forgetting to import Matplotlib                            | Some customizations need Matplotlib    | `import matplotlib.pyplot as plt`                 |
| Using Seaborn plot inside a Matplotlib figure incorrectly | Wrong use of axes                      | Use: `sns.barplot(..., ax=ax)`                    |
| Incorrect order of variables (x/y flipped)                 | Wrong axes orientation                 | Flip x and y for horizontal charts                |
| Misunderstanding default behavior of `barplot`            | It calculates the mean, not sum        | Use `estimator=sum` to change behavior            |
