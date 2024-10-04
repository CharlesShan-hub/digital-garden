---
{"dg-publish":true,"permalink":"/programming/c/yu-bei-zhi-shi/","contentClasses":".content svg {width: 100%; height: auto;}"}
---


# 预备知识

### 1.1 C++简介

三种不同的编程方式：过程，OOP，泛型

***

### 1.2 C++简史

#### 1.2.1 C 语言

汇编直接操作硬件，C 语言提高了可移植性

#### 1.2.2 C语言编程原理

1. 程序 = 数据+算法。C 语言强调的是算法。
2. 结构化编程(structured programming)，比如 for 循环，do while 循环，if else 语句
3. 自顶向下(top-down)的设计：模块化开发

#### 1.2.3 面向对象编程

C++ 语言强调的是数据。

#### 1.2.4 C++和泛型编程

比如，一个并不局限于某个特定类型的函数。

#### 1.2.5 C++的起源

和C 一样，贝尔实验室，主页：[http://www.research.att.com/-bs/](http://www.research.att.com/-bs/)

***

### 1.3 可移植性和标准

#### 1.3.1 C++的发展

* Stroustrup 编写的《The Programming Language》
* Ellis 和 Stroustrup 编写的《The Annotated C++ Reference Manual》
* C++98：描述了已有的 C++特性，还对该语言进行了扩展，添加了异常、运行阶段类型识别(RTTI)、模板 和标准模板库(STL)
* C++03：修订错误、减少多义性
* C++11：消除不一致性

#### 1.3.2 本书遵循的 C++标准

***

### 1.4 程序创建的技巧

* 源代码 -> 编译器 -> 目标代码
* 目标代码 + 启动代码 + 库代码 -> 链接程序 -> 可执行代码

#### 1.4.1 创建源代码文件

1. 常见的集成开发环境（详见书）
2. 不同的 C++实现笃定的源代码文件扩展名（详见书）

#### 1.4.2 编译和链接

以下为Linux 的命令，其他操作系统上的编译运行方法（详见书）

* 普通的编译：`g++ spiffy.cxx`
* 加入链接库：`g++ spiffy.cxx -lg++`
* 编译多个文件：`g++ my.cxx precious.cxx`&#x20;
* 也可以通过之前生成的.o文件编译：`g++ my.cxx precious.o`