# Numpy 基础

**基本属性操作**

* 变量.shape →返回矩阵大小 *[比如(2,3,2)指2个3x2矩阵]*

* 变量.ndim →返回ndarray维度 *[用几个数字做ndarray的坐标就有几个维度，维度也等于轴数]*

* 变量.dtype →返回数据类型

* 变量.astype(np.int32/np.float64) →转换数据类型

* 变量.copy() →复制变量

* 变量.append() →用于在列表末尾添加新的对象

___

**数学运算操作**

* 变量.swapaxes(1,2) →对调2轴和3轴

* 变量.mean() →对矩阵中所有元素求平均值

* 变量.sum() →对矩阵中所有元素求和

* 变量.sum(axis=0) →对矩阵中所有列求和

* 变量.sum(axis=1) →对矩阵中所有行求和

* 变量.cumsum(axis=0) →对矩阵中所有列求累加

* 变量.cumprod(axis=0) →对矩阵中所有列求累乘法

* 变量=np.sqrt(矩阵) →对矩阵每个元素开方

* 变量=np.exp(矩阵) →对矩阵每个元素做平方

* 变量=np.maximum(矩阵1,矩阵2) →对矩阵1和矩阵2逐元素比较取最大值放进一个矩阵

* 变量=np.modf(矩阵) →取出矩阵每个元素的整数部分和小数部分，整数部分放一个矩阵，小数部分放一个矩阵

* 变量.sort(1) →对变量的每1行做排序

___

**线性代数**

* 变量.T →对矩阵做转置 *[对于(1,2,3)形状变为(3,2,1)形状]*

* 变量=np.dot(矩阵1,矩阵2) →对矩阵1和矩阵2做矩阵相乘

* 变量.transpose((1,0,2)) →对每个元素来说，将坐标(i,j,k)变为(j,i,k)

* 变量=np.linalg.inv(矩阵) →对矩阵求逆

___

**生成坐标**

* 变量 xs,ys =np.meshgrid(point_array,point_array ) →生成坐标

___

**循环替代**

* 变量=np.where(condition,变量1，变量2) →如果条件成立取变量1的元素，不成立取变量2的元素，结果放入变量中 *[替代循环]*

* 变量= (对变量1的操作 for 变量1 in 范围)

___

**生成array**

* 变量=np.arange() →创建ndarray *[顺序]*

* 变量=np.arange().reshape(()) →创建ndarray *[前面个数后面形状]*

* 变量=np.zero() →创建ndarray *[全0]*

* 变量=np.ones() →创建ndarray *[全1]*

* 变量=np.identity() →创建ndarray *[单位矩阵]*

* 变量=np.empty() →创建ndarray *[不如zero]*

* 变量=np.array() →创建ndarray *[自定义]*

* 变量=np.random.rand() →创建ndarray *[0-1均匀分布随机数]*

* 变量=np.random.randn() →创建ndarray *[均值0方差1的正态分布随机数]*

* 变量=np.random.normal() →创建ndarray *[均值0方差1的正态分布随机数]*

___

**切片和索引**

* 一维变量[1] →取出第2个元素

* 一维变量[1:5] →取出1到4个元素

* 一维变量[:] →取出所有元素

* 二维变量[1] →取出第2行

* 二维变量[:1] →取出前2行

* 二维变量[1,2] →取出第2行第3列元素

* 二维变量[1][2] →取出第2行第3列元素

* 二维变量[:1,2:] →取出前2行和3列以后元素

* 二维变量[:1,2] →取出前2行和第3列元素 *[返回的是1x2矩阵]*

* 二维变量[:1,2:3] →取出前2行和第3列元素 *[返回的是2x1矩阵,因为索引降维，切片不降维]*

* 三维变量[1] →取出第2个矩阵

* 三维变量[1,2] →取出第2个矩阵的第3行

* 三维变量[1,2,3] →取出第2个矩阵的第3行第4个元素

* 变量[条件 (比如 name_array == 'Bob')] →当name_array的字符串为'Bob'时，取出变量array对应位置的元素/行/矩阵 *[注意：用布尔索引时，索引个数要与轴的坐标个数一致且优先级 矩阵>行>元素]*

* 变量[name_array == 'Bob',2:] →当name_array的字符串为'Bob'时，取出变量array对应位置的元素/行/矩阵 ,再取出3列以后的元素

* 变量[变量<0]=0 →将变量中的负数置为0

* 二维变量[[1,3,5]] →取出第2、4、6行

* 二位变量[[1,3,5],[2,4,6]] →取出第2、4、6行和3、5、7列的元素

* 二维变量[[1,3,5,7]][:,[0,2,1,3]] →取出第2、4、6、8行，再将得到的矩阵取出所有行，将列按照[0,2,1,3]排序

___

**集合运算**

* 变量=np.unique(矩阵) →对矩阵中的元素求并集 *[(1,1,2,2)变为(1,2)]*

___

**文件输入与输出**

* np.save('文件名',变量) →把变量存到文件中

* np.load('文件名') →载入文件

___

# Pandas 基础

