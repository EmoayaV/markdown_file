# 图卷积网络

博客地址：https://blog.csdn.net/yyl424525/article/details/100058264



## 1. 为什么会出现图[卷积神经网络](https://so.csdn.net/so/search?q=卷积神经网络&spm=1001.2101.3001.7020)？

![image-20220824133612881](D:\markdown file\截图\image-20220824133612881.png)

![image-20220824133632019](D:\markdown file\截图\image-20220824133632019.png)



## 2. 图卷积网络的两种理解方式

![image-20220824141604288](D:\markdown file\截图\image-20220824141604288.png)

### 2.1 基于空间的图卷积网络

![image-20220824141700677](D:\markdown file\截图\image-20220824141700677.png)

![image-20220823162500006](D:\markdown file\截图\image-20220823162500006.png)

![image-20220823162654735](D:\markdown file\截图\image-20220823162654735.png)

![image-20220823162728453](D:\markdown file\截图\image-20220823162728453.png)



### 2.2 基于频域的图卷积网络

![image-20220824142240581](D:\markdown file\截图\image-20220824142240581.png)



## 3. 谱图理论(spectral graph theory)

原文地址：https://blog.csdn.net/yyl424525/article/details/100058264

原文地址：https://zhuanlan.zhihu.com/p/80817719



### 3.1 矩阵、特征值和特征向量

![image-20220824142456955](D:\markdown file\截图\image-20220824142456955.png)

![image-20220824142537883](D:\markdown file\截图\image-20220824142537883.png)

![image-20220824144151285](D:\markdown file\截图\image-20220824144151285.png)

![image-20220824145310765](D:\markdown file\截图\image-20220824145310765.png)

![image-20220824144208208](D:\markdown file\截图\image-20220824144208208-16613233289281.png)

![image-20220824144331095](D:\markdown file\截图\image-20220824144331095.png)



### 3.2 瑞利商 Rayleigh quotient

原文地址：https://www.baidu.com/link?url=p-mknfTTeTamNKbefMZLVv-h4HYUrxseXRu9lqZPBWYceEP2zFBRMzcj7QvNElG1X5bHMMRQIoR173BIrPOeAq&wd=&eqid=d59274df00001f350000000363071f6e



* 厄米特矩阵 Hermitian Matrix

![image-20220825151028205](D:\markdown file\截图\image-20220825151028205.png)

![image-20220825152058477](D:\markdown file\截图\image-20220825152058477.png)

![image-20220825152135714](D:\markdown file\截图\image-20220825152135714.png)



* 瑞利商 Rayleigh quotient

![image-20220825152251252](D:\markdown file\截图\image-20220825152251252.png)

不过机器学习中遇不到复数，所以Hermitian矩阵可以写为实对称矩阵



### 3.3 谱图理论的介绍

![image-20220825143828583](D:\markdown file\截图\image-20220825143828583.png)

![image-20220825142733845](D:\markdown file\截图\image-20220825142733845.png)

![image-20220825143621993](D:\markdown file\截图\image-20220825143621993.png)



## 4. 拉普拉斯矩阵 Laplacian matrix

![image-20220825161906098](D:\markdown file\截图\image-20220825161906098.png)



### 4.1 拉普拉斯矩阵的几种形式

* 普通形式的拉普拉斯矩阵

![image-20220825162029756](D:\markdown file\截图\image-20220825162029756-16614156316321.png)



* 对称归一化形式的拉普拉斯矩阵

![image-20220825162129568](D:\markdown file\截图\image-20220825162129568.png)



* 随机游走归一化形式的拉普拉斯矩阵

![image-20220825162235069](D:\markdown file\截图\image-20220825162235069.png)



### 4.2 无向图的拉普拉斯矩阵的性质

![image-20220825162546006](D:\markdown file\截图\image-20220825162546006.png)

![image-20220825162720368](D:\markdown file\截图\image-20220825162720368.png)



### 4.3 拉普拉斯矩阵的谱分解

![image-20220825163923168](D:\markdown file\截图\image-20220825163923168.png)

![image-20220825164005520](D:\markdown file\截图\image-20220825164005520.png)



## 5. 图上的傅里叶变换以及卷积

### 5.1 转换关系

![image-20220825165138827](D:\markdown file\截图\image-20220825165138827-16614174998133.png)



### 5.2 图上的傅里叶变换

* DFT和IDFT的简单回顾

![image-20220826132528641](D:\markdown file\截图\image-20220826132528641.png)

![image-20220826132622196](D:\markdown file\截图\image-20220826132622196.png)

![image-20220826132707523](D:\markdown file\截图\image-20220826132707523.png)

![image-20220826132652426](D:\markdown file\截图\image-20220826132652426.png)

![image-20220826132735198](D:\markdown file\截图\image-20220826132735198.png)



* 定义图上的DFT和IDFT

![image-20220825170120198](D:\markdown file\截图\image-20220825170120198-16614180814705.png)



* 图上的DFT

![image-20220826130035584](D:\markdown file\截图\image-20220826130035584.png)

![image-20220826132622196](D:\markdown file\截图\image-20220826132622196.png)

注意：图的傅里叶变换与DFT十分相似，λ == k，i == n。



* 图上的IDFT

![image-20220826130422346](D:\markdown file\截图\image-20220826130422346.png)

![image-20220826132652426](D:\markdown file\截图\image-20220826132652426.png)

注意：图的傅里叶逆变换与IDFT十分相似，λ == k，i == n。。

注意：f(1) ,  f(2) , ... 是时域信号，也就是图。f^^^(λ~1~) , f^^^(λ~2~) , ... 是频域信号，也就是图的频谱，其中λ~1~ , λ~2~ , ... 类似于频谱的频率。



### 5.3 图卷积

![image-20220826135749821](D:\markdown file\截图\image-20220826135749821.png)

![image-20220826135724385](D:\markdown file\截图\image-20220826135724385.png)



### 5.4 为什么拉普拉斯矩阵的特征向量可以作为傅里叶变换的基？特征值表示频率？

![image-20220826140417981](D:\markdown file\截图\image-20220826140417981.png)

* 为什么拉普拉斯矩阵的特征向量可以作为傅里叶变换的基

![image-20220826140442721](D:\markdown file\截图\image-20220826140442721.png)



* 怎么理解拉普拉斯矩阵的特征值表示频率？

#### ![image-20220826140620401](D:\markdown file\截图\image-20220826140620401.png)



## 6. GCN

![image-20220826141606356](D:\markdown file\截图\image-20220826141606356.png)



### 6.1 Spectral CNN

![image-20220827113040428](D:\markdown file\截图\image-20220827113040428.png)



### 6.2 ChebNet

![image-20220827113352133](D:\markdown file\截图\image-20220827113352133.png)

![image-20220827113435048](D:\markdown file\截图\image-20220827113435048.png)

![image-20220827113447798](D:\markdown file\截图\image-20220827113447798.png)

![image-20220827113506922](D:\markdown file\截图\image-20220827113506922.png)

![image-20220827113531481](D:\markdown file\截图\image-20220827113531481.png)

![image-20220827113543149](D:\markdown file\截图\image-20220827113543149.png)

### 6.3 CayleyNet

![image-20220827115012117](D:\markdown file\截图\image-20220827115012117.png)



### 6.4 GCN

![image-20220827115053077](D:\markdown file\截图\image-20220827115053077.png)

![image-20220827115114149](D:\markdown file\截图\image-20220827115114149.png)

![image-20220827115145387](D:\markdown file\截图\image-20220827115145387.png)

![image-20220827115201128](D:\markdown file\截图\image-20220827115201128.png)

![image-20220827115223998](D:\markdown file\截图\image-20220827115223998.png)

![image-20220827115238606](D:\markdown file\截图\image-20220827115238606.png)



### 6.4 GCN的优缺点

![image-20220827115247217](D:\markdown file\截图\image-20220827115247217.png)

![image-20220827115304914](D:\markdown file\截图\image-20220827115304914.png)













