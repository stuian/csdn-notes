## paperweekly 自动文摘（三~）

### Abstractive ###

#### 难点 ####

1. 理解文档
1. 可读性强
1. 简练总结

#### 评价 ####

自动文摘最大的一个难点是评价问题，如何有效地、合理地评价一篇文摘的效果是一个很难的问题。

标注语料问题。自动评价需要给定一系列文档以及他们的参考文摘，用来测试不同的算法效果。TAC（Text Analysis Conference）和TREC（Text REtrieval Conference）两个会议提供了相关的评测数据集

现有的评价标准存在的一个重要问题在于没有考虑语义层面上的相似，评价extractive还好，但评价abstractive就会效果不好了。

> 突破点：在词、句子甚至段落这个层面上的表示学习研究的非常多，也有很多的state-of-the-art的结果，所以做语义层面上的评价并不难。


## abstrative（2016年3月份之前）的技术 ##

- Encoder-Decoder（2014）
> decoder部分其实类似于语言模型

- Attention Mechanism（2015）
- Neural Summarization

使用deep learning技术来做abstractive summarization的paper屈指可数，大体的思路也类似，大概如下：

0、首先将自动文摘的问题构造成一个seq2seq问题，通常的做法是将某段文本的first sentence作为输入，headlines作为输出，本质上变成了一个headlines generative问题。

1、选择一个big corpus作为训练、测试集。自动文摘的技术没有太成熟的一个重要原因在于没有一个成熟的大规模语料。一般来说都选择Gigawords作为训练、测试集，然后用DUC的数据集进行验证和对比。

2、选择一个合适的encoder，这里可以选simple rnn，lstm rnn，gru rnn，simple birnn，lstm birnn，gru birnn，deep rnn，cnn，以及各种各样的cnn。不同model之间的组合都是一种创新，只不过创新意义不太大。用encoder将输入文本表示成一个向量。

3、选择一个合适的decoder，decoder的作用是一个language model，用来生成summary words。

4、设计一个合适的attention model。不仅仅基于encoder last hidden state vector和上文来预测输出文本序列，更要基于输入中“注意力”更高的词来预测相应的词。

5、设计一个copy net。只要是语言模型都会存在相同的问题，比如out-of-vocabulary词的处理，尤其是做新闻类摘要的生成时，很多词都是人名、机构名等专有名词，所以这里需要用copy net 将输入中的词copy过来生成输出。在生成中文摘要问题上，将words降维到characters可以避免oov的问题，并且取得不错的结果。（为什么？）