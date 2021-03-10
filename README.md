# CS_736_project

* NLP基础知识汇总：

    * [【推荐！】SQuAD官方指南以及相关模型解析](http://web.stanford.edu/class/cs224n/project/default-final-project-handout-squad-track.pdf)
    
    * [【必看！】SQuAD任务变种解析](http://web.stanford.edu/class/cs224n/project/default-final-project-handout-robustqa-track.pdf)

    * DL+ML全中文讲解(李宏毅2020)[课程主页](http://speech.ee.ntu.edu.tw/~tlkagk/courses_ML20.html) [B站链接](https://www.bilibili.com/video/BV1JE411g7XF)

    * [一些基础模型的视频讲解](https://www.youtube.com/c/CodeEmporium/videos)
 
    * [非常全面的中文版ML+DL+NLP知识梳理](https://github.com/NLP-LOVE/ML-NLP)
    
    * [NLP入门](https://github.com/NLP-LOVE/Introduction-NLP) 
    
    * 2019版CS224N[[课件]](http://web.stanford.edu/class/cs224n/)[[课程视频(中文字幕)]](https://www.bilibili.com/video/BV1s4411N7fC)
    
    * 2017版CS224N[[课件]](https://web.stanford.edu/class/archive/cs/cs224n/cs224n.1174/syllabus.html)[[课程视频(中文字幕)]](https://www.bilibili.com/video/BV1pt411h7aT)
    
      <details>
      <summary>19和17版的区别</summary>
      17版课程作业用的是tensorflow, 19版用的是pytorch   
   
      19版里多了character models, transformers,  multitask learn等内容
      </details>
    
    * [某NLP大佬的17版CS224N的课程笔记](https://www.hankcs.com/?s=cs224n)
    
    * [Andrew Ng 深度学习入门（中文字幕）](https://www.bilibili.com/video/BV1gb411j7Bs)


    
   
* 一些有用的链接

    * [要用的数据和leaderboard](https://rajpurkar.github.io/SQuAD-explorer/)
    
* 论文阅读
    * 关系抽取-RE(Relation Extraction)
      * [综述](https://arxiv.org/abs/2004.03186) [翻译版](https://blog.csdn.net/weixin_42691585/article/details/105561709)
         <details>
         <summary>笔记</summary>
         关系抽取是指从文本中抽取关系事实.现如今由于网络文本爆发式增长，所以需要构建更有效的模型。  
   
         优化方向具体分为三类:  
         1. 如何利用更多的数据    
            远程监督(即自动标记),但是会出现很多noise，所以需要使用种种方式来去噪  
         2. 当样本不足时,如何更有效的利用现有的数据  
            few shot：使用优质资源训练出更robust的模型然后套用到新任务上：  
               1.metric learning：度量现有数据和训练示例的距离，然后对查询进行分类  
               2.meta-learning:元学习  
         3. 如何处理更复杂的上下文  
            1.提取句子内关系  
            2.构建句子间实体图  
         4. 如何面向更多的开放域(现实中不断有新的关系生成)  
         关系抽取流程:  
         1. 一个命名体识别器,用于从文本中识别命名实体.  
         2. 一个实体连接器,用于将实体连接到现有知识图谱  
         3. 一个关系分类器,用于确定给定上下文的实体之间的关系(最难,因为需要理解上下文)  
         </details>
    * 命名实体识别-NER(Named Entity Recognition)
      * [综述](https://arxiv.org/abs/1812.09449) [翻译版](http://pelhans.com/2019/09/23/kg_paper-note4/#%E6%8C%87%E9%92%88%E7%BD%91%E7%BB%9C)
         <details>
         <summary>笔记</summary>
         命名实体识别是用来识别命名实体的文本范围，并将之分类为预定义的类别，例如人，位置，组织等。  
   
         一般做命名实体识别有三种方式：   
         1. 基于手工制定的规则：麻烦，适合数据量特别小的情况  
         2. 无监督方式：不准确  
         3. 基于特征的机器学习：需要精心设计特征+HMM,CRF,DT...  
         4. 基于深度学习：可以端到端  
         流程：  
         1. 输入的分布式表示：embedding和其他人工特征  
         2. 语义编码：通过CNN,RNN,LM,Transformer获得语义信息  
         3. 标签解码：通过MLP,CRF,RNN,PN输出分类结果  
         </details>
    * 文本分类-TC(Text Classification)
      * [综述](https://arxiv.org/abs/2004.03705v1) [翻译版](https://blog.csdn.net/qq_38331611/article/details/106995742)
         <details>
         <summary>笔记</summary>
         常见分类任务：情感分类，新闻分类，话题分类，QA问答，自然语言推理(NLI)  
         QA问答：抽取式：基于问题对句子做分类，选择个别句子作为答案。生成式：不属于TC
         自然语言推理：一段文字是否由另外一段文字推理得出的:Y/N  
         常见方法：feed-forward,RNN,CNN...
         
         
         
         </details>
