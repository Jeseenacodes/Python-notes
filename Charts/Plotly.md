# Plotly 

Plotly is interactive and browser-based.

## Workflow 

| **Step**                    | **Description**                 | **Example / Notes**                               |
| --------------------------- | ------------------------------- | ------------------------------------------------- |
| **1. Import**               | Import Plotly Express           | `import plotly.express as px`                     |
| **2. Load Data**            | Load a dataset into a DataFrame | `df = px.data.tips()`                             |
| **3. Choose Chart Type**    | Select the chart function       | `px.bar`, `px.line`, `px.scatter`, `px.histogram` |
| **4. Plot**                 | Create the visualization        | `fig = px.bar(df, x="day", y="total_bill")`       |
| **5. Customize (Optional)** | Modify titles, colors, labels   | `fig.update_layout(title="Sales Chart")`          |
| **6. Show / Save**          | Display or export the figure    | `fig.show()`                                      |


## Customization

| **Customization** | **Purpose**                     | **Code Example**                                            |
| ----------------- | ------------------------------- | ----------------------------------------------------------- |
| **Title**         | Add a chart title               | `fig.update_layout(title="Sales by Day")`                   |
| **Axis Labels**   | Label x-axis and y-axis         | `fig.update_layout(xaxis_title="Day", yaxis_title="Sales")` |
| **Colors**        | Color bars/points by a category | `px.bar(df, x="day", y="total_bill", color="sex")`          |
| **Theme / Style** | Apply a Plotly theme            | `fig.update_layout(template="plotly_dark")`                 |
| **Figure Size**   | Adjust width and height         | `fig.update_layout(width=800, height=400)`                  |
| **Legend**        | Customize legend title          | `fig.update_layout(legend_title="Customer Type")`           |


## How to Code for Plotly

| **Chart Type**                  | **Purpose**                                     | **Plotly Code**                                        |
| ------------------------------- | ----------------------------------------------- | ------------------------------------------------------ |
| **Column Chart (Vertical Bar)** | Compare values across categories                | `px.bar(df, x="day", y="total_bill")`                  |
| **Horizontal Bar Chart**        | Compare values when category names are long     | `px.bar(df, x="total_bill", y="day", orientation="h")` |
| **Line Chart**                  | Show trends over time or continuous data        | `px.line(df, x="day", y="tip")`                        |
| **Scatter Plot**                | Show relationship between two numeric variables | `px.scatter(df, x="total_bill", y="tip")`              |
| **Histogram**                   | Show distribution of a single numeric variable  | `px.histogram(df, x="total_bill")`                     |
| **Box Plot**                    | Show spread, outliers, quartiles                | `px.box(df, x="day", y="tip")`                         |


## Common Errors

* Forgetting `fig.show()` → chart not displayed
* Using wrong column names
* Trying to use Matplotlib syntax in Plotly
* Passing lists instead of DataFrames
* Using `orientation='h'` incorrectly
* Not updating layout using `update_layout()`
* Mixing Plotly Express and Plotly Graph Objects

---
