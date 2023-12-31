[GNN入门之路: 01.图拉普拉斯矩阵的定义、推导、性质、应用](https://zhuanlan.zhihu.com/p/368878987)

[GNN入门之路: 02.谱域方法：Spectral CNN，ChebyNet，GCN](https://zhuanlan.zhihu.com/p/369382428)

[GNN入门之路: 03.空间域方法：GraphSAGE，GAT，MPNN](https://zhuanlan.zhihu.com/p/369425550)

[图神经网络入门](https://zhuanlan.zhihu.com/p/105605774)

[视频链接](https://www.bilibili.com/video/BV1Ux4y157ZD/?p=2&spm_id_from=pageDriver&vd_source=320c7991448cfd9ab61c95f538663e07)

## GNN

![image-20230303151002806](D:\markdown file\截图\image-20230303151002806.png)

首先，图的构造是点、边组成。

点，一般由特征向量构成，点具体是要由自己定义，比如想看人的关系，人的特征构成了点，想预测交通流量，路口特征就是点。

边，分为又向和无向边，边是否连接决定了点之间有没有关系。

图，一般来说是全局的特征。

![image-20230303152735311](D:\markdown file\截图\image-20230303152735311.png)

图神经网络的目的是重构特征、整合特征。这和NLP的任务其实是有点相似的，看上图，如果把点、边都看作NLP中的单个词，我们学习的目的就是去找一个最符合这个点、边的特征，这个特征在embedding中不断更新。输出就是对点分类回归，边分类回归、图分类回归。

![image-20230303154057841](D:\markdown file\截图\image-20230303154057841.png)

邻接矩阵描述了一个点的邻居有哪些，注意这里是以图像为例子，所以邻居最多有9个，如果不是图像邻居可以超过5个。

![image-20230303154237756](D:\markdown file\截图\image-20230303154237756.png)

图神经网络非常灵活，能不能构成图靠自己想。

![image-20230303154405312](D:\markdown file\截图\image-20230303154405312.png)

![image-20230303155122646](D:\markdown file\截图\image-20230303155122646.png)

![image-20230303155129344](D:\markdown file\截图\image-20230303155129344.png)

CV和NLP任务中GNN不常见，那么图神经网络的优势是什么？

1.传统神经网络最大的要求是输入的格式一定是固定的，这也表明传统神经网络无法处理输入的格式不固定的数据。

2.图神经网络的优势是处理输入数据的格式不固定、不规则的时候，这时用图的结构处理输入数据比硬套传统神经网络的方式好，比如分子结构，道路交通结构等。

![image-20230303155225236](D:\markdown file\截图\image-20230303155225236.png)

![image-20230303155334653](D:\markdown file\截图\image-20230303155334653.png)

图神经网络有几种级别的任务，第一种是图级别的任务，第二种是边级别的任务，第三种是点级别的任务。

![image-20230303155556810](D:\markdown file\截图\image-20230303155556810.png)

实际中邻接矩阵不是保存为NxN的形式，N是点的个数，而是2xM的形式，M表示边的个数，2表示source和target，比如[[1, 0], [2, 0], ...]表示点1到点0有边，点2到点0有边。

![image-20230303161655487](D:\markdown file\截图\image-20230303161655487.png)

![image-20230303162412092](D:\markdown file\截图\image-20230303162412092.png)

消息传递机制（或者叫每个点如何更新，类似于MLP中第一层到第二层如何更新）

一开始每个点都由特征向量，这个向量是输入，但是每个点连接的方式是不同的，如果要更新点的特征向量一定要更新他们邻居的信息，最简单的方式是直接把相连点的向量和自己点的向量相加，但是这样肯定不合理。比较合理的方式是在每个边设置一个可学习参数W，

![image-20230303165644089](D:\markdown file\截图\image-20230303165644089.png)

GNN网络变得是什么，不变的是什么？

GNN网络变得是点的特征，边的可学习参数，不变的是图的结构，也就是邻接矩阵。

那为什么GNN要多层？

类似于CNN中的感受野，层数越多，看的越广，感受野越大，考虑的邻居越多。

![image-20230303165649372](D:\markdown file\截图\image-20230303165649372.png)

我们最后输出的是什么，类似于NLP我们最后得到的主要是每个点的特征，我们可以借这个特征去完成下游的任务。

## GCN

![image-20230303170210137](D:\markdown file\截图\image-20230303170210137.png)

虽然叫图卷积，但是和卷积没什么关系。

![image-20230305143953701](D:\markdown file\截图\image-20230305143953701.png)

![image-20230305144055277](D:\markdown file\截图\image-20230305144055277.png)

![image-20230305145125159](D:\markdown file\截图\image-20230305145125159.png)

图任务中，不一定所有点都有标签，比如交通流量数据，边缘道路可能没有信息，但是这也不影响模型训练。GCN比较适合这种半监督的任务。

![image-20230305145351905](D:\markdown file\截图\image-20230305145351905.png)

![image-20230305145700850](D:\markdown file\截图\image-20230305145700850.png)

GCN的基本思想就是消息传递机制，要更新黄色的点，先把黄色的点和周围的邻居的特征做个加和平均（一定是加和平均，因为是GCN），再经过一个MLP，得到更新后的黄色点的特征。

经验之谈，一般的GCN的层数不太多，可能与感受野的大小相关，只要你认识6个人就可以认识全世界。

![image-20230305150017917](D:\markdown file\截图\image-20230305150017917.png)

图的构成，邻接矩阵A，节点的度D，节点特征F。相比图论多了一个度的概念。

![image-20230305150200208](D:\markdown file\截图\image-20230305150200208.png)

GCN的特征更新就是邻接矩阵A乘特征向量F。

![image-20230305150326512](D:\markdown file\截图\image-20230305150326512.png)

但是在进行特征关系前要对邻接矩阵做一些改动，因为如果用邻接矩阵A乘以特征向量F，只考虑了邻居的特征，没考虑自己，所以还要将邻接矩阵和度矩阵相加，得到新的邻接矩阵，以此加入自己的特征。

![image-20230305160203050](D:\markdown file\截图\image-20230305160203050.png)

![image-20230305160339172](D:\markdown file\截图\image-20230305160339172.png)

但是像之前那样也有问题，如果单纯的将邻接矩阵和度矩阵相加作为一个新的邻接矩阵，会导致一个节点的邻居越多，特征越大，这也有点不合理，所以要做个平均。

最后的步骤简单来说就是将结点的特征相加（包括自己），最后做个平均。

![image-20230305160849418](D:\markdown file\截图\image-20230305160849418.png)

但是这样还不够，因为这样只对行做了归一化的操作，还要对列做平均，相当于batchnormal。但是还是有问题，因为这样相当于做了两次归一化的操作，明显不合理，

![image-20230305161638293](D:\markdown file\截图\image-20230305161638293.png)

为了解决归一化两次的问题，干脆开个根号。

![image-20230305171608996](D:\markdown file\截图\image-20230305171608996.png)