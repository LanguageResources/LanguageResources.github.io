
可视化工具ECHARTS

一、下载地址：http://echarts.baidu.com/download.html

二、简介

    ECharts，缩写来自Enterprise Charts，商业级数据图表，一个纯Javascript的图表库，可以流畅的运行在PC和移动设备上，兼容当前绝大部分浏览器（IE6/7/8/9/10/11，chrome，firefox，Safari等），底层依赖轻量级的Canvas类库ZRender，提供直观，生动，可交互，可高度个性化定制的数据可视化图表。创新的拖拽重计算、数据视图、值域漫游等特性大大增强了用户体验，赋予了用户对数据进行挖掘、整合的能力。

三、使用教程

1、下载
   
   进入官网，直接在下载页面下载完整版（其中包括所有的图表和组件）
   下载后的结果是一个插件，只要将自己写的文档保存为.html格式，然后与插件放在同一个文件夹下，打开文档网页后即可    显示图表。
   
2、使用方式
   
   直接创建文本文档，保存成.html格式即可。
 
  （1）引入ECharts
       ECharts3 开始不再强制使用 AMD 的方式按需引入，代码里也不再内置 AMD 加载器。因此引入方式简单了很多，只需        要像普通的 JavaScript 库一样用 script 标签引入。
       
       代码如下：
       <!DOCTYPE html>
       <html>
       <head>
           <meta charset="utf-8">
           <title>ECharts</title>
           <!-- 引入 echarts.js -->
           <script src="echarts.min.js"></script>
       </head>

  （2）绘图前为Echarts准备一个具体高宽的DOM容器
       引入Echarts之后，还需要一个“画布”，就像我们写网页时，需要将整个页面作为“画布”，在上面确定                  要“画”在左中右等。
       
       代码如下：
        <!-- 为ECharts准备一个具备大小（宽高）的Dom -->
        <div id="main" style="width: 1000px;height:800px;"></div>
  
  （3）通过 echarts.init 方法初始化一个 echarts 实例并通过 setOption 方法生成一个简单的图
       
       代码如下：
         <script type="text/javascript">
            // 基于准备好的dom，初始化echarts实例
             var myChart = echarts.init(document.getElementById('main'));
         // 指定图表的配置项和数据
      option = {
          title : {
              text: '平面媒体流行语',
              subtext: '2013年15份报纸',
              x:'center'
             },
             ......

   
   （4）最后成图实例


   （5）各种图的绘制
        
        官网上有很多图的实例，使用者可以根据自己的需要找到自己需要的图，点进去，就有每种图的Option，然后按照格         式加入数据即可。

四、相关论文

    1.王子毅,张春海.基于ECharts的数据可视化分析组件设计实现[J].微型机与应用,2016,35(14):46-48+51.
    2.贾宁.Echarts在移动数据通信中的应用[J].移动通信,2016,40(20):50-53.
    3.王龙,王一男.基于ECharts的可视化高校综合信息分析决策系统[J].现代电子技术,2017,40(06):68-70.


