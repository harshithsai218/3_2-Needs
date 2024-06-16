# Visualizing Data

## Visualizing Data: Bar Charts, Line Charts, and Scatterplots

### Bar Charts
**Description:** Bar charts represent categorical data with rectangular bars, where the length or height of each bar is proportional to the value it represents. They are used to compare different categories of data.

**Example:**
Suppose we have data on the number of products sold in different regions in a month.

| Region  | Products Sold |
|---------|---------------|
| North   | 150           |
| South   | 200           |
| East    | 180           |
| West    | 220           |

To visualize this data, a bar chart can be created where each bar's height represents the number of products sold in each region.

**Python Code:**
```python
import matplotlib.pyplot as plt

regions = ['North', 'South', 'East', 'West']
products_sold = [150, 200, 180, 220]

plt.bar(regions, products_sold, color='blue')
plt.xlabel('Region')
plt.ylabel('Products Sold')
plt.title('Products Sold in Different Regions')
plt.show()
```

![](img/2024-06-16-17-42-05.png)


### Line Charts
**Description:** Line charts display data points connected by straight lines. They are used to track changes over short and long periods.

**Example:**
Consider data showing the temperature changes over a week.

| Day       | Temperature (°C) |
|-----------|-------------------|
| Monday    | 20                |
| Tuesday   | 22                |
| Wednesday | 19                |
| Thursday  | 24                |
| Friday    | 23                |
| Saturday  | 25                |
| Sunday    | 22                |

A line chart can illustrate how the temperature changes throughout the week.

**Python Code:**
```python
import matplotlib.pyplot as plt

days = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
temperature = [20, 22, 19, 24, 23, 25, 22]

plt.plot(days, temperature, marker='o', color='red')
plt.xlabel('Days')
plt.ylabel('Temperature (°C)')
plt.title('Temperature Changes Over a Week')
plt.show()
```

![](img/2024-06-16-17-42-35.png)

### Scatterplots
**Description:** Scatterplots show the relationship between two variables using dots. Each dot represents an observation in the dataset.

**Example:**
Suppose we have data on the height and weight of individuals.

| Height (cm) | Weight (kg) |
|-------------|-------------|
| 150         | 50          |
| 160         | 60          |
| 170         | 70          |
| 180         | 80          |
| 190         | 90          |

A scatterplot can be used to visualize the correlation between height and weight.

**Python Code:**
```python
import matplotlib.pyplot as plt

height = [150, 160, 170, 180, 190]
weight = [50, 60, 70, 80, 90]

plt.scatter(height, weight, color='green')
plt.xlabel('Height (cm)')
plt.ylabel('Weight (kg)')
plt.title('Height vs Weight')
plt.show()
```

![](img/2024-06-16-17-42-59.png)

<details>

<summary>Other Types of Charts</summary>

## Other Types of Charts


pie charts
```python
products_sold = [150, 200, 180, 220]
regions = ['North', 'South', 'East', 'West']
plt.pie(products_sold, labels=regions, autopct='%1.1f%%')
```

histograms
```python
temperature = [20, 22, 19, 24, 23, 25, 22]
plt.hist(temperature, bins=5)
```

box plots
```python
temperature = [20, 22, 19, 24, 23, 25, 22]
plt.boxplot(temperature)
```

</details>


