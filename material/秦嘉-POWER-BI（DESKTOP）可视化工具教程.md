秦嘉 POWER BI（DESKTOP）可视化工具教程
#一、  下载链接：

[https://powerbi.microsoft.com/zh-cn/desktop/](https://powerbi.microsoft.com/zh-cn/desktop/)

#二、   工具简介

Power BI (Power Business Intelligence），是微软为Office组件提供的一套商业智能工具，能在较短时间内生成各种高度可视化的报表，主要应用于报表制作与发布。

Power BI Desktop 允许用户生成高级查询、模型和实现数据可视化效果的报表。 通过 Power BI Desktop，可以生成数据模型、创建报表，并通过发布到 Power

BI 服务共享工作。 Power BI Desktop 可免费下载。

Power BI 包括了如下的一些组件和服务：

Excel组件：

查询增强版（Power Query）：轻松地链接公众数据或者企业数据源

建模增强版（Power Pivot）：直接在Excel中创建复杂的数据模型

视图增强版（Power View）：创建报表和交互式数据可视化分析视图

地图增强版（Power Map）：在Excel中的3D地图标注地理空间数据的体验

Office365：

商业智能增强版网站：分享查看并于BI网站互动

商业智能Q&A：使用日常用语去发现、发掘并报告你的数据

查询和数据化管理：分享、管理查询数据源

#三、  使用方式

##1、 下载desktop版本power bi并简单注册

![image](http://upload-images.jianshu.io/upload_images/10432152-70f90ad5e99798f5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![image](http://upload-images.jianshu.io/upload_images/10432152-11875a2ffe4fea6a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

Power BI Desktop 中有三种视图：报表视图、数据视图和关系视图。Power BI Desktop 还包含 查询编辑器，其会在单独的窗口打开。 在查询编辑器中，你可以生成查询和转换数据，然后将经过优化的数据模型加载到 Power BI Desktop，并创建报表。

上图屏幕沿 Power BI Desktop 左侧自上而下显示了三个视图图标：报表、数据和关系。当前显示的视图以左侧的黄色条表示。 在此示例中，当前显示了报表视图。用户可以通过选择这三个图标的任意一个更改视图。

##2、  通过get data导入数据

![image](http://upload-images.jianshu.io/upload_images/10432152-385d7320e2d587ed.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

既可通过选择本地文件导入数据，也可通过“web”、“more”等加载在线数据。

选择文件之后，会显示“导航器”对话框。在这里选择需要导入的工作表（可以选择多个）。选择工作表之后，可以直接点“加载”，也可以点“编辑”来打开“查询编辑器”修改ETL脚本（加载后仍可重新编辑）。如果直接点“加载”之后，Power BI就会把选择的工作表中的数据加载进来，此时可以在“数据”视图中预览其中的数据，右侧的“字段”边栏也会显示表及其包含的字段。

##3、   示例1：将 Excel 工作簿导入Power BI Desktop

若要导入工作簿，请在 Power BI Desktop 中选择**文件 -> 导入 -> Excel 工作簿内容**。

选择工作簿后，Power BI Desktop 将分析该工作簿并将其转换为 Power BI Desktop 文件 (.pbix)。 注意这是一次性事件，通过这些步骤创建 Power BI Desktop 文件后，Power BI Desktop 文件将独立于原始 Excel 工作簿，并且可以在不影响原始工作簿的情况下修改或更改（以及保存和共享）Power BI Desktop 文件。

导入完成后，将显示**摘要**页面，页面上会描述已转换项目并列出不能导入的所有项目。

![image](http://upload-images.jianshu.io/upload_images/10432152-1b7efdace780d4e4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

选择**关闭**后，将在Power BI Desktop 中加载该报表。 下图显示了导入 Excel 工作簿后 Power BI Desktop 的状态：Power BI Desktop 基于工作簿内容自动加载报表。

![image](http://upload-images.jianshu.io/upload_images/10432152-774cdac467db820a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

由于已导入工作簿，你可以继续处理报表（例如创建新的可视化效果、添加数据或创建新的报表页）以及继续使用 Power BI Desktop 中的所有功能和特性。

##4、  调整和合并数据

由于我们已经连接到数据源，我们需要调整数据以符合我们的需求。 有时候调整意味着 *转换* 数据，例如重命名列或表格、将文字更改为数字、删除行、将第一列设置为标题列等。

Power BI Desktop 中的查询编辑器除能在功能区中提供可用的工作，还能够充分利用右键菜单。 大部分可在**转换**功能区选择的内容也可通过右键单击项目（如某列）并从所显示的菜单中进行选择。

##5、   生成报表

加载表格之后可以进行其他更改，而且你可以重新加载模型来应用所做的任何更改。 但是目前这样就够了。 在 Power

BI Desktop 报表视图中，你可以开始生成报表。

报表视图具有五个主要区域：

######1)  功能区，用于显示与报表和可视化效果相关联的常见任务

######2)  报表视图或画布，可在其中创建和排列可视化效果

######3) 底部的页面选项卡，用于选择或添加报表页

######4)  可视化效果窗格，你可以在其中更改可视化效果、自定义颜色或轴、应用筛选器、拖动字段等

######5) 字段窗格，可在其中将查询元素和筛选器拖到报表视图，或拖到可视化效果的筛选器窗格

若要创建可视化效果，只需将字段从字段列表拖到报表视图即可。


![image](http://upload-images.jianshu.io/upload_images/10432152-d4114d8e06da85e8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##7、  共享报表

当我们已经有完整的 Power BI Desktop 报表，我们可以在 Power BI 服务上与他人共享。

有几种方法可以在 Power BI Desktop 中共享你的工作。 可以发布到 Power BI 服务，直接从 Power BI 服务上传 .pbix 文件，或保存 .pbix 文件，然后就像任何其他文件一样发送它。

![image](http://upload-images.jianshu.io/upload_images/10432152-28506aab5ed95908.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

当登录并完成此发布过程后，将看到以下对话框。

![image](http://upload-images.jianshu.io/upload_images/10432152-e1e026fd8eb6c2ea.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

而当登录到 Power BI 时，你将在该服务的**仪表板**、**报表**和**数据集**区域看到你刚加载的 Power BI

Desktop 文件。

#四、   相关论文

周敏.Power BI Premium 提供价格亲民的企业级功能[J].计算机与网络,2017,43(10):39.

王国平.Microsoft Power BI数据可视化与数据分析[M].北京：电子工业出版社.2018.

马世权著.从Excel到Power BI商业智能数据分析[M].北京：电子工业出版社.2018.

另附：工具官网指导：[https://docs.microsoft.com/zh-cn/power-bi/desktop-getting-started](https://docs.microsoft.com/zh-cn/power-bi/desktop-getting-started)
