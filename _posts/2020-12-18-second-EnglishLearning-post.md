---
layout: post  
categories: posts   
title: English Learning--描述电视节目    
tags: [English Learning, Episode, Television Programme]   
date-string: DECEMBER 18, 2020

---
* **引言：**最近观看了一场TEDx Talks王佑哲 | 没有方向？先从当个积极的迷惘人开始！从七月入职以来，焦躁和迷茫感一直伴随着我。我似乎一直在后悔自己的选择，想来当初还是应该选择自己擅长的领域或者说和自己所擅长相近的领域。恰巧我在逛油管时偶然看到了这个演讲，于是又诱发我关于自我探索的思考。以下是这篇文章的主要内容：   
	> TEDx Talks 这场演讲的主要内容  
	> 感悟    
	> 第一篇英语学习笔记    

********
   
### 做一个积极的迷惘人   
 
    
&emsp;&emsp;迷惘是每个人都会经历的人生阶段，有的人人生中会经历一个或多个迷惘阶段。作者结合其亲身经历告诉我们当经历迷惘时，**持续有规律的积累，是走出迷惘的关键！**    
  
  ![](/images/2020/2020-12-18/20201218-00.png)
&emsp;&emsp; **figure()**的作用相当于**放画图纸的木板**，我们不能在这个木板上直接作画，因为会把木板弄脏；所以创建好一个Figure后，还要 一张(多张) **画图纸**(利用**add_subplot()**)，你可在木板上放一张画图纸，也可以放多张画图纸。    
请看下面的实验：     

```python   

	import matplotlib.pyplot as plt
	import numpy as np
	data = np.arange(10)
	fig = plt.figure()
	ax1 = fig.add_subplot(2,2,1)
	ax2 = fig.add_subplot(2,2,2)
	ax3 = fig.add_subplot(2,2,3)
	ax4 = fig.add_subplot(2,2,4)
	plt.show() 
```  

运行结果：   
![](/images/2019/October/20191023-00.png)

&emsp;&emsp;首先利用 figure() 创建一个木板，然后利用 add\_subplot() 在这张画板上创建了四张画纸(创建子图)；(2,2,1)分别表示创建 2 行 2 列共四个子图，1 代表放在第一个位置。如果只在画板上只画一张图，虽然可以不用创建 add\_subplot()；但我还是强烈建议你创建一张子图来绘图，利用 Figure.add\_subplot(1,1,1) 实现，这是一个好的习惯；我们后面会讲到。
  
**另注：**  
 > 1. [figure()](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.figure) 和 [add_subplot()](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.figure.Figure.html#matplotlib.figure.Figure.add_subplot) 的参数设置，这里我不逐一详说，大家点链接看就行了。要用什么参数根据官方说明添加即。  
> 2. Figure.add\_subplot() 和 plt.subplot() 作用一样，但是推荐使用 Figure.add\_subplot()。   
> 3. add\_axes()可以用来绘制子图的子图。   
> 4. `grid = plt.Gridspec()`实现更加复杂的绘图排列，实际上是对画板区域进行划分，使得没个区域放的子图的样子有所不同。参考链接：[plt.Gridspec()](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.gridspec.GridSpec.html#examples-using-matplotlib-gridspec-gridspec)

********


### 区分 plt. 和 axes.   
  
&emsp;&emsp;这两个的区别其实就是 **函数式绘图** 和 **面向对象式绘图**， 我们来看下试验：   
```python   
  
	import matplotlib.pyplot as plt
	import numpy as np
	data = np.arange(10)
	fig = plt.figure()
	ax1 = fig.add_subplot(2,2,1)
	ax1.plot(data)
	ax2 = fig.add_subplot(2,2,2)
	ax3 = fig.add_subplot(2,2,3)
	ax4 = fig.add_subplot(2,2,4)
	plt.plot(data)
	plt.show()
```          

运行结果：   
![](/images/2019/October/20191023-01.png)     
&emsp;&emsp;从图中可以看出：ax1.plot() 是精准的作用于 ax1 这个子图，而 plt.plot() 是作用于程序里面它上方最近的一个子图。所以在绘图时，能不用 plt. 就尽量不用，因为它不是精准作用于对象的，很容易造成混乱。另外细心的看官们应该能发现 ax2,ax3的坐标的不同，这说明这**四个坐标刻度是独立存在的**，不会相互影响(当然你也可以设定成互相关联，这取决于你的目的)，没有画图就不会变化。**我们作图时应时刻牢记利用面向对象式绘图，哪怕画图板上就绘制一张图！**    

****    
### Matplotlib作图的基本步骤   

> 1. 创建画板：`fig = plt.figure()` ，后面还可以跟着对画板的各种处理；   
> 2. 创建子图：`axis = fig.subplot()`，一次创建多张子图，axes 是一个数组；   
> 3. 面向对象式绘图；     
> 4. 显示图片或者保存图片,etc.     

**另注：**  
> plt.imshow(image) or ax.imshow(image)，将一张图片显示在特定的子坐标图上；    
> plt.show() 在电脑上显示所有绘制的坐标图。