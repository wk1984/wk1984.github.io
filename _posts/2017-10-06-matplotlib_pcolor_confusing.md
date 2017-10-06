---
layout: post
title: Pcolor to show true data
date: 2017-10-06
categories: blog
tags: [python, matplotlib, pyplot, pcolor]
header-img: img/top.png    #这篇文章标题背景图片
---
```python
import numpy as np
import matplotlib.pyplot as plt

data = np.array([(1,3,5),(2,1,4),(5,9,0),(8,1,2)])
data_str = np.array(data, dtype=str)

x = np.arange(3)
y = np.arange(4)

for i,temp in enumerate(x):
    for j,dump in enumerate(y):
        
        plt.text(x[i],y[j],data_str[j,i])
        
x,y = np.meshgrid(x,y)

cmap = plt.colormaps()

plt.pcolor(x,y,data, vmin=-0.5, vmax=9.5,cmap=plt.cm.get_cmap('tab10'))

plt.colorbar(ticks=np.arange(0,10))

plt.xlim([-0.5,2.5])
plt.ylim([-0.5,3.5])
plt.xticks([0,1,2])
plt.yticks([0,1,2,3])

plt.show()
```

you will see:

![Example Figure 1:](/img/pcolor_showing1.png "Figure 1")

That is not actually what the array shows. In other words, the colors are not consistent with the number in array.

Thus, we need to "cheat" pcolor to make a right figure:

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
data_str = np.array(data, dtype=str)

x = np.arange(3)
y = np.arange(4)

for i,temp in enumerate(x):
    for j,dump in enumerate(y):
        
        plt.text(x[i],y[j],data_str[j,i])
        
x, y = conduct_xy_for_pcolor(x, y) # make new x & y, see the user-defined function
        
x,y = np.meshgrid(x,y)

cmap = plt.colormaps()

plt.pcolor(x,y,data, vmin=-0.5, vmax=9.5,cmap=plt.cm.get_cmap('tab10'))

plt.colorbar(ticks=np.arange(0,10))

plt.xlim([-0.5,2.5])
plt.ylim([-0.5,3.5])
plt.xticks([0,1,2])
plt.yticks([0,1,2,3])

plt.show()
```

Then you can get the right result:

![Example Figure 2:](/img/pcolor_showing2.png "Figure 2")