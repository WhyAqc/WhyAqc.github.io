---
title: Spark、Scala学习（2）——scala数组
date: 2018-01-23 21:55:39
tags:
- spark
- scala
---

# 两种数组
>定长数组：Array
>变长数组：ArrayBuffer
## 知识点
- 提供初始值时不要使用new,复杂对象数组没有提供初始值时必须提供new
>
```
scala> val numberArray = new Array[int](10)
numberArray:Array[Int] = Array(null, null, null, null, null, null, null, null, null, null)
```
>这里如果不加new，会报错
```
//导入可变包，Scala中的可变集合都是放在mutable中，使用时要导入
scala> import scala.collection.mutable.ArrayBuffer
import scala.collection.mutable.ArrayBuffer
```
- 变长数组的更多操作:增，删，改
```
scala> val arrayBuffer = ArrayBuffer[Int]()
arrayBuffer: scala.collection.mutable.ArrayBuffer[Int] = ArrayBuffer()

//在尾部添加一个值
scala> arrayBuffer += 1
res17: arrayBuffer.type = ArrayBuffer(1)

//在尾部添加多个元素
scala> arrayBuffer += (2, 3, 4, 5)
res19: arrayBuffer.type = ArrayBuffer(1, 2, 3, 4, 5)

//在尾部添加一个集合
scala> arrayBuffer ++= Array(6, 7, 8, 9)
res20: arrayBuffer.type = ArrayBuffer(1, 2, 3, 4, 5, 6, 7, 8, 9)

//移除最后2个元素
scala> arrayBuffer.trimEnd(2)

//在开头移除1一个元素
scala> arrayBuffer.trimStart(2)

scala> arrayBuffer
res23: scala.collection.mutable.ArrayBuffer[Int] = ArrayBuffer(2, 3, 4, 5, 6, 7)


//在任意位置插入或者删除元素
scala> arrayBuffer.insert(2, 6)
//ArrayBuffer(2, 3, 6, 4, 5, 6, 7)

scala> arrayBuffer.insert(1, 2, 3, 4)
//ArrayBuffer(2, 1, 2, 3, 4, 3, 6, 4, 5, 6, 7)

scala> arrayBuffer.remove(2)
//ArrayBuffer(2, 1, 3, 4, 3, 6, 4, 5, 6, 7)

scala> arrayBuffer.remover(1, 8)
//ArrayBuffer(2, 7)
```
- 两者之间的转换
```
//变长转换长定长
scala > arrayBuffer.toArray
//Array(2, 7)

//定长转换成变长
scala>res7.toBuffer
//ArrayBuffer(2, 7)
```
- 常用算法
> 求和、求最大值、求最小值
排序：
```
//sorted方法将数组或数组缓冲排序并返回经过排序的数组或数组缓冲，原始数组被保留
scala>val b = ArrayBuffer(1, 7, 2, 9)
b:ArrayBuffer[Int] = ArrayBuffer(1, 7, 2, 9)
scala>val bSorted = b.sorted(_<_)
bSorted: ArrayBuffer[Int] = ArrayBuffer(1, 2, 7, 9)
```
> 转String：

```
//toString()方法
scala> intArr.toString()
res94: String = [I@141aba8

//mkString()方法
scala> intArr.mkString(",")
res96: String = 1,2,3,4,5,6,7,8,9,10

scala> intArr.mkString("<",",",">")
res97: String = <1,2,3,4,5,6,7,8,9,10>
```


