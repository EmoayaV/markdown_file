## 1. 概述

![image-20220906131703014](D:\markdown file\截图\image-20220906131703014.png)



## 2. GAN的基本原理

![image-20220908114421994](D:\markdown file\截图\image-20220908114421994.png)

![gan](D:\markdown file\截图\gan.jpeg)

![image-20220906131912984](D:\markdown file\截图\image-20220906131912984.png)

![image-20220906133440452](D:\markdown file\截图\image-20220906133440452.png)

在GAN里面想训练一个generator，generator其实就是一个神经网络，输入一个向量经过generator后会输出一组高维度向量，再用这组高纬度向量生成想要的结果，既可以用于生成图片也可以生成句子。

通常输入的向量每一个维度会对应到图片的某种特征，改变输入向量某个维度下的数值也会改变输出结果的某个特征

![image-20220906133620800](D:\markdown file\截图\image-20220906133620800.png)

在GAN里面还会训练一个discriminator来判断generator生成结果的好坏。

![image-20220906141254835](D:\markdown file\截图\image-20220906141254835.png)

![image-20220906141800364](D:\markdown file\截图\image-20220906141800364.png)

GAN的思想就想生物进化的过程，捕食者是discriminator，被捕食者就是generator

![image-20220906142225709](D:\markdown file\截图\image-20220906142225709.png)

这就产生了两个问题，为什么generator不自己去学习而是要依靠discriminator，为什么discriminator不自己去生成图片而是依靠generator生成图片？

下面是算法的具体流程：

![image-20220906142939073](D:\markdown file\截图\image-20220906142939073.png)

![image-20220906143348962](D:\markdown file\截图\image-20220906143348962.png)

第一步先固定generator参数，去训练discriminator参数，先把向量输入generator生成一组图片，再把generator产生的图片标为低分，数据集中的图片标为高分去训练discriminator。

第二步先固定discriminator参数，去训练generator参数，先把向量输入generator生成一组图片，再通过discriminator给生成的图片打分，我们希望打分越高越好，以此来训练generator。

实际中会把generator和discriminator是一个巨大的网络，比如generator是一个5层mlp，discriminator是一个5层mlp，那么实际中会设计一个11层网络，前5层是generator，第6层是一个很宽的hidden layer，表示generator生成的图片，后5层是discriminator，训练的时候就是固定后5层，只调前5层。

![image-20220906170702297](D:\markdown file\截图\image-20220906170702297.png)

上图是算法的具体表示，在一个epoch内，先固定generator参数，去训练discriminator参数。

其中D(x^i^)表示真实样本经过判别器的结果，D(x_tilda^i^)表示生成器生成的样本经过判别器的结果，θ~d~表示判别器D的参数。

经过判别器后会生成一个0到1的数字，表示类别的概率，越接近1表示来自真实样本的概率越大，如果想让判别器的效果好，那么logD(x^i^)的数值越大越好，log(1-D(x_tilda^i^))的数值同样越大越好，所以要最大化损失函数V_tilda.

再固定discriminator参数，去训练generator参数。

其中G(z^i^)表示经过生成器生成的图片，D(G(z^i^))表示把生成的图片放入判别器，如果生成的图片接近真实样本，那么log(D(G(z^i^)))就会增大，所以说要最大化损失V_tilda。



## 3. 以结构学习的方式看GAN

![image-20220907105208195](D:\markdown file\截图\image-20220907105208195.png)

![image-20220907105304827](D:\markdown file\截图\image-20220907105304827.png)

结构学习就是输出是序列、矩阵、图像、树等的复杂情况。

![image-20220907111934680](D:\markdown file\截图\image-20220907111934680.png)

![image-20220907112533319](D:\markdown file\截图\image-20220907112533319.png)

结构学习的输出往往要看整个结构的信息，单看一个元素的输出是不知道结果好坏的，要看整个的输出才知道结果好坏。

![image-20220907112456453](D:\markdown file\截图\image-20220907112456453.png)

generator主要是产生一个一个的元素，不知道整体结构信息，discriminator主要是从整体结构看结果好不好。



## 4. 可以单独用Generator生成图片吗？

![image-20220907113231855](D:\markdown file\截图\image-20220907113231855.png)

要单独训练generator非常简单，是一种监督学习，给每个图片给一个向量就行，过程是和图片分类任务相反的过程，单独用generator训练也可以看作一个最基础的分类任务。

![image-20220907113511753](D:\markdown file\截图\image-20220907113511753.png)

![image-20220907113637719](D:\markdown file\截图\image-20220907113637719.png)

![image-20220907113741404](D:\markdown file\截图\image-20220907113741404.png)

其最大的问题是如何为每一个图片选取合适的向量。

这个问题可以先将图片输入一个encoder，让encoder为每个图片生成一个合适的向量。

在auto-enconder里，其实generator就相当于encoder部分。

![image-20220907114205825](D:\markdown file\截图\image-20220907114205825.png)

![image-20220907114216487](D:\markdown file\截图\image-20220907114216487.png)

上面是先把图片放入encoder里生成二维向量，再把向量放入decoder生成图片，再以每个二维向量为坐标，把相应的图片放入坐标轴产生的结果。

![image-20220907114513298](D:\markdown file\截图\image-20220907114513298.png)

![image-20220907114828023](D:\markdown file\截图\image-20220907114828023.png)

用auto-encoder的方式只能处理已经见过的向量的情况，但是如果输入的向量没有见过，那么产生的结果会非常差。

为了解决这种情况，就产生了VAE技术，其在encoder处，不仅产生向量，还产生一组方差，将方差与正态分布的采样相乘，在加入encoder生成的向量里，这样就可以解决上述的情况。

实际上这可以看作数据增广的一种方式，其核心思想就是在训练时就尽量加入测试时可能会遇到的样本。也可以看作一种防止过拟合的方式，因为加入了噪音。

![image-20220907134714418](D:\markdown file\截图\image-20220907134714418.png)

![image-20220907134900286](D:\markdown file\截图\image-20220907134900286.png)

![image-20220907135358948](D:\markdown file\截图\image-20220907135358948.png)

光用generator有什么问题呢？

generator的损失是计算生成的图像和真实图像之间的差距，那么就会出现上述图片里的问题，比如前两幅图都错了1个像素，后两个图错了6个像素，对于机器而言，前两幅图生成的额比后两幅图好，但是对于人而言，后两幅图比前两幅图好。

所以如果想改善上述的问题，那么就必须让每个神经元之间都有联系都有大局观，比如在输出层的而每个神经元都对应一个像素，一个神经元输出了有颜色的像素，他想让旁边的像素也产生颜色，这样理论上就可以改善结果，但是实际上是不太可能做到的，如果要做到也有办法，就是在最后一层再加几层神经网络，所以实际中如果用AE和GAN同时生成图片，那么AE往往需要更深的网络才可以达到与GAN相同的结果。

这就是单独训练一个generator困难的地方。



## 5. 可以单独用Discriminator生成图片吗？

![image-20220907140752535](D:\markdown file\截图\image-20220907140752535.png)

![image-20220907141449783](D:\markdown file\截图\image-20220907141449783.png)

Discriminator可能有不同的名字，比如Evaluation func，potential func， energy func。

对于generator来说产生图片是一个像素一个像素产生的，所以很难考虑到像素之间的关系，但是对于Discriminator来说就很好去考虑到像素之间的关系，用个卷积核就很容易去做到，对于Discriminator来说，一般是产生完图片后，再把产生的图片丢给Discriminator来判断产生的图片与真实图片的区别。

![image-20220907141845883](D:\markdown file\截图\image-20220907141845883.png)

![image-20220907141934276](D:\markdown file\截图\image-20220907141934276.png)

![image-20220907142338229](D:\markdown file\截图\image-20220907142338229.png)

用Discriminator生成图片是可行的，就是穷举所有像素的组合，把打分高的挑出来，但是会很慢，然而慢不是最关键的问题，最关键的问题是如何去训练discriminator，通常来说如果有二次元头像的数据集，一般全是正面样本，没有负面样本，那么训练出的discriminator看到什么都是正面样本，都会给高分。

![image-20220907142550487](D:\markdown file\截图\image-20220907142550487.png)

![image-20220907142947707](D:\markdown file\截图\image-20220907142947707.png)

![image-20220907143355626](D:\markdown file\截图\image-20220907143355626.png)

现在问题就是如何去产生负面样本，这是一个非常困难的问题。

但是这个问题也有解决方法，可以用迭代的方法来解决，在第一次迭代，首先随机生成一堆负样本，然后把正样本给1负样本给0，让D去学习，再用D去生成图片。在第二次迭代，首先把负样本换位第一次迭代生成的样本，然后把正样本给1负样本给0，让D去学习，再用D去生成图片。类似于排除法。

![image-20220907144131668](D:\markdown file\截图\image-20220907144131668.png)

![image-20220907144323013](D:\markdown file\截图\image-20220907144323013.png)

生成器擅长生成，但是不擅长判别，判别器擅长判别，不擅长生成。实际上GAN就是把图片生成交给机器做了，不用人工手动的去解argmax的问题

