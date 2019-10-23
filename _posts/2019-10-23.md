---
layout: post  
categories: posts   
title: 对 Matplotlib 画图步骤的基本理解    
tags: [python, Matplotlib, plt，figure, add_subplot]   
date-string: OCTOBER 23, 2019

---
* **引言：**最近需要用 Matplotlib 绘制坐标图，遇到几个问题；本文就这个问题做一个总结：   
	> 区分 figure() 和 add_subplot()  
	> 区分 plt 和 axes   
	> 理解了上面两个，Matplotlib 画图步骤就明白了    
   
###区分 figure() 和 add_subplot()  
    
<font color=#FF8C00>**figure()**</font>的作用相当于**<font color=#FF8C00>放画图纸的木板</font>**，我们不能在这个木板上直接作画，因为会把木板弄脏；所以创建好一个Figure后，还要 **<font color=#FF8C00>一张(多张)画图纸(利用add_subplot())</font>**，你可在木板上放一张画图纸，也可以放多张画图纸。    
请看下面两个实验：     

```python   

	data = np.arange(10)
	fig = plt.figure()   
	plt.plot(data)   
	plt.show()     

```  
