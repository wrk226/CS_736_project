# CS_736_project

* NLP基础知识：

    * [一些基础模型的视频讲解](https://www.youtube.com/c/CodeEmporium/videos)
 
    * [非常全面的中文版ML+DL+NLP知识梳理](https://github.com/NLP-LOVE/ML-NLP)
    
    * [NLP入门](https://github.com/NLP-LOVE/Introduction-NLP) 
    
    * [cs224N的slide和note，NLP基础课](http://web.stanford.edu/class/cs224n/)
    
    * [cs224N的课程视频](https://www.youtube.com/watch?v=8rXD5-xhemo&list=PLoROMvodv4rOhcuXMZkNm7j3fVwBBY42z)
    
    * [八种常用的embedding方式](https://easyai.tech/blog/nlp-%E9%A2%86%E5%9F%9F%E9%87%8C%E7%9A%848-%E7%A7%8D%E6%96%87%E6%9C%AC%E8%A1%A8%E7%A4%BA%E6%96%B9%E5%BC%8F%E5%8F%8A%E4%BC%98%E7%BC%BA%E7%82%B9/)
 
    * [fastText讲解](https://www.jiqizhixin.com/articles/2018-06-05-3) 
      <details>
      <summary>什么是fastText？</summary>
         fastText 就是使用了subword n-gram思想，将同一个词语分解成等宽的几个substring，比如apple=[app,ppl,ple]。然后对每个substring分别计算embedding(类似word2vec)，最终词语的embedding是所有substring embedding vector之和。
      
      一个优势是同一个substring可能出现在不同word中（词根词缀），从而可以找出词与词之间的联系，而且有助于低频词甚至是未出现词语的表达。
      
      fastText另一个优势是使用了多层softmax用来加速。其实就是把本来的1对N的softmax变成了1对2对4对8...的二叉树形式，每个node就相当于一次逻辑回归，也即sigmoid。
      </details>

    * [EM算法/期望极大算法(Expectation Maximization algorithm)](https://zhuanlan.zhihu.com/p/78311644) 
      <details>
      <summary>什么是似然函数？（Likelihood function）</summary>
         假设我们现在有一个硬币，随机投掷一次硬币出现正面的概率为p。
   
         现在我们连续投掷了两次硬币，结果硬币都是正面。       
         似然函数就是：p=0.1, 0.2, 0.3...的概率。         
         也即L=p^2(p代表正面朝上，p^2就是两次都是正面朝上)         
         简而言之，似然性，是用于在已知某些观测所得到的结果时，对有关事物之性质的参数进行估值。
      </details>
      <details>
      <summary>什么是MLE/最大似然估计？(maximum likelihood estimation)</summary>
         还是上面的例子，随机投掷一次硬币出现正面的概率为p，现在连续抛两次硬币都是正面，那么当p取什么值的时候似然性最大呢？
   
         显而易见，p=1的概率最大，也即当p=1时似然值最大。         
         而这个p=1就是我们的最大似然估计。         
         一般来说计算MLE的时候是先估计变量的分布（伯努利分布，指数分布，高斯分布...）每个分布里都会有自带的系数。         
         比如投硬币就符合伯努利分布，里面的系数就是之前提到的p。         
         有了变量分布公式后可以由此建立最大似然函数。然后找似然函数的最大值就完事了，一般可能涉及到求导，取log值之类的数学操作。
      </details>
            </details>
      <details>
      <summary>什么是EM算法？</summary>
         EM算法实质上就是当似然函数难以找出最大值的情况下采取的迭代计算方式。
   
         一般来说似然函数难以求导的原因是因为里面包含隐藏变量。         
         举个例子，投掷硬币，现在有硬币A,B,C,每次投掷的时候我都会先抛一次A（A的结果不作记录），如果A是正面的话就用B投掷，如果A是反面的话就用C投掷。用B或C的结果作为这一次抛掷的结果。这时候A的正反面概率就是隐藏变量，因为我们无法直接观测到A是正面还是反面。
   
         EM算法步骤如下：

         1. 给要求的参数基于一个随机的初始估计值
         2. 找到另一个能使似然函数变大的参数
         3. 不断迭代直到收敛

         显而易见，这里最重要的就是第二步，如何找到一个新的更好的参数。一般方式就是直接将初始值或者上一次迭代的值代入概率分布，然后计算出期望函数，最后求出期望函数的极大值和对应的新的参数。
      </details>

      
    
    * [HMM/隐马尔可夫模型(Hidden Markov model)](https://zh.wikipedia.org/wiki/%E9%9A%90%E9%A9%AC%E5%B0%94%E5%8F%AF%E5%A4%AB%E6%A8%A1%E5%9E%8B) 
      <details>
      <summary>什么是HMM？</summary>
      HMM模型是用于描述一个随机序列的模型。  
   
      这个随机序列中每一时刻（天）都有一个状态/隐藏变量/hidden variable（心情）和一个观测值（我的行为）。  
      HMM假设：1. 观测值（我的行为）仅仅取决于当前时刻的状态（今天心情）。2. 当前时刻的状态（今天心情）仅仅取决于前一时刻的状态（昨天心情）。  
      而HMM能解决的问题一般都是当一个随机过程中的某些值缺失时用于求解缺失值的方法。        
      求解HMM过程时我们会使用到的条件一般是：初始概率分布（第一天各种心情的概率），状态转移概率分布（前一天的心情对第二天心情的影响），观测概率分布（特定心情下我会做各种事的概率）  
      hmm经典三大问题：  
      1. 已知我这个月每天的行为，求解我下个月第一天会做什么(一般用前向算法，也即一天天往后推，一直推到下个月一号)
      2. 已知我这个月每天的行为，求解我这个月每天为各种心情的概率（前向后向算法都可以）
      3. 已知我这个月每天的行为，求解我这个月最可能的心路历程（一般用维特比(viterbi algorithm)算法，即每一步都求可能性的最大值就完事了，一个动态规划算法）
      
      求解过程基本就是简单的概率运算。  
      </details>
    
    * [CRF/条件随机场(Conditional Random Field)](https://www.cnblogs.com/kerwins-AC/p/9584862.html) 
    
      [CRF的直观理解](https://www.zhihu.com/question/35866596/answer/412520896) 
    
      <details>
      <summary>什么是CRF？</summary>
      一般在NLP中聊到的都是线性链条件随机场（linear chain CRF）
   
      CRF和HMM非常类似，只不过HMM的概率模型是有方向的，而CRF的概率模型是无方向的。     
      HMM中t时刻的状态仅仅与t-1时刻的状态有关，而CRF中t时刻的状态与t-1和t+1都有关（因为无方向嘛）。  
      HMM中想要求得t时刻的状态需要用t-1时刻的状态乘以状态转移矩阵，得到每个状态的概率值。然后再通过观测/发射(emission)概率矩阵来得到每个观测值的可能性。  
      而CRF中是直接使用特征函数进行打分，符合一个特征就+1分，不符合就为0。  
      这里的特征有两类，一类是t时刻与t-1,t+1时刻之间的关系特征。例1:如果昨天我心情不好，今天心情一定不会很好。例2:如果我明天开心，那么今天心情一定不会很差。  
      另一类是t时刻自己的特征。例:如果今天我心情不好就肯定不会出门购物  
      这里的特征都是非黑即白的，而且特征数量是不固定的。像HMM中，每个行动与心情都有一个对应的状态转移概率，但是CRF中就不是这样，可以一对多也可以多对一。  
      </details>
    

* 一些有用的链接

    * [要用的数据和leaderboard](https://rajpurkar.github.io/SQuAD-explorer/)