**常规操作**

* 变量.values → 查看当前series的值

* 变量.index → 查看当前series的键、目录

* 变量.describe →查看变量的统计特性

* 变量['键'] →查看键对应的值

* 变量['键']=值 →更改键对应的值

* 变量[条件] →当值满足条件，抓出符合条件的键值对

* pd.isnull() →查看当前Series数据是否有缺失，如果有确实返回True，没有返回False

* Series变量1+Series变量2 →相同的键对应的值相加

___

**DataFrame**

* 变量.head →查看DataFrame的前5行

* 变量.columns →查看DataFrame的行目录

* 变量.loc[] →抓取DataFrame的一行 *[**最常用**]*

* 变量.T →DataFrame转置

* 变量.values →抓出DataFrame的值，返回的是array

* 变量=pd.DataFrame(data,columns行目录=[],index列目录=[]) →生成DataFrame

* 新DataFrame=pd.crosstab(DataFrame['列1'],DataFrame['列2']) →从DataFrame中取出列1和列2分别作为新DataFrame的index和columns

___

**生成series**

* 变量=pd.Series([值]或者字典,index=[键]) →创建series *[创建出来的series类似字典，不是list]*

___

**索引和切片**

* 变量.reindex() →重建索引，对Series和DataFrame类都适用

* 变量.loc[] →抓取DataFrame的一行或一列

* **变量.iloc[1:2,1:3] →抓出第2行第1、2列的数据，里面只能写数字，最好用冒号表示** *[**最常用**]*

 * 变量.drop() →删除一行或一列

___

**函数**

* f=lambda 自变量 : 函数表达式 →定义一个匿名函数

* 变量.apply(匿名函数) →使用匿名函数，如果是DataFrame类型，默认对行之间进行操作

* 变量.apply(匿名函数,axis='columns') →使用匿名函数，如果是DataFrame类型，对列之间进行操作

* 变量.applymap(匿名函数) →使用匿名函数，逐元素进行操作

___

**数学计算**

* 变量1.corr(变量2) →计算变量1和变量2的相关系数

* 变量1.corr() →调出相关系数矩阵

* 变量1.cov(变量2) →计算变量1和变量2的协方差

* 变量1.cov() →调出协方差矩阵

___

# 数据载入、存储和文件格式

* 变量.values →查看变量

* !tape 文件名 →查看文件内容

* **变量=pd.read_csv() →打开csv文件**

* 变量=json.loads(文件名) →打开json文件

* 变量=pd.read_json(文件名) →打开json文件并转为DataFrame或Series格式

* 变量=pd.read_html(文件名) →打开html文件

* 变量=pd.HDFStore(文件名) →将文件存储为HDF5格式，并且可以用变量调用

* 变量=pd.read_excel(文件名) →打开excel文件

* 在网页的数据操作
    * 先找到数据集的网址，令target_url=("网址")
    * 读取文件，令df=pd.read_csv(target_url,header=None)
    * 定义开头第一行，令df.columns=['','','','']
    * 查看前几行，令dftrain.head()

___

# 数据预处理

**常规**

* 变量.isnull() →寻找是否有missing data

* 变量.dropna() →滤除missing data

* 变量.fillna() →将missing data改为数值

* 变量.duplicated() →查看是否有重复行

* 变量.drop_duplicated() →删除重复行

* 变量.map(函数) →对变量的每一行都执行函数的操作

* 变量.replace({数据1:数据2,数据3:数据4}) →将数据1、3替换为数据2、4

* 变量.rename(index=..，columns=..) →对index和columns进行操作

* 变量.describe() →查看数据的大致内容

* 变量=pd.cut(数据list，区间list) →将数据放入区间

* 变量=pd.qcut(数据list，4) →将数据平均分为4份

* 变量=pd.qcut(数据list，[0,0.2,0.6,1.0]) →将数据按照20%40%40%分为三份

* 变量=pd.value_counts(上面的变量) →统计每个区间的样本数

* 随机排列 **[重要]**
    * array= np.random.permutation(5) →生成一个随机的array有5个数
    * 变量.take(array) →对变量的行进行随机排列

* 变量.sample(n=3) →不重复的随机抓取3行 **[重要]**

* 变量.sample(n=3,replace=True) →有重复的随机抓取3行 **[重要]**

* 变量=pd.get_dummies(DataFrame['列']) →将一列k个不同的值转换为k列值为0或1的矩阵 **[重要]**

* 变量=pd.get_dummies(DataFrame) →将一列k个不同的非数字值转换为k列值为0或1的矩阵 **[重要，最常用，要注意使用时标签不能为数字，如果为数字要将转换为字母]**

* 与其他列合并 **[重要]**
    * 变量1=pd.get_dummies(DataFrame['列'],prefix='列的名称') →将一列k个不同的非数字值转换为k列值为0或1的矩阵并且columns加上列的名称 
    * 变量2=DataFrame[['其他列']].join(变量1) →将将其他列与做完get_dummies后的列进行合并

 **字符串**

* 字符串.split('分隔符') →以分隔符为标准将字符串分开

* 字符串.strip() →删除空白

* 字符串.index('字符') →找出字符第一次出现的位置

* 字符串.replace('字符1','字符2') →将字符1替换为字符2

___

# 数据合并

* 变量.set_index() →设置一个DataFrame的index

* np.concatenate([array1,array2],axis=1) →对array1和array2沿着轴axis=1做合并

* **pd.concat([DataFrame1,DataFrame2],axis=1,ignore_index=True) →对DataFrame1和DataFrame2沿着轴axis=1做合并,并且重新生成index**

* DataFrame1.combine_first(DataFrame2) →将DataFrame1和DataFrame2重叠合并

* 变量.stack() →堆叠操作，行标题旋转成列标题

* 变量.unstack() →拆堆操作，列标题旋转成行标题

___

# matplotlib 基础

* plt.imshow(矩阵) →将矩阵可视化

* plt.plot(数据,linestyle='--',color='g'，marker='o'，drawstyle='steps-post',label='steps-post') →画**折线图**，线为--虚线，颜色为绿色，并且把每一点用黑点标注,绘画风格为平顶抽样型，并且线条的标签为steps-post，会显示在图片的左上角
* plt.legend(loc='best') →在适中的地方显示折线图

* 画子图，直方图，散点图    
    * fig=plt.figure() →创建一个空的画图区域
    * ax1=fig.add_subplot(2，2，1) →表示画一个2x2大小的空白子图(行有两个子图，列有两个子图)，且位置在第1个
    * ax1.hist(数据,bins=20,color='k'，alpha=0.3) →在第一个空白子图上画**直方图**，横坐标划分为20份，颜色是黑色，透明的0.3(灰色)
    * ax2.scatter(横坐标数据，纵坐标数据) →画**散点图**

* fig，axes=plt.subplot(2,3) →创建一个fig的画图区域，每个子图为axes，大小为2x3
* axes[0,1] →表示第1行第2个子图

* plt.subplots_adjust() →调整每个子图之间的间隔

* plt.close('all') →结束画图，如果不结束下一次画图将画在上一张图上

* 图像/子图像.set_xticks([0,250,500,750,1000]) →以0,250..1000为x轴刻度画图
* 图像/子图像.set_xticklabels(['one','two','three'],rotation=30,fontsize='small']) →以字符串'one','two','three'为x轴刻度画图，并且字体旋转30°，字号为小字

* plt.title("标题") →写标题，标题中写数学符号具体看(https://matplotlib.org/2.0.2/users/mathtext.html)
* 图像/子图像.set_title('my plot') →对图像/子图像写上标题
* 图像/子图像.set_xlabel('xlabel') →写上x坐标轴的名称

* 图像/子图像.set_xlim([a,b]) →设置x轴的显示区间
* 图像/子图像.set_ylim([a,b]) →设置y轴的显示区间

* rect=plt.Rectangle((0.2, 0.75), 0.4, 0.15, color='k', alpha=0.3) →长方形左下角为(0.2, 0.75)，长0.4宽0.15
* circ=plt.Circle((0.7, 0.2), 0.15, color='b', alpha=0.3) →圆心为(0.7, 0.2)，版半径0.15
* pgon=plt.Polygon([[0.15, 0.15], [0.35, 0.4], [0.2, 0.6]],color='g', alpha=0.5) →多边形，三个点的坐标为[0.15, 0.15], [0.35, 0.4], [0.2, 0.6]
* ax.add_patch(rect) →在子图ax上画出长方形
* ax.add_patch(circ) →在子图ax上画出圆形
* ax.add_patch(pgon) →在子图ax上画出多边形

* plt.savefig('名字.svg/pdf/png') →保存图像

* DataFrame/Series.plot() →画出DataFrame/Series的折线图

* DataFrame/Series.plot.bar(ax=axes[0],color='k') →在第一个子图上画竖的**柱状图**，x轴为index值

* DataFrame/Series.plot.barh(ax=axes[1],color='k') →在第二个子图上画横的**柱状图**，y轴为index值

* Series.plot.density() →画出Series的**密度图**，可以理解为直方图的连续化

* sns.distplot(数据,bins=100,color='k') →用seaborn的方法同时画出**直方图和密度图**

* sns.regplot('x轴数据','y轴数据'，data=数据) →用seaborn的方法同时画出**散点图**以及一条线性回归线

___

# 数据分组和聚合

* Grouped=DataFrame['data'].groupby(DataFrame['key']或者'key') →在一个DataFrame中按照key对data做分组，data和key都是columns名，grouped不会被打印出来，但是可以对grouped这个变量做操作，比如Grouped.mean()表示对Grouped中的组分别求期望

* Grouped=DataFrame.groupby(DataFrame['key']或者'key') ['data'] →与上面相同

* Grouped.agg('函数'或者['函数1','函数2','函数3']) →按照函数的方式对Grouped数据进行聚合，一个函数作为一列结果输出

* Grouped.describe() →查看Grouped数据的基本统计数据

___

# 时间序列

* 变量=datatime.now() →显示当前时间
