---
title: "Seaborn使用(1)：Controlling figure aesthetics"
date: 2017-08-09T22:44:30+08:00
draft: false
tags: 
   - Python
   - Seaborn
   - 数据可视化
categories:
  - 归档
---
# 风格设置
Drawing attractive figures is important. When making figures for yourself, as you explore a dataset, it’s nice to have plots that are pleasant to look at. Visualizations are also central to communicating quantitative insights to an audience, and in that setting it’s even more necessary to have figures that catch the attention and draw a viewer in.

<!--more-->

Matplotlib is highly customizable, but it can be hard to know what settings to tweak to achieve an attractive plot. Seaborn comes with a number of customized themes and a high-level interface for controlling the look of matplotlib figures.

### Controlling figure aesthetics:
1. Seaborn figure styles
2. Removing axes spines
3. Temporarily setting figure style
4. Overriding elements of the seaborn styles
5. Scaling plot elements



### Seaborn figure styles


```python
#%matplotlib inline
import numpy as np
import matplotlib as mpl
import matplotlib.pyplot as plt
import seaborn as sns
np.random.seed(sum(map(ord, "aesthetics")))
```


```python
def sinplot(flip=1):
    x = np.linspace(0, 14, 100)
    for i in range(1, 7):
        plt.plot(x, np.sin(x + i * .5) * (7 - i) * flip)
```


```python
sinplot()
```


![png](../output_4_0.png)


### To switch to seaborn defaults, simply call the set() function. ###


```python
sns.set()
sinplot()
```


![png](../output_6_0.png)


### 5种主题风格 ###
* darkgrid
* whitegrid
* dark
* white
* ticks


```python
sns.set_style('whitegrid')
data = np.random.normal(size=(20, 6)) + np.arange(6) / 2
# print(help(np.random.normal))
# print(data)
sns.boxplot(data=data)
```




    <matplotlib.axes._subplots.AxesSubplot at 0xaf23470>




![png](../output_8_1.png)


For many plots, (especially for settings like talks, where you primarily want to use figures to provide impressions of patterns in the data), the grid is less necessary.


```python
sns.set_style('dark')
sinplot()
```


![png](../output_10_0.png)



```python
sns.set_style('white')
sinplot()
```


![png](../output_11_0.png)


Sometimes you might want to give a little extra structure to the plots, which is where ticks come in handy:


```python
sns.set_style('ticks')
sinplot()
```


![png](../output_13_0.png)


### Removing axes spines ###


```python
sinplot()
sns.despine()
```


![png](../output_15_0.png)


### violinplot

Some plots benefit from offsetting the spines away from the data, which can also be done when calling **<font color='red'>despine()</font>**. When the ticks don’t cover the whole range of the axis, the trim parameter will limit the range of the surviving spines.


```python
f, ax = plt.subplots()
ax.set_title('Violinplot')
sns.violinplot(data=data)
sns.despine(offset=10, trim=True)
```


![png](../output_18_0.png)


You can also control which spines are removed with additional arguments to despine()


```python
sns.set_style("whitegrid")
sns.boxplot(data=data, palette="deep")
sns.despine(left=True)
```


![png](../output_20_0.png)


### Temporarily setting figure style
Although it’s easy to switch back and forth, you can also use the *axes_style()* function in a with statement to temporarily set plot parameters. This also allows you to make figures with differently-styled axes:


```python
with sns.axes_style("darkgrid"):
    plt.subplot(211)
    sinplot()
plt.subplot(212)
sinplot(-1)
```


![png](../output_22_0.png)


### Overriding elements of the seaborn styles


```python
sns.axes_style()
```




    {'axes.axisbelow': True,
     'axes.edgecolor': '.8',
     'axes.facecolor': 'white',
     'axes.grid': True,
     'axes.labelcolor': '.15',
     'axes.linewidth': 1.0,
     'figure.facecolor': 'white',
     'font.family': ['sans-serif'],
     'font.sans-serif': ['Arial',
      'DejaVu Sans',
      'Liberation Sans',
      'Bitstream Vera Sans',
      'sans-serif'],
     'grid.color': '.8',
     'grid.linestyle': '-',
     'image.cmap': 'rocket',
     'legend.frameon': False,
     'legend.numpoints': 1,
     'legend.scatterpoints': 1,
     'lines.solid_capstyle': 'round',
     'text.color': '.15',
     'xtick.color': '.15',
     'xtick.direction': 'out',
     'xtick.major.size': 0.0,
     'xtick.minor.size': 0.0,
     'ytick.color': '.15',
     'ytick.direction': 'out',
     'ytick.major.size': 0.0,
     'ytick.minor.size': 0.0}



You can then set different versions of these parameters:


```python
sns.set_style("darkgrid", {"axes.facecolor": ".9"})
sinplot()
```


![png](../output_26_0.png)


### Scaling plot elements


```python
sns.set()
sns.set_context('paper')
sinplot()
```


![png](../output_28_0.png)



```python
sns.set_context('talk')
sinplot()
```


![png](../output_29_0.png)



```python
sns.set_context('poster')
sinplot()
```


![png](../output_30_0.png)



```python
sns.set_context('notebook', font_scale=1.5 ,rc={"lines.linewidth": 2.5})
sinplot()
```


![png](../output_31_0.png)

