---
title: Spark、Scala学习（0）——搭建环境
date: 2018-01-23 21:43:35
tags: 
- spark 
- scala
categories:
- 学习
---
## Spark运行环境和版本对应
### java
> 1.7
### scala
> 2.10.6
>> **注意scala与spark的版本要对应好，不然会报错，如下。**
```
Error:scalac: Error: object BooleanRef does not have a member create
scala.reflect.internal.FatalError: object BooleanRef does not have a member create
```
>> **其中，BooleanRef 会各种变，什么Long、Value等，都是因为版本没对应!百度好spark支持的scala版本最重要**
### hadoop
> 1.6.0
>> 根据集群版本选择
### Spark
> 1.6.3
>> spark官网在下载时很人性的给出了spark和hadoop的版本对应
