# pyecharts —— 一个用于生成 Echarts 图表的类库

---

## pyecharts是什么
pyecharts 是一个用于生成 Echarts 图表的类库。Echarts 是百度开源的一个数据可视化 JS 库。
用 Echarts 生成的图可视化效果非常棒，pyecharts 是为了与 Python 进行对接，方便在 Python 中直接使用数据生成图。

ECharts，缩写来自Enterprise Charts，商业级数据图表，一个纯Javascript的图表库， 可以流畅的运行在PC和移动设备上，兼容当前绝大部分浏览器 （IE6/7/8/9/10/11，chrome，firefox，Safari等），底层依赖轻量级的Canvas类库ZRender， 提供直观，生动，可交互，可高度个性化定制的数据可视化图表。创新的拖拽重计算、数据视图、 值域漫游等特性大大增强了用户体验，赋予了用户对数据进行挖掘、整合的能力。

pyecharts 是一个用于生成 Echarts 图表的类库。 使用pyEcharts可以直接将Python代码转化为Echarts的JavaScript代码，简化Echarts和Python项目的集成。 pyecharts可以非常方便地和Flask集成，完全可以使用Flask调用pyecharts动态生成图表同时插入其他html元素，返回给浏览器。


pyecharts的详细文档说明位于：http://pyecharts.org/#/zh-cn           
pyecharts的示例网站位于：http://pyecharts.herokuapp.com

---

## pyecharts的安装
pyecharts可以安装在python 2.7或以上的任何计算机上。你可以直接使用pip安装。

- 使用pip安装：
```
pip install pyecharts

```

---

## pyechats的简单说明
> 这里简单说明一下各种参数
### 图形初始化
> 图表类初始化所接受的参数（所有类型的图表都一样）。

- title -> str  
主标题文本，支持 \n 换行，默认为 ""
- subtitle -> str   
副标题文本，支持 \n 换行，默认为 ""
- width -> int  
画布宽度，默认为 800（px）
- height -> int     
画布高度，默认为 400（px）
- title_pos -> str/int      
标题距离左侧距离，默认为'left'，有'auto', 'left', 'right', 'center'可选，也可为百分比或整数
- title_top -> str/int      
标题距离顶部距离，默认为'top'，有'top', 'middle', 'bottom'可选，也可为百分比或整数
- title_color -> str        
主标题文本颜色，默认为 '#000'
- subtitle_color -> str     
副标题文本颜色，默认为 '#aaa'
- title_text_size -> int        
主标题文本字体大小，默认为 18
- subtitle_text_size -> int     
副标题文本字体大小，默认为 12
- background_color -> str       
画布背景颜色，默认为 '#fff'
- page_title -> str     
指定生成的 html 文件中 <title> 标签的值。默认为'Echarts'
- jshost-> str      
自定义每个实例的 JavaScript host


### 通用配置项
> 通用配置项均在 add() 中设置
- xyAxis：直角坐标系中的 x、y 轴(Line、Bar、Scatter、EffectScatter、Kline)
- dataZoom：dataZoom 组件 用于区域缩放，从而能自由关注细节的数据信息，或者概览数据整体，或者去除离群点的影响。(Line、Bar、Scatter、EffectScatter、Kline、Boxplot)
- legend：图例组件。图例组件展现了不同系列的标记(symbol)，颜色和名字。可以通过点击图例控制哪些系列不显示。
- label：图形上的文本标签，可用于说明图形的一些数据信息，比如值，名称等。
- lineStyle：带线图形的线的风格选项(Line、Polar、Radar、Graph、Parallel)
- grid3D：3D笛卡尔坐标系组配置项，适用于 3D 图形。（Bar3D, Line3D, Scatter3D)
- axis3D：3D 笛卡尔坐标系 X，Y，Z 轴配置项，适用于 3D 图形。（Bar3D, Line3D, Scatter3D)
- visualMap：是视觉映射组件，用于进行『视觉编码』，也就是将数据映射到视觉元素（视觉通道）
- markLine&markPoint：图形标记组件，用于标记指定的特殊数据，有标记线和标记点两种。（Bar、Line、Kline）
- tooltip：提示框组件，用于移动或点击鼠标时弹出数据内容
- toolbox：右侧实用工具箱

### 图表的种类
> pyecharts可以画的各种图形
- Bar（柱状图/条形图）
- Bar3D（3D 柱状图）
- Boxplot（箱形图）
- EffectScatter（带有涟漪特效动画的散点图）
- Funnel（漏斗图）
- Gauge（仪表盘）
- Geo（地理坐标系）
- GeoLines（地理坐标系线图）
- Graph（关系图）
- HeatMap（热力图）
- Kline（K线图）
- Line（折线/面积图）
- Line3D（3D 折线图）
- Liquid（水球图）
- Map（地图）
- Parallel（平行坐标系）
- Pie（饼图）
- Polar（极坐标系）
- Radar（雷达图）
- Sankey（桑基图）
- Scatter（散点图）
- Scatter3D（3D 散点图）
- ThemeRiver（主题河流图）
- TreeMap（树图）
- WordCloud（词云图）

