---
layout: post
title: Pcolor to show true data
date: 2017-09-21
categories: blog
tags: [python, matplotlib, pyplot, pcolor]
header-img: img/top.png    #这篇文章标题背景图片
---
```python
import numpy as np
import matplotlib.pyplot as plt

data = np.array([(1,3,5),(2,1,4),(5,9,0),(8,1,2)])

x = np.arange(3)
y = np.arange(4)
x,y = np.meshgrid(x,y)

plt.pcolor(x,y,data,vmin=0, vmax=9)

plt.xlim([-0.5,2.5])
plt.ylim([-0.5,3.5])
plt.xticks([0,1,2])
plt.yticks([0,1,2,3])

plt.show()
```

you will see the upper subplot.

That is not actually what the array shows. 

We need to "cheat" pcolor to make a right figure:

```python
import numpy as np
import matplotlib.pyplot as plt

#==================================

def conduct_xy_for_pcolor(x, y):
        
    dx = np.unique(np.diff(x*1E7))
    dy = np.unique(np.diff(y*1E7))
                
    if (dx.size>1 or dy.size>1):
            
        raise RuntimeError('Non-uniform dx/dy')
        
    lons_p1 = list(x) + [x[-1] + 1, ]
    lons_m1 = [x[0] - 1] + list(x)
    lons_corn = [(a + b) / 2.0 for a, b in zip(lons_p1, lons_m1) ]
        
    lats_p1 = list(y) + [y[-1] + 1, ]
    lats_m1 = [y[0] - 1] + list(y)
    lats_corn = [(a + b) / 2.0 for a, b in zip(lats_p1, lats_m1) ]
        
    return lons_corn, lats_corn

#==================================

data = np.array([(1,3,5),(2,1,4),(5,9,0),(8,1,2)])

x = np.arange(3)
y = np.arange(4)

x, y = conduct_xy_for_pcolor(x, y) # make new x & y, see the user-defined function

x,y = np.meshgrid(x,y)

plt.pcolor(x, y, data, vmin=0, vmax=9)

plt.xlim([-0.5,2.5])
plt.ylim([-0.5,3.5])
plt.xticks([0,1,2])
plt.yticks([0,1,2,3])

plt.show()
```

Then you can get the right result as bottom shows.

![Example Figure:](/img/pcolor_showing.png "Figure Showing")