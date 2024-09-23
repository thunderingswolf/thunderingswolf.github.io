---
title: java基础
date: 2021-01-02 21:42:30
categories:
- tech
- java
tags: 
- tech
- java
---

# java基础

java基础最重要的资料就是官方白皮书，诸多基础概念，白皮书写的都比较详细，不可忽略的内容。如需细品的Jave SE Platform 概览图：


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

## 个人理解

java是一个很大的生态，写代码的时候只是从源代码的角度涉及很小一块，我把编出的代码看作是四方库；java整体上，核心流程大致涉及：四方库、三方库、二方库、编译器、类加载器、JVM。

java程序的整体过程可以描述为：根据业务需要引入二方库、三方库，根据java语法编写源代码（四方库），完成后将源代码提交给编译器编译为字节码；使用java内置类加载器或自己编写的类加载器（四方库）加载字节码供jvm解释执行，jvm将字节码根据不同的操作系统平台解释成不同的机器指令，在操作系统允许的权限下，调用机器资源达到预期目标。

细节过程并不严谨，且在这个过程中，继续分析：可分为-编写、编译、解释、执行；整个过程是由多个组件合作完成的，不同阶段参与度是不同的，比如四方库的编写，属于**构建**，自由发挥的空间比较大；编译器、类加载器、JVM环节如果已经选定，属于**使用**，多是优化配置；当然java白皮书中对各组件并没有十分严格的限制，jdk中也只是提供了某些默认实现，如果需要或者有能力，完全可以自行实现从编译器、类加载器、JVM相关组件，也确实有。有几点需要注意，并不是所有的组件都是java语言实现的，比如编译器、部分类加载器、JVM并不是Java实现的；二方库和三方库并没有明确的限定，二方库特指jdk中已经集成了的，比如derby；

按照这条主线上涉及的组件或环节，再衍生分析对java的学习思路。

依据语法，写出编译器能识别的内容，依据语言特性组织代码之间的关系；衍生出对操作系统内存、cpu、设备的操作，对数据结构、算法、设计模式的应用。依据对二方库、三方库的依赖，衍生出ant、maven、gradle等技术。自定义类加载器和提供第三方库的角度，衍生出各种第三方库，如spring、hadoop等生态。根据执行过程中优化需求，衍生出对jvm的内存结构、垃圾回收机制、垃圾收集器实现机制的了解。java的多线程特性，引出并发编程方面的需求，需要关注线程状态、多个线程通信、线程安全等内容。java的网络特性，衍生出对计算机网络协议方面的需求，如netty、rpc/grpc等技术。数据的传递又涉及序列化、反序列化技术，如json、protobuf等格式。

总而言之，技术的学习应当明确对一种技术，目标到底是使用还是构建。虽然构建有助于使用，但学习过程中并不是所有的技术都必须构建的，学习过程中尽量时刻明确定位，避免陷入其中。

再谈具体的知识点，具体的知识点是为知识体系的构建服务的，解决问题的本质是在知识体系下选取合适的知识点应用到合适的位置和阶段上。

java的生态很大，比如spring技术栈、hadoop技术栈都有足够多的内容供学习研究，但还是力求知其然知其所以然，知道自己从事或学习的知识在一颗大树的什么位置，向上向下都是有关联和方向的。

计算机技术学习的路上有很多知识点，日新月异，变化繁多。但总有些东西是基础中的基础，万变不离其中，我们暂称其为内功，另外一些则是招式，当然并没有十分明确的界限。比如数据结构、算法、设计模式，这些大概可以称为内功，而编程语言、框架等则可称为招式。



Java主线，所有均为对象，对象内容的存储内存的分配也是以堆为主；只是存在了一些特殊情况，比如基础类型、string，本地方法，即时编译等情况，无外乎是因为使用频率或效率、空间原因，做出的优化策略。所以java需要把握主线

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