
# TensorFlow 深度学习框架
## **1.简单介绍**

### 1.1  TensorFlow名字的由来
 1. TensorFlow是Google开源的一款人工智能学习系统。
 2. Tensor的意思是张量，代表N维数组；Flow的意思是流，代表基于数据流图的计算。
 3. 把N维数字从流图的一端流动到另一端的过程，就是人工智能神经网络进行分析和处理的过程。
 
### 1.2  TensorFlow安装
 1. 系统win7
 2. 安装Python，我这里下载的是版本3.5.2，[下载地址](www.python.org)
 3. 安装Eclipse，[下载地址](http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/junosr2)，导入pydev插件
 4. cmd下pip install tensorflow,导入TensorFlow模块  
 
**注意：** 安装的时候有可能出现各种问题，要特别留意安装版本问题，以及环境变量的配置。

 ### 1.3 TensorFlow学习过程
 对于计算机专业来说，学习任何新的工具，一定要以官方文档为主，网上各种教程为辅。
 以下为个人的学习过程（代码放在个人GitHub上）
 1. 基础入门： 我这里看的是中文的官方文档[链接](http://wiki.jikexueyuan.com/project/tensorflow-zh/get_started/basic_usage.html)
 2. 简单练手项目：Mnist手写识别练习——GitHub[地址](https://github.com/LexiHu/hello-world/blob/master/minst.py)
 3. TensorBoard练手项目：LSTM循环神经网络——GitHub[地址](https://github.com/LexiHu/hello-world/tree/tensorboard/TensorFlow)
 
 
## 2.TensorFlow基础知识

### 2.1 张量Tensor
   在TensorFlow框架中，所有的数据都表示为**张量**Tensor,可以看成矩阵、数组、列表，在不同的编程系统中这几种数据类型都很类似。区别是，在TensorFlow深度学习框架中的Tensor,通常都是高维度的数据。
 
### 2.2 计算图Graph
   TensorFlow 是一个编程系统, 使用**图**Graph来表示计算任务. 图中的**节点**被称之为 op (operation 的缩写). 一个 op 获得 0 个或多个 Tensor, 执行计算, 产生 0 个或多个 Tensor. 每个 Tensor 是一个类型化的多维数组. 例如, 你可以将一小组图像集表示为一个四维浮点数数组, 这四个维度分别是 batch, height, width, channels。
    计算图可接受的数据除**张量**Tenser外，还可接受**numpy**中的数据对象**矩阵**ndarray
### 2.3 会话Session
   当我们建立好计算图之后，其实这只是一个计算框架，数据并没有传进来。我们需要启动一个**会话**Session，一个session其实可以启动多张计算图Graph，在这个会话中，我们可以传入数据，访问图中任何一个节点。
### 2.4 feed_fetch机制
   启动会话Session后的赋值和访问节点操作。
   **feed**机制，为已经构建好的计算图中的**占位符**placeholder节点传入数据。 
   **fetch**机制，要获取计算图中的节点op的值，可以通过fetch方式
   
## 3.简单练习
   有了以上TensorFlow的基础知识后，我们便可以简单启动一个小程序了。
   


```python
import tensorflow as tf
#构建计算图——3个节点
input1 = tf.placeholder(tf.float32) # 占位符
input2 = tf.constant(2.) #常量
output = tf.add(input1, input2) #加法操作
#启动会话
with tf.Session() as sess:
  print( sess.run([output], feed_dict={input1:[7.]}))#feed机制向placeholder传数据

# 输出:
# [array([9.], dtype=float32)]
```

    [array([ 9.], dtype=float32)]
    

# 4 相关paper
    Comparative Study of Deep Learning Software Frameworks
    TF.Learn: TensorFlow's High-level Module for Distributed Machine Learning
    TensorFlow: Large-Scale Machine Learning on Heterogeneous Distributed Systems

