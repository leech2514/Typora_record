# spark测试题1

## 第二章

**1、什么是spark及spark的特点**

spark是一个多语言引擎，用于大规模数据分析的统一引擎，它支持批/流处理，支持纯 SQL 开发等。

特点：简单（支持多种语言色API算法，能快速构建解决算法），通用（支持批处理，实时流处理，sparkSQL，机器学习，图计算）
             兼容性好（能很方便的与其他开源产品融合），速度快

 

## 第三章`

1、spark的生态体系包括哪些

2、spark的集群架构及常见的master、worker、executor、applicationMaster等概念

3、什么是spark中的driver，及driver的功能

- 含义：spark中的驱动器
- 功能：
  - 

4、spark常见的部署模式有哪些

- local模式：直接可以再idea中运行
- standalone：本身就有资源调度服务，因此此模式下也就不需要依赖其它资源调度器。整个集群是主从结构，一个主节点Master和多个slave节点，启动的进程为Worker。单节点模式容易出现单点故障
- Yarn：称为spark on Yarn，spark作为客户端，将作业提交给yarn服务，由于在生产环境中，很多时候都要与 Hadoop 使用同一个集群，因此采用 Yarn来管理资源调度，可以有效提高资源利用率，Yarn 模式又分为 ==Yarn Cluster 模式==和 ==Yarn Client 模式==

5、spark on yarn两种部署模式的分析

- yarn cluster模式：一般用在生产环境
- yarn client模式：更多是测试环境

两种部署模式的区别主要是driver的部署位置不同造成，cluster模式是通过ResourceManager某个NodeManager中创建driver

6、SparkContext的功能有哪些？

- 创建RDD的API,spark集群的唯一接口（sparkSession封装了sparkcontext）
- 提供的对外使用spark的接口，通过SparkContext来使用spark内部的程序

> 1. 通往spark集群的唯一入口，用来创建RDDs、累加器变量和广播变量等
> 2. 核心作用：初始化spark应用程序运行所需要的核心组件，包括高层调度器DAGScheduler、底层调度器TaskScheduler和调度器的通信终端
> 3. 一个jvm进程只能有一个SparkContext实例（调用stop方法可以停止该实例）

**7、spark-submit是什么及常见的参数有哪些？**

--class 提交的类

--name

-- master 任务提交的位置，包括本地集群、yarn部署集群等

具体的jar包地址

> --master 任务提交到哪里执行，选项：local[线程个数]、yarn等
>
> --deploy-mode 部署模式，spark on yarn的两种部署模式
>
> --class 应用程序的主类，仅针对Java或Scala应用
>
> --name 指定应用程序的名称，在yarn调度器下只对cluster模式生效
>
> --jar 本地jar包的路径
>
> -- queue QUEUE_NAME 任务提交到那个队列
>
> 等等

 

## 第四章

1、什么是RDD以及如何理解RDD中所说的弹性

- RDD弹性分布式数据集，spark数据抽象的一种（RDD、dataframe、dataset）
- 弹性主要体现在用适用区间代替适用点。体现在六方面
  - 存储可弹：自动进行磁盘和内存间数据存储的切换（内存不足，自动加载到磁盘）
  - 基于Lineage（血缘）的高效容错；（可能和RDD的持久化（cache、persist、checkpoint）有关系）
  - 如果Task失败会自动进行特定次数的重试
  - stage如果失败会自动进行特定次数的重试，并且只重试失败的分片（不懂？？？？）
  - checkpoint、cache和persist（检查点和持久化）
  - 数据分片的高度弹性（不懂？？？）

2、RDD核心属性的五元组是哪五个并且做简单的解释

3、job、stage、task之间的关系及并行度和分区之间的关系

4、常见的转换算子的理解

​	i、相似算子的比较，如map和mapPartition、repartitions和coalesce等比较他们之间的异同点及优缺点

​	ii、有哪些算子会产生shuffle

5、Transformation算子和Action算子的概念及区分原则

6、什么是DAG及宽窄依赖

7、简述spark中stage的划分原则及流程

8、为什么要排序，为什么要做文件合并

9、spark中默认的shuffle及常见的shuffle的比较

10、什么是持久化，什么是检查点，以及两者的区别

11、cache和persist的区别有哪些

12、什么是容错以及spark中的容错机制有哪些

13、什么是分区器及spark中常见的分区器有哪些

 

## 第五章

1、什么是广播变量及使用的场景有哪些

2、什么是累加器变量及使用的场景有哪些

 

## 第七章

1、为什么说Spark在某种程度上可以直接取代MapReduce

 

## 第八章

1、什么是DataFrame和DataSe以及RDD、DataFrame和DataSet之间的区别及转换 

2、详细论述SparkSession的功能

3、spark sql中支持几种join方式，分别是什么

4、spark sql中支持几种join策略及策略如何选择

5、管理表和外部表的区别

6、spark sql中通常支持哪几种内置的文件格式的读取与写入

7、Hive on Spark和Spark on Hive的定义及区别

8、spark sql中什么是UDF和UDAD及两者的注册

9、什么是catalyst及catalyst在整个spark sql中地位

10、catalyst包含哪几个模块，对应的功能又是什么

11、什么是CBO和RBO



## 其它提问

**1.如何区分算子是transformation算子还是action算子的规则是什么？** 

2.哪些算子是宽依赖算子？哪些算子是窄依赖算子？如何区分？

> 宽依赖算子：groupbykey/partitionby/repartition
>
> 窄依赖算子：map/filter/union/mappartitions