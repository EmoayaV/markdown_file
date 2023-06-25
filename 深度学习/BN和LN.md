https://ugirc.blog.csdn.net/article/details/121809153

https://blog.csdn.net/qq_38683460/article/details/129235637



主要文章

https://ugirc.blog.csdn.net/article/details/121877901?spm=1001.2101.3001.6650.3&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-3-121877901-blog-122778085.235%5Ev36%5Epc_relevant_anti_vip_base&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-3-121877901-blog-122778085.235%5Ev36%5Epc_relevant_anti_vip_base&utm_relevant_index=6



![image-20230519122304798](D:\markdown file\截图\image-20230519122304798.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/c513d4fed7814539a50c6ef65eaa7d9d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA55m96ams6YeR576B5L6g5bCR5bm0,size_20,color_FFFFFF,t_70,g_se,x_16)

![img](https://img-blog.csdnimg.cn/44e902a1ed6e4f189ffb63ced6af953d.png)

![3a6a21134b6e4660a652e8fe4c68c035](D:\markdown file\截图\3a6a21134b6e4660a652e8fe4c68c035.gif)

BN：对不同通道（或者dim维度）的同一特征（或同一神经元）进行归一化的操作

LN：对单个单词的所有特征（embedding向量）进行归一化操作







#### 深入理解NLP中LayerNorm的原理以及LN的代码详解
在介绍LayerNorm之前，我们先来思考一下，为什么NLP中要引入LayerNorm？

如果你学过一点深度学习，那么应该多多少少听过BatchNorm这个东西。BN简单来说就是对一批样本按照每个特征维度进行归一化。BN具体细节请看我的另一篇博客：深入理解BatchNorm的原理
![在这里插入图片描述](https://img-blog.csdnimg.cn/8f53bfd425f8428290ca95bd625e5881.png)

但在NLP领域，每个样本通常是一个句子，而句子中包含若干个单词。这时如果使用BN去做过归一化通常效果会很差

![在这里插入图片描述](https://img-blog.csdnimg.cn/8933785e25454a519703b1e7469ff4a7.png)

那有没有更好的归一化方法呢？

有的，我们今天就来看一看NLP中常用的归一化操作：LayerNorm

#### LayerNorm原理

在NLP中，大多数情况下大家都是用LN（LayerNorm）而不是BN（BatchNorm）。最直接的原因是BN在NLP中效果很差，所以一般不用。

![在这里插入图片描述](https://img-blog.csdnimg.cn/285ce4bb42db411780edeb7d8a0fab24.png)

LayerNorm中没有batch的概念，所以不会像BatchNorm那样跟踪统计全局的均值方差，因此train()和eval()对LayerNorm没有影响。

#### 说明：nn.LayerNorm与nn.BatchNorm用法上有很大的差异
nn.BatchNorm2d(num_features)中的num_features一般是输入数据的第2维(从1开始数），BatchNorm中weight和bias与num_features一致。

nn.LayerNorm(normalized_shape)中的normalized_shape是最后的几维，LayerNorm中weight和bias的shape就是传入的normalized_shape。
在取平均值和方差的时候两者也有差异：

BN是把除了轴num_features外的所有轴的元素放在一起，取平均值和方差的，然后对每个元素进行归一化，最后再乘以对应的γ 和β （共享）。BN共有num_features个mean和var，（假设输入数据的维度为(N,num_features, H, W））。
而LN是把normalized_shape这几个轴的元素都放在一起，取平均值和方差的，然后对每个元素进行归一化，最后再乘以对应的γ 和β（每个元素不同）。LN共有N1*N2个mean和var（假设输入数据的维度为(N1,N2,normalized_shape），normalized_shape表示多个维度）

#### 示例1：NLP中的LayerNorm（常用）
NLP的输入一般是(batch, sentence_length, embedding_dim)，则LayerNorm层有embedding_dim个参数γ \gammaγ和β \betaβ。也就是对于输入的单词序列，LN是对一个单词的embedding向量进行归一化的

![img](https://img-blog.csdnimg.cn/44e902a1ed6e4f189ffb63ced6af953d.png)

#### 图解：🤩Layer Norm到底是怎么对单词归一化的？

![在这里插入图片描述](https://img-blog.csdnimg.cn/d984a3edb42b4569b142388ebda7adf3.png)

#### 思考题1：为什么Layer Norm是对每个单词的Embedding做归一化？

看到这，可能很多人会有疑问了，为什么Layer Norm是对每个单词的embedding进行归一化，而不是对这个序列的所有单词embedding向量的相同维度进行归一化呢？

我一开始也是觉得应该对所有单词embedding向量归一化，但后来发现pytorch官方实现的LayerNorm并不是这样实现的，而是对每个单词的embedding进行了归一化。

后来，我想明白了，因为每个序列（每个样本）的单词个数不一样，但在代码实现的时候会进行padding，比如一个序列原始单词数为30个，另一个序列原始单词数是8，然后你统一padding成了30个单词，那如果按照相同维度，进行归一化，norm的信息就会被无意义的padding的embedding冲淡的！这显然是不合理的。
#### 思考题2：为什么BN训练和测试时有区别，而LN没区别？
BatchNorm的统计量是一个batch算出来的，在线测试时，不太可能累计一个batch资料后再进行测试的。所以在训练的时候要记录统计量running mean和running var，作为预测时的均值和方差。详见博客：深入理解BatchNorm的原理

而LayerNorm训练和测试的时候不需要model.train()和model.eval()，是因为它只针对一个样本，不是针对一个batch，所以LayerNorm只有参数gamma和beta，没有统计量，因此LN训练和预测没有区别。

下面这个图C表示通道数，H,W表示高和宽，由于可视化的原因，下图把H,W放在一起了，实际上像下图**橙色**形状是一个特征图（某个通道下的H*W）

![在这里插入图片描述](https://img-blog.csdnimg.cn/c513d4fed7814539a50c6ef65eaa7d9d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA55m96ams6YeR576B5L6g5bCR5bm0,size_20,color_FFFFFF,t_70,g_se,x_16)

显然LN求mean和var的时候是把整个蓝色元素都放在一起求的，然后每个元素都用这个mean和var进行归一化，不过这里每个元素对应的γ 和β 是不同的，因为γ 和β也有C ∗ H ∗ W 个。

#### 附：BN、LN、IN、GN的区别
神经网络中有很多归一化的算法：Batch Normalization (BN)、Layer Normalization (LN)、Instance Normalization (IN)、Group Normalization (GN)

他们的公式都是差不多的，就是减去均值，除以标准差，再施以线性映射。（只不过在对哪些维度求均值、方差，以及参数γ 和β 怎么对应有差异）
![在这里插入图片描述](https://img-blog.csdnimg.cn/285ce4bb42db411780edeb7d8a0fab24.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/f5fe362c39604d198181703a56bf4dc2.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA55m96ams6YeR576B5L6g5bCR5bm0,size_20,color_FFFFFF,t_70,g_se,x_16)	对于每一种Norm方法而言，每个像蓝色这样的区域会计算出一个均值和方差，在这个蓝色区域内的元素都会用这个均值和方差进行归一化。至于线性映射时参数γ 和β 怎么对应不同Norm时有差异的，我前面提到过BN和LN在这点上的差异。
