# Characteristics
- Pyplot has procedure interface
- Pyplot bases on Matplotlib object

# Line Plots
```
import matplotlib.pyplot as plt
x = [0, 0.5, 1, 1.5, 2, 2.5, 3]
y = [0, 0.25, 1, 2.25, 4, 6.25, 9]
plt.plot(x, y)
plt.show() # without plt.show(), it shows the Matplotlib object
```

# Scatter Plots
```
import matplotlib.pyplot as plt
x = [0, 0.5, 1, 1.5, 2, 2.5, 3]
y = [0, 0.25, 1, 2.25, 4, 6.25, 9]
plt.scatter(x, y, color='m')
plt.show()
```

# Customzing Plots

## Markers
- ^  v  .  o  +  x  D(Diamond)  s(Square)  * 
```
import matplotlib.pyplot as plt
x = [0, 0.5, 1, 1.5, 2, 2.5, 3]
y = [0, 0.25, 1, 2.25, 4, 6.25, 9]
plt.plot(x, y, '^')
plt.show()
```

## Colors
- b  g  r  y  k (black)  w  c(cyan)  m(magenta) <br>
- tab:blue tab:orange tab:green tab:red tab:purple tab:brown tab:pink tab:gray tab:olive tab:cyan
```
import matplotlib.pyplot as plt
x = [0, 0.5, 1, 1.5, 2, 2.5, 3]
y = [0, 0.25, 1, 2.25, 4, 6.25, 9]
plt.plot(x, y, color='tab:cyan')
plt.show()
```

## Line Styles and Widths
- linestyle ls : --(dashed) -(solid) :(dotted) -.(dash-dot)
- linewidth lw
```
import matplotlib.pyplot as plt
x = [0, 0.5, 1, 1.5, 2, 2.5, 3]
y = [0, 0.25, 1, 2.25, 4, 6.25, 9]
plt.plot(x, y, ls=':', lw=3)
plt.show()
```

## Combination
- For one line
```
import matplotlib.pyplot as plt
x = [0, 0.5, 1, 1.5, 2, 2.5, 3]
y = [0, 0.25, 1, 2.25, 4, 6.25, 9]
plt.plot(x, y, 'r:^')
plt.show()
```
- For multiple lines
```
import matplotlib.pyplot as plt
x = [0, 0.5, 1, 1.5, 2, 2.5, 3]
y1 = [0, 0.25, 1, 2.25, 4, 6.25, 9]
y2 = [1, 4, -7, 9, 8, 9, 20]
plt.plot(x, y1, 'r:^', x, y2, 'c--o')
plt.show()
```

# Plot Legends, Title, Axis Labels, Limits

## Legends
- 'best'=0 'upper right'=1 'upper left'=2 'lower left'=3 'lower right'=4 'right'=5
- 'center left'=6 'center right'=7 'lower center'=8 'upper center'=9 'center'=10
```
import matplotlib.pyplot as plt
x = [0, 0.5, 1, 1.5, 2, 2.5, 3]
y = [0, 0.25, 1, 2.25, 4, 6.25, 9]
plt.plot(x, y, label='a line')
plt.legend(loc=0)
plt.show()
```

## Title
```
import matplotlib.pyplot as plt
x = [0, 0.5, 1, 1.5, 2, 2.5, 3]
y = [0, 0.25, 1, 2.25, 4, 6.25, 9]
plt.plot(x, y, label='a line')
plt.title('A Line')
plt.show()
```

## Axis Labels
```
import matplotlib.pyplot as plt
x = [0, 0.5, 1, 1.5, 2, 2.5, 3]
y = [0, 0.25, 1, 2.25, 4, 6.25, 9]
plt.plot(x, y)
plt.xlabel('x axis')
plt.ylabel('y axis')
plt.show()
```

## Limits
```
import matplotlib.pyplot as plt
x = [0, 0.5, 1, 1.5, 2, 2.5, 3]
y = [0, 0.25, 1, 2.25, 4, 6.25, 9]
plt.plot(x, y)
plt.xlim(1, 2)
plt.ylim(2, 4)
plt.show()
```

## LaTex
```
import matplotlib.pyplot as plt
x = [0, 0.5, 1, 1.5, 2, 2.5, 3]
y = [0, 0.25, 1, 2.25, 4, 6.25, 9]
plt.rc('text', usetex=True)
plt.plot(x, y, label=r'A line with $x^{} and \sqrt y^{}$'.format(1, 2)) # r is raw for avoiding Python recognize \ in $ $
plt.legend(loc='lower center')
plt.show()
```

# Histogram
```
import numpy as np
import matplotlib.pyplot as plt
data = np.random.randn(1000)
plt.hist(data, bins=5, density=True) # bins=10, density=False are default
plt.show()
``` 

# Customizing Histogram

## Color, Edgecolor, Linewidth
- tab:color cannot be applied
```
import numpy as np
import matplotlib.pyplot as plt
data = np.random.randn(1000)
plt.hist(data, color='k', edgecolor='y', lw=5)
plt.show()
```

## Alpha, Hatch
- Alpha set the transparency of the bars from 0 to 1.
- Hatch set the fill pattern. / | x + o O *
```
import numpy as np
import matplotlib.pyplot as plt
data = np.random.randn(1000)
plt.hist(data, alpha=0.3, hatch='*')
plt.show()
```

# Histogram Legend, Title, Label, Grid, Limit, Tick, Scale

## Legend, Title, Label
```
import numpy as np
import matplotlib.pyplot as plt
data = np.random.randn(1000)
plt.hist(data, bins=5, density=True, label='Random Numbers')
plt.legend(loc='best')
plt.title('A Histogram')
plt.xlabel('x axis')
plt.ylabel('y axis')
plt.show()
```

## Grid
- configuring the grid lines
- argument: axis can get x or y, linestyle, color (tab:color cannot be applied)
```
import numpy as np
import matplotlib.pyplot as plt
data = np.random.randn(1000)
plt.hist(data, bins=5, density=True)
plt.grid(axis='x', linestyle='-.', color='g')
plt.show()
```

## Limit
```
import numpy as np
import matplotlib.pyplot as plt
data = np.random.randn(1000)
plt.hist(data, bins=5, density=True)
plt.xlim(-2, 2)
plt.ylim(0, 0.2)
plt.show()
```

## Ticks
- setting tick locations
```
import numpy as np
import matplotlib.pyplot as plt
data = np.random.randn(1000)
plt.hist(data, bins=5, density=True)
plt.xticks(range(5))
plt.yticks([0, 0.1, 0.3, 0.5])
plt.show()
```

## Scale
- setting the scaling of y-axis
- scale type: linear, log, logit, symlog
```
import numpy as np
import matplotlib.pyplot as plt
data = np.random.randn(1000)
plt.hist(data, bins=5, density=True)
plt.yscale('log')
plt.show()
```

# Multiple Axes
- setting two y-axes for one x-axis
```
# creating data
years = range(2000, 2005)
rate1 = [5, 4.3, 3.7, 4.6, 5.2]
rate2 = [25.3, 28.9, 35.3, 12.1, 47.5]
# plotting rate1
line1 = plt.plot(years, rate1, 'k-.*', label='rate 1')
plt.ylabel('rate 1')
# requesting multiple axes
plt.twinx()
# plotting rate2
line2 = plt.plot(years, rate2, 'y:^', label='rate 2')
plt.ylabel('rate 2')
# combination
lines = line1 + line2
labels = [line1[0].get_label(), line2[0].get_label()]
#    for line in lines: # from the book
#        labels.append(line.get_label()) 
# showing
plt.legend(lines, labels)
plt.show()
```
