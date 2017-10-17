# text-classification

文本分类是基本的NLP问题。在实际的应用中，需要在国外为一些科技企业做online marketing（网络流量的获取；商业主要有四个方面，流量；展示-电商短板，餐饮环境永不可取代；销售-电商；提货-快递），文本分类的需求来自两个方面：一是资讯内容的分类，二是特定类别的资讯中预测高阅读量文章。中文的文本分类与英文的文本分类，方法不见得完全相同，也有人在做，个人只做过中文文本数据的预处理。

文本分类的pilot research，数据有以下几个类型：
1. sentiment analysis
* 电影评论数据，标准数据集
* twitter data

2. topic analysis
* game title, provided by Siraj Raval in youtube lectures
* reddit api data, 类别由用户自己选择，可能有标注错误，不是标准数据集，不适合在初步建模中使用

文本分类产品的test效果展示，可以在github上下载项目，修改数据文件，运行python程序，就能看到分类的结果。

## How to frame problems in text classification
