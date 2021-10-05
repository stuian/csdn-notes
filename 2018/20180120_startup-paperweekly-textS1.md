## papeweekly 自动文摘（一）感悟

2016-03-20

我的感受是非监督学习还有很大的进步空间，我们也必须让机器学会非监督学习，才能去接近真的人工智能。（因为我们人和动物的学习都是通过非监督）

目前深度学习在图片和语音上确实做的不错，但是在nlp上却不尽人意。笔者的理解是，前两者主要是一些技术问题，后者则更多的是要去解决理解方面的问题，毕竟语言的意思实在是太复杂了。

Christopher D. Manning在他的文章里说了这样一句话

>     However, I would encourage everyone to think about problems, architectures, cognitive science, and the details of human language, how it is learned, processed, and how it changes, rather than just chasing state-of-the-art numbers on a benchmark task.

大致意思是希望我们能去思考人类语言的问题，结构，认知科学和细节，而不只是仅仅去追求一个超过之前方法的模型。（唯”模型“论）


### 正文

### 1、作者的想法

> RSarxiv是一个arxiv paper数据库的搜索和个性化推荐系统。
> 基于查询的自动文摘

作者希望在arxiv上搜索论文的时候输入一个关键词，除了能返回一个paper列表，还能返回一个非常精炼的survey(了解每篇文章的核心内容)

### 2、文本摘要介绍

- 单文档摘要 or 多文档摘要

- 抽取式 or 生成式

- 人类语言包括字、词、短语、句子、段落、文档这几个level，研究难度依次递增，理解句子、段落尚且困难，何况是文档，这是自动文摘最大的难点。

#### 文本摘要发展的局限

- 评价

> 没有固定的标准

- 数据集

> 很难像机器翻译一样对数据集文本进行标准化

### NLU与NLG

![](https://pic3.zhimg.com/80/v2-807199dde25c6cb90051cf3cd2cdea97_hd.jpg)
