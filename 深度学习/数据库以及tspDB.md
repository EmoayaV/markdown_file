## [视频链接](https://www.bilibili.com/video/BV1av411r7yB/?vd_source=320c7991448cfd9ab61c95f538663e07)

![image-20230306192825704](D:\markdown file\截图\image-20230306192825704.png)

![image-20230306192854786](D:\markdown file\截图\image-20230306192854786.png)

![image-20230306192941166](D:\markdown file\截图\image-20230306192941166.png)

![image-20230306193055854](D:\markdown file\截图\image-20230306193055854.png)

![image-20230306193212057](D:\markdown file\截图\image-20230306193212057.png)

![image-20230306193335800](D:\markdown file\截图\image-20230306193335800.png)

![image-20230306193522875](D:\markdown file\截图\image-20230306193522875.png)

![image-20230306193701059](D:\markdown file\截图\image-20230306193701059.png)

------------------------------------------------------------------------------------------------------------------------------------------------------

![image-20230306193804677](D:\markdown file\截图\image-20230306193804677.png)

![image-20230306193810388](D:\markdown file\截图\image-20230306193810388.png)

![image-20230306194329129](D:\markdown file\截图\image-20230306194329129.png)

------------------------------------------------------------------------------------------------------------------------------------------------------

![image-20230306194609046](D:\markdown file\截图\image-20230306194609046.png)

[安装视频](https://www.bilibili.com/video/BV1Ce4y187n5/?spm_id_from=333.337.search-card.all.click&vd_source=320c7991448cfd9ab61c95f538663e07)

[安装博客](https://linux.cn/article-11480-1.html)

[安装博客2](https://www.cnblogs.com/qiyebao/p/4562557.html)

>检查PostgreSQL 是否已经安装
>
>```
>rpm -qa | grep postgres    检查PostgreSQL 是否已经安装
>rpm -qal | grep postgres   检查PostgreSQL 安装位置
>```

[官方安装教程](https://www.postgresql.org/download/linux/ubuntu/)

>安装命令（默认安装在/usr/lib/postgresql）
>
>```
>sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
>wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
>sudo apt-get update
>sudo apt-get -y install postgresql
>```

[使用Docker安装 **推荐**]()

> [Docker简介](https://www.bilibili.com/video/BV1s54y1n7Ev/?spm_id_from=333.788.recommend_more_video.-1&vd_source=320c7991448cfd9ab61c95f538663e07)
>
> [Docker从入门到实践](https://yeasy.gitbook.io/docker_practice/)
>
> [安装Docker](https://docs.docker.com/engine/install/ubuntu/)

![image-20230307092318572](D:\markdown file\截图\image-20230307092318572.png)

> 查看服务进程
>
> ps aux | grep sshd
>
> ps aux | grep postgres

>启动数据库服务
>
>su postgre
>
>cd /usr/lib/postgresql/15/bin
>
>./pg_ctl

>关闭数据库服务
>
>./pg_ctl stop -D /usr/lib/postgresql

![image-20230307144955859](D:\markdown file\截图\image-20230307144955859.png)

![image-20230307145059246](D:\markdown file\截图\image-20230307145059246.png)

|          命令          |                             代码                             |
| :--------------------: | :----------------------------------------------------------: |
|       创建数据库       |                    create database xxxx;                     |
|     修改数据库名称     |             alter database xxxx rename to xxxx1;             |
|       删除数据库       |                     drop database xxxx;                      |
|     创建数据表对象     | create table xxxx (id int, name varchar(30), birthday date, score numeric(5, 2)); |
|       修改数据表       |              alter table xxxx rename to xxxx1;               |
|   修改数据表中的字段   |              alter table xxxx rename id to id1;              |
| 修改数据表中的数据类型 | alter table xxxx rename alter column name type vatchar(40);  |
|   删除数据表中的字段   |               alter table xxxx drop column id;               |
|   添加数据表中的字段   |      alter table xxxx add column address varchar(200);       |
|       删除数据表       |       drop table xxxx; 或者 drop table if exist xxxx;        |

![image-20230322164336549](D:\markdown file\截图\image-20230322164336549.png)

![image-20230322145635280](D:\markdown file\截图\image-20230322145635280.png)

![image-20230322145759329](D:\markdown file\截图\image-20230322145759329.png)

![image-20230322150211761](D:\markdown file\截图\image-20230322150211761.png)

![image-20230322150818634](D:\markdown file\截图\image-20230322150818634.png)

![image-20230322151302983](D:\markdown file\截图\image-20230322151302983.png)

![image-20230322164356804](D:\markdown file\截图\image-20230322164356804.png)

![image-20230322151412438](D:\markdown file\截图\image-20230322151412438.png)

![image-20230322151440205](D:\markdown file\截图\image-20230322151440205.png)

![image-20230322151549523](D:\markdown file\截图\image-20230322151549523.png)

![image-20230322155709849](D:\markdown file\截图\image-20230322155709849.png)

![image-20230322155920331](D:\markdown file\截图\image-20230322155920331.png)

![image-20230322155944711](D:\markdown file\截图\image-20230322155944711.png)

![image-20230322162502848](D:\markdown file\截图\image-20230322162502848.png)

![image-20230322163342723](D:\markdown file\截图\image-20230322163342723.png)

![image-20230322163359843](D:\markdown file\截图\image-20230322163359843.png)

![image-20230322163637133](D:\markdown file\截图\image-20230322163637133.png)

![image-20230322163755190](D:\markdown file\截图\image-20230322163755190.png)

![image-20230322164243831](D:\markdown file\截图\image-20230322164243831.png)

![image-20230322164253791](D:\markdown file\截图\image-20230322164253791.png)

![image-20230322164451476](D:\markdown file\截图\image-20230322164451476.png)

![image-20230322164615897](D:\markdown file\截图\image-20230322164615897.png)

![image-20230322164825711](D:\markdown file\截图\image-20230322164825711.png)

![image-20230322164852752](D:\markdown file\截图\image-20230322164852752.png)

![image-20230322164858482](D:\markdown file\截图\image-20230322164858482.png)

![image-20230322165603186](D:\markdown file\截图\image-20230322165603186.png)

|   命令   |                   代码                   |
| :------: | :--------------------------------------: |
| 创建索引 | create index 索引名称 on 表名(字段名称); |
| 删除索引 |           drop index 索引名称;           |

![image-20230322165859160](D:\markdown file\截图\image-20230322165859160.png)

![image-20230322165910967](D:\markdown file\截图\image-20230322165910967.png)

![image-20230322170759035](D:\markdown file\截图\image-20230322170759035.png)

|       命令       |                代码                 |
| :--------------: | :---------------------------------: |
|     创建视图     | create view 视图名称 as select语句; |
| 查询（查看）视图 |       select * from 视图名称;       |
|     删除视图     |         drop view 视图名称;         |

![image-20230322171012166](D:\markdown file\截图\image-20230322171012166.png)

![image-20230322171150786](D:\markdown file\截图\image-20230322171150786.png)

![image-20230322171434891](D:\markdown file\截图\image-20230322171434891.png)

![image-20230322171621084](D:\markdown file\截图\image-20230322171621084.png)

![image-20230322171719845](D:\markdown file\截图\image-20230322171719845.png)

![image-20230322171748486](D:\markdown file\截图\image-20230322171748486.png)

![image-20230322172329101](D:\markdown file\截图\image-20230322172329101.png)

|               命令               |                             代码                             |
| :------------------------------: | :----------------------------------------------------------: |
|        在数据表中插入数据        |            insert  into 表名 values 插入数据内容;            |
|   在数据表中的指定字段插入数据   |     insert  into 表名(插入字段内容) values 插入数据内容;     |
|      在数据表中批量插入数据      | insert  into 表名 values 插入数据内容1, 插入数据内容2, 插入数据内容3; |
|      在数据表中批量插入数据      |             insert  into 表1 select * from 表2;              |
| 在数据表中的指定字段批量插入数据 | insert  into 表1(插入字段内容) select 插入字段内容 from 表2; |

![image-20230322172403893](D:\markdown file\截图\image-20230322172403893.png)

![image-20230322172415645](D:\markdown file\截图\image-20230322172415645.png)

![image-20230322193853754](D:\markdown file\截图\image-20230322193853754.png)

|          命令          |                            代码                            |
| :--------------------: | :--------------------------------------------------------: |
|   在数据表中更新数据   | update 表名 set 更新字段名称 = 更新的字段内容 where  条件; |
| 在数据表中批量更新数据 |       update 表名 set 更新字段名称 = 更新的字段内容;       |

![image-20230322194022069](D:\markdown file\截图\image-20230322194022069.png)

![image-20230322194032275](D:\markdown file\截图\image-20230322194032275.png)

![image-20230322194550266](D:\markdown file\截图\image-20230322194550266.png)

|        命令        |                    代码                     |
| :----------------: | :-----------------------------------------: |
| 在数据表中删除数据 |        delete from 表名 where 条件;         |
|     删除数据表     | delete from 表名; 或者 truncate table 表名; |

![image-20230322194851743](D:\markdown file\截图\image-20230322194851743.png)

![image-20230323110305420](D:\markdown file\截图\image-20230323110305420.png)

![image-20230323112712215](D:\markdown file\截图\image-20230323112712215.png)

![image-20230323110825255](D:\markdown file\截图\image-20230323110825255.png)

![image-20230323110925212](D:\markdown file\截图\image-20230323110925212.png)

![image-20230323112343523](D:\markdown file\截图\image-20230323112343523.png)

![image-20230323112324987](D:\markdown file\截图\image-20230323112324987.png)

![image-20230323112546947](D:\markdown file\截图\image-20230323112546947.png)

主键就是数据表中唯一标识一条数据的主要方式

![image-20230323112750915](D:\markdown file\截图\image-20230323112750915.png)

![image-20230323112759571](D:\markdown file\截图\image-20230323112759571.png)

![image-20230323113619439](D:\markdown file\截图\image-20230323113619439.png)

![image-20230323113628099](D:\markdown file\截图\image-20230323113628099.png)

|      命令      |                             代码                             |
| :------------: | :----------------------------------------------------------: |
|    创建主键    |         create table 表名(字段名 int primary, ...);          |
|    创建主键    | create table 表名(字段名 int, ..., constraint 主键名称 primary key(字段名)); |
|    创建外键    | create table 表名(字段名 int, ..., constraint 主键名称 foreign key (字段名) reference 关联表(关联表字段名)); |
|  创建非空约束  |  create table 表名( ..., 字段名 varchar(30) not null, ...);  |
|  创建唯一约束  |   create table 表名( ..., 字段名 varchar(30) unique, ...);   |
| 创建默认值约束 | create table 表名( ..., 字段名 numeric(9, 2) default 0.0, ...); |

![image-20230323113721783](D:\markdown file\截图\image-20230323113721783.png)

![image-20230323113735720](D:\markdown file\截图\image-20230323113735720.png)

![image-20230323123154697](D:\markdown file\截图\image-20230323123154697.png)

![image-20230323123204903](D:\markdown file\截图\image-20230323123204903.png)

![image-20230323123631550](D:\markdown file\截图\image-20230323123631550.png)

![image-20230323123649858](D:\markdown file\截图\image-20230323123649858.png)

![image-20230323123703794](D:\markdown file\截图\image-20230323123703794.png)

![image-20230323123715358](D:\markdown file\截图\image-20230323123715358.png)

![image-20230323123736389](D:\markdown file\截图\image-20230323123736389.png)

![image-20230323123527078](D:\markdown file\截图\image-20230323123527078.png)

![image-20230323123538299](D:\markdown file\截图\image-20230323123538299.png)

![image-20230323123802592](D:\markdown file\截图\image-20230323123802592.png)

![image-20230323123827795](D:\markdown file\截图\image-20230323123827795.png)

![image-20230323123908936](D:\markdown file\截图\image-20230323123908936.png)

![image-20230323123933188](D:\markdown file\截图\image-20230323123933188.png)

![image-20230323123945513](D:\markdown file\截图\image-20230323123945513.png)

![image-20230323150836847](D:\markdown file\截图\image-20230323150836847.png)

![image-20230323151415117](D:\markdown file\截图\image-20230323151415117.png)

![image-20230323153138342](D:\markdown file\截图\image-20230323153138342.png)

![image-20230323153149356](D:\markdown file\截图\image-20230323153149356.png)

![image-20230323154110598](D:\markdown file\截图\image-20230323154110598.png)

![image-20230323154844037](D:\markdown file\截图\image-20230323154844037.png)

![image-20230323154852498](D:\markdown file\截图\image-20230323154852498.png)

![image-20230323155422575](D:\markdown file\截图\image-20230323155422575.png)

|                         命令                         |                             代码                             |
| :--------------------------------------------------: | :----------------------------------------------------------: |
|                    查询表全部内容                    |                     select * from 表名;                      |
|                 查询表具体字段的内容                 |         select 字段名1, 字段名2, 字段名3 from 表名;          |
|               查询表具体字段的指定内容               |    select 字段名1, 字段名2, 字段名3 from 表名 where 条件;    |
|      查询表具体字段的内容并根据字段内容升序排序      | select 字段名1, 字段名2, 字段名3 from 表名 order by 字段名3; |
|      查询表具体字段的内容并根据字段内容降序排序      | select 字段名1, 字段名2, 字段名3 from 表名 order by 字段名 desc; |
|               查询表的前n条数据的内容                |               select * from 表名 limit 数量n;                |
|              查询表的m到m+n条数据的内容              |         select * from 表名 limit 数量n offset 数量m;         |
|              内连接查询（从两个表查询）              | select 字段名1, 字段名2, 字段名3 from 表名1, 表名2 where 条件; 或 select 字段名1, 字段名2, 字段名3 from 表名1 inner join 表名2 on 条件; |
| 左连接查询（返回左表所有的数据内容包括不匹配的数据） | select 字段名1, 字段名2, 字段名3 from 表名1 left outer join 表名2 on 条件1 where 条件2; |
|  子查询EXIST（内部的子查询产生结果才执行外部查询）   | select 字段名1 from 表名1 where exists (select 字段名2 from 表名2 where 条件) |
|                       子查询IN                       | select 字段名1 from 表名1 where 字段名2 in (select 字段名3 from 表名2 where 条件) |
|                      标量子查询                      | select 字段名1, 字段名2, (select 字段名3 from 表1 where 条件) from 表2; |
|              查询结果合并（有重复结果）              |  select 字段名1 from 表1 union all select 字段名2 from 表2;  |
|              查询结果合并（无重复结果）              |    select 字段名1 from 表1 union select 字段名2 from 表2;    |

[如何将linux中的数据库连接到win下](https://blog.csdn.net/omg_self/article/details/51416876?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-51416876-blog-98389366.235%5Ev27%5Epc_relevant_3mothn_strategy_recovery&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-51416876-blog-98389366.235%5Ev27%5Epc_relevant_3mothn_strategy_recovery&utm_relevant_index=1)
