## Table Content
- [What is Matplotlib?](#what-is-matplotlib)
- [Installation](#installation)
- [Basic Syntax and Usage](#basic-syntax-and-usage)
- [Key Components](#key-components)
- [Customizing Plots](#customizing-plots)

## What is Matplotlib?
1) Matplotlib is a Python 2D plotting library that makes it easy to create static, animated, and interactive visualizations.
2) It is widely used for data visualization and supports various chart types, including line charts, bar charts, scatter plots, histograms, and more.

## Installation
To start using Matplotlib, you need to install it using pip:
```bash
pip install matplotlib
```

## Basic Syntax and Usage
- Basic Example: Plotting a Line Graph
```python
import matplotlib.pyplot as plt

# Data
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

# Plot the data
plt.plot(x, y)

# Add title and labels
plt.title('Line Graph Example')
plt.xlabel('X-axis')
plt.ylabel('Y-axis')

# Show the plot
plt.show()
```

## Key Components
1) Figure: The overall window or page where the plot appears.
    - Example: plt.figure()
2) Axes: The area where the data is plotted (includes x and y axis)
    - Example: ax = plt.axes()
3) Plot: The actual drawing of data points (lines, bars, etc.).

0) this is an example using Figure and Axes This is like OBJ oriented Aproach rather than pyplot:
```python
import matplotlib.pyplot as plt
# Data
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

# Create a figure and a single axes
fig, ax = plt.subplots()

# Plot on the axes
ax.plot(x, y)

# Customize the plot using the axes
ax.set_title('OO API Line Graph')
ax.set_xlabel('X-axis')
ax.set_ylabel('Y-axis')

plt.show()
```



## Common Plot Types
- Line Plot
```python
plt.plot(x, y)
```

- Scatter Plot
```python
plt.scatter(x, y)
```

- Bar Plot
```python
plt.bar(x, y)
```

- Histogram
```python
plt.hist(data)
```

-Pie Example
```python
labels = ['A', 'B', 'C', 'D']
sizes = [15, 30, 45, 10]
plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=90)
plt.axis('equal')  # Equal aspect ratio ensures that pie is drawn as a circle.
plt.show()

```

- Example creating using bar plot you can use anything else too depending parameter etc
```python
import matplotlib.pyplot as plt

# Data
categories = ['A', 'B', 'C', 'D']
values = [4, 7, 1, 8]

# Bar Plot
plt.bar(categories, values)

# Customizations
plt.title('Bar Plot Example')
plt.xlabel('Categories')
plt.ylabel('Values')

# Show Plot
plt.show()
```

##  Customizing Plots
- Title and Labels
```python
plt.title('Title Here')
plt.xlabel('X-axis Label')
plt.ylabel('Y-axis Label')
```

- Gridlines
```python
plt.grid(True)
```

- Multiple Plots in One
```python
plt.subplot(2, 1, 1)  # First subplot (2 rows, 1 column, first plot)
plt.plot(x, y)
plt.subplot(2, 1, 2)  # Second subplot
plt.plot(x, [i ** 2 for i in x])
```

- Saving Figures You can save the figure to a file instead of displaying it.
```python
plt.savefig('plot.png')
```