# Hbase

hbase是干什么的？它解决了HDFS的那些问题？

复合式的键值对（map），底层是bigtable

快速的原因：整个架构是依赖hdfs，本身是一个稀疏的map，按key进行排序，还支持索引机制。底层用的是LSM树

# ClickHouse

使用merge tree的底层搜索引擎，MergeTree 存储引擎实际上是基于 LSM 树（Log-Structured Merge-tree）的一种变体。

不依赖hdfs

可存储、可查询。且更快

是个分析型数据库。

