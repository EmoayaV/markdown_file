## 1. 摘要abs和导言intro

[文章链接](C:\Users\Emoaya\Desktop\文章\精读文章_tspDB\tspDB论文.pdf)

### 1.1 在干什么，有什么贡献

问题：现在机器学习的瓶颈是耗时，把数据从数据库DB移到算法上会非常耗时。

目的：想做一个实时的预测系统。

解决方法：直接在数据库上集成一个预测功能，tspDB就是将预测功能直接整合到数据库postgreSQL上。

贡献：1.tspdb实时预测 系统，2.在tspDB的基础上，提出了一种基于时间序列的增量多元矩阵分解方法。（这种方法还可以通过准确估计时间序列的时变方差来产生可靠的预测区间，从而解决时间序列分析中的一个重要问题。）

## 2.引言

挑战：可以说，ML的主要瓶颈不是缺乏对预测算法的访问（为此存在许多优秀的开源ML库）。相反，它需要复杂的工程和数据处理，将数据从数据存储或数据库(DB)中提取到特定的工作环境格式(例如spark数据帧)，以便可以训练预测算法，并以可扩展的方式这样做

















































