## Pandas

参考
[Dataquest | Exploratory Data Visualization](https://app.dataquest.io/course/exploratory-data-visualization)

### Line Charts
```py
import matplotlib.pyplot as plt
# Generate an empty plot
plt.plot() 

# plt will maintain and update plot internally 
# show() will display the plot and internal state will be destroyed
plt.show() 

# Generating a line chart
plt.plot(x_values, y_values)

# Set x-axis 
plt.xticks(*args, **kwargs)
plt.xticks(rotation=90) # rotate 90

# Set label and title
plt.xlabel('xlabel')
plt.ylabel('ylabel')
plt.title('title')
```

### Multiple plots
```py
# Create a figure which can be considered as container for plots
fig = plt.figure()

# Add a new subplot to an existing figure, return an Axes object(a plot)
axes_obj = fig.add_subplot(nrows, ncols, plot_number)

# 



```