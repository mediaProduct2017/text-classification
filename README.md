# text-classification

文本分类是基本的NLP问题。在实际的应用中，需要在国外为一些科技企业做online marketing（网络流量的获取；商业主要有四个方面，流量；展示-电商短板，餐饮环境永不可取代；销售-电商；提货-快递），文本分类的需求来自两个方面：一是资讯内容的分类，二是特定类别的资讯中预测高阅读量文章。所以需要对英文文本进行分类。

中文的文本分类与英文的文本分类，方法不见得完全相同，未来也打算做，目前，个人只做过中文文本数据的预处理，分词、提取特征词、词云分析等。在中文建模部分，大概知道理论上应该怎么做，但没有实际做过中文文本分类的完整模型。

文本分类的pilot research，数据有以下几个类型：
1. sentiment analysis

[learn-SentimentAnalysis](https://github.com/mediaProduct2017?tab=repositories)

* 电影评论数据（正面或负面评价），标准数据集
naturally labeled data; automatically labeled data, mannually labeled data, unlabeled data

得到的模型可以用于transfer learning, 监测电影口碑的舆情

* twitter data（积极或消极）

2. topic analysis

[topic-classifier](https://github.com/mediaProduct2017/topic-classifier)

[lstm-classification](https://github.com/arfu2016/nlp/tree/master/nlp_models/lstm-classification)

[Text Classification with CNN and RNN](https://github.com/arfu2016/text-classification-cnn-rnn)

* reddit api data, 类别由用户自己选择，可能有标注错误，不是标准数据集，不适合在初步建模中使用

3. 文本（或标题）与用户评价、用户阅读量的联系

[text-reco](https://github.com/mediaProduct2017/text-reco)

* game title, provided by Siraj Raval in youtube lectures，标题与用户评价的联系

文本分类产品的test效果展示，可以在github上下载项目，修改数据文件，运行python程序，就能看到分类的结果。

4. fasttext

[FastText using pre-trained word vector for text classification](https://stackoverflow.com/questions/47692906/fasttext-using-pre-trained-word-vector-for-text-classification)

FastText's native classification mode depends on you training the word-vectors yourself, using texts with known classes. The word-vectors thus become optimized to be useful for the specific classifications observed during training. So that mode typically wouldn't be used with pre-trained vectors.

If using pre-trained word-vectors, you'd then somehow compose those into a text-vector yourself (for example, by averaging all the words of a text together), then training a separate classifier (such as one of the many options from scikit-learn) using those features.

FastText supervised training has -pretrainedVectors argument which can be used like this:

    $ ./fasttext supervised -input train.txt -output model -epoch 25 \
           -wordNgrams 2 -dim 300 -loss hs -thread 7 -minCount 1 \
           -lr 1.0 -verbose 2 -pretrainedVectors wiki.ru.vec
           
Few things to consider:

Chosen dimension of embeddings must fit the one used in pretrained vectors. E.g. for Wiki word vectors is must be 300. It is set by -dim 300 argument.

As of mid-February 2018, Python API (v0.8.22) doesn't support training using pretrained vectors (the corresponding parameter is ignored). So you must use CLI (command line interface) version for training. However, a model trained by CLI with pretrained vectors can be loaded by Python API and used for predictions.

For large number of classes (in my case there were 340 of them) even CLI may break with an exception so you will need to use hierarchical softmax loss function (-loss hs)

Hierarchical softmax is worse in performance than normal softmax so it can give up all the gain you've got from pretrained embeddings.

The model trained with pretrained vectors can be several times larger than one trained without.
In my observation, the model trained with pretrained vectors gets overfitted faster than one trained without           

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
