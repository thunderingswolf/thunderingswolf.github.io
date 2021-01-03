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

java基础最重要的资料就是官方白皮书，诸多基础概念，白皮书写的都比较详细，不可忽略的内容。如需细品的Jave SE Platform 概览图：

![img](../../images/java-基础/2167990.jpg)

## 概念

### [Java Runtime Environment (JRE)](http://docs.oracle.com/javase/8/docs/technotes/guides/index.html#jre-jdk)

Java Runtime Environment (JRE) 提供运行用 Java 编程语言编写的应用和小程序所需的库、Java 虚拟机和其他组件。此外，JRE 还包括两项关键的部署技术：[Java 插件](https://www.oracle.com/technetwork/java/plugin-137649.html?ssSourceSiteId=otncn) — 使小程序可以在常用浏览器中运行；以及 Java Web Start — 通过网络部署独立的应用。它还是用于企业软件开发和部署的 Java 2 Platform, Enterprise Edition (J2EE) 的基础。JRE 不包含用于开发应用和小程序的工具和实用程序，如编译器或调试器。

### [Java Development Kit (JDK)](http://docs.oracle.com/javase/8/docs/technotes/guides/index.html#jre-jdk)

JDK 是 JRE 的超集，不但包含 JRE 中的所有内容，还包含开发应用和小程序所需的工具，如编译器和调试器。上面的示意图阐释了 Java SE 平台中的所有技术以及彼此之间关系。

### [Java SE API](https://www.oracle.com/technetwork/cn/java/javase/documentation/api-jsp-136079-zhs.html)

Java SE 应用编程接口 (API) 定义了应用或小程序对编译后的 Java SE 类库中的功能请求和使用的方式。（Java SE 类库也是 Java SE 平台的一部分。）

Java SE API 由核心技术、桌面（或客户端）技术以及其他技术组成。

- 核心组件提供在数据库访问、安全性、远程方法调用 (RMI) 和通讯等关键领域编写强大的企业级程序的基本功能。
- 桌面组件添加了全面的特性，帮助构建可为部署产品（如 Java 插件）、组件建模 API（如 JavaBeans）以及图形用户界面提供丰富用户体验的应用。
- 其他组件完善了此功能。

### [Java 虚拟机](https://www.oracle.com/technetwork/cn/java/javase/tech/index-jsp-136373-zhs.html)

[Java 虚拟机](https://www.oracle.com/technetwork/cn/java/javase/tech/index-jsp-136373-zhs.html)确保了 Java SE 平台的硬件和操作系统无关性、轻量级编译代码（字节码）和平台安全性。

### [Java 平台工具](https://www.oracle.com/technetwork/java/javase/tech/tools-jsp-138765.html?ssSourceSiteId=otncn)

Java SE 平台可与一系列工具协同工作，这些工具包括集成开发环境 (IDE)、性能和测试工具以及性能监视工具。



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