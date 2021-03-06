---
title: 算法学习记录-3
author: Pertal
top: false
cover: false
toc: true
mathjax: true
tags:
  - - 数据结构与算法之美
  - - 极客时间
  - - 学习
categories:
  - 算法与数据结构
summary: '算法学习记录Day03,进入基础篇的学习'
abbrlink: 94f519fc
date: 2020-07-15 15:57:55
password:
---

# 前言

前两天的学习主要学习了算法的介绍以及算法的时间和空间复杂度分析的问题，并且学习了最好，最坏，平均，均摊时间复杂度，今天的学习从数组开始。

# 知识总结

## 问题引入

首先我们要带着一个问题来学习**为什么数组要从*0*开始编号，而不是从*1*开始进行编号？**

### 解答

a表示**首地址**，那么a[0],这里0其实准确是**偏移量(offset)**,那么a[k]其实表示的就是偏移**k**个**type_size**的位置，那么a[k]计算公式为：

```c
a[k]_address  = base_address + k * type_size	
```

如果从**1**开始，那么计算a[k]的公式为：

```c
a[k]_address = base_address + (k-1) * type_size
```

这里的话多了一次减法操作，其实**最主要**原因可能是**历史原因**。

## 数组

### 数组定义

**数组（Array）**是一种**线性表**数据结构。它用一组**连续的内存**空间，来存储一组具有**相同类型**的数据。

### 数组的三要素

#### 线性表

**线性表**是排成像**一条线**一样的结构，**只**有**前后**关系，同样的线性表结构也有**链表**，**队列**，**栈**。

**非线性表**，并不是简单的**前后**关系。

#### 连续内存空间

**数组**由需要给与它一段**连续**的空间存储内容，计算机给其分配时是的内存是**连续的**，因此这里会出现一个**弊端**就是如果没有**写满**，那么会造成**内存**的**浪费**。

#### 相同类型的数据

作为**数组**，在构造时它存放的**数据类型**是相同的，如果不同会出现报错。

#### 随机访问特性

由于**连续内存空间**和**相同类型的数据**的限制，让其出现了**操作低效率**的问题，但是同样也让其能够实现**随机访问**，算是有利有弊。

#### 如何实现利用下标随机访问数组元素

首先分配一个长度**10**的**int**类型的数组 `int[] a = new int[10];`,那么计算机就会给它分配一块**连续空间**，这里假设为1000-1039，同样假设首地址为`base_address = 1000`.

计算机会给每个**内存单元**分配一个地址，计算机通过**地址**访问内存中的**数据**，当计算机需要**随机访问**数组中**某个元素**，需要利用**寻址公式**，计算元素的**内存地址 **。

```c
// 要寻找下标的内存地址 = 首地址 + 下标 * 元素大小
a[i]_address = base_address + i * data_type_size;
```

#### 一个“错误“的纠正

**数组**和**链表**的**区别**，**错误**答案经常回答：**链表**适合**插入**、**删除**，时间复杂度为$ O(1) $;**数组**适合**查找**，时间复杂度为$ O(1) $。

数组适合**查找**，但查找即使排序好的数组，利用**二分查找**，时间复杂度为$ O(logn) $,**正确**的表达是**数组**支持**随机访问**，根据**下标**进行**随机访问**的时间复杂度为$ O(1) $。

### 低效的“插入”和“删除”

#### 插入操作

假设这里执行插入操作，插入位置为第**k**个位置，那么我们可以得到下面这样的代码：

```c
// 这里我们假设数组长度为n 实际上并不能这么写 这里假设数组的空间会自动扩充
int[] a = a[n]
for(int i = k ; i < n - 1 ; i++)  
{
	a[i+1] = a[i]; 
}

```

通过这个我们可以计算时间复杂度

首先是**最好时间复杂度**，那么这时候为$ O(1) $,这个情况属于**特殊情况**，比如插入在末尾；接下来是**最坏时间复杂度**，那么这个时候在首尾，可能需要执行$ O(n) $次的操作，因为要将从**0**开始到**n**都往后移位；之后就是平均复杂度，这里出现的情况总共有**n**种，那么可以得到如下的公式：
$$
\frac{1+2+3+\cdots+n}{n} = \frac{\frac{n(n+1)}{2}}{n}=\frac{n(n+1)}{2n}=\frac{n+1}{2}=O(n)
$$

##### 特例

除了这种移动的操作，还有一种**骚操作**，那就是直接把**原来位置**的元素移动到**末尾**，然后再插入位置在**k**的元素，这样复杂度就变成了$ O(1) $，但是这是一种**特例**操作，只有特定情况使用。

#### 删除操作

删除操作其实同插入一样，如果要删除**k**位置的数据，删除完我们要**搬移**相关的数据，所以这样的话，**最好时间复杂度**为$ O(1) $,**最坏时间复杂度**为$ O(n) $，**平均时间复杂度**为$O(n)$。

##### 特例

这个情况在**连续**删除操作执行时，我们可以**记录**数据**被删除**，当数组存储空间**没有**时，我们在**执行**一次**删除**操作。

这样的例子是**JVM**的**标记清楚垃圾回收算法**

### 警惕数据访问越界的问题

对于**C语言**，数组访问越界并没规定编译器该如何处理，因此这种情况下，容易出现**逻辑错误**，这样很多计算机病毒就可以利用**数组越界**访问**非法地址**来实现攻击；其他语言，有些具有**越界检查**。

### 容器是否能代替数组

#### 容器的优势

1. 封装了数组操作的细节
2. 支持动态扩容

**注**：创建容器之前最好事先指定数据大小。

#### 数组的优势

1. 容器**无法存储**基本类型，需要**封装**，因此具有**性能消耗**。
2. 数组操作简单情况下，直接使用数组方便
3. 多维数组下，数组显示直观

# 思考题

1. 前面我基于数组的原理引出 JVM 的标记清除垃圾回收算法的核心理念。我不知道你是否使用 Java 语言，理解 JVM，如果你熟悉，可以在评论区回顾下你理解的标记清除垃圾回收算法。

   这一题以后再答。

2. 前面我们讲到一维数组的内存寻址公式，那你可以思考一下，类比一下，二维数组的内存寻址公式是怎样的呢？

   一维数组的计算公式为：

   ```c
   a[i]_address = base_address + i * data_type_size
   ```

   二维数组的计算公式为：

   ```c
   //注意 这里假设数组为m*n的
   /*
   	那么这里 i < m j < n
   	由于内存是一个线性的结构
   	那么它的存储也是线性的
   	如果我要i要取到第二层的，那么
   	前面就排了第一层n个j，
   	之后再加上此层的j
   */
   a[i][j]_address = base_address + (i * n + j) * type_size
   ```

   