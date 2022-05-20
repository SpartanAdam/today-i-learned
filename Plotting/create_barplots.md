# Create a barplot

Creating singular barplots can be done via `plt.bar`, but you can also combine two or more charts together to layout bars next to each other, like so:

```python
import matplotlib.pyplot as plt
import numpy as np

fig, ax = plt.subplots(figsize=(15,6))

labels = ['College 1', 'College 2', 'College 3', 'College 4',' College 5']
means = [80, 70, 64, 78, 81]
py_means = [90, 56, 81, 80, 90]

x = np.arange(len(labels))  # the label locations
width = 0.35

rects1 = plt.bar(x - width / 2,
        means,
        width=width,
        edgecolor='black',
        color='#FF8A4A',
        label='2022')

rects2 = plt.bar(x + width / 2,
        py_means,
        width=width,
        edgecolor='black',
        color='#FFC000',
        label='2021')

# Add bar labels
def autolabel(rects):
    """Attach a text label above each bar in *rects*, displaying its height."""
    for rect in rects:
        height = rect.get_height()
        ax.annotate('{}'.format(height),
                    xy=(rect.get_x() + rect.get_width() / 2, height),
                    xytext=(0, 3),  # 3 points vertical offset
                    textcoords="offset points",
                    ha='center', va='bottom')

# Apply the function
autolabel(rects1)
autolabel(rects2)

# Additional formatting with titles, labels etc
ax.set_ylabel('Overall Satisfaction')
ax.set_xticks(x)
ax.set_xticklabels(labels, rotation=90)
ax.set_yticks(np.arange(0, 101, 10))
ax.legend(loc='center left', bbox_to_anchor=(1, 0.5), ncol=1, fancybox=True)
plt.tight_layout()
plt.show()
```

![Barplot example](/graph_examples/barplots.png)