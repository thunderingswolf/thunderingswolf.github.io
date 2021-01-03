---
title: java基础
date: 2021-01-02 21:42:30
categories:
- 技术
tags:
- java
- outline
---

# java基础

- 数据类型
- String
- 运算
- 关键字
- Object
- 继承
- 反射
- 异常
- 泛型
- 注解
- 特性



## 数据类型

基础数据类型：

- 字符型（char）：16bit、‘\u0000--u\ffff’、‘\u0000’
- 布尔型（boolean）：1bit、true/false、false
- 数值型
  - 整数类型
    - 字节（byte）：8bit、-128--127、0
    - 短整型（short）：16bit、-32768--32768、0
    - 整型（int）：32bit、--、0
    - 长整型（long）：64bit、--、0
  - 浮点类型
    - 浮点数（float）：32bit、--、0.0f
    - 双精度浮点数（double）：64bit、--、0.0d

引用数据类型：

- 类（class）
- 接口（interface）
- 数组（array）

## String

String 不属于基础类型， String 属于对象。

String类中使用字符数组保存字符串，private　final　char　value[]，所以string对象是不可变的。

String中的对象是不可变的，也就可以理解为常量，线程安全。

## 运算



## 关键字

## Object

## 继承

## 反射

## 异常

## 泛型

## 注解

## 特性

1. 简单易学；

2. 面向对象（封装，继承，多态）；

3. 平台无关性（Java虚拟机实现平台无关性）；

4. 可靠性；

5. 安全性；

6. 支持多线程（C++语言没有内置的多线程机制，因此必须调用操作系统的多线程功能来进行多线程程序设计，而Java语言却提供了多线程支持）；

7. 支持网络编程并且很方便（Java语言诞生本身就是为简化网络编程设计的，因此Java语言不仅支持网络编程而且很方便）；

8. 编译与解释并存；