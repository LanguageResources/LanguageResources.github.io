# ConceptNet 介绍
官网：[ConceptNet](http://conceptnet.io/)
## 简介：
ConceptNet是由MIT构建的语义网络，其中包含了大量计算机应该了解的关于这个世界的信息，这些信息有助于计算机做更好的搜索、回答问题以及理解人类的意图。它由一些代表概念的结点构成，这些概念以自然语言的单词或者短语形式表达，并且其中标示了这些概念的关系。ConceptNet5是一个开源项目，其使用GPLv3协议进行开源。
## 使用方法：
数据格式：ConceptNet 是Linked Open Data，其数据以JSON-LD格式组织。
WebAPI：发出HTTP请求，获得JSON格式数据。
```
>>> import requests
>>> obj = requests.get('http://api.conceptnet.io/c/en/example').json()
>>> obj.keys()
dict_keys(['view', '@context', '@id', 'edges'])

>>> len(obj['edges'])
20

>>> obj['edges'][2]
{'@id': '/a/[/r/IsA/,/c/en/example/n/,/c/en/information/n/]',
 'dataset': '/d/wordnet/3.1',
 'end': {'@id': '/c/en/information/n',
  'label': 'information',
  'language': 'en',
  'sense_label': 'n',
  'term': '/c/en/information'},
 'license': 'cc:by/4.0',
 'rel': {'@id': '/r/IsA', 'label': 'IsA'},
 'sources': [{'@id': '/s/resource/wordnet/rdf/3.1',
   'contributor': '/s/resource/wordnet/rdf/3.1'}],
 'start': {'@id': '/c/en/example/n',
  'label': 'example',
  'language': 'en',
  'sense_label': 'n',
  'term': '/c/en/example'},
 'surfaceText': [[example]] is a type of [[information]]',
 'weight': 2.0}
```
Local Python API:
1. 安装：
> 1.Docker打包安装   
> 2. 自定义安装  
2. 使用：
如果本地已经成功安装了ConceptNet ，就可以使用Local Python API.
```
>>> from conceptnet5.db.query import AssertionFinder
>>> cnfinder = AssertionFinder()
>>> cnfinder.lookup('/c/en/example')
[... lots of edges ...]
>>> cnfinder.query({'node': '/c/en/example'})
[... the same edges ...]
```
## 相关论文
1. ConceptNet — a practical commonsense reasoning tool-kit 
H Liu and P Singh
2. ConceptNet 5.5: An Open Multilingual Graph of General Knowledge
Robert Speer, Joshua Chin, Catherine Havasi
3. Representing General Relational Knowledge in ConceptNet 5
Robert Speer and Catherine Havasi