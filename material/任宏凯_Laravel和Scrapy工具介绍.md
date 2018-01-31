# 工具介绍
### 任宏凯  201721198583  计算机应用技术
# 一．工具
	代码实战可参考：云盘链接：https://pan.baidu.com/s/1o9dhrGA 密码：xyt2
## 1.1 Scrapy框架
![](https://i.imgur.com/tX1TWNR.png)
#####                        Scrapy架构图  
#### ①Scrapy Engine(引擎): 负责Spider、ItemPipeline、Downloader、Scheduler中间的通讯，信号、数据传递等。
#### ②Scheduler(调度器): 它负责接受引擎发送过来的Request请求，并按照一定的方式进行整理排列，入队，当引擎需要时，交还给引擎。
#### ③Downloader（下载器）：负责下载Scrapy Engine(引擎)发送的所有Requests请求，并将其获取到的Responses交还给Scrapy Engine(引擎)，由引擎交给Spider来处理。
#### ④Spider（爬虫）：它负责处理所有Responses,从中分析提取数据，获取Item字段需要的数据，并将需要跟进的URL提交给引擎，再次进入Scheduler(调度器)。
#### ⑤Item Pipeline(管道)：它负责处理Spider中获取到的Item，并进行后期处理（详细分析、过滤、存储等）的地方。
#### ⑥Downloader Middlewares（下载中间件）：你可以当作是一个可以自定义扩展下载功能的组件。
#### ⑦Spider Middlewares（Spider中间件）：你可以理解为是一个可以自定扩展和操作引擎和Spider中间通信的功能组件（比如进入Spider的Responses和从Spider出去的Requests）。

## 1.2 Laravel框架
## 1.2.1框架简介
#### 框架是一堆代码的集合，这些代码里边有变量、常量、方法、函数、类。也有设计模式，例如：MVC、单例、AR、工厂等。框架最大的特点是使得程序的业务逻辑与数据模型分开。
## 1.2.2框架分类
#### a.重量级：功能多、OOP面向对象、维护性好、生命力非常顽强。
#### ZendFramework:zend公司官方框架，重量级的，功能非常丰富
#### Yii：重量级，OOP面向对象，功能丰富，外国人使用最多的框架
#### Cakephp：功能非常丰富，单速度慢
#### Symphony：国外重量级框架，功能丰富
#### b.轻量级：功能实用，面向过程和面向对象混合
#### Codeigniter：轻量级框架，开发速度快
#### ThinkPHP：国人开发的一个轻量级框架，注释都是中文的，国人使用非常广泛
#### Laravel：介于轻量级和重量级之间
![](https://i.imgur.com/BNYMKFh.png)
#######                       FIG.2  statistics on the popularity of each framework
## Vue.js
#### 渐进式JavaScript框架，易用、灵活、高效。最大的三个特点：双向数据绑定、MVVM、虚拟DOM。
 ![](https://i.imgur.com/LoTMYjN.png)
#####                             图3 MVVM模式
## Element-UI
 ![](https://i.imgur.com/X9nBgdh.png)
##### 图4 Element网站快速成型工具
#### 特点：
#### a.一致性 Consistency
	与现实生活一致：与现实生活的流程、逻辑保持一致，遵循用户习惯的语言和概念；在界面中一致：所有的元素和结构需保持一致，比如：设计样式、图标和文本、元素的位置等。
#### b.反馈 Feedback
	控制反馈：通过界面样式和交互动效让用户可以清晰的感知自己的操作；
	页面反馈：操作后，通过页面元素的变化清晰地展现当前状态。
#### c.效率 Efficiency
	简化流程：设计简洁直观的操作流程；
	清晰明确：语言表达清晰且表意明确，让用户快速理解进而作出决策；
	帮助用户识别：界面简单直白，让用户快速识别而非回忆，减少用户记忆负担。
#### d.可控 Controllability
	用户决策：根据场景可给予用户操作建议或安全提示，但不能代替用户进行决策；
	结果可控：用户可以自由的进行操作，包括撤销、回退和终止当前操作等。


