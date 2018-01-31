## ROCStory 数据集介绍

### 2017级 计算机应用技术 刘璐 201721198590
这个语料库是我现在学习和工作中接触的最多的一个，所以在本次大作业中拿出来分享一些我对于这个语料库的理解，以及我在工作中做的一些笔记和一些我看过的相关的论文。
### ==download web：==
http://cs.rochester.edu/nlp/rocstories/
---

### ==paper for this dataset and evaluation==
https://arxiv.org/pdf/1604.01696.pdf
---

### ==introduction==
- #### background
    - Representation and learning of commonsense knowledge is one of the foundational problems in the quest to enable deep language understanding;

    - Story understanding is an extremely challenging task in natural language understanding with a longrunning history in AI ;
    
    - This issue is particularly challenging for understanding causal and correlational relationships between events（事件之间的因果和相关关系）;

    - Recently, there has been a renewed interest in story and narrative understanding based on progress made in core NLP tasks. 

    - research has been hindered（阻碍） by the lack of a proper evaluation framework.

- #### main goals:
    - The corpus contains a variety of commonsense causal and temporal relations between everyday events. *该语料库注重常识关系和因果关系的构建*
    - The corpus is a high quality collection of nonfictional daily short life stories.*该语料库只包含真实事件（这种真实指的是不含虚构内容，比如说一只小狗踢足球等等）*

- #### example of this corpus:
| storyid |	storytitle	| sentence1 | sentence2	| sentence3	| sentence4 |	sentence5 |
| :-------- | --------:| :--: |:--: |:--: |:--: |:--: |
|9a51198e-96f1-42c3-b09d-a3e1e067d803 |	Overweight Kid	|Dan's parents were overweight .|	Dan was overweight as well .|	The doctors told his parents it was unhealthy .|	His parents understood and decided to make a change .	|They got themselves and Dan on a diet .|
617e7ada-3878-488d-bd56-40695b91f053|	The Bike Accident|	Carrie had just learned how to ride a bike .	|She didn't have a bike of her own .|	Carrie would sneak rides on her sister's bike .	|She got nervous on a hill and crashed into a wall .|	The bike frame bent and Carrie got a deep gash on her leg .|
79b0da1f-e460-4173-ba58-8c9e2553c53a|	Beach|	Morgan enjoyed long walks on the beach .|	She and her boyfriend decided to go for a long walk .|	After walking for over a mile , something happened .|	Morgan decided to propose to her boyfriend .|	Her boyfriend was upset he didn't propose to her first .|
d173b7de-4611-4cdf-934c-912834755e41	|The bad customer .|Jane was working at a diner .|	Suddenly , a customer barged up to the counter .	|He began yelling about how long his food was taking .|	Jane didn't know how to react .|	Luckily , her coworker intervened and calmed the man down .|
---

### ==the evaluation framework for this corpus==
- This system is given a four-sentence ‘context’ and two alternative endings to the story, called ‘right ending’ and ‘wrong ending’. 
- Hence, in this test the fifth sentence is blank. Then the system’s task is to choose the right ending. 
- 简单来说：这个评测就是给出一个故事的plot(前四句话)，让你的模型在训练之后在两个ending（只有一个正确）中选择正确的结局。算是一个二分类问题。
- examples:
![image](https://note.youdao.com/yws/public/resource/73e29effc5e0cc0d936657213e813746/xmlnote/BF192F26C8664F83A218F688D4B358F6/519)
- 这个评测现在有很多人在做，后面我会附上一些现有的成果paper。 
---

### ==our work for this corpus:==
- 我们做的是一个故事生成的任务，旨在根据故事的plot(前4句话)，生成故事的结局（ending，最后一句）
- 现在主要用到的方法：
    - seq2seq+attn
    - RL
    - external knowledge（还在尝试）
---

### ==references==
#### for this corpus:
- [A Corpus and Cloze Evaluation for Deeper Understanding of Commonsense Stories](https://arxiv.org/pdf/1604.01696.pdf)

#### for the evaluation works:
1. [An RNN-based Binary Classifier for the Story Cloze Test.](http://www.aclweb.org/anthology/W17-0911)
2. [Story Cloze Evaluator: Vector Space Representation Evaluation by Predicting What Happens Next](http://www.aclweb.org/anthology/W16-2505)
3. [Reasoning with Heterogeneous Knowledge for Commonsense Machine Comprehension](http://www.aclweb.org/anthology/D17-1216)
4. [Story Comprehension for Predicting What Happens Next](http://www.aclweb.org/anthology/D17-1168)
