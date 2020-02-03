---
title: "Seaborn使用(2)：Choosing color palettes"
date: 2017-08-14T18:44:30+08:00
draft: false
tags: 
   - Python
   - Seaborn
   - 数据可视化
categories:
  - 归档
---
# 调色板
颜色很重要，如果使用的好，就会帮助你突出数据的特征。

* color_palette()能传入任何Matplotlib所支持的颜色
* color_palette()不写参数则默认颜色
* set_palette()设置所有图的颜色

下面是使用seaborn的color palettes的一些例子，这些例子官网上面都已经有详细的介绍。

网址为：http://seaborn.pydata.org/tutorial/color_palettes.html#palette-tutorial

<!--more-->

```python
%matplotlib inline
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
```


```python
sns.set(rc={"figure.figsize": (6, 6)})
np.random.seed(sum(map(ord, "palettes")))
```


```python
current_palette = sns.color_palette()
sns.palplot(current_palette)
```


![png](../output_3_0.png)



```python
sns.palplot(sns.color_palette("hls", 8))
```


![png](../output_4_0.png)



```python
data = np.random.normal(size=(20, 8)) + np.arange(8) / 2
sns.boxplot(data=data, palette=sns.color_palette("hls", 8))
```




    <matplotlib.axes._subplots.AxesSubplot at 0xb1a9b70>




![png](../output_5_1.png)



```python
sns.palplot(sns.husl_palette(8))
```


![png](../output_6_0.png)



```python
# l- lightness
# s- saturation 
sns.palplot(sns.hls_palette(8, l=.3, s=.8))
```


![png](../output_7_0.png)



```python
sns.palplot(sns.color_palette("Paired", 10))
```


![png](../output_8_0.png)



```python
sns.palplot(sns.color_palette("Set2", 10))
```


![png](../output_9_0.png)



```python
sns.palplot(sns.color_palette("deep"))
sns.palplot(sns.color_palette("muted"))
sns.palplot(sns.color_palette("pastel"))
sns.palplot(sns.color_palette("bright"))
sns.palplot(sns.color_palette("dark"))
sns.palplot(sns.color_palette("colorblind"))

# print(help(sns.color_palette))
```

    Help on function palplot in module seaborn.miscplot:
    
    palplot(pal, size=1)
        Plot the values in a color palette as a horizontal array.
        
        Parameters
        ----------
        pal : sequence of matplotlib colors
            colors, i.e. as returned by seaborn.color_palette()
        size :
            scaling factor for size of plot
    
    None
    


![png](../output_10_1.png)



![png](../output_10_2.png)



![png](../output_10_3.png)



![png](../output_10_4.png)



![png](../output_10_5.png)



![png](../output_10_6.png)



```python
flatui = ["#9b59b6", "#3498db", "#95a5a6", "#e74c3c", "#34495e", "#2ecc71"]
sns.palplot(sns.color_palette(flatui))
```


![png](../output_11_0.png)



```python
plt.plot([0, 1], [0, 1], sns.xkcd_rgb["pale red"], lw=3)
plt.plot([0, 1], [0, 2], sns.xkcd_rgb["medium green"], lw=3)
plt.plot([0, 1], [0, 3], sns.xkcd_rgb["denim blue"], lw=3);
```


![png](../output_12_0.png)



```python
colors = ["windows blue", "amber", "greyish", "faded green", "dusty purple"]
sns.palplot(sns.xkcd_palette(colors))
```


![png](../output_13_0.png)



```python
sns.palplot(sns.color_palette("Blues"))
```


![png](../output_14_0.png)



```python
sns.palplot(sns.color_palette("BuGn_r"))
```


![png](../output_15_0.png)



```python
x, y = np.random.multivariate_normal([0, 0], [[1, -.5], [-.5, 1]], size=300).T
cmap = sns.cubehelix_palette(light=1, as_cmap=True)
sns.kdeplot(x, y, cmap=cmap, shade=True);
```


![png](../output_16_0.png)



```python
sns.choose_cubehelix_palette()
```


![png](../output_17_0.png)



```python
sns.palplot(sns.light_palette("green"))
```


![png](../output_18_0.png)



```python
sns.palplot(sns.dark_palette("purple"))
```


![png](../output_19_0.png)



```python
sns.palplot(sns.color_palette("RdBu_r", 7))
```


![png](../output_20_0.png)



```python
sns.palplot(sns.diverging_palette(220, 20, n=7))
```


![png](../output_21_0.png)



```python
def sinplot(flip=1):
    x = np.linspace(0, 14, 100)
    for i in range(1, 7):
        plt.plot(x, np.sin(x + i * .5) * (7 - i) * flip)
```


```python
sns.set_palette("husl")
sinplot()
```


![png](../output_23_0.png)


