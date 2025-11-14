
# Data Visualization

4 major purposes of data visualization: Comparison, Composition, Time Series, Distribution.

| **Purpose**      | **Meaning**                                   | **Example Charts**                                                          | **What They Answer**                                                                                                                     |
| ---------------- | --------------------------------------------- | --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Comparison**   | Compare values between categories or groups   | Bar Chart, Column Chart, Line (multi), Scatter, Dot Plot                    | - Which category is highest? <br> - Which groups differ? <br> - Who performs better or worse?                                          |
| **Composition**  | Show how a whole is divided into parts        | Pie, Donut, Treemap, Sunburst, Stacked Bar, 100% Stacked Bar                | - What % does each part contribute? <br> - How does composition change?<br> - What is the breakdown of categories?                    |
| **Time Series**  | Show change over time                         | Line Chart, Area Chart, Stacked Area, Time-Series Scatter, Calendar Heatmap | - How does this metric change over time? <br> - Are there trends or seasonality? <br> - When are peaks or dips?                        |
| **Distribution** | Show how data is spread, shaped, or clustered | Histogram, Box Plot, Violin Plot, KDE Plot, Hexbin Plot                     | - What values are most common? <br> - Are there outliers? <br> - Is the data skewed or symmetric? <br> - Where are the dense clusters? |


## Charts

| **Chart Type**        | **What It Shows**                        | **When to Use**                   | **Example Insight**                     |
| --------------------- | ---------------------------------------- | --------------------------------- | --------------------------------------- |
| **Bar Chart**         | Compares category values                 | Ranking, comparing groups         | "Product A sells the most."             |
| **Line Chart**        | Trend over time                          | Time-series, growth/decline       | "Sales rise in December."               |
| **Scatter Plot**      | Relationship between 2 numeric variables | Correlation, detecting patterns   | "More ads → more sales."                |
| **Pie Chart**         | Parts of a whole (%)                     | Simple proportions                | "40% customers prefer A."               |
| **Histogram**         | Distribution of 1 numeric variable       | Data shape, skewness              | "Most customers are 25–35."             |
| **Box Plot**          | Spread + outliers                        | Compare distributions             | "Branch B has more variation."          |
| **Violin Plot**       | Distribution + density shape             | Detailed distribution compare     | "Group A has two peaks."                |
| **Heatmap**           | Color-based intensity matrix             | Correlation, category vs category | "Strong correlation between X and Y."   |
| **Pair Plot**         | All variable relationships               | Exploratory data analysis (EDA)   | "Height & weight strongly related."     |
| **Count Plot**        | Frequency of categories                  | Class imbalance, category count   | "Blue cars occur most often."           |
| **Area Chart**        | Filled trend over time                   | Volume, cumulative patterns       | "Traffic grows yearly."                 |
| **Stacked Bar Chart** | Parts-of-whole by group                  | Subcategories in categories       | "Returning customers drive most sales." |

---

| **Advanced Charts**                        | **What It Shows / Why It’s Useful**          | **Typical Use Case**                                           |
| ----------------------------------------- | -------------------------------------------- | -------------------------------------------------------------- |
| **Facet/Grid Plots (FacetGrid, catplot)** | Multiple mini-charts split by category       | Compare trends across segments (e.g., sales by region & month) |
| **Joint Plot**                            | Scatter + distribution in one view           | Relationship + density of two variables                        |
| **Regression Plot (regplot, lmplot)**     | Trend line + confidence band                 | Regression analysis, forecasting insight                       |
| **Swarm Plot**                            | All individual data points (non-overlapping) | Detailed look at distribution per category                     |
| **Hexbin Plot**                           | Density of scatter points for large datasets | Visualizing millions of points                                 |
| **2D KDE Plot**                           | Smooth density contours for two variables    | Advanced distribution analysis                                 |
| **Annotated Charts**                      | Highlights, labels, callouts                 | Storytelling dashboards, presentations                         |
| **Dual-Axis Chart**                       | Two different scales on one graph            | Compare unrelated metrics (e.g., sales vs temperature)         |
| **Stacked Area Chart**                    | Category trend over time                     | Contribution changes over time                                 |
| **Bubble Chart**                          | Scatter + bubble size (3rd variable)         | Multi-variable insights (e.g., sales vs margin vs revenue)     |
| **Treemap**                               | Hierarchical % breakdown                     | Market share distribution                                      |
| **Sunburst Chart**                        | Multi-level hierarchical breakdown           | Customer family → category → product patterns                  |
| **Radar/Spider Chart**                    | Multi-metric comparison                      | Comparing features, scores, or performance                     |
| **Animated Charts**                       | Time-evolving visuals                        | Storytelling (e.g., sales-over-time animation)                 |
| **Interactive Plots (Plotly)**            | Hover, zoom, filters                         | Dashboards, web apps                                           |
| **Geospatial Maps**                       | Data tied to locations                       | Choropleth maps, heatmaps, GPS data                            |

---

## Matplotlib vs Seaborn vs Plotly — Syntax Summary

| **Chart Type**   | **Matplotlib**                      | **Seaborn**                        | **Plotly (Express)**                     |
| ---------------- | ----------------------------------- | ---------------------------------- | ---------------------------------------- |
| **Bar Chart**    | `plt.bar(x, y)`                     | `sns.barplot(x=, y=, data=df)`     | `px.bar(df, x=, y=)`                     |
| **Line Chart**   | `plt.plot(x, y)`                    | `sns.lineplot(x=, y=, data=df)`    | `px.line(df, x=, y=)`                    |
| **Scatter Plot** | `plt.scatter(x, y)`                 | `sns.scatterplot(x=, y=, data=df)` | `px.scatter(df, x=, y=)`                 |
| **Pie Chart**    | `plt.pie(values)`                   | ❌ (no direct)                      | `px.pie(df, values=, names=)`            |
| **Histogram**    | `plt.hist(values)`                  | `sns.histplot(values, bins=)`      | `px.histogram(df, x=)`                   |
| **Box Plot**     | `plt.boxplot(values)`               | `sns.boxplot(x=, y=, data=df)`     | `px.box(df, x=, y=)`                     |
| **Violin Plot**  | ❌ (complex manual)                  | `sns.violinplot(x=, y=, data=df)`  | `px.violin(df, x=, y=)`                  |
| **Heatmap**      | `plt.imshow(matrix)`                | `sns.heatmap(df, annot=True)`      | `px.imshow(df)`                          |
| **Area Chart**   | `plt.fill_between(x, y)`            | ❌                                  | `px.area(df, x=, y=)`                    |
| **Pair Plot**    | ❌                                   | `sns.pairplot(df)`                 | `px.scatter_matrix(df)`                  |
| **Count Plot**   | ❌                                   | `sns.countplot(x=, data=df)`       | `px.bar(df, x=, y=None)` *(auto counts)* |
| **Stacked Bar**  | `df.plot(kind='bar', stacked=True)` | ❌                                  | `px.bar(df, x=, y=, color=)`             |

## Summary

* **Matplotlib →** Low-level → write more code → full control
* **Seaborn →** High-level → fewer lines → statistical charts
* **Plotly →** Interactive → beautiful dashboards → simplest syntax

