## Hownet 知网

- #### [Welcome to  Hownet](http://www.keenage.com/html/c_index.html)
- #### 简介：
    <font size=3>知网（Hownet）是我国计算语言学家董振东、董强在上世纪90年代提出并制作的一个常识知识库。知网以汉语和英语的词汇所代表的概念为描述对象，意在揭示概念与概念之间及概念所具有的属性之间的关系。这也是知网对“知识”的定义，将知识看做一种系统关系，并将之结构化、可视化，就是知网所做的事情。
</font>

- #### 知网的特点：
    <font size=3>知网采用意义分解的方法来描述概念。它从词语的义项中抽取出最小的意义单位（即义原），用义原和角色关系来描述词汇和词汇概念。义原不仅是知网中最小的语义单位，也是知网知识系统的基本单位。在这个过程中，董振东和董强先生始终坚持“分类宜粗不宜细，特征描述宜粗不宜细”的原则，使得知网2000个义原都是唯一而没有歧义的。
    
    事件概念分类的双轴轮（Biaxial Theory）是知网构架的支点，充分揭示了事物间复杂的关系，便于建立概念的描述体系和建立推理机制。知网中事件可以分为动态和静态两种，静态的事件又可以分为表示关系的和表示事物发展状态的，动态的事件表示行为动作的“改变”。在知网中，事件共计812类，除事件自身这一最高类别外，静态事件有215类，动态事件有596类。静态事件中，表示关系的有52类，表示状态的有163类。动态事件中，与静态事件中表示关系的相对应，即表示改变关系的有222类，而与静态事件中表示状态的相对应，即表示改变状态的有336类。在596类动态事件中，还包括了38类被知网称为“泛动”的事件，就是表示“行动”但没有明确表示改变关系还是改变状态的词，例如“试”“做”等。
</font>
    
- #### 知网系统的概貌：
    <font size=3>知网系统包括了下列数据文件和程序：</p>**1. 中英双语知识词典**：包含内容有框架网描写的词汇和义原释义及语义角色。根据事件、实体属性、第二特征等分类别放置；</br>![知网文档分类.png](http://upload-images.jianshu.io/upload_images/1860473-4335a921b805dd99.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)</p>**2. 知网管理工具**：包含了知网的概念计算工具和语义相似度计算工具及其API；</br>![知网工具说明.png](http://upload-images.jianshu.io/upload_images/1860473-e62e328883beed62.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)</p>**3. 知网说明文件**：</br>&emsp;&emsp;动态角色与属性，</br>&emsp;&emsp;词类表，</br>&emsp;&emsp;同义、反义以及对义组的形成，</br>&emsp;&emsp;事件关系和角色转换，</br>&emsp;&emsp;标识符号及其说明</br>![知网API.png](http://upload-images.jianshu.io/upload_images/1860473-8f417c46ce998a46.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)</p>

    基于知网的义原分析，我们可以计算词语之间的相似度以及抽取词语框架。最新版本的知网规模如下：</br>
![知网规模.png](http://upload-images.jianshu.io/upload_images/1860473-d06e4cc6e823718b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

</font>

- #### 相关论文
1. Dong. Zhendong. Knowledge description: what, how, and who ?[A]. Manuscript & Program of International Symposium on Electronic Dictionary [C]. Tokyo:1988.18.
2. Zhendong Dong, Qiang Dong. HowNet and the Computation of Meaning [M]. Singapore:World Scientific Publishing Company, 2006.
3. 董振东、董强、郝长伶，知网的理论发现 [J]中文信息学报，2007.7.
4. 刘群，李素建，基于《知网》的词汇语义相似度计算 第三届中文词汇语义学研讨会论文集
5. Yilin Niu, Ruobing Xie, Zhiyuan Liu, Maosong Sun. Improved Word Representation Learning with Sememes. In ACL, 2017.
6. Ruobing Xie, Xingchi Yuan, Zhiyuan Liu, Maosong Sun. Lexical Sememe Prediction via Word Embeddings and Matrix Factorization. In IJCAI, 2017.
7. Xiangkai Zeng, Cheng Yang, Cunchao Tu, Zhiyuan Liu, Maosong Sun. Chinese LIWC Lexicon Expansion via Hierarchical Classification of Word Embeddings with Sememe Attention. In AAAI, 2018.
