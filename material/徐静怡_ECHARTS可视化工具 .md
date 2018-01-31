
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
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>ECharts</title>
    <!-- 引入 echarts.js -->
    <script src="echarts.min.js"></script>
</head>
<body>
    <!-- 为ECharts准备一个具备大小（宽高）的Dom -->
    <div id="main" style="width: 1000px;height:800px;"></div>
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
    tooltip : {
        trigger: 'item',
        formatter: "{a} <br/>{b} : {c} ({d}%)"
    },
    legend: {
        type: 'scroll',
        orient: 'vertical',
        right: 10,
        top: 20,
        bottom: 20,
        data: ['中央八项规定', '棱镜门', 'H7N9禽流感', '土豪', '自贸试验区', '单独二胎', '中国大妈', '光盘行动', '女汉子', '十面霾伏', '三中全会', '全面深化改革', '斯诺登', '中国梦', '自贸区', '防空识别区', '曼德拉', '土豪', '雾霾', '嫦娥三号', '党的群众路线教育实践活动', '钓鱼岛', '党内法规', '专题民主生活会', '八项规定', '新型城镇化', '车改', '周边外交', '正“四风”', '老虎苍蝇一起打', '叙利亚问题', '台风“海燕”', '波士顿爆炸案', '撒切尔夫人逝世', '美政府关门', '韩亚空难', '底特律破产', '穆尔西下台', '开城事件', '泰国局势', '民营银行', '遗产税', '互联网金融', '比特币', '钱荒', '中国大妈', '信息消费', '余额宝', '自住型商品房', '存款税', '神十', '4G（第四代移动通信技术）', '3D打印', '无人机', '旅行者1号', '运_20', '天河二号', '可燃冰', '玉兔号', '石墨烯', '太空授课', '汉字听写大会', '高考改革', '最美校长', '通用规范汉字表', '游学团', '积分入学', '减负十条', '慕课', '大学章程', '旅游法', '大黄鸭', '恒大夺冠', '最美乡村', '网络文学', '卡马乔', '孙杨', '园博会', '文明出游', '天山', '哈尼梯田', '珠算申遗', '小时代', '小伙伴', '女汉子', '爸爸去哪儿', '飞机大战', '高端大气上档次', '上头条', '五仁月饼', '网络新成语', '熊孩子', '双十一', 'H7N9禽流感', '转基因', '郑益龙', '光盘行动', '社会抚养会', '广场舞', '二维码', '潮汐车道', '打车软件', '以房养老', '汽车三包', '宽带中国', '常回家看看', '棚户区改造', '“三旧”改造', '定制公交', '清洁空气行动计划', '新消法', '弃婴岛']
    },
    series : [
        {
            name: '姓名',
            type: 'pie',
            radius : '55%',
            center: ['40%', '50%'],
            data: [
                {'name': '中央八项规定', 'value': 0},
{'name': '棱镜门', 'value': 1153},
{'name': 'H7N9禽流感', 'value': 9174},
{'name': '土豪', 'value': 3818},
{'name': '自贸试验区', 'value': 1332},
{'name': '单独二胎', 'value': 826},
{'name': '中国大妈', 'value': 1195},
{'name': '光盘行动', 'value': 909},
{'name': '女汉子', 'value': 1447},
{'name': '十面霾伏', 'value': 109},
{'name': '三中全会', 'value': 14310},
{'name': '全面深化改革', 'value': 11220},
{'name': '斯诺登', 'value': 15422},
{'name': '中国梦', 'value': 36991},
{'name': '自贸区', 'value': 6983},
{'name': '防空识别区', 'value': 3277},
{'name': '曼德拉', 'value': 7943},
{'name': '土豪', 'value': 3818},
{'name': '雾霾', 'value': 19925},
{'name': '嫦娥三号', 'value': 3836},
{'name': '党的群众路线教育实践活动', 'value': 7528},
{'name': '钓鱼岛', 'value': 8611},
{'name': '党内法规', 'value': 4461},
{'name': '专题民主生活会', 'value': 2490},
{'name': '八项规定', 'value': 7999},
{'name': '新型城镇化', 'value': 5119},
{'name': '车改', 'value': 2406},
{'name': '周边外交', 'value': 752},
{'name': '正“四风”', 'value': 379},
{'name': '老虎苍蝇一起打', 'value': 51},
{'name': '叙利亚问题', 'value': 2176},
{'name': '台风“海燕”', 'value': 485},
{'name': '波士顿爆炸案', 'value': 654},
{'name': '撒切尔夫人逝世', 'value': 12},
{'name': '美政府关门', 'value': 14},
{'name': '韩亚空难', 'value': 185},
{'name': '底特律破产', 'value': 162},
{'name': '穆尔西下台', 'value': 262},
{'name': '开城事件', 'value': 0},
{'name': '泰国局势', 'value': 43},
{'name': '民营银行', 'value': 1801},
{'name': '遗产税', 'value': 1790},
{'name': '互联网金融', 'value': 3123},
{'name': '比特币', 'value': 6676},
{'name': '钱荒', 'value': 2274},
{'name': '中国大妈', 'value': 1195},
{'name': '信息消费', 'value': 1502},
{'name': '余额宝', 'value': 2086},
{'name': '自住型商品房', 'value': 944},
{'name': '存款税', 'value': 187},
{'name': '神十', 'value': 1826},
{'name': '4G（第四代移动通信技术）', 'value': 4},
{'name': '3D打印', 'value': 5025},
{'name': '无人机', 'value': 4624},
{'name': '旅行者1号', 'value': 230},
{'name': '运_20', 'value': 0},
{'name': '天河二号', 'value': 394},
{'name': '可燃冰', 'value': 415},
{'name': '玉兔号', 'value': 243},
{'name': '石墨烯', 'value': 556},
{'name': '太空授课', 'value': 978},
{'name': '汉字听写大会', 'value': 539},
{'name': '高考改革', 'value': 1087},
{'name': '最美校长', 'value': 307},
{'name': '通用规范汉字表', 'value': 304},
{'name': '游学团', 'value': 353},
{'name': '积分入学', 'value': 239},
{'name': '减负十条', 'value': 291},
{'name': '慕课', 'value': 418},
{'name': '大学章程', 'value': 183},
{'name': '旅游法', 'value': 4719},
{'name': '大黄鸭', 'value': 2412},
{'name': '恒大夺冠', 'value': 183},
{'name': '最美乡村', 'value': 1099},
{'name': '网络文学', 'value': 1437},
{'name': '卡马乔', 'value': 6639},
{'name': '孙杨', 'value': 11741},
{'name': '园博会', 'value': 2856},
{'name': '文明出游', 'value': 571},
{'name': '天山', 'value': 2666},
{'name': '哈尼梯田', 'value': 362},
{'name': '珠算申遗', 'value': 30},
{'name': '小时代', 'value': 3707},
{'name': '小伙伴', 'value': 5616},
{'name': '女汉子', 'value': 1447},
{'name': '爸爸去哪儿', 'value': 1652},
{'name': '飞机大战', 'value': 83},
{'name': '高端大气上档次', 'value': 552},
{'name': '上头条', 'value': 353},
{'name': '五仁月饼', 'value': 245},
{'name': '网络新成语', 'value': 8},
{'name': '熊孩子', 'value': 564},
{'name': '双十一', 'value': 3214},
{'name': 'H7N9禽流感', 'value': 9174},
{'name': '转基因', 'value': 8469},
{'name': '郑益龙', 'value': 1208},
{'name': '光盘行动', 'value': 909},
{'name': '社会抚养会', 'value': 0},
{'name': '广场舞', 'value': 1913},
{'name': '二维码', 'value': 6685},
{'name': '潮汐车道', 'value': 603},
{'name': '打车软件', 'value': 1147},
{'name': '以房养老', 'value': 1289},
{'name': '汽车三包', 'value': 1616},
{'name': '宽带中国', 'value': 360},
{'name': '常回家看看', 'value': 1460},
{'name': '棚户区改造', 'value': 2323},
{'name': '“三旧”改造', 'value': 159},
{'name': '定制公交', 'value': 977},
{'name': '清洁空气行动计划', 'value': 526},
{'name': '新消法', 'value': 172},
{'name': '弃婴岛', 'value': 362}
                ],
            itemStyle: {
                emphasis: {
                    shadowBlur: 10,
                    shadowOffsetX: 0,
                    shadowColor: 'rgba(0, 0, 0, 0.5)'
                }
            }
        }
    ]
};




        // 使用刚指定的配置项和数据显示图表。
        myChart.setOption(option);
    </script>
</body>
</html>
   （5）各种图的绘制
        官网上有很多图的实例，使用者可以根据自己的需要找到自己需要的图，点进去，就有每种图的Option，然后按照格         式加入数据即可。

四、相关论文

    1.王子毅,张春海.基于ECharts的数据可视化分析组件设计实现[J].微型机与应用,2016,35(14):46-48+51.
    2.贾宁.Echarts在移动数据通信中的应用[J].移动通信,2016,40(20):50-53.
    3.王龙,王一男.基于ECharts的可视化高校综合信息分析决策系统[J].现代电子技术,2017,40(06):68-70.


