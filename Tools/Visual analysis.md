# Visual Analysis
```python
import seaborn as sns
%matplotlib inline
import matplotlib.pyplot as plt
```

---

Contents<br>
[1. Settings](#-1.-settings)<br>
[2. 单变量数值分布](#-2.-单变量数值分布)<br>
[3. 二元类别](#-3.-二元类别)<br>

---
## 1. Settings
```python
%config InlineBackend.figure_format = 'svg'  # 图像格式
from pylab import rcParams
rcParams['figure.figsize'] = 5, 4  # 默认绘图尺寸
```

## 2. 单变量数值分布
### 2.1 直方图

```python
df[features].hist(figsize=(12, 4));
```

<img src="https://image-cdn.jqr.com/editor/170/669/1706691977-5aa7888ee630d" alt="drawing" width="600"/>


### 2.2 密度图
比直方图更清晰，不依赖于柱个数

```python
df[features].plot(
	kind='density', 
	subplots=True, 
	layout=(1, 2), 
	sharex=False, 
	figsize=(12, 4));
```

<img src="https://image-cdn.jqr.com/editor/198/198/1981981243-5aa788c5f0d24" alt="drawing" width="600"/>


同时查看直方图与密度图

```python
sns.distplot(df[feature]);
```

其中直方图数值已经归一化

<img src="https://image-cdn.jqr.com/editor/707/016/707016171-5aa789a6096b9"  alt="drawing" width="300"/>

### 2.3 箱图(box plot)

``` python
_, ax = plt.subplots(figsize=(3, 4))
sns.boxplot(data=df['Total intl calls'], ax=ax);
```

```python
df = pd.DataFrame(np.random.rand(10,5),columns=['A','B','C','D','E'])
plt.figure(figsize =(10,4))
f = df.boxplot(sym = 'o',
              vert = True,
              whis = 1.5,
              patch_artist = True,
              meanline = False,
              showmeans = True,
              showbox = True,
              showcaps = True,
              showfliers = True,
              notch = False, 
              return_type = 'dict'
              )
```

> 1. 箱形图的主要组成部分是箱（box）、须（whisker）和单独的数据点（离群值）<br>
> 2. 箱子显示了分布的四分位距；它的长度由25%（Q1，下四分位数）和75%（Q3，上司分位数）决定。箱中的水平线表示中位数（50%）。<br>
> 3. 从箱子处延伸出来的线被称为须。它们表示数据点的总体散布。<font style="color:rgb(255,0,0)"><b>须最多延伸至(Q1 - 1.5xIQR, Q3 + 1.5xIQR)的区间，且不超过min和max</b></font>，其中IQR=Q3-Q1，也就是四分位距。<br>
> 4. 离群值是须之外的数据点，它们作为单独的数据点，沿着中轴绘制。<br>

<img src="https://www.jqr.com/editor/123/118/1231183368-5aa78a853c506" alt="boxplot" width="200"/>

---
* 五数概括法
	* min、Q1、中位数、Q3、max
	* 计算Q1和Q3时，exclude Q2
	* IQR = Q3 - Q1
	* 距离中位数大于1.5倍IQR的值：
<font style="color:rgb(255,0,0)"><b>异常值 Outliner</b></font>

---


### 2.4 提琴图(violin plot)

```python
_, axes = plt.subplots(1, 2, sharey=True, figsize=(6, 4))
sns.boxplot(data=df['Total intl calls'], ax=axes[0]); sns.violinplot(data=df['Total intl calls'], ax=axes[1]);
```

> 箱形图和提琴图类似。<br>
> 二者的区别是，箱形图显示了单独样本的特定统计数据，而提琴图聚焦于平滑后的整体分布。

<img src="https://www.jqr.com/editor/340/140/3401401425-5aa78dcd83acf" alt="violinplot" width="400"/>

---

## 3. 二元类别

### 3.1 条形图

类别之间，count的比较

> 1

```python

```