
# Robobrowser——一个轻量级爬虫库
---------------------------------------
>常用于爬虫和简单的web测试，纯python编写，用起来很方便，语法自然，且易学。另外，robobrowser建立在requests和BeautifulSoup之上，容易被人们接受。官方介绍Robobrowser是：Your friendly neighborhood web scraper。

## 实现原理
---------------------------------------
### 要点
- RoboState类里，页面上内容的抓取和处理实际上委托给了BeautifulSoup。RoboState类的_parsed对象实际上就是BeautifulSoup的实例；

- RoboState类中保存了每个请求的响应内容——response.content；

- RoboBrowser类里，发送请求的方法实际上委托给了requests类——session;

- RoboBrowser类里比较复杂就是保存每次访问的状态，以及实现back和forward功能。其主要思想是把所有的访问历史都放在内存里，然后通过游标去访问；

- 每次页面发生变化，也就是open和submit_form之后都会调用_update_state方法去更新当前状态；
- [点击这里](https://github.com/jmcarp/robobrowser) 了解详情.

### 流程梳理
- RoboBrowser()实例化的时候，会new 1个requests的session用于发送http请求,同时初始化游标为－1并且当前的status列表初始化为空;

- RoboBrowser.open(url)方法调用时，session对象会访问具体的url，然后更新游标和status列表。基本思想是往status列表里append 1个新new出来的RoboState对象；

- RoboBrowser.find()方法调用时，使用当前游标处的state对象的_parsed对象的find方法去抓取页面内容，实际上就是BeautifulSoup的find方法；

## 安装Robobrowser
---------------------------------------
- 使用pip安装：<pre><code>      
        pip install robobrowser -i http://pypi.douban.com/simple/
</code></pre>

## 小例子
---------------------------------------
- **新建1个start.py文本文件，代码如下**
<pre><code>      
        import re
        from robobrowser import RoboBrowser

        b = RoboBrowser(history=True)
        b.open('http://itest.info/courses/2')

        title = b.select('.headline h2')
        print title[0].text

        infos = b.select('h4')

        for info in infos:
            print info.text
</code></pre>

## 文档查询
---------------------------------------
- **robobrowser自带文档shu说明，命令行运行：**
<pre><code>        
        python -m pydoc -p 1234
</code></pre>

## 简单的爬虫
---------------------------------------
### 代码讲解
<pre><code>        
        import re
        from robobrowser import RoboBrowser

        url = 'http://itest.info/courses/2'
        b = RoboBrowser(history=True)
        b.open(url)

        class_name = b.select('.headline h2')
        print class_name[0].text

        class_desc = b.select('.tag-box')
        print class_desc[0].text 

        class_time = b.select('h4')
        print class_time[0].text

        teacher = b.select('.thumbnail-style h3')
        print teacher[0].text

        qq = b.find(text=re.compile('QQ'))
        print qq

        qq_group = b.find(text=re.compile('\+selenium'))
        print qq_group
</code></pre>
  
- b = RoboBrowser(history=True) b.open(url) 用来创建browser和打开url；
- b.select() 方法可以接受css选择器，返回页面上所有符合条件的元素的集合，也就是说返回的是list，可以进行迭代；
- b.find()，只返回1个精确的结果；
- 注意，find和select方法返回的均是Beautiful Soup的tag对象或对象集合；

## 抓取制定内容
---------------------------------------
### 背景
 robobrowser支持Beautiful Soup，一般来说通过下面3个方法获取页面上感兴趣的内容
     - find
     - find_all
     - select
     
### find方法
  find方法是返回页面上符合条件的第1个元素。<pre><code>        
        import re
        from robobrowser import RoboBrowser
        url = 'http://itest.info/courses/2'
        b = RoboBrowser(history=True)
        b.open(url)

        title = b.find('title')  
        print title.text

        img = b.find(id='logo-header')
        print img['src']

        print b.find(href='/courses/4').text

        print b.find(class_='active', text=re.compile('python')).text
</code></pre>

### find_all方法
 find_all方法的用法跟find基本相同，但是find_all会返回所有符合条件的tag的集合(ResultSet)。<pre><code>        
        import re
        from robobrowser import RoboBrowser

        url = 'http://itest.info/courses/2'
        b = RoboBrowser(history=True)
        b.open(url)

        all_links = b.find_all('a')  
        for link in all_links:
        print link.text

        divs = b.find_all(class_='container')
        print divs

        first_two_p = b.find_all('p', limit=2)
        print first_two_p

        print b.find_all(['meta', 'img'])
</code></pre>

### select方法
 select方法支持css选择器，返回的是list。<pre><code>        
        import re
        from robobrowser import RoboBrowser

        url = 'http://itest.info/courses/2'
        b = RoboBrowser(history=True)
        b.open(url)

        all_links = b.select('a')  
        for link in all_links:
        print link.text

        divs = b.select('.container')
        print len(divs)
</code></pre>

### 其他技巧
- 找到页面上所有具有id属性的元素  b.find_all(id=True)
- 不递归查找元素。也就是说只在的直接子后代中查找  b.find('p', recursive=False)

##  follow_link
---------------------------------------
### 方法介绍
 robobrowser的  follow_link  方法可以点击链接并自动完成跳转。<pre><code>        
        import re
        from robobrowser import RoboBrowser
        url = 'http://www.qq.com/'
        b = RoboBrowser(history=True)
        b.open(url)

        today_top = b.find(id='todaytop').a  
        print today_top['href']
        b.follow_link(today_top)

        title = b.select('.hd h1')[0]
        print '*************************************'
        print title.text
        print '*************************************'

        print b.find(id='articleContent').text
</code></pre>
- follow_link的用法，一般来说都是用find/select/find_all方法过滤出相应的链接，然后调用b.follow_link(link)的方式去点击该链接。

## 表单操作
---------------------------------------
### 方法介绍
<pre><code>        
        import re
        from robobrowser import RoboBrowser

        url = 'http://testerhome.com/account/sign_in/'
        b = RoboBrowser(history=True)
        b.open(url)

        login_form = b.get_form(action='/account/sign_in')
        print login_form

        login_form['user[login]'].value = 'your account'
        login_form['user[password]'].value = 'your password'

        b.submit_form(login_form)
        print b.select('.alert.alert-success')[0].text
</code></pre>

- get_form  方法用来抓取form;
- submit_form  方法用来提交表单;
- form[name].value=  方法用来给文本框赋值，也就是说往文本框里写内容;

## Beauiful Soup的过滤器
---------------------------------------
### 字符串
最简单的过滤器是字符串.在搜索方法中传入一个字符串参数,Beautiful Soup会查找与字符串完整匹配的内容,下面的例子用于查找文档中所有的b标签:<pre><code>
        soup.find_all('b')
</code></pre>

### 正则表达式
如果传入正则表达式作为参数,Beautiful Soup会通过正则表达式的 match() 来匹配内容.下面例子中找出所有以b开头的标签,这表示  body  和  b  标签都应该被找到:<pre><code>
        import re
        for tag in soup.find_all(re.compile("^b")):
            print(tag.name)
</code></pre>

下面代码找出所有名字中包含”t”的标签:<pre><code>
        for tag in soup.find_all(re.compile("t")):
            print(tag.name)
</code></pre>

### 列表
如果传入列表参数,Beautiful Soup会将与列表中任一元素匹配的内容返回.下面代码找到文档中所有  a  标签和  b  标签:<pre><code> 
        soup.find_all(["a", "b"]) 
</code></pre>

### True
True 可以匹配任何值,下面代码查找到所有的tag,但是不会返回字符串节点<pre><code>        
        for tag in soup.find_all(True):
            print(tag.name)
</code></pre>

### 方法
如果没有合适过滤器,那么还可以定义一个方法,方法只接受一个元素参数 ,如果这个方法返回 True 表示当前元素匹配并且被找到,如果不是则反回 False

下面方法校验了当前元素,如果包含 class 属性却不包含 id 属性,那么将返回 True:<pre><code>        
        def has_class_but_no_id(tag):
            return tag.has_attr('class') and not tag.has_attr('id')
</code></pre>

将这个方法作为参数传入 find_all() 方法,将得到所有标签：<pre><code>       
        soup.find_all(has_class_but_no_id)
</code></pre>

> 常用于爬虫和简单的web测试，纯python编写，用起来很方便。
