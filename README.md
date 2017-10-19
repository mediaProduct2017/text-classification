# text-classification

文本分类是基本的NLP问题。在实际的应用中，需要在国外为一些科技企业做online marketing（网络流量的获取；商业主要有四个方面，流量；展示-电商短板，餐饮环境永不可取代；销售-电商；提货-快递），文本分类的需求来自两个方面：一是资讯内容的分类，二是特定类别的资讯中预测高阅读量文章。所以需要对英文文本进行分类。

中文的文本分类与英文的文本分类，方法不见得完全相同，未来也打算做，目前，个人只做过中文文本数据的预处理，分词、提取特征词、词云分析等。在中文建模部分，大概知道理论上应该怎么做，但没有实际做过中文文本分类的完整模型。

文本分类的pilot research，数据有以下几个类型：
1. sentiment analysis
* 电影评论数据（正面或负面评价），标准数据集
* twitter data（积极或消极）

2. topic analysis
* reddit api data, 类别由用户自己选择，可能有标注错误，不是标准数据集，不适合在初步建模中使用

3. 文本（或标题）与用户评价、用户阅读量的联系
* game title, provided by Siraj Raval in youtube lectures，标题与用户评价的联系

文本分类产品的test效果展示，可以在github上下载项目，修改数据文件，运行python程序，就能看到分类的结果。

## How to frame problems in text classification

## 算法的选择

深度学习之前的常用算法是naive bayesian（朴素贝叶斯）和SVM（支持向量机），近年来，随着深度学习技术的进步，众多文献显示深度学习有着更好的效果。RNN with LSTMs和CNN是最基本的深度学习算法，所以首先尝试这两个算法。

另外，看到的2015年的一篇论文报道了一种基于EMD和类似KNN思想的一种算法，我也进行了尝试。

最后还是决定用deep learning来做。deep learning相对EMD有三大优势：第一，准确率更高；第二，虽然EMD速度更快，但主要是胜在不需要训练，deep learning的模型训练好以后，在test阶段，二者是差不多的，甚至test阶段deep learning的模型还要更快一些；第三，当前deep learning的技术发展很快，全世界很多研发人员精力都放在deep learning上，如果未来这个方向继续有技术突破，我们能很快用在我们的产品上。

未来，还需要尝试的深度学习算法包括facebook的FastText（基于CNN）、TextCNN（CNN用于文本分类的开山模型）、CNN+RNN、RCNN、Bi-GRU（RNN的一种）等方法。最终确定适合具体的分类问题的算法。

## 产品

* 电影评论的情感分析产品（需要选择最为合适的算法）

* 科技类资讯分类产品

* 资讯阅读量预测产品
