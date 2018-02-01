Matplotlib数据可视化分析
姓名：何晓文   学号：201721198580  专业：计算机应用技术

链接：https://matplotlib.org/users/pyplot_tutorial.html

详细介绍
Matplotlib是基于Python语言的开源项目，旨在为Python提供一个数据绘图包。用户在熟悉了核心对象之后，可以轻易地定制图像。Matplotlib能够创建多数类型的图表，如条形图，散点图，条形图，饼图，堆叠图，3D 图和地图图表。

函数式绘图和面向对象式绘图：
	函数式绘图参考了matlab里面的绘图函数语法，简单易上手
	面向对象式绘图更懂matplotlib底层架构，有更多的功能

环境搭建
	Anaconda 清华镜像
	PyCharm  非常好用的Python集成开发环境，并且Commumity版是免费的
使用说明
使用matplotlib库绘图的五个步骤：
	创建一个图纸 (figure)
	在图纸上创建一个或多个绘图(plotting)区域(也叫子图，坐标系/轴，axes)
	在plotting区域上描绘点、线等各种marker
	为plotting添加修饰标签(绘图线上的或坐标轴上的)
	其他各种DIY

例1：
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches
fig, ax = plt.subplots()
xy1 = np.array([0.2, 0.8])
rect = mpatches.Rectangle(xy1, 0.2, 0.1, color='r')
plt.axis('equal')
plt.grid()
plt.show()
 

例2：
import numpy as np
import matplotlib.pyplot as plt

mu, sigma = 100,15
x = mu+sigma*np.random.randn(10000)

n, bins, patches = plt.hist(x, 50, normed = 1, facecolor='g',alpha=0.75)

plt.xlabel('Smarts')
plt.ylabel('Probability')
plt.title('Histogram of IQ')
plt.text(60, 0.025, r'$\mu=100,\ \sigma=15$')
plt.axis([40, 160, 0, 0.03])
plt.grid(True)
plt.show()
 

Reference:
https://matplotlib.org/users/license.html#copyright-policy
http://blog.csdn.net/hustqb/article/details/53287374
http://blog.csdn.net/wizardforcel/article/details/54407212

