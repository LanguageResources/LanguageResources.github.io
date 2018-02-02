Computational Network Toolkit (CNTK) 是微软出品的开源深度学习工具包。本文介绍CNTK的基本内容，如何写CNTK的网络定义语言，以及跑通一个简单的例子。

根据微软开发者的描述，CNTK的性能比Caffe，Theano， TensoFlow等主流工具都要强。它支持CPU和GPU模式，所以没有GPU，或者神经网络比较小的实验，直接用CPU版的CNTK跑就行了。 其开源主页在 https://github.com/Microsoft/CNTK 它把神经网络描述成一个有向图的结构，叶子节点代表输入或者网络参数，其他节点计算步骤。 它支持卷积神经网络和递归神经网络。 由于CNTK刚推出不久，大众教程估计不多，而且bug估计也不少。我学习的时候，主要参考三个资料：

1.**官方入门教程** https://github.com/Microsoft/CNTK/wiki/Tutorial 本文也主要以这里的教程为例

2.**官方论坛** https://github.com/Microsoft/CNTK/issues

3.**官方论文** http://research.microsoft.com/pubs/226641/CNTKBook-20160217..pdf

安装CNTK： https://github.com/Microsoft/CNTK/wiki/CNTK-Binary-Download-and-Configuration 去这个页面找符合自己系统的版本。 对于Windows用户，CNTK有编译好的CPU和GPU版本。已经编译好的包最方便了，解压，然后把目录（类似%...%、CNTK-2016-02-08-Windows-64bit-CPU-Only\cntk\cntk）添加到PATH变量中就行了。 有条件的人也可以自己编译源代码，稍微麻烦一些，各种依赖关系，好处是源码更新的比较快。

安装好CNTK之后，运行一个程序，就是一个简单的命令行： CNTK configFile=your_config_file ， 其中，your_config_file 是网络的定义文件，大概长这样： command=Train:Test Train=[ action="train"

    NDLNetworkBuilder = [
    ...
    ]

    SGD = [
    ...
    ]

    reader = [
    ...
　　　　]

]

Test=[ ... ]

运行的入口就是command命令，command后面接需要依次运行的模块，用冒号分开。 每个模块里面需要定义的事情比较类似，主要是定义输入的格式，网络结构，学习算法（目前只有SGD）和参数。 在定义网络结构的时候，会指明哪些节点是优化目标，哪些是评价指标，以及哪些是输出的点。

众所周知，把神经网络的隐藏层去掉之后，输入直接连到输出层，这样就行成了一个logistics regression分类器。所以https://github.com/Microsoft/CNTK/wiki/Tutorial 这个教程就指导大家如何构建一个LR。

Output模块和Test的流程基本一样，只不过最后一个不是评估，而是把属于OutputNodes的值给输出到文件。 Output模块会指定一个输出目录 outputPath = "LR.txt" ， 输出的文件以“LR.txt”为前缀，再加上变量命作为文件名。例如"LR.txt.W0"。

#output the results Output=[

action="write"

reader=[
    
    readerType="UCIFastReader"
    
    file="Test.txt"
    
    features=[
        
        dim=$dimension$
        
        start=0
    
    ]
    
    labels=[
        
        start=2
        
        dim=1
        
        labelType=regression
    
    ]

]

outputPath = "LR.txt"       # dump the output as text
]

dumpNodeInfo 用来输出参数的值。这在调试中很有用，例如去看看网络的参数是如何变化的：

dumpNodeInfo=[
``` stylus
enter code here
    action=dumpnode
    
    printValues=true
]
####################################################################

B=LearnableParameter [1,1] NeedGradient=true

-6.67130613

####################################################################

EP=SquareError ( labels , s )

features=InputValue [ 2 x 1 {1,2} ]

labels=InputValue [ 1 x 1 {1,1} ]

LR=Logistic ( labels , s )

s=Sigmoid ( z )

t=Times ( W , features )

W=LearnableParameter [1,2] NeedGradient=true

1.23924482 1.59913719

####################################################################

z=Plus ( t , B )
```



全部的代码如下。 train文件 https://github.com/Microsoft/CNTK/wiki/Tutorial/Train-3Classes.txt 
test 文件 https://github.com/Microsoft/CNTK/wiki/Tutorial/Test-3Classes.txt。 数据是2维的.
![图片](https://raw.githubusercontent.com/lichaomessi/images/master/380470-20160421230002445-58655114.png)

**相关论文：**
  F Seide ， A Agarwal-------CNTK: Microsoft's Open-Source Deep-Learning Toolkit
