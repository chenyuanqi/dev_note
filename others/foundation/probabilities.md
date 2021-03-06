
### 概率论
概率（Probability）就是描述了事件发生可能性的一个数值。  
概率论是对数据产生的过程进行建模，然后研究某种模型所产生的数据有什么特性。  

在概率的世界里，有很多概念。我们用随机变量（Random Variable）来描述事件所有可能出现的状态，使用概率分布 （Probability Distribution）来描述每个状态出现的可能性。  
随机变量又可以分为离散型随机变量（Discrete Random Variable）和连续型随机变量（Continuous Random Variable）。  
> 假设使用一个随机变量 x 来表示新闻类型，如果在 100 篇新闻中，有 60 篇是娱乐新闻，有 20 篇是科技新闻，有 20 篇是体育新闻。  
> 那么看到娱乐新闻的概率就是 60%，看到科技新闻的概率就是 20%，看到体育新闻的概率就是 20%。这三组数据就可以构成变量 x 的**概率分布**P(x)。  
> 再添加另一个随机变量 y，表示新闻属于国际的还是国内的，新的概率分布就需要由 x 和 y 这两个变量联合起来才能决定，这种概率就称为**联合概率（Joint Probability）**。  
> 对于离散型随机变量，通过联合概率 P(x, y) 在 y 上求和，就可以得到 P(x)，这个 P(x) 就是**边缘概率（Marginal Probability）**。对于连续型随机变量，我们可以通过联合概率 P(x, y) 在 y 上的积分，推导出边缘概率 P(x)。  
> 边缘概率可以帮助我们去除那些不需要关心的事件，把联合概率转换为非联合概率，例如从 P(x, y) 得到 P(x)，从而忽略 y 事件。  
> 对于多个随机变量，还有一个很重要的概念是**条件概率**：某个事件受其他事件影响之后出现的概率。比如在国际新闻中出现科技新闻的概率就是 5/30=16.67%。  

### 贝叶斯定理
贝叶斯定理（Bayes’ theorem）

### 朴素贝叶斯分类算法
朴素贝叶斯（Naive Bayes）分类算法  

### 信息熵
如信息熵（Entropy）

### 决策树
决策树（Decision Tree）