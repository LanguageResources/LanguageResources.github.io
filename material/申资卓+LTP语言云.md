
## LTP 语言云

LTP 语言云由哈尔滨工业大学社会计算与信息检索实验室开发，提供分句、分词、词性标注、句法分析、语义角色标注等自动语言分析功能，曾获 CoNLL 2009七国语言句法语义分析评测 总成绩第一名，中文信息学会钱伟长一等奖等重要成绩和荣誉。

### 分句

分句提供对文本的断句功能，一般以中文句号、问号、感叹号等划分句子，实例代码如下：


```python
from pyltp import SentenceSplitter
sents = "python。数据！分析？"
sents = SentenceSplitter.split(sents)
print("\n".join(sents))
```

    python。
    数据！
    分析？
    

### 分词
执行分词功能时，需加载LTP的分词模块cws.model


```python
model_path = "D:\Tools\LTP\ltp_data\cws.model"
from pyltp import Segmentor
sent = "我爱北京天安门"
segmentor = Segmentor()
segmentor.load(model_path)
words = segmentor.segment(sent)
words_list = list(words)
words_list
```




    ['我', '爱', '北京', '天安门']



### 词性标注


```python
model_path = "D:\Tools\LTP\ltp_data\pos.model"
from pyltp import Postagger
words = ['我', '爱', '北京', '天安门']
postagger = Postagger()
postagger.load(model_path)
postags = postagger.postag(words)
for word,tag in zip(words,postags):
    print (word+'/'+tag)
```

    我/r
    爱/v
    北京/ns
    天安门/ns
    

### 句法分析
LTP句法分析提供依存句法分析功能，分析结果以该词的父节点词语及句法关系的键值对表示


```python
model_path = "D:\Tools\LTP\ltp_data\parser.model"
from pyltp import Parser
words = ['我', '爱', '北京', '天安门']
parser = Parser()
parser.load(model_path)
arcs = parser.parse(words, postags)
print ("\t".join("%d:%s" % (arc.head, arc.relation) for arc in arcs))
```

    2:SBV	0:HED	4:ATT	2:VOB
    

### 相关论文

刘挺 车万翔 李正华 语言技术平台[J], 中文信息学报, 2011(6)
