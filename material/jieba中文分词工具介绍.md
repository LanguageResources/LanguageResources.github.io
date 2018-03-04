
# “结巴”中文分词：做最好的 Python 中文分词组件:
>"Jieba" (Chinese for "to stutter") Chinese text segmentation: built to be the best Python Chinese word segmentation module.

## 什么是jieba库？
![Aaron Swartz](https://raw.githubusercontent.com/CSerV/MarkdownPhotos/master/9150e4e5jw1fcbbf6amp6j207p06k3yq.jpg)

jieba 是一个python实现的分词库，对中文有着很强大的分词能力。
听到这个解释可能不足以让你了解，到底什么是jieba。所以我们首先要了解下面这些概念：
#### 1）、什么是中文分词？
即：中文文本，从形式上看是由汉字、标点符号等组成的一个字符串。由字组成词，再组成句子、文章等。那么分词，就是按照一定的规则把字符串重新组合成词序列的过程。

#### 2）、为什么要分词？
（a）在中文里面，词是最小的能够独立活动的有意义的语言成分

（b）英文中单词以空格作为自然分界，虽然也有短语划分的问题。但中文词没有一个形式上的分界，相对而言难度大了许多

（c）分词作为中文自然语言处理的基础工作，质量的好坏对后面的工作影响很大

<font color=red>因此有了这些概念我们便知jieba就是专门为实现中文分词的强大工具！</font>

这里是jieba的详细文档：https://pypi.python.org/pypi/jieba/ 

jieba的github主页位于：https://github.com/fxsjy/jieba

## jieba特点

* 支持三种分词模式：  


* 精确模式，试图将句子最精确地切开，适合文本分析；  


* 全模式，把句子中所有的可以成词的词语都扫描出来, 速度非常快，但是不能解决歧义；  


* 搜索引擎模式，在精确模式的基础上，对长词再次切分，提高召回率，适合用于搜索引擎分词。  


* 支持繁体分词  


* 支持自定义词典  


* MIT 授权协议


## 安装及使用说明

代码对 Python 2/3 均兼容

* 全自动安装：easy_install jieba 或者pip install jieba / pip3 install jieba  


* 半自动安装：先下载 http://pypi.python.org/pypi/jieba/ ，解压后运行 python setup.py install  


* 手动安装：将 jieba 目录放置于当前目录或者 site-packages 目录  


* 通过 import jieba 来引用  




## 算法

* 基于前缀词典实现高效的词图扫描，生成句子中汉字所有可能成词情况所构成的有向无环图 (DAG)  


* 采用了动态规划查找最大概率路径, 找出基于词频的最大切分组合  


* 对于未登录词，采用了基于汉字成词能力的 HMM 模型，使用了 Viterbi 算法  


## 主要功能
>jieba的功能十分丰富，限于篇幅原因，这里只介绍两个。

### 1、分词
***

* jieba.cut 方法接受三个输入参数: 需要分词的字符串；cut_all 参数用来控制是否采用全模式；HMM 参数用来控制是否使用 HMM 模型  


* jieba.cut_for_search 方法接受两个参数：需要分词的字符串；是否使用 HMM 模型。该方法适合用于搜索引擎构建倒排索引的分词，粒度比较细  


* 待分词的字符串可以是 unicode 或 UTF-8 字符串、GBK 字符串。注意：不建议直接输入 GBK 字符串，可能无法预料地错误解码成 UTF-8  


* jieba.cut以及 jieba.cut_for_search 返回的结构都是一个可迭代的 generator，可以使用 for 循环来获得分词后得到的每一个词语(unicode)，或者用  


* jieba.lcut 以及jieba.lcut_for_search 直接返回 list  


* jieba.Tokenizer(dictionary=DEFAULT_DICT) 新建自定义分词器，可用于同时使用不同词典。jieba.dt 为默认分词器，所有全局分词相关函数都是该分词器的映射。  



代码示例：


```python
# encoding=utf-8
import jieba

seg_list = jieba.cut("我来到北京清华大学", cut_all=True)
print("Full Mode: " + "/ ".join(seg_list))  # 全模式

seg_list = jieba.cut("我来到北京清华大学", cut_all=False)
print("Default Mode: " + "/ ".join(seg_list))  # 精确模式

seg_list = jieba.cut("他来到了网易杭研大厦")  # 默认是精确模式
print(", ".join(seg_list))

seg_list = jieba.cut_for_search("小明硕士毕业于中国科学院计算所，后在日本京都大学深造")  # 搜索引擎模式
print(", ".join(seg_list))

```

    Full Mode: 我/ 来到/ 北京/ 清华/ 清华大学/ 华大/ 大学
    Default Mode: 我/ 来到/ 北京/ 清华大学
    他, 来到, 了, 网易, 杭研, 大厦
    小明, 硕士, 毕业, 于, 中国, 科学, 学院, 科学院, 中国科学院, 计算, 计算所, ，, 后, 在, 日本, 京都, 大学, 日本京都大学, 深造
    

### 2、添加自定义词典

***

#### 载入词典

* 开发者可以指定自己自定义的词典，以便包含 jieba 词库里没有的词。虽然 jieba 有新词识别能力，但是自行添加新词可以保证更高的正确率  


* 用法： jieba.load_userdict(file_name) # file_name 为文件类对象或自定义词典的路径  


* 词典格式和 dict.txt 一样，一个词占一行；每一行分三部分：词语、词频（可省略）、词性（可省略），用空格隔开，顺序不可颠倒。file_name 若为路径或二进制方式打开的文件，则文件必须为 UTF-8 编码。  


* 词频省略时使用自动计算的能保证分出该词的词频。  




```python
创新办 3 i
云计算 5
凱特琳 nz
台中
```

* 更改分词器（默认为jieba.dt）的 tmp_dir 和 cache_file 属性，可分别指定缓存文件所在的文件夹及其文件名，用于受限的文件系统。  


范例：
* 自定义词典：https://github.com/fxsjy/jieba/blob/master/test/userdict.txt  
  
  
* 用法示例：https://github.com/fxsjy/jieba/blob/master/test/test_userdict.py  


```
之前： 李小福 / 是 / 创新 / 办 / 主任 / 也 / 是 / 云 / 计算 / 方面 / 的 / 专家 /
```
```
加载自定义词库后：　李小福 / 是 / 创新办 / 主任 / 也 / 是 / 云计算 / 方面 / 的 / 专家 /
```

#### 调整词典

* 使用 add_word(word, freq=None, tag=None)和 del_word(word) 可在程序中动态修改词典。  
  
  
* 使用 suggest_freq(segment, tune=True) 可调节单个词语的词频，使其能（或不能）被分出来。  
  
  
 
* 注意：自动计算的词频在使用 HMM 新词发现功能时可能无效。  


代码示例：


```python
>>> print('/'.join(jieba.cut('如果放到post中将出错。', HMM=False)))
如果/放到/post/中将/出错/。
>>> jieba.suggest_freq(('中', '将'), True)
494
>>> print('/'.join(jieba.cut('如果放到post中将出错。', HMM=False)))
如果/放到/post/中/将/出错/。
>>> print('/'.join(jieba.cut('「台中」正确应该不会被切开', HMM=False)))
「/台/中/」/正确/应该/不会/被/切开
>>> jieba.suggest_freq('台中', True)
69
>>> print('/'.join(jieba.cut('「台中」正确应该不会被切开', HMM=False)))
「/台中/」/正确/应该/不会/被/切开
```

* "通过用户自定义词典来增强歧义纠错能力" --- https://github.com/fxsjy/jieba/issues/14