### 用户自定义
- Grid 类：并行显示多张图
- Overlap 类：结合不同类型图表叠加画在同张图上
- Page 类：同一网页按顺序展示多图
- Timeline 类：提供时间线轮播多张图

---


## pyecharts的简单使用
>这里简单的介绍一下如何画图 

### Bar（柱状图/条形图）
> 柱状/条形图，通过柱形的高度/条形的宽度来表现数据的大小。    
Bar.add() 方法签名

```
add(name, x_axis, y_axis,
    is_stack=False,
    bar_category_gap='20%', **kwargs)
```
- name -> str   
图例名称
- x_axis -> list    
x 坐标轴数据
- y_axis -> list    
y 坐标轴数据
- is_stack -> bool      
数据堆叠，同个类目轴上系列配置相同的 stack 值可以堆叠放置
- bar_category_gap -> int/str       
类目轴的柱状距离，当设置为 0 时柱状是紧挨着（直方图类型），默认为 '20%'


```
from pyecharts import Bar

attr = ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"]
v1 = [5, 20, 36, 10, 75, 90]
v2 = [10, 25, 8, 60, 20, 80]
bar = Bar("柱状图数据堆叠示例")
bar.add("商家A", attr, v1, is_stack=True)
bar.add("商家B", attr, v2, is_stack=True)
bar.render()

```
![image](https://user-images.githubusercontent.com/19553554/35081600-0ea23f0c-fc50-11e7-894b-65ad0f611a01.gif)

### Graph（关系图）
> 用于展现节点以及节点之间的关系数据。    
Graph.add() 方法签名

```
add(name, nodes, links,
    categories=None,
    is_focusnode=True,
    is_roam=True,
    is_rotatelabel=False,
    layout="force",
    graph_edge_length=50,
    graph_gravity=0.2,
    graph_repulsion=50, **kwargs)
```
- name -> str       
图例名称
- nodes -> dict     
关系图结点，包含的数据项有      
name：结点名称（必须有！）  
x：节点的初始 x 值  
y：节点的初始 y 值  
value：结点数值     
category：结点类目      
symbol：标记图形    
symbolSize：标记图形大小
- links -> dict     
结点间的关系数据，包含的数据项有    
source：边的源节点名称的字符串，也支持使用数字表示源节点的索引（必须有！）  
target：边的目标节点名称的字符串，也支持使用数字表示源节点的索引（必须有！）    
value：边的数值，可以在力引导布局中用于映射到边的长度
- categories -> list    
结点分类的类目，结点可以指定分类，也可以不指定。    
如果节点有分类的话可以通过 nodes[i].category 指定每个节点的类目，类目的样式会被应用到节点样式上
- is_focusnode -> bool  
是否在鼠标移到节点上的时候突出显示节点以及节点的边和邻接节点。默认为 True
- is_roam -> bool/str       
开启鼠标缩放和平移漫游。默认为 True    
如果只想要开启缩放或者平移，可以设置成'scale'或者'move'。设置成 True 为都开启
- is_rotatelabel -> bool    
是否旋转标签，默认为 False
- graph_layout -> str   
关系图布局，默认为 'force'      
none：不采用任何布局，使用节点中必须提供的 x， y 作为节点的位置。        
circular：采用环形布局      
force：采用力引导布局
- graph_edge_length -> int      
力布局下边的两个节点之间的距离，这个距离也会受 repulsion 影响。默认为 50。        
支持设置成数组表达边长的范围，此时不同大小的值会线性映射到不同的长度。值越小则长度越长
- graph_gravity -> int      
节点受到的向中心的引力因子。该值越大节点越往中心点靠拢。默认为 0.2
- graph_repulsion -> int        
节点之间的斥力因子。默认为 50。    
支持设置成数组表达斥力的范围，此时不同大小的值会线性映射到不同的斥力。值越大则斥力越大
- graph_edge_symbol -> str/list    
边两端的标记类型，可以是一个数组分别指定两端，也可以是单个统一指定。默认不显示标记，常见的可以设置为箭头，如下：edgeSymbol: ['circle', 'arrow']
- graph_edge_symbolsize -> int/list    
边两端的标记大小，可以是一个数组分别指定两端，也可以是单个统一指定。

```
from pyecharts import Graph

nodes = [{"name": "结点1", "symbolSize": 10},
         {"name": "结点2", "symbolSize": 20},
         {"name": "结点3", "symbolSize": 30},
         {"name": "结点4", "symbolSize": 40},
         {"name": "结点5", "symbolSize": 50},
         {"name": "结点6", "symbolSize": 40},
         {"name": "结点7", "symbolSize": 30},
         {"name": "结点8", "symbolSize": 20}]
links = []
for i in nodes:
    for j in nodes:
        links.append({"source": i.get('name'), "target": j.get('name')})
graph = Graph("关系图-力引导布局示例")
graph.add("", nodes, links, repulsion=8000)
graph.render()

```
![image](https://user-images.githubusercontent.com/19553554/35082109-05240854-fc53-11e7-9e92-dd9437c55383.png)

> 剩下的图如何画就不一一展示了，可以自行阅读说明文档画图。