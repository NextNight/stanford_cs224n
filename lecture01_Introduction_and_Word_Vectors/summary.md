# 第一章节的个人阅读总结

第一章节主要讲了词向量的发展历程，主要是以下三个部分：
- one-hot词向量
- 基于共现矩阵的矩阵分解的词向量[LSA]
- 基于语言模型的模型训练的词向量[word2vec]
由于NLP任务的第一步就是向量化，所以如何得到词向量是很重要的，而最简单的就是one-hot，但是one-hot不能表示单词之间的关系，单词间相互独立，不
能体现单词间的相似度，并且单词向量的维度巨大(等于词表的大小)，十分稀疏(只有一个位置为1，其他为0)，因此提出了利用SVD矩阵降维的思路，对文档-单
词的共现矩阵进行分解，这样可以在空间上表示单词的相似度同时也可以得到低位的稠密向量，然而当文档过多的时候维护的矩阵过于巨大，导致计算困难，因此
提出了单词-单词的共现矩阵，相比于文档-单词的矩阵消耗的空间小了很多。但是随着文档数增多词汇表仍然很大而且这个矩阵十分稀疏(因为有大部分的词没有
共现数据)。基于矩阵的分解这种方式需要频繁的矩阵更新和矩阵分解，计算过程复杂。最后在神经网络兴起的时候提出了训练`语言模型`的词向量生成方式
word2vec，通过训练一个语言模型并优化迭代，最终得到稠密的词向量表示，既能够体现单词的语义信息又能够表示单词间的空间关系。在这里主要是详细讲解
word2vec的两种算法cbow和skip-gram的原理，以及两种优化算法hierarchical softmax和Negative sampling的原理。采用两种优化算法的本质是加快
训练速度`由于在原始的softmax作为输出的时候，算法的更新参数是所有的单词向量矩阵，而softmax归一化的时候同样需要计算一个向量与整个词表的向量的
点积和，`这就是第一章节的全部内容。

# 关于相关读物的简单介绍

- word2vec原始论文：[Efficient Estimation of Word Representations in Vector Space](./doc/Efficient%20Estimation%20of%20Word%20Representations%20in%20Vector%20Space.pdf)：介绍了cbow和skip-gram
- word2vec优化:[distributed-representations-of-words-and-phrases-and-their-compositionality](./doc/distributed-representations-of-words-and-phrases-and-their-compositionality.pdf):介绍了hierarchical softmax和Negative sampling
- 一个简单的难以超越的句子向量表示：[A SIMPLE BUT TOUGH-TO-BEAT BASELINE FOR SENTENCE EMBEDDINGS](./doc/A%20SIMPLE%20BUT%20TOUGH-TO-BEAT%20BASELINE%20FOR%20SENTENCE%20EMBEDDINGS.pdf)
如何优化词向量。

# 关于作业的说明
- 课程作业：[exploring_word_vectors.ipynb](./job/exploring_word_vectors.ipynb)
    - 说明：主要是介绍单词类比和相似度，通过一些案例来发现存在的问题。其中要下载Google-new的词向量，比较大，需要科学上网,有需要可以联系。
- 练习题：[Gensim word vector visualization.ipynb](./job/Gensim word vector visualization.ipynb)
    - 说明：使用Gensim工具加载 glove词向量，并转换成word2vec的格式，然后展示单词的相似度，单词类比，以及对部分词向量PCA降维可视化。展现
    出单词之间关系，需要跟根据提示下载glove的词向量。

# 关于笔记和幻灯片
- 笔记：笔记中标注了部分翻译可以查看
    