
## Plotting Graphs with Pandas

Pandas has built-in plotting capabilities powered by **Matplotlib**, allowing quick and simple data visualization directly from DataFrames and Series.

---

### Enabling Plotting

First, make sure you have **Matplotlib** installed:

```bash
pip install matplotlib
import pandas as pd
import matplotlib.pyplot as plt
```
---

#### Common Plot Types in Pandas

| Plot Type               | Method                      | Description                              | Example                                         |
| ----------------------- | --------------------------- | ---------------------------------------- | ----------------------------------------------- |
| **Line Plot**           | `.plot()` or `.plot.line()` | Shows trends over time                   | `df.plot(x='Date', y='Sales')`                  |
| **Bar Plot**            | `.plot.bar()`               | Compares values across categories        | `df.plot.bar(x='Category', y='Revenue')`        |
| **Horizontal Bar Plot** | `.plot.barh()`              | Horizontal version of bar plot           | `df.plot.barh(x='Category', y='Revenue')`       |
| **Histogram**           | `.plot.hist()`              | Displays frequency distribution          | `df['Age'].plot.hist(bins=20)`                  |
| **Box Plot**            | `.plot.box()`               | Shows spread and outliers                | `df.plot.box()`                                 |
| **Area Plot**           | `.plot.area()`              | Displays cumulative totals               | `df.plot.area(alpha=0.5)`                       |
| **Pie Chart**           | `.plot.pie()`               | Shows proportions                        | `df['MarketShare'].plot.pie(autopct='%1.1f%%')` |
| **Scatter Plot**        | `.plot.scatter()`           | Displays relationships between variables | `df.plot.scatter(x='Height', y='Weight')`       |
| **Density Plot**        | `.plot.kde()`               | Smooth distribution curve                | `df['Price'].plot.kde()`                        |

```python
df.plot(kind='bar', color='skyblue', figsize=(8, 5), title='Sales by Category')
plt.xlabel('Category')
plt.ylabel('Sales')
plt.grid(True)
plt.show()
```
##### Common customization options:
- color= → set colors
- figsize= → control figure size
- title= → add chart title
- grid= → toggle grid lines
--- 

```python
# Multiple Columns Example 
df[['Sales', 'Profit']].plot(kind='line', figsize=(8,5), title='Sales & Profit Over Time')
plt.show()
```
---
#### Tips
- Use .plot(subplots=True) to show multiple charts at once.
- Combine Pandas plotting with Seaborn for advanced styling.
```python
# For inline charts in Jupyter Notebook 
%matplotlib inline
```
