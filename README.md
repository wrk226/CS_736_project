# CS_736_project

* NLP基础知识：

    * [一些基础模型的视频讲解](https://www.youtube.com/c/CodeEmporium/videos)
 
    * [非常全面的中文版ML+DL+NLP知识梳理](https://github.com/NLP-LOVE/ML-NLP)
    
    * [NLP入门](https://github.com/NLP-LOVE/Introduction-NLP) 
    
    * [cs224N的slide和note，NLP基础课](http://web.stanford.edu/class/cs224n/)
    
    * [cs224N的课程视频](https://www.youtube.com/watch?v=8rXD5-xhemo&list=PLoROMvodv4rOhcuXMZkNm7j3fVwBBY42z)
    
    * [八种常用的embedding方式](https://easyai.tech/blog/nlp-%E9%A2%86%E5%9F%9F%E9%87%8C%E7%9A%848-%E7%A7%8D%E6%96%87%E6%9C%AC%E8%A1%A8%E7%A4%BA%E6%96%B9%E5%BC%8F%E5%8F%8A%E4%BC%98%E7%BC%BA%E7%82%B9/)
 
    * [fastText讲解](https://www.jiqizhixin.com/articles/2018-06-05-3) 
    
      fastText 就是使用了subword n-gram思想，将同一个词语分解成等宽的几个substring，比如apple=[app,ppl,ple]。然后对每个substring分别计算embedding(类似word2vec)，最终词语的embedding是所有substring embedding vector之和。
      
      一个优势是同一个substring可能出现在不同word中（词根词缀），从而可以找出词与词之间的联系，而且有助于低频词甚至是未出现词语的表达。
      
      fastText另一个优势是使用了多层softmax用来加速。其实就是把本来的1对N的softmax变成了1对2对4对8...的二叉树形式，每个node就相当于一次逻辑回归，也即sigmoid。
      

* 一些有用的链接

    * [要用的数据和leaderboard](https://rajpurkar.github.io/SQuAD-explorer/)

