
# Matplotlib
Fundamental plotting library in Python. Other libraries like Seaborn, Pandas plots, Plotly are built on top of it. Helps visualize trends, comparisons, distributions, time-series.

## Workflow 
1. Import matplotlib.pyplot.
2. Prepare data.
3. Choose chart type.
4. Plot.
5. Customize (optional).
6. Show or save the figure.


## Matplotlib has 2 ways to write code:

(A) Pyplot Style (Beginner-Friendly)

1. Uses plt state machine
2. Fast and easy
3. Good for small scripts & learning
```python
plt.plot(x, y)
plt.title("My Chart")
plt.xlabel("X")
plt.ylabel("Y")
plt.show()
```
(B) Object-Oriented Style (Professional)

1. Uses fig, ax = plt.subplots()
2. Recommended for dashboards, multiple plots, custom visuals
3. Good transition for intermediate learners
```python
fig, ax = plt.subplots()
ax.plot(x, y)
ax.set_title("My Chart")
plt.show()
```
---

## Matplotlib Syntax Table

| **Chart Type**        | **Matplotlib Syntax**                               | **What It Answers**              |
| --------------------- | --------------------------------------------------- | -------------------------------- |
| **Bar Chart**         | `plt.bar(x, y)`                                     | Compares categories               |
| **Horizontal Bar Chart**         | `plt.barh(x, y)`                                     | Compares categories               |
| **Line Chart**        | `plt.plot(x, y)`                                    | Trends over time                 |
| **Scatter Plot**      | `plt.scatter(x, y)`                                 | Relationship between 2 variables |
| **Pie Chart**         | `plt.pie(values, labels=labels, autopct='%1.1f%%')` | Part-to-whole composition        |
| **Histogram**         | `plt.hist(values)`                                  | Distribution of one variable     |
| **Box Plot**          | `plt.boxplot(values)`                               | Spread, outliers                 |
| **Area Chart**        | `plt.fill_between(x, y)`                            | Cumulative trends over time      |
| **Stacked Bar Chart** | `df.plot(kind='bar', stacked=True)`                 | Composition + comparison         |

## Customizations

### **Titles & Labels**

```python
plt.title("Sales Trend")
plt.xlabel("Month")
plt.ylabel("Revenue ($)")
```

### **Colors & Styles**

```python
plt.plot(x, y, color="red", linestyle="--", marker="o")
```

### **Figure Size**

```python
plt.figure(figsize=(8, 4))
```

### **Legend**

```python
plt.legend(["2024 Sales"])
```

## Subplots

```python
fig, ax = plt.subplots(1, 2, figsize=(10, 4))
ax[0].plot(x, y)
ax[1].bar(categories, values)
plt.show()
```

“`subplots` allows multiple charts inside one figure.”

---

## Common Errors 
1. Forgetting plt.show()
2. Wrong indentation
3. Mismatch of x & y lengths
4. Trying to plot strings without converting to datetime
5. Overusing pyplot instead of understanding figure/axis
