---
title: Spark、Scala学习（1）——spark算子
date: 2018-01-23 21:54:35
tags:
- spark
- scala
categories:
- 学习
---

[两类常用算子示意图](http://note.youdao.com/noteshare?id=0778b37ae517600f91d6c8a9b7d9e02f&sub=BDB9D1C094604D0BA3C71DE3FE72C930)


#####  RDD：弹性分布式数据集，是一种特殊集合 ‚ 支持多种来源 ‚ 有容错机制 ‚ 可以被缓存 ‚ 支持并行操作，一个RDD代表一个分区里的数据集

### transformation（转换）算子
这种变换并不触发提交作业，完成作业中间过程处理。
Transformation属于延迟计算，当一个RDD转换成另一个RDD时` 并没有立即进行转换 `，仅仅是记住了数据集的逻辑操作

* map
* flatMap
* distinct
* coalesce
> **def coalesce(numPartitions: Int, shuffle: Boolean = false)(implicit ord: Ordering[T] = null): RDD[T]**
> 将RDD的分区数量重新调整为numPartitions个,如果shuffle为true，分区数量可以大于原值。
* ` repartition `
> **def repartition(numPartitions: Int)(implicit ord: Ordering[String]): org.apache.spark.rdd.RDD[String]**
相当于 coalesce 的shuttle 为true


### action（执行）算子
这类算子会触发 SparkContext 提交 Job 作业。
Action触发Spark作业的运行，真正` 触发转换算子的计算 `


##### 从小方向来说，Spark 算子大致可以分为以下三类:
1. Value数据类型的Transformation算子，这种变换并不触发提交作业，针对处理的数据项是Value型的数据。
2. Key-Value数据类型的Transfromation算子，这种变换并不触发提交作业，针对处理的数据项是Key-Value型的数据对。
3. Action算子，这类算子会触发SparkContext提交Job作业。
