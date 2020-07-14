---
title: Java面试题
date: 2020-07-14 21:23:42
tags:java
---

# Java面试题梳理

## 1.Java基础

### Java基本类型-多少字节？

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

  

### Java语言有哪些特点？

1. 简单易学；
2. 面向对象（封装，继承，多态）；
3. 平台无关性（Java虚拟机实现平台无关性）；
4. 可靠性；
5. 安全性；
6. 支持多线程（C++语言没有内置的多线程机制，因此必须调用操作系统的多线程功能来进行多线程程序设计，而Java语言却提供了多线程支持）；
7. 支持网络编程并且很方便（Java语言诞生本身就是为简化网络编程设计的，因此Java语言不仅支持网络编程而且很方便）；
8. 编译与解释并存；

### 什么是Java虚拟机？为什么Java被称作是“平台无关的编程语言”？

Java虚拟机是一个可以执行Java字节码的虚拟机进程。Java源文件被编译成能被Java虚拟机执行的字节码文件。

Java被设计成允许应用程序可以运行在任意的平台，而不需要程序员为每一个平台单独重写或者是重新编译。Java虚拟机让这个变为可能，因为它知道底层硬件平台的指令长度和其他特性。

### 什么是JDK\JRE\JVM-联系与区别?

这几个是Java中很基本很基本的东西，但是我相信一定还有很多人搞不清楚！为什么呢？因为我们大多数时候在使用现成的编译工具以及环境的时候，并没有去考虑这些东西。

**JDK:** 顾名思义它是给开发者提供的开发工具箱,是给程序开发者用的。它除了包括完整的JRE（Java Runtime Environment），Java运行环境，还包含了其他供开发者使用的工具包。

**JRE:** 普通用户而只需要安装JRE（Java Runtime Environment）来运行Java程序。而程序开发者必须安装JDK来编译、调试程序。

**JVM：** 当我们运行一个程序时，JVM负责将字节码转换为特定机器代码，JVM提供了内存管理/垃圾回收和安全机制等。这种独立于硬件和操作系统，正是java程序可以一次编写多处执行的原因。

**区别与联系：**

1. JDK用于开发，JRE用于运行java程序 ；
2. JDK和JRE中都包含JVM ；
3. JVM是java编程语言的核心并且具有平台独立性。

### JDK 和 JVM 有什么区别？

JDK 是 Java Development Kit 的首字母缩写，是提供给 Java 开发人员的软件环境，包含 JRE 和一组开发工具。可分为以下版本：

- 标准版（大多数开发人员用的就是这个）
- 企业版
- 微型版

JDK 包含了一个私有的 JVM 和一些其他资源，比如说编译器（javac 命令）、解释器（java 命令）等，帮助 Java 程序员完成开发工作。

![](C:/Work/workspaces/xyzy/hexo/source/images/java/31-4.jpg)

### JVM 和 JRE 有什么区别？

Java RuntimeEnvironment（JRE）是 JVM 的实现。JRE 由 JVM 和 Java 二进制文件以及其他类组成，可以执行任何程序。JRE 不包含 Java 编译器，调试器等任何开发工具。

![](C:/Work/workspaces/xyzy/hexo/source/images/java/31-5.jpg)

### JDK和JRE的区别是什么？

Java运行时环境(JRE)。它包括Java虚拟机、Java核心类库和支持文件。它不包含开发工具（JDK）--编译器、调试器和其他工具。

Java开发工具包(JDK)是完整的Java软件开发包，包含了JRE，编译器和其他的工具(比如：JavaDoc，Java调试器)，可以让开发者开发、编译、执行Java应用程序。

### JRE、JDK、JVM 及 JIT 之间有什么不同？

JRE 代表 Java 运行时（Java run-time），是运行 Java 引用所必须的。JDK 代表 Java 开发工具（Java development kit），是 Java 程序的开发工具，如 Java 编译器，它也包含 JRE。JVM 代表 Java 虚拟机（Java virtual machine），它的责任是运行 Java 应用。JIT 代表即时编译（Just In Time compilation），当代码执行的次数超过一定的阈值时，会将 Java 字节码转换为本地代码，如，主要的热点代码会被准换为本地代码，这样有利大幅度提高 Java 应用的性能。

### 哪个类是所有类的超类？

java.lang.Object 是所有 Java 类的超类，我们不需要继承它，因为是隐式继承的。

### Java 中 `main` 方法的重要性是什么？

每个程序都需要一个入口，对于 Java 程序来说，入口就是 main 方法。

```
public static void main(String[] args) {
    
}
```



- public关键字是另外一个访问修饰符，除了可以声明方法和变量（所有类可见），还可以声明类。main 方法必须声明为 public。
- static关键字表示该变量或方法是静态变量或静态方法，可以直接通过类访问，不需要实例化对象来访问。
- void关键字用于指定方法没有返回值。

另外，main 关键字为方法的名字，Java 虚拟机在执行程序时会寻找这个标识符；args 为 main 方法的参数名，它的类型为一个 String 数组，也就是说，在使用 java 命令执行程序的时候，可以给 main 方法传递字符串数组作为参数。

```powershell
java HelloWorld 沉默王二 沉默王三
```

javac命令用来编译程序，java 命令用来执行程序，HelloWorld 为这段程序的类名，沉默王二和沉默王三为字符串数组，中间通过空格隔开，然后就可以在 main方法中通过 args[0] 和 args[1] 获取传递的参数值了。

```java
public class HelloWorld {
    public static void main(String[] args) {
        if ("沉默王二".equals(args[0])) {
            
        }if ("沉默王三".equals(args[1])) {
            
        }
    }
}
```

main 方法的写法并不是唯一的，还有其他几种变体，尽管它们可能并不常见，可以简单来了解一下。

第二种，把方括号 往 args 靠近而不是String 靠近：

```java
public static void main(String []args) { 
}
```

第三种，把方括号 放在 args 的右侧：

```java
public static void main(String args[]) { 
}
```

第四种，还可以把数组形式换成可变参数的形式：

```java
public static void main(String...args) { 
}
```

第五种，在 main 方法上添加另外一个修饰符 strictfp，用于强调在处理浮点数时的兼容性：

```java
public strictfp static void main(String[] args) { 
}
```

也可以在 main 方法上添加 final 关键字或者 synchronized 关键字。

第六种，还可以为 args 参数添加 final 关键字：

```java
public static void main(final String[] args) { 
}
```

第七种，最复杂的一种，所有可以添加的关键字统统添加上：

```java
final static synchronized strictfp void main(final String[] args) { 
}
```

当然了，并不需要为了装逼特意把 main 方法写成上面提到的这些形式，使用 IDE 提供的默认形式就可以了。

### Java 声称的平台独立性指的是什么？

常见的操作系统有 Windows、Linux、OS-X，那么平台独立性意味着我们可以在任何操作系统中运行相同源代码的 Java 程序，比如说我们可以在 Windows 上编写 Java 程序，然后在 Linux 上运行它。

### 什么是字节码？最大好处是？

**先看下java中的编译器和解释器：**

Java中引入了虚拟机的概念，即在机器和编译程序之间加入了一层抽象的虚拟的机器。这台虚拟的机器在任何平台上都提供给编译程序一个的共同的接口。

编译程序只需要面向虚拟机，生成虚拟机能够理解的代码，然后由解释器来将虚拟机代码转换为特定系统的机器码执行。在Java中，这种供虚拟机理解的代码叫做 字节码（即扩展名为 .class的文件），它不面向任何特定的处理器，只面向虚拟机。

每一种平台的解释器是不同的，但是实现的虚拟机是相同的。Java源程序经过编译器编译后变成字节码，字节码由虚拟机解释执行，虚拟机将每一条要执行的字节码送给解释器，解释器将其翻译成特定机器上的机器码，然后在特定的机器上运行。这也就是解释了Java的编译与解释并存的特点。

Java源代码---->编译器---->jvm可执行的Java字节码(即虚拟指令)---->jvm---->jvm中解释器----->机器可执行的二进制机器码---->程序运行。

**采用字节码的好处：**

Java语言通过字节码的方式，在一定程度上解决了传统解释型语言执行效率低的问题，同时又保留了解释型语言可移植的特点。所以Java程序运行时比较高效，而且，由于字节码并不专对一种特定的机器，因此，Java程序无须重新编译便可在多种不同的计算机上运行。

### Java和C++的区别

我知道很多人没学过C++，但是面试官就是没事喜欢拿咱们Java和C++比呀！没办法！！！就算没学过C++，也要记下来！

- 都是面向对象的语言，都支持封装、继承和多态
- Java不提供指针来直接访问内存，程序内存更加安全
- Java的类是单继承的，C++支持多重继承；虽然Java的类不可以多继承，但是接口可以多继承。
- Java有自动内存管理机制，不需要程序员手动释放无用内存

### 字符型常量和字符串常量的区别

1. **形式上:** 字符常量是单引号引起的一个字符 字符串常量是双引号引起的若干个字符
2. **含义上:** 字符常量相当于一个整形值(ASCII值),可以参加表达式运算 字符串常量代表一个地址值(该字符串在内存中存放位置)
3. **占内存大小上:** 字符常量只占一个字节 字符串常量占若干个字节(至少一个字符结束标志)

### String vs StringBuffer vs StringBuilder？String为什么是不可变的？

**可变性**　

String类中使用字符数组保存字符串，private　final　char　value[]，所以string对象是不可变的。StringBuilder与StringBuffer都继承自AbstractStringBuilder类，在AbstractStringBuilder中也是使用字符数组保存字符串，char[]value，这两种对象都是可变的。 　　

**线程安全性**

String中的对象是不可变的，也就可以理解为常量，线程安全。AbstractStringBuilder是StringBuilder与StringBuffer的公共父类，定义了一些字符串的基本操作，如expandCapacity、append、insert、indexOf等公共方法。StringBuffer对方法加了同步锁或者对调用的方法加了同步锁，所以是线程安全的。StringBuilder并没有对方法进行加同步锁，所以是非线程安全的。 　　

**性能**

每次对String 类型进行改变的时候，都会生成一个新的String对象，然后将指针指向新的String 对象。StringBuffer每次都会对StringBuffer对象本身进行操作，而不是生成新的对象并改变对象引用。相同情况下使用StirngBuilder 相比使用StringBuffer 仅能获得10%~15% 左右的性能提升，但却要冒多线程不安全的风险。

**对于三者使用的总结：**

如果要操作少量的数据用 = String 单线程操作字符串缓冲区 下操作大量数据 = StringBuilder 多线程操作字符串缓冲区 下操作大量数据 = StringBuffer

### java中String、StringBuild、StringBuffer的区别？？？


**答：**

String是不可变类，因此对String进行操作都会产生新的String对象，容易导致效率低下，浪费内存空间。因此，为了应对经常性的字符串操作，引入了StringBuffer、StringBuild这种字符串变量。

StringBufffer和StringBuild最大的区别，就是StringBuffer线程安全，但效率低，而StringBuild线程不安全，但效率高，且此两者只能通过构造函数的方式初始化。而String可以通过构造函数和字面量复制两种方式。

### 自动装箱与拆箱

**装箱**：将基本类型用它们对应的引用类型包装起来；

**拆箱**：将包装类型转换为基本数据类型；

### java中==和equals()的区别？？？

**答：**

简单来说==适合应用于基本数据类型的比较，而重写后equals()方法适合应用于引用类型的比较。原因在于基本类型变量直接存储的是值本身，而引用类型变量存储的是对象的引用，当引用相同时，用==比较，自然会是true,当引用不同时，用==比较，则会是false.equlals方法是object中的方法，对于所有继承于object的类都会有该方法.

当使用equals方法是需对此方法进行重写，如果没有对equals方法重写，则比较的是引用类型的，变量所指向的对象的地址，没有重写的equals,和==效果相同，只有重写了equals,比较的才会是所指对象的内容。

### ==与equals(重要)

**==** : 它的作用是判断两个对象的地址是不是相等。即，判断两个对象是不是同一个对象。(基本数据类型==比较的是值，引用数据类型==比较的是内存地址)

**equals()** : 它的作用也是判断两个对象是否相等。但它一般有两种使用情况：

- 情况1：类没有覆盖equals()方法。则通过equals()比较该类的两个对象时，等价于通过“==”比较这两个对象。

- 情况2：类覆盖了equals()方法。一般，我们都覆盖equals()方法来两个对象的内容相等；若它们的内容相等，则返回true(即，认为这两个对象相等)。

  举个例子：

  ![](C:/Work/workspaces/xyzy/hexo/source/images/java/equals%E4%BE%8B%E5%AD%90.jpg)

**说明：**

- String中的equals方法是被重写过的，因为object的equals方法是比较的对象的内存地址，而String的equals方法比较的是对象的值。
- 当创建String类型的对象时，虚拟机会在常量池中查找有没有已经存在的值和要创建的值相同的对象，如果有就把它赋给当前引用。如果没有就在常量池中重新创建一个String对象。

### hashCode与equals（重要）

面试官可能会问你：“你重写过 hashcode 和 equals 么，为什么重写equals时必须重写hashCode方法？”

**hashCode（）介绍**

hashCode() 的作用是获取哈希码，也称为散列码；它实际上是返回一个int整数。这个哈希码的作用是确定该对象在哈希表中的索引位置。hashCode() 定义在JDK的Object.java中，这就意味着Java中的任何类都包含有hashCode() 函数。

散列表存储的是键值对(key-value)，它的特点是：能根据“键”快速的检索出对应的“值”。这其中就利用到了散列码！（可以快速找到所需要的对象）

**为什么要有hashCode**

**我们以“HashSet如何检查重复”为例子来说明为什么要有hashCode：**

当你把对象加入HashSet时，HashSet会先计算对象的hashcode值来判断对象加入的位置，同时也会与其他已经加入的对象的hashcode值作比较，如果没有相符的hashcode，HashSet会假设对象没有重复出现。但是如果发现有相同hashcode值的对象，这时会调用equals（）方法来检查hashcode相等的对象是否真的相同。如果两者相同，HashSet就不会让其加入操作成功。如果不同的话，就会重新散列到其他位置。（摘自我的Java启蒙书《Head fist java》第二版）。这样我们就大大减少了equals的次数，相应就大大提高了执行速度。

**hashCode（）与equals（）的相关规定**

1. 如果两个对象相等，则hashcode一定也是相同的
2. 两个对象相等,对两个对象分别调用equals方法都返回true
3. 两个对象有相同的hashcode值，它们也不一定是相等的
4. **因此，equals方法被覆盖过，则hashCode方法也必须被覆盖**
5. hashCode()的默认行为是对堆上的对象产生独特值。如果没有重写hashCode()，则该class的两个对象无论如何都不会相等（即使这两个对象指向相同的数据）

### hashCode()和equals()方法的重要性体现在什么地方？

Java中的HashMap使用hashCode()和equals()方法来确定键值对的索引，当根据键获取值的时候也会用到这两个方法。如果没有正确的实现这两个方法，两个不同的键可能会有相同的hash值，因此，可能会被集合认为是相等的。而且，这两个方法也用来发现重复元素。所以这两个方法的实现对HashMap的精确性和正确性是至关重要的。

### Java中的值传递和引用传递

**值传递**是指对象被值传递，意味着传递了对象的一个副本，即使副本被改变，也不会影响源对象。（因为值传递的时候，实际上是将实参的值复制一份给形参。）

**引用传递**是指对象被引用传递，意味着传递的并不是实际的对象，而是对象的引用。因此，外部对引用对象的改变会反映到所有的对象上。（因为引用传递的时候，实际上是将实参的地址值复制一份给形参。）

### .”static”关键字是什么意思？Java中是否可以覆盖(override)一个private或者是static的方法？

“static”关键字表明一个成员变量或者是成员方法可以在没有所属的类的实例变量的情况下被访问。

Java中static方法不能被覆盖，因为方法覆盖是基于运行时动态绑定的，而static方法是编译时静态绑定的。static方法跟类的任何实例都不相关，所以概念上不适用。

java中也不可以覆盖private的方法，因为private修饰的变量和方法只能在当前类中使用，如果是其他的类继承当前类是不能访问到private变量或方法的，当然也不能覆盖。

### 是否可以在static环境中访问非static变量？

static变量在Java中是属于类的，它在所有的实例中的值是一样的。当类被Java虚拟机载入的时候，会对static变量进行初始化。如果你的代码尝试不用实例来访问非static的变量，编译器会报错，因为这些变量还没有被创建出来，还没有跟任何实例关联上。

### 在一个静态方法内调用一个非静态成员为什么是非法的？

由于静态方法可以不通过对象进行调用，因此在静态方法里，不能调用其他非静态变量，也不可以访问非静态变量成员。

### Java中，什么是构造方法？什么是构造方法重载？什么是复制构造方法？

当新对象被创建的时候，构造方法会被调用。每一个类都有构造方法。在程序员没有给类提供构造方法的情况下，Java编译器会为这个类创建一个默认的构造方法。

Java中构造方法重载和方法重载很相似。可以为一个类创建多个构造方法。每一个构造方法必须有它自己唯一的参数列表。

Java不支持像C++中那样的复制构造方法，这个不同点是因为如果你不自己写构造方法的情况下，Java不会创建默认的复制构造方法。

### 在Java中定义一个不做事且没有参数的构造方法的作用

Java程序在执行子类的构造方法之前，如果没有用super()来调用父类特定的构造方法，则会调用父类中“没有参数的构造方法”。因此，如果父类中只定义了有参数的构造方法，而在子类的构造方法中又没有用super()来调用父类中特定的构造方法，则编译时将发生错误，因为Java程序在父类中找不到没有参数的构造方法可供执行。解决办法是在父类里加上一个不做事且没有参数的构造方法。　

### import java和javax有什么区别

刚开始的时候JavaAPI所必需的包是java开头的包，javax当时只是扩展API包来说使用。然而随着时间的推移，javax逐渐的扩展成为Java API的组成部分。但是，将扩展从javax包移动到java包将是太麻烦了，最终会破坏一堆现有的代码。因此，最终决定javax包将成为标准API的一部分。

所以，实际上java和javax没有区别。这都是一个名字。

### 成员变量与局部变量的区别有那些？

1. 从语法形式上，看成员变量是属于类的，而局部变量是在方法中定义的变量或是方法的参数；成员变量可以被public,private,static等修饰符所修饰，而局部变量不能被访问控制修饰符及static所修饰；但是，成员变量和局部变量都能被final所修饰；
2. 从变量在内存中的存储方式来看，成员变量是对象的一部分，而对象存在于堆内存，局部变量存在于栈内存
3. 从变量在内存中的生存时间上看，成员变量是对象的一部分，它随着对象的创建而存在，而局部变量随着方法的调用而自动消失。
4. 成员变量如果没有被赋初值，则会自动以类型的默认值而赋值（一种情况例外被final修饰但没有被static修饰的成员变量必须显示地赋值）；而局部变量则不会自动赋值。

### 创建一个对象用什么运算符？对象实体与对象引用有何不同？

new运算符，new创建对象实例（对象实例在堆内存中），对象引用指向对象实例（对象引用存放在栈内存中）。一个对象引用可以指向0个或1个对象（一根绳子可以不系气球，也可以系一个气球）;一个对象可以有n个引用指向它（可以用n条绳子系住一个气球）。

### 什么是方法的返回值？返回值在类的方法里的作用是什么？

方法的返回值是指我们获取到的某个方法体中的代码执行后产生的结果！（前提是该方法可能产生结果）。返回值的作用:接收出结果，使得它可以用于其他的操作！

### 17、什么是构造函数 ？？？


**答：**
1）、构造函数必须和类名相同，并且不能有返回值（返回值也不能为void）
2）、每个类可以有多个构造函数，构造函数可以有多个参数。
3）、构造函数总是伴随new 操作一起调用，且不能直接调用，必须由系统调用。
4）、构造函数主要作用完成对象的初始化工作。
5）、构造函数不能被继承，因此，不能被覆盖，但是可以重载。

### 一个类的构造方法的作用是什么？若一个类没有声明构造方法，改程序能正确执行吗？为什么？

主要作用是完成对类对象的初始化工作。可以执行。因为一个类即使没有声明构造方法也会有默认的不带参数的构造方法。

### 构造方法有哪些特性？

1. 名字与类名相同；
2. 没有返回值，但不能用void声明构造函数；
3. 生成类的对象时自动执行，无需调用。

### 静态方法和实例方法有何不同？

1. 在外部调用静态方法时，可以使用"类名.方法名"的方式，也可以使用"对象名.方法名"的方式。而实例方法只有后面这种方式。也就是说，调用静态方法可以无需创建对象。
2. 静态方法在访问本类的成员时，只允许访问静态成员（即静态成员变量和静态方法），而不允许访问实例成员变量和实例方法；实例方法则无此限制.

### 对象的相等与指向他们的引用相等，两者有什么不同？

对象的相等 比的是内存中存放的内容是否相等而引用相等 比较的是他们指向的内存地址是否相等。

### 在调用子类构造方法之前会先调用父类没有参数的构造方法，其目的是？

帮助子类做初始化工作。

### 为什么 Java 不支持多重继承？

如果有两个类共同继承（extends）一个有特定方法的父类，那么该方法会被两个子类重写。然后，如果你决定同时继承这两个子类，那么在你调用该重写方法时，编译器不能识别你要调用哪个子类的方法。这也正是著名的菱形问题，见下图。

![](C:/Work/workspaces/xyzy/hexo/source/images/java/31-6.jpg)

ClassC 同时继承了 ClassA 和ClassB，ClassC 的对象在调用 ClassA 和 ClassB 中重载的方法时，就不知道该调用 ClassA 的方法，还是 ClassB 的方法。

### 为什么 Java 不是纯粹的面向对象编程语言？

之所以不能说 Java 是纯粹的面向对象编程语言，是因为 Java 支持基本数据类型，比如说 int、short、long、double 等，尽管它们有自己的包装器类型，但它们的确不能算是对象。

### path 和 classpath 之间有什么区别？

path 是操作系统用来查找可执行文件的环境变量，我的电脑上就定义了下图这些 path 变量，比如 Java 和 Maven 的。

![](C:/Work/workspaces/xyzy/hexo/source/images/java/31-7.jpg)

classpath 是针对 Java 而言的，用于指定 Java 虚拟机载入的字节码文件路径。



### `main` 方法可以重载吗

可以，一个类中可以有多个名称为“main”的方法：

```java
public class MainTest {
    public static void main(String[] args) {
        System.out.println("main(String[] args)");
    }
    public static void main(String[] args,String arg) {
        System.out.println("(String[] args,String arg");
    }
}
```

但该类在运行的时候，只会找到一个入口，即 public static void main(String[] args)。

### 一个 Java 源文件中有多个 public 类吗？

一个 Java 源文件中不能有多个 public 类。

![](C:/Work/workspaces/xyzy/hexo/source/images/java/31-9.jpg)

### 什么是 Java 的 package（包）？

在 Java 中，我们使用 package（包）对相关的类、接口和子包进行分组。这样做的好处有：

- 使相关类型更容易查找；
- 避免命名冲突，比如说 `com.itwanger.Hello` 和 `com.itwangsan.Hello` 不同；
- 通过包和访问权限控制符来限定类的可见性。

可以使用 package 关键字来定义一个包名，需要注意的是，这行代码必须处于一个类中的第一行。强烈建议在包中声明类，不要缺省，否则就失去了包结构的带来的好处。

包的命名应该遵守以下规则：

- 应该全部是小写字母；
- 可以包含多个单词，单词之间使用“.”连接，比如说 `java.lang`；
- 名称由公司名或者组织名确定，采用倒序的方式，比如说，我个人博客的域名是 www.itwanger.com，所以我创建的包名是就是 com.itwanger.xxxx。

每个包或者子包都在磁盘上有自己的目录结构，如果 Java 文件时在 `com.itwanger.xxxx` 包下，那么该文件所在的目录结构就应该是 `com->itwanger->xxxx`。

默认情况下，java.lang 包是默认导入的，我们不需要显式地导入该包下的任何类。

```java
package com.cmower.bb;
public class PackageTest {
    public static void main(String[] args) {
        Boolean.toString(true);
    }
}
```

Boolean类属于 java.lang 包，当使用它的时候并不需要显式导入。

### Java中final关键字的理解 ？？？

**答：**

final在Java中是一个保留的关键字，可以声明成员变量、方法、类以及本地变量。一旦你将引用声明作final，你将不能改变这个引用了，编译器会检查代码，如果你试图将变量再次初始化的话，编译器会报编译错误。

1）、final关键字可以用于成员变量、本地变量、方法以及类。

2）、final方法不能被重写。

3）、final类不能被继承。

4）、final关键字不同于finally关键字，后者用于异常处理5）、final关键字容易与finalize()方法搞混，后者是在Object类中定义的方法，是在垃圾回收之前被JVM调用的方法。

### 16、Java中public、private、protected关键字的理解 ？？？


**答：**
1）、public 表明该成员变量或者方法，对所有类或者对象都是可见的，所有类和对象都可以直接访问。
2）、private 表明该成员变量或者方法是私有的，只有当前类对其具有访问权限。
3）、protected 表明成员变量或者方法对该类自身，与它在同一个包中的其他类可见，在其他包中的该类的子类都可见。
4）、dafault 表明该成员变量或者方法只有自己和与其位于同一个包中的类可见，若父类和子类位于同一个包中，则具有访问权限，如父类和子类不在同一个包中，则没有访问权限。

### 什么是访问权限修饰符？

访问权限修饰符对于 Java 来说，非常重要，目前共有四种：public、private、protected和 default（缺省）。

一个类只能使用 public 或者 default 修饰，public 修饰的类你之前已经见到过了，现在我来定义一个缺省权限修饰符的类给你欣赏一下。

```java
class Dog {
    
}
```

哈哈，其实也没啥可以欣赏的。缺省意味着这个类可以被同一个包下的其他类进行访问；而 public 意味着这个类可以被所有包下的类进行访问。

假如硬要通过 private 和 protected 来修饰类的话，编译器会生气的，它不同意。

![](C:/Work/workspaces/xyzy/hexo/source/images/java/31-10.jpg)

private 可以用来修饰类的构造方法、字段和方法，只能被当前类进行访问。protected 也可以用来修饰类的构造方法、字段和方法，但它的权限范围更宽一些，可以被同一个包中的类进行访问，或者当前类的子类。

可以通过下面这张图来对比一下四个权限修饰符之间的差别：

![](C:/Work/workspaces/xyzy/hexo/source/images/java/31-11.jpg)

- 同一个类中，不管是哪种权限修饰符，都可以访问；
- 同一个包下，private 修饰的无法访问；
- 子类可以访问 public 和 protected 修饰的；
- public修饰符面向世界，哈哈，可以被所有的地方访问到。

### 什么是 final 关键字？

final 关键字修饰类的时候，表示该类无法被继承。比如，String 类就是 final 的，无法被继承。

final 关键字修饰方法的时候，表示子类无法覆盖它。

final 关键字修饰变量的时候，表示该变量只能被赋值一次，尽管变量的状态可以更改。

### 什么是 static 关键字？

static 关键字可以用来修饰类变量，使其具有全局性，即所有对象将共享同一个变量。

static 关键字可以用来修饰方法，该方法称为静态方法，只可以访问类的静态变量，并且只能调用类的静态方法。

### finally 和 finalize 有什么区别？

finally 通常与 try-catch 块一起使用，即使 try-catch 块引发了异常，finally 块中的代码也会被执行，用于释放 try 块中创建的资源。

finalize 是 Object 类的一个特殊方法，当对象正在被垃圾回收时，垃圾收集器将会调用该方法。可以重写该方法用于释放系统资源。

### 可以将一个类声明为 static 的吗？

不能将一个外部类声明为 static 的，但可以将一个内部类声明为 static 的——称为静态内部类。

### 什么是静态导入？

如果必须在一个类中使用其他类的静态变量或者静态方法，通常我们需要先导入该类，然后使用“类名.变量/方法”的形式调用。

```java
import java.lang.Math;
double test = Math.PI * 5;
```

也可以通过静态导入的方式，就不需要再使用类名了。

```java
import static java.lang.Math.PI;
double test = PI * 5;
```

不过，静态导入容易引发混乱（变量名或者方法名容易冲突），因此最好避免使用静态导入。

### 什么是 try-with-resources？

try-with-resources 是 Java 7 时引入的一个自动资源管理语句，在此之前，我们必须通过 try-catch-finally 的方式手动关闭资源，当我们忘记关闭资源的时候，就容易导致内存泄漏。

### 什么是 multi-catch？

Java 7 改进的另外一个地方就是 multi-catch，可以在单个 catch 中捕获多个异常，当一个 try 块抛出多个类似的异常时，这种写法更短，更清晰。

```java
catch(IOException | SQLException ex){
    logger.error(ex);
    throw new MyException(ex.getMessage);
}
```

当有多个异常的时候，可以使用管道表示符“|”隔开。

### 什么是 static 块？

static 块是由 Java ClassLoader 将类加载到内存中时执行的代码块。通常用于初始化类的静态变量或者创建静态资源。

### java中Static关键字有哪些特点？？？


**1)、static成员变量**
静态变量：属于类，内存中只有一个复制，所有实例都指向同一个内存地址，只要类被加载，静态变量就会本分配空间，调用方式有两种。类.静态变量 和 对象.静态变量
实例变量：属于对象，只有对象被创建，实例对象才会被分配空间，调用方式：对象.实例变量


**2)、static成员方法**
静态方法：属于类，不需要创建对象，就可以被调用。调用方式：类.静态方法 和 对象.静态方法
非静态方法：属于对象，只能在对象被创建出来之后才可以被使用。
注意：static方法中，不能使用this和super关键字，不能调用非static方法，只能访问所属类的静态成员变量和静态成员方法。

# 7、java中length属性与length()方法有什么区别？？？


**答：**

length属性属于数组，用来获取数组的长度；而length()方法属于String 用来计算字符串长度。

### **17）Java 中应该使用什么数据类型来代表价格？**

如果不是特别关心内存和性能的话，使用BigDecimal，否则使用预定义精度的 double 类型。

### **18）怎么将 byte 转换为 String？**

可以使用 String 接收 byte[] 参数的构造器来进行转换，需要注意的点是要使用的正确的编码，否则会使用平台默认编码，这个编码可能跟原来的编码相同，也可能不同。

### **19）Java 中怎样将 bytes 转换为 long 类型？**

这个问题你来回答 :-)

### **20）我们能将 int 强制转换为 byte 类型的变量吗？如果该值大于 byte 类型的范围，将会出现什么现象？**

是的，我们可以做强制转换，但是 Java 中 int 是 32 位的，而 byte 是 8 位的，所以，如果强制转化是，int 类型的高 24 位将会被丢弃，byte 类型的范围是从 -128 到 128。

### **21）存在两个类，B 继承 A，C 继承 B，我们能将 B 转换为 C 么？如 C = (C) B；**

### **22）哪个类包含 clone 方法？是 Cloneable 还是 Object？**

java.lang.Cloneable 是一个标示性接口，不包含任何方法，clone 方法在 object 类中定义。并且需要知道 clone() 方法是一个本地方法，这意味着它是由 c 或 c++ 或 其他本地语言实现的。

### **23）Java 中 ++ 操作符是线程安全的吗？**

不是线程安全的操作。它涉及到多个指令，如读取变量值，增加，然后存储回内存，这个过程可能会出现多个线程交差。

### **24）a = a + b 与 a += b 的区别**

+= 隐式的将加操作的结果类型强制转换为持有结果的类型。如果两这个整型相加，如 byte、short 或者 int，首先会将它们提升到 int 类型，然后在执行加法操作。如果加法操作的结果比 a 的最大值要大，则 a+b 会出现编译错误，但是 a += b 没问题，如下：

```
byte a = 127;
byte b = 127;
b = a + b; // error : cannot convert from int to byte
b += a; // ok
```

（译者注：这个地方应该表述的有误，其实无论 a+b 的值为多少，编译器都会报错，因为 a+b 操作会将 a、b 提升为 int 类型，所以将 int 类型赋值给 byte 就会编译出错）

### **25）我能在不进行强制转换的情况下将一个 double 值赋值给 long 类型的变量吗？**

不行，你不能在没有强制类型转换的前提下将一个 double 值赋值给 long 类型的变量，因为 double 类型的范围比 long 类型更广，所以必须要进行强制转换。

### **26）3\*0.1 == 0.3 将会返回什么？true 还是 false？**

false，因为有些浮点数不能完全精确的表示出来。

### **27）int 和 Integer 哪个会占用更多的内存？**

Integer 对象会占用更多的内存。Integer 是一个对象，需要存储对象的元数据。但是 int 是一个原始类型的数据，所以占用的空间更少。

### **28）为什么 Java 中的 String 是不可变的（Immutable）？**

Java 中的 String 不可变是因为 Java 的设计者认为字符串使用非常频繁，将字符串设置为不可变可以允许多个客户端之间共享相同的字符串。更详细的内容参见答案。

### **29）我们能在 Switch 中使用 String 吗？**

从 Java 7 开始，我们可以在 switch case 中使用字符串，但这仅仅是一个语法糖。内部实现在 switch 中使用字符串的 hash code。

### **30）Java 中的构造器链是什么？**

当你从一个构造器中调用另一个构造器，就是Java 中的构造器链。这种情况只在重载了类的构造器的时候才会出现。

JVM 底层 与 GC（Garbage Collection） 的面试问题

### **31）64 位 JVM 中，int 的长度是多数？**

Java 中，int 类型变量的长度是一个固定值，与平台无关，都是 32 位。意思就是说，在 32 位 和 64 位 的Java 虚拟机中，int 类型的长度是相同的。

### **32）Serial 与 Parallel GC之间的不同之处？**

Serial 与 Parallel 在GC执行的时候都会引起 stop-the-world。它们之间主要不同 serial 收集器是默认的复制收集器，执行 GC 的时候只有一个线程，而 parallel 收集器使用多个 GC 线程来执行。

### **33）32 位和 64 位的 JVM，int 类型变量的长度是多数？**

32 位和 64 位的 JVM 中，int 类型变量的长度是相同的，都是 32 位或者 4 个字节。

### **34）Java 中 WeakReference 与 SoftReference的区别？**

虽然 WeakReference 与 SoftReference 都有利于提高 GC 和 内存的效率，但是 WeakReference ，一旦失去最后一个强引用，就会被 GC 回收，而软引用虽然不能阻止被回收，但是可以延迟到 JVM 内存不足的时候。

### **35）WeakHashMap 是怎么工作的？**

WeakHashMap 的工作与正常的 HashMap 类似，但是使用弱引用作为 key，意思就是当 key 对象没有任何引用时，key/value 将会被回收。

### **36）JVM 选项 -XX:+UseCompressedOops 有什么作用？为什么要使用？**

当你将你的应用从 32 位的 JVM 迁移到 64 位的 JVM 时，由于对象的指针从 32 位增加到了 64 位，因此堆内存会突然增加，差不多要翻倍。这也会对 CPU 缓存（容量比内存小很多）的数据产生不利的影响。因为，迁移到 64 位的 JVM 主要动机在于可以指定最大堆大小，通过压缩 OOP 可以节省一定的内存。通过 -XX:+UseCompressedOops 选项，JVM 会使用 32 位的 OOP，而不是 64 位的 OOP。

### **37）怎样通过 Java 程序来判断 JVM 是 32 位 还是 64 位？**

你可以检查某些系统属性如 sun.arch.data.model 或 os.arch 来获取该信息。

### **38）32 位 JVM 和 64 位 JVM 的最大堆内存分别是多数？**

理论上说上 32 位的 JVM 堆内存可以到达 2^32，即 4GB，但实际上会比这个小很多。不同操作系统之间不同，如 Windows 系统大约 1.5 GB，Solaris 大约 3GB。64 位 JVM允许指定最大的堆内存，理论上可以达到 2^64，这是一个非常大的数字，实际上你可以指定堆内存大小到 100GB。甚至有的 JVM，如 Azul，堆内存到 1000G 都是可能的。

### **“a==b”和”a.equals(b)”有什么区别？**

如果 a 和 b 都是对象，则 a==b 是比较两个对象的引用，只有当 a 和 b 指向的是堆中的同一个对象才会返回 true，而 a.equals(b) 是进行逻辑比较，所以通常需要重写该方法来提供逻辑一致性的比较。例如，String 类重写 equals() 方法，所以可以用于两个不同对象，但是包含的字母相同的比较。

### **45）a.hashCode() 有什么用？与 a.equals(b) 有什么关系？**

hashCode() 方法是相应对象整型的 hash 值。它常用于基于 hash 的集合类，如 Hashtable、HashMap、LinkedHashMap等等。它与 equals() 方法关系特别紧密。根据 Java 规范，两个使用 equal() 方法来判断相等的对象，必须具有相同的 hash code。

### 12、HashCode（）与equals的关系？？？


答：
1)、hashcode是object类的一个方法，返回值是该对象的哈希码值，同一个对象的哈希码值一定相等，但是不同的对象的哈希码值也是有可能相等的。


2)、equals同样是object类的一个方法，比较两个对象是否是同一个对象，其内部实现是通过==来比较两个对象的内存地址是否相等的，如果需要比较两个对象的内容是否相等，则需要重写equals方法，重写的equals方法用于比较对象的内容是否相等。

3)、因此如果两个对象根据equals()方法比较相等，那么这两个对象的hashcode()返回值一定相等，如果两个对象的hashcode()返回值相等，其equals()比较结果也不一定是true。

### **46）final、finalize 和 finally 的不同之处？**

final 是一个修饰符，可以修饰变量、方法和类。如果 final 修饰变量，意味着该变量的值在初始化后不能被改变。finalize 方法是在对象被回收之前调用的方法，给对象自己最后一个复活的机会，但是什么时候调用 finalize 没有保证。finally 是一个关键字，与 try 和 catch 一起用于异常的处理。finally 块一定会被执行，无论在 try 块中是否有发生异常。

### **47）Java 中的编译期常量是什么？使用它又什么风险？**

公共静态不可变（public static final ）变量也就是我们所说的编译期常量，这里的 public 可选的。实际上这些变量在编译时会被替换掉，因为编译器知道这些变量的值，并且知道这些变量在运行时不能改变。这种方式存在的一个问题是你使用了一个内部的或第三方库中的公有编译时常量，但是这个值后面被其他人改变了，但是你的客户端仍然在使用老的值，甚至你已经部署了一个新的jar。为了避免这种情况，当你在更新依赖 JAR 文件时，确保重新编译你的程序。

### String类通过new创建和直接赋值字符串的区别？？？

**答：**

方式一：String a = “aaa” ;方式二：String b = new String(“aaa”);

- 两种方式都能创建字符串对象，但方式一要比方式二更优。
- 因为字符串是保存在常量池中的，而通过new创建的对象会存放在堆内存中。

**一：常量池中已经有字符串常量”aaa”**

- 通过方式一创建对象，程序运行时会在常量池中查找”aaa”字符串，将找到的”aaa”字符串的地址赋给a。
- 通过方式二创建对象，无论常量池中有没有”aaa”字符串，程序都会在堆内存中开辟一片新空间存放新对象。

**二：常量池中没有字符串常量”aaa”**

- 通过方式一创建对象，程序运行时会将”aaa”字符串放进常量池，再将其地址赋给a。
- 通过方式二创建对象，程序会在堆内存中开辟一片新空间存放新对象，同时会将”aaa”字符串放入常量池，相当于创建了两个对象。

### 14、Java中Int与integer用==比较详解？？？

**答：**

①、无论如何，Integer与new Integer不会相等。不会经历拆箱过程，因为它们存放内存的位置不一样。（要看具体位置，可以看看这篇文章：点击打开链接）

②、两个都是非new出来的Integer，如果数在-128到127之间，则是true,否则为false。

③、两个都是new出来的,则为false。

④、int和integer(new或非new)比较，都为true，因为会把Integer自动拆箱为int，其实就是相当于两个int类型比较。

### **JDK 和 JRE 有什么区别？**

- JDK：Java Development Kit 的简称，java 开发工具包，提供了 java 的开发环境和运行环境。
- JRE：Java Runtime Environment 的简称，java 运行环境，为 java 的运行提供了所需环境。

具体来说 JDK 其实包含了 JRE，同时还包含了编译 java 源码的编译器 javac，还包含了很多 java 程序调试和分析的工具。简单来说：如果你需要运行 java 程序，只需安装 JRE 就可以了，如果你需要编写 java 程序，需要安装 JDK。

### **2. == 和 equals 的区别是什么？**

**== 解读**

对于基本类型和引用类型 == 的作用效果是不同的，如下所示：

- 基本类型：比较的是值是否相同；
- 引用类型：比较的是引用是否相同；

代码示例：

```
String x = "string";
String y = "string";
String z = new String("string");
System.out.println(x==y); // true
System.out.println(x==z); // false
System.out.println(x.equals(y)); // true
System.out.println(x.equals(z)); // true
```

代码解读：因为 x 和 y 指向的是同一个引用，所以 == 也是 true，而 new String()方法则重写开辟了内存空间，所以 == 结果为 false，而 equals 比较的一直是值，所以结果都为 true。

**equals 解读**

equals 本质上就是 ==，只不过 String 和 Integer 等重写了 equals 方法，把它变成了值比较。看下面的代码就明白了。

首先来看默认情况下 equals 比较一个有相同值的对象，代码如下：

```
class Cat {
    public Cat(String name) {
        this.name = name;
    }
 
    private String name;
 
    public String getName() {
        return name;
    }
 
    public void setName(String name) {
        this.name = name;
    }
}
 
Cat c1 = new Cat("王磊");
Cat c2 = new Cat("王磊");
System.out.println(c1.equals(c2)); // false
```

输出结果出乎我们的意料，竟然是 false？这是怎么回事，看了 equals 源码就知道了，源码如下：

```
public boolean equals(Object obj) {
    return (this == obj);
}
```

原来 equals 本质上就是 ==。

那问题来了，两个相同值的 String 对象，为什么返回的是 true？代码如下：

```
String s1 = new String("老王");
String s2 = new String("老王");
System.out.println(s1.equals(s2)); // true
```

同样的，当我们进入 String 的 equals 方法，找到了答案，代码如下：

```

```

原来是 String 重写了 Object 的 equals 方法，把引用比较改成了值比较。

总结 ：== 对于基本类型来说是值比较，对于引用类型来说是比较的是引用；而 equals 默认情况下是引用比较，只是很多类重新了 equals 方法，比如 String、Integer 等把它变成了值比较，所以一般情况下 equals 比较的是值是否相等。

### **3. 两个对象的 hashCode()相同，则 equals()也一定为 true，对吗？**

不对，两个对象的 hashCode()相同，equals()不一定 true。

代码示例：

```
String str1 = "通话";
String str2 = "重地";
System.out.println(String.format("str1：%d | str2：%d",  str1.hashCode(),str2.hashCode()));
System.out.println(str1.equals(str2));
```

执行的结果：

```

```

代码解读：很显然“通话”和“重地”的 hashCode() 相同，然而 equals() 则为 false，因为在散列表中，hashCode()相等即两个键值对的哈希值相等，然而哈希值相等，并不一定能得出键值对相等。

### **4. final 在 java 中有什么作用？**

final 修饰的类叫最终类，该类不能被继承。

final 修饰的方法不能被重写。

final 修饰的变量叫常量，常量必须初始化，初始化之后值就不能被修改。

### **5. java 中的 Math.round(-1.5) 等于多少？**

等于 -1，因为在数轴上取值时，中间值（0.5）向右取整，所以正 0.5 是往上取整，负 0.5 是直接舍弃。

### **6. String 属于基础的数据类型吗？**

String 不属于基础类型，基础类型有 8 种：byte、boolean、char、short、int、float、long、double，而 String 属于对象。

### **7. java 中操作字符串都有哪些类？它们之间有什么区别？**

操作字符串的类有：String、StringBuffer、StringBuilder。

String 和 StringBuffer、StringBuilder 的区别在于 String 声明的是不可变的对象，每次操作都会生成新的 String 对象，然后将指针指向新的 String 对象，而 StringBuffer、StringBuilder 可以在原有对象的基础上进行操作，所以在经常改变字符串内容的情况下最好不要使用 String。

StringBuffer 和 StringBuilder 最大的区别在于，StringBuffer 是线程安全的，而 StringBuilder 是非线程安全的，但 StringBuilder 的性能却高于 StringBuffer，所以在单线程环境下推荐使用 StringBuilder，多线程环境下推荐使用 StringBuffer。

### **8. String str="i"与 String str=new String("i")一样吗？**

不一样，因为内存的分配方式不一样。String str="i"的方式，java 虚拟机会将其分配到常量池中；而 String str=new String("i") 则会被分到堆内存中。

### **9. 如何将字符串反转？**

使用 StringBuilder 或者 stringBuffer 的 reverse() 方法。

```
// StringBuffer reverse
StringBuffer stringBuffer = new StringBuffer();
stringBuffer.append("abcdefg");
System.out.println(stringBuffer.reverse()); // gfedcba
// StringBuilder reverse
StringBuilder stringBuilder = new StringBuilder();
stringBuilder.append("abcdefg");
System.out.println(stringBuilder.reverse()); // gfedcba
```

### **10. String 类的常用方法都有那些？**

- indexOf()：返回指定字符的索引。
- charAt()：返回指定索引处的字符。
- replace()：字符串替换。
- trim()：去除字符串两端空白。
- split()：分割字符串，返回一个分割后的字符串数组。
- getBytes()：返回字符串的 byte 类型数组。
- length()：返回字符串长度。
- toLowerCase()：将字符串转成小写字母。
- toUpperCase()：将字符串转成大写字符。
- substring()：截取字符串。
- equals()：字符串比较。

###  **为什么要使用克隆？**

想对一个对象进行处理，又想保留原有的数据进行接下来的操作，就需要克隆了，Java语言中克隆针对的是类的实例。

### **62. 如何实现对象克隆？**

有两种方式：

1). 实现Cloneable接口并重写Object类中的clone()方法；

2). 实现Serializable接口，通过对象的序列化和反序列化实现克隆，可以实现真正的深度克隆，代码如下：

```
import java.io.ByteArrayInputStream;

import java.io.ByteArrayOutputStream;

import java.io.ObjectInputStream;

import java.io.ObjectOutputStream;

import java.io.Serializable;

 

public class MyUtil {

 

    private MyUtil() {

        throw new AssertionError();

    }

 

    @SuppressWarnings("unchecked")

    public static <T extends Serializable> T clone(T obj) throws Exception {

        ByteArrayOutputStream bout = new ByteArrayOutputStream();

        ObjectOutputStream oos = new ObjectOutputStream(bout);

        oos.writeObject(obj);

 

        ByteArrayInputStream bin = new ByteArrayInputStream(bout.toByteArray());

        ObjectInputStream ois = new ObjectInputStream(bin);

        return (T) ois.readObject();

 

        // 说明：调用ByteArrayInputStream或ByteArrayOutputStream对象的close方法没有任何意义

        // 这两个基于内存的流只要垃圾回收器清理对象就能够释放资源，这一点不同于对外部资源（如文件流）的释放

    }

}
```

下面是测试代码：



```
import java.io.Serializable;

 

/**

 * 人类

 * @author nnngu

 *

 */

class Person implements Serializable {

    private static final long serialVersionUID = -9102017020286042305L;

 

    private String name;    // 姓名

    private int age;        // 年龄

    private Car car;        // 座驾

 

    public Person(String name, int age, Car car) {

        this.name = name;

        this.age = age;

        this.car = car;

    }

 

    public String getName() {

        return name;

    }

 

    public void setName(String name) {

        this.name = name;

    }

 

    public int getAge() {

        return age;

    }

 

    public void setAge(int age) {

        this.age = age;

    }

 

    public Car getCar() {

        return car;

    }

 

    public void setCar(Car car) {

        this.car = car;

    }

 

    @Override

    public String toString() {

        return "Person [name=" + name + ", age=" + age + ", car=" + car + "]";

    }

}
```



```
/**

 * 小汽车类

 * @author nnngu

 *

 */

class Car implements Serializable {

    private static final long serialVersionUID = -5713945027627603702L;

 

    private String brand;       // 品牌

    private int maxSpeed;       // 最高时速

 

    public Car(String brand, int maxSpeed) {

        this.brand = brand;

        this.maxSpeed = maxSpeed;

    }

 

    public String getBrand() {

        return brand;

    }

 

    public void setBrand(String brand) {

        this.brand = brand;

    }

 

    public int getMaxSpeed() {

        return maxSpeed;

    }

 

    public void setMaxSpeed(int maxSpeed) {

        this.maxSpeed = maxSpeed;

    }

 

    @Override

    public String toString() {

        return "Car [brand=" + brand + ", maxSpeed=" + maxSpeed + "]";

    }
}
class CloneTest {

 

    public static void main(String[] args) {

        try {

            Person p1 = new Person("郭靖", 33, new Car("Benz", 300));

            Person p2 = MyUtil.clone(p1);   // 深度克隆

            p2.getCar().setBrand("BYD");

            // 修改克隆的Person对象p2关联的汽车对象的品牌属性

            // 原来的Person对象p1关联的汽车不会受到任何影响

            // 因为在克隆Person对象时其关联的汽车对象也被克隆了

            System.out.println(p1);

        } catch (Exception e) {

            e.printStackTrace();

        }

    }

}
```

注意：基于序列化和反序列化实现的克隆不仅仅是深度克隆，更重要的是通过泛型限定，可以检查出要克隆的对象是否支持序列化，这项检查是编译器完成的，不是在运行时抛出异常，这种是方案明显优于使用Object类的clone方法克隆对象。让问题在编译的时候暴露出来总是好过把问题留到运行时。

### **63. 深拷贝和浅拷贝区别是什么？**

浅拷贝只是复制了对象的引用地址，两个对象指向同一个内存地址，所以修改其中任意的值，另一个值都会随之变化，这就是浅拷贝（例：assign()）

深拷贝是将对象及值复制过来，两个对象修改其中任意的值另一个值不会改变，这就是深拷贝（例：JSON.parse()和JSON.stringify()，但是此方法无法复制函数类型）

### 请说出 Java 14 版本中更新的重要功能。

Java 14 发布于 2020 年 3 月 17 日，更新的重要功能有：

- switch表达式；
- instanceof增强表达式，预览功能；
- 文本块，第二次预览；
- Records，预览功能。

### 请说出 Java 13 版本中更新的重要功能。

Java 13 发布于 2019 年 9 月 17 日，更新的重要功能有：

- 文本块，预览功能；
- switch表达式，预览功能；
- JavaSocket 重新实现；
- FileSystems.newFileSystem 方法；
- 支持Unicode 12.1；
- 可伸缩、低延迟的垃圾收集器改进，用于返回未使用的内存。

### 请说出 Java 12 版本中更新的重要功能。

Java 12 发布于 2019 年 3 月 19 日，更新的重要功能有：

- JVM 更新；
- File.mismatch 方法；
- 紧凑型数字格式；
- String类新增了一些方法，比如说 indent。

### 请说出 Java 11 版本中更新的重要功能。

Java 11 是继 Java 8 之后的第二个商用版本，如果你下载的是 Oracle JDK，则需要进行付费；如果想继续使用免费版本，需要下载 OpenJDK。

![](C:/Work/workspaces/xyzy/hexo/source/images/java/31-1.jpg)

Oracle JDK 中会有一些 Open JDK 没有的、商用闭源的功能。

Java 11 更新的重要功能有：

- 可以直接使用 java 命令运行 Java 程序，源代码将会隐式编译和运行。
- String类新增了一些方法，比如说 isBlank、lines、strip 等等；
- Files类新增了两个读写方法，readString 和 writeString；
- 可以在 Lambda 表达式中使用 var 作为变量类型。

### 请说出 Java 10 版本中更新的重要功能。

Java 10 更新的重要功能有：

- 局部变量类型推断，举个例子，var list = newArrayList;，可以使用 var 来作为变量类型，Java 编译器知道 list 的类型为字符串的 ArrayList；
- 增强 java.util.Locale；
- 提供了一组默认的根证书颁发机构（CA）。

### 请说出 Java 9 版本中更新的重要功能。

Java 9 更新的重要功能有：

- 模块系统；
- 不可变的 List、Set、Map 的工厂方法；
- 接口中可以有私有方法；
- 垃圾收集器改进。

### 请说出 Java 8 版本中更新的重要功能。

Java 8 发布于 2014 年 3 月份，可以说是 Java 6 之后最重要的版本更新，深受开发者的喜爱。

- 函数式编程和 Lambda 表达式；
- Stream 流；
- JavaDate Time API；
- 接口中可以使用默认方法和静态方法。

## 2.面向对象

### 面向对象vs面向过程

**面向过程**

**优点：** 性能比面向对象高，因为类调用时需要实例化，开销比较大，比较消耗资源;比如单片机、嵌入式开发、Linux/Unix等一般采用面向过程开发，性能是最重要的因素。

**缺点：** 没有面向对象易维护、易复用、易扩展

**面向对象**

**优点：** 易维护、易复用、易扩展，由于面向对象有封装、继承、多态性的特性，可以设计出低耦合的系统，使系统更加灵活、更加易于维护

**缺点：** 性能比面向过程低

### 封装、继承、多态概念

**封装**

封装把一个对象的属性私有化，同时提供一些可以被外界访问的属性的方法，如果不想被外界方法，我们大可不必提供方法给外界访问。但是如果一个类没有提供给外界访问的方法，那么这个类也没有什么意义了。

**继承**

继承是使用已存在的类的定义作为基础建立新类的技术，新类的定义可以增加新的数据或新的功能，也可以用父类的功能，但不能选择性地继承父类。通过使用继承我们能够非常方便地复用以前的代码。

**关于继承如下3点请记住：**

1. 子类拥有父类非private的属性和方法。
2. 子类可以拥有自己属性和方法，即子类可以对父类进行扩展。
3. 子类可以用自己的方式实现父类的方法。（以后介绍）。

**多态**

所谓多态就是指程序中定义的引用变量所指向的具体类型和通过该引用变量发出的方法调用在编程时并不确定，而是在程序运行期间才确定，即一个引用变量倒底会指向哪个类的实例对象，该引用变量发出的方法调用到底是哪个类中实现的方法，必须在由程序运行期间才能决定。

在Java中有两种形式可以实现多态：继承（多个子类对同一方法的重写）和接口（实现接口并覆盖接口中同一方法）。

### 重载(overload)  vs 重写(override)

**重载：** 发生在同一个类中，方法名必须相同，参数类型不同、个数不同、顺序不同，方法返回值和访问修饰符可以不同，发生在编译时。 　　

**重写：** 发生在父子类中，方法名、参数列表必须相同，返回值范围小于等于父类，抛出的异常范围小于等于父类，访问修饰符范围大于等于父类；如果父类方法访问修饰符为private则子类就不能重写该方法。

### 重写（Override）和重载（Overload）区别？

先来看一段重写的代码吧。

```java
class LaoWang{
    public void write {
        System.out.println("老王写了一本《基督山伯爵》");
    }
}
public class XiaoWang extends LaoWang {
    @Override
    public void write {
        System.out.println("小王写了一本《茶花女》");
    }
}
```

重写的两个方法名相同，方法参数的个数也相同；不过一个方法在父类中，另外一个在子类中。就好像父类 LaoWang 有一个 write 方法（无参），方法体是写一本《基督山伯爵》；子类 XiaoWang 重写了父类的 write 方法（无参），但方法体是写一本《茶花女》。

来写一段测试代码。

```java
public class OverridingTest {
    public static void main(String[] args) {
        LaoWang wang = new XiaoWang;wang.write;
    }
}
```

大家猜结果是什么？

```powershell
小王写了一本《茶花女》
```

在上面的代码中，们声明了一个类型为 LaoWang 的变量 wang。在编译期间，编译器会检查 LaoWang 类是否包含了 write 方法，发现 LaoWang 类有，于是编译通过。在运行期间，new 了一个 XiaoWang 对象，并将其赋值给 wang，此时 Java 虚拟机知道 wang 引用的是 XiaoWang 对象，所以调用的是子类 XiaoWang 中的 write 方法而不是父类 LaoWang 中的 write 方法，因此输出结果为“小王写了一本《茶花女》”。

再来看一段重载的代码吧。

```java
class LaoWang{
    public void read {
        System.out.println("老王读了一本《Web全栈开发进阶之路》");
    }
    public void read(String bookname) {
        System.out.println("老王读了一本《" + bookname + "》");
    }
}
```

重载的两个方法名相同，但方法参数的个数不同，另外也不涉及到继承，两个方法在同一个类中。就好像类 LaoWang 有两个方法，名字都是 read，但一个有参数（书名），另外一个没有（只能读写死的一本书）。

来写一段测试代码。

```java
public class OverloadingTest {
    public static void main(String[] args) {
        LaoWang wang = new LaoWang;wang.read;wang.read("金瓶梅");
    }
}
```

这结果就不用猜了。变量 wang 的类型为 LaoWang，wang.read 调用的是无参的read 方法，因此先输出“老王读了一本《Web全栈开发进阶之路》”；wang.read("金瓶") 调用的是有参的 read(bookname) 方法，因此后输出“老王读了一本《金瓶》”。在编译期间，编译器就知道这两个 read 方法时不同的，因为它们的方法签名（=方法名称+方法参数）不同。

简单的来总结一下：

1）编译器无法决定调用哪个重写的方法，因为只从变量的类型上是无法做出判断的，要在运行时才能决定；但编译器可以明确地知道该调用哪个重载的方法，因为引用类型是确定的，参数个数决定了该调用哪个方法。

2）多态针对的是重写，而不是重载。

![](C:/Work/workspaces/xyzy/hexo/source/images/java/31-8.jpg)

- 如果在一个类中有多个相同名字的方法，但参数不同，则称为方法重载。

- 父类中有一个方法，子类中有另外一个和它有相同签名（方法名相同，参数相同、修饰符相同）的方法时，则称为方法重写。子类在重写父类方法的时候可以加一个@Override 注解。

### java中重载（overload）、重写（override）的区别？？？


**答：**

**1）**重载是通过不同的方法参数来区分的，例如不同的参数个数、不同的参数类型、或者不同的参数顺序。不能通过方法的访问权限、返回值类型、和抛出异常类型类进行重载。

**2）**覆盖是指子类函数覆盖父类函数，覆盖一个方法，并对其重写。重写需要注意，子类必须与父类中，被重写的方法有相同的函数名、相同的参数、相同的返回值、以及抛出异常也必须保持一致。

### 说出几条 Java 中方法重载的最佳实践？**

下面有几条可以遵循的方法重载的最佳实践来避免造成自动装箱的混乱。

a）不要重载这样的方法：一个方法接收 int 参数，而另个方法接收 Integer 参数。

b）不要重载参数数量一致，而只是参数顺序不同的方法。

c）如果重载的方法参数个数多于 5 个，采用可变参数。

### 构造器Constructor是否可被override

在讲继承的时候我们就知道父类的私有属性和构造方法并不能被继承，所以Constructor也就不能被override,但是可以overload,所以你可以看到一个类中有多个构造函数的情况。

### 什么是接口？

接口是 Java 编程语言中的一个核心概念，不仅在 JDK 源码中使用很多，还在 Java 设计模式、框架和工具中使用很多。接口提供了一种在 Java 中实现抽象的方法，用于定义子类的行为约定。

### 接口和抽象类的区别是什么？

1. 接口的方法默认是public，所有方法在接口中不能有实现，抽象类可以有非抽象的方法
2. 接口中的实例变量默认是final类型的，而抽象类中则不一定
3. 一个类可以实现多个接口，但最多只能实现一个抽象类
4. 一个类实现接口的话要实现接口的所有方法，而抽象类不一定
5. 接口不能用new实例化，但可以声明，但是必须引用一个实现该接口的对象 从设计层面来说，抽象是对类的抽象，是一种模板设计，接口是行为的抽象，是一种行为的规范。

###  接口和抽象类的区别是什么？

Java提供和支持创建抽象类和接口。它们的实现有共同点，不同点在于：

接口中所有的方法隐含的都是抽象的。而抽象类则可以同时包含抽象和非抽象的方法。

类可以实现很多个接口，但是只能继承一个抽象类

类可以不实现抽象类和接口声明的所有方法，当然，在这种情况下，类也必须得声明成是抽象的。

抽象类可以在不提供接口方法实现的情况下实现接口。

Java接口中声明的变量默认都是final的。抽象类可以包含非final的变量。

Java接口中的成员函数默认是public的。抽象类的成员函数可以是private，protected或者是public。

接口是绝对抽象的，不可以被实例化，抽象类也不可以被实例化。

也可以参考JDK8中抽象类和接口的区别

### java中接口和抽象类的区别？？？


**答：**

**1）**、抽象类和接口都不能直接实例化
**2）**、抽象类要被子类继承（extends），接口要被类实现（implements）
**3）**、接口只能做方法的声明，且所有方法访问权限必须是public，抽象类中可以做方法声明，也可以做方法的实现。
**4）**、接口中定义的变量只能是公共的静态
常量，抽象类中的变量可以是普通变量。
**5）**、抽象类里的抽象方法必须全部被子类所实现，如果子类不能全部实现父类的抽象方法，那么该子类只能是抽象类。同理如果在实现接口的时候，如果不能实现接口方法，那么该类也只能为抽象类。
**6）**、抽象方法只能声明，不能实现，接口是设计的结果，抽象类是重构的结果。
**7）**、抽象类里可以没有抽象方法。
**8）**、一个类里有抽象方法，那么这个类只能是抽象类。
**9）**、抽象方法需要被实现，因此不能是私有的，也不能是静态的。
**10）**、接口可以继承接口，并可多继承接口，但类只能单根继承。

### 10.什么是值传递和引用传递？

值传递是对基本型变量而言的,传递的是该变量的一个副本,改变副本不影响原变量.

引用传递一般是对于对象型变量而言的,传递的是该对象地址的一个副本, 并不是原对象本身 。

一般认为,java内的基础类型数据传递都是值传递. java中实例对象的传递是引用传递

### java中this和super的区别？？？


**答：**

**1)、this三大作用**
1、普通的直接引用（指向当前对象的指针）
2、形参与成员名字重名（用this区分）
3、引用构造函数


**2)、super三大作用**
1、普通的直接引用（指向当前对象的父类）
2、子类中的成员变量或者方法和父类成员变量和方法重名。
3、引用构造函数


super（参数）：调用基类中的某一个构造函数（应该为构造函数中的第一条语句）


this（参数）：调用本类中另一种形成的构造函数（应该为构造函数中的第一条语句）


super:　它引用当前对象的直接父类中的成员（用来访问直接父类中被隐藏的父类中成员数据或函数，基类与派生类中有相同成员定义时如：super.变量名 super.成员函数据名（实参）


this：它代表当前对象名（在程序中易产生二义性之处，应使用this来指明当前对象；如果函数的形参与类中的成员数据同名，这时需用this来指明成员变量名）


调用super()必须写在子类构造方法的第一行，否则编译不通过。每个子类构造方法的第一条语句，都是隐含地调用super()，如果父类没有这种形式的构造函数，那么在编译的时候就会报错。


super()和this()类似,区别是，super()从子类中调用父类的构造方法，this()在同一类内调用其它方法。
super()和this()均需放在构造方法内第一行。尽管可以用this调用一个构造器，但却不能调用两个。


this和super不能同时出现在一个构造函数里面，因为this必然会调用其它的构造函数，其它的构造函数必然也会有super语句的存在，所以在同一个构造函数里面有相同的语句，就失去了语句的意义，编译器也不会通过。


this()和super()都指的是对象，所以，均不可以在static环境中使用。包括：static变量,static方法，static语句块。
从本质上讲，this是一个指向本对象的指针, 然而super是一个Java关键字。

### Java支持多继承么？

Java中类不支持多继承，只支持单继承（即一个类只有一个父类）。 但是java中的接口支持多继承，，即一个子接口可以有多个父接口。（接口的作用是用来扩展对象的功能，一个子接口继承多个父接口，说明子接口扩展了多个功能，当类实现接口时，类就扩展了相应的功能）。

### 多态的实现机制是什么 ？？？


**答：**

**多态主要有一下两种表现形式。**
1）、方法的重载（overload）。重载是指同一个类中有多个同名的方法，但是这些方法具有着不同的参数，重载可以被看做一个类中方法的多态性。
2）、方法的覆盖（overide）。子类可以覆盖父类的方法，因此同样的方法会在父类和子类中有着不同的表现形式。这种形式，因为只有在调用时才能确定调用的是哪个方法，因此被称为运行时多态。

**抽象类必须要有抽象方法吗？**

不需要，抽象类不一定非要有抽象方法。

```
abstract class Cat {
    public static void sayHi() {
        System.out.println("hi~");
    }
}
```

上面代码，抽象类并没有抽象方法但完全可以正常运行。

### **12. 普通类和抽象类有哪些区别？**

普通类不能包含抽象方法，抽象类可以包含抽象方法。

抽象类不能直接实例化，普通类可以直接实例化。

### **13. 抽象类能使用 final 修饰吗？**

不能，定义抽象类就是让其他类继承的，如果定义为 final 该类就不能被继承，这样彼此就会产生矛盾，所以 final 不能修饰抽象类，如下图所示，编辑器也会提示错误信息：





### **14. 接口和抽象类有什么区别？**

- 实现：抽象类的子类使用 extends 来继承；接口必须使用 implements 来实现接口。
- 构造函数：抽象类可以有构造函数；接口不能有。
- main 方法：抽象类可以有 main 方法，并且我们能运行它；接口不能有 main 方法。
- 实现数量：类可以实现很多个接口；但是只能继承一个抽象类。
- 访问修饰符：接口中的方法默认使用 public 修饰；抽象类中的方法可以是任意访问修饰符。

## 3.集合

### Java集合类框架的基本接口有哪些？

集合类接口指定了一组叫做元素的对象。集合类接口的每一种具体的实现类都可以选择以它自己的方式对元素进行保存和排序。有的集合类允许重复的键，有些不允许。

Java集合类提供了一套设计良好的支持对一组对象进行操作的接口和类。Java集合类里面最基本的接口有：

Collection：代表一组对象，每一个对象都是它的子元素。

Set：不包含重复元素的Collection。

List：有顺序的collection，并且可以包含重复元素。

Map：可以把键(key)映射到值(value)的对象，键不能重复。

### 为什么集合类没有实现Cloneable和Serializable接口？

克隆(cloning)或者是序列化(serialization)的语义和含义是跟具体的实现相关的。因此，应该由集合类的具体实现来决定如何被克隆或者是序列化。

### 什么是迭代器(Iterator)？

Iterator接口提供了很多对集合元素进行迭代的方法。每一个集合类都包含了可以返回迭代器实例的

迭代方法。迭代器可以在迭代的过程中删除底层集合的元素,但是不可以直接调用集合的

remove(Object Obj)删除，可以通过迭代器的remove()方法删除。

### Iterator和ListIterator的区别是什么？

下面列出了他们的区别：

Iterator可用来遍历Set和List集合，但是ListIterator只能用来遍历List。

Iterator对集合只能是前向遍历，ListIterator既可以前向也可以后向。

ListIterator实现了Iterator接口，并包含其他的功能，比如：增加元素，替换元素，获取前一个和后一个元素的索引，等等。

### 快速失败(fail-fast)和安全失败(fail-safe)的区别是什么？

一：快速失败（fail—fast）

在用迭代器遍历一个集合对象时，如果遍历过程中对集合对象的结构进行了修改（增加、删除），则会抛出Concurrent

Modification Exception。

原理：迭代器在遍历时直接访问集合中的内容，并且在遍历过程中使用一个 modCount 变量。集合在被遍历期间如果结构发生变化，就会改变modCount的值。每当迭代器使用hashNext()/next()遍历下一个元素之前，都会检测modCount变量是否为expectedmodCount值，是的话就返回遍历；否则抛出异常，终止遍历。

注意：这里异常的抛出条件是检测到 modCount！=expectedmodCount

这个条件。如果集合发生变化时修改modCount值刚好又设置为了expectedmodCount值，则异常不会抛出。因此，不能依赖于这个异常是否抛出而进行并发操作的编程，这个异常只建议用于检测并发修改的bug。

场景：java.util包下的集合类都是快速失败的，不能在多线程下发生并发修改（迭代过程中被修改）。

二：安全失败（fail—safe）

采用安全失败机制的集合容器，在遍历时不是直接在集合内容上访问的，而是先复制原有集合内容，在拷贝的集合上进行遍历。

原理：由于迭代时是对原集合的拷贝进行遍历，所以在遍历过程中对原集合所作的修改并不能被迭代器检测到，所以不会触发Concurrent

Modification Exception。

缺点：基于拷贝内容的优点是避免了Concurrent Modification Exception，但同样地，迭代器并不能访问到修改后的内容，即：迭代器遍历的是开始遍历那一刻拿到的集合拷贝，在遍历期间原集合发生的修改迭代器是不知道的。

场景：java.util.concurrent包下的容器都是安全失败，可以在多线程下并发使用，并发修改。

### Java中的HashMap的工作原理是什么？

Java中的HashMap是以键值对(key-value)的形式存储元素的。HashMap需要一个hash函数，它使用hashCode()和equals()方法来向集合/从集合添加和检索元素。当调用put()方法的时候，HashMap会计算key的hash值，然后把键值对存储在集合中合适的索引上。如果key已经存在了，value会被更新成新值。HashMap的一些重要的特性是它的容量(capacity)，负载因子(load factor)和扩容极限(threshold resizing)。

### HashMap和Hashtable有什么区别？

HashMap和Hashtable都实现了Map接口，因此很多特性非常相似。但是，他们有以下不同点：

HashMap允许键和值是null，而Hashtable不允许键或者值是null。

Hashtable是同步的，而HashMap不是。因此，HashMap更适合于单线程环境，而Hashtable适合于多线程环境。

HashMap提供了可供应用迭代的键的集合，因此，HashMap是快速失败的。另一方面，Hashtable提供了对键的列举(Enumeration)。

一般认为Hashtable是一个遗留的类。

### 数组(Array)和列表(ArrayList)有什么区别？什么时候应该使用Array而不是ArrayList？

下面列出了Array和ArrayList的不同点：

Array可以包含基本类型和对象类型，ArrayList只能包含对象类型。

Array大小是固定的，ArrayList的大小是动态变化的。

ArrayList提供了更多的方法和特性，比如：addAll()，removeAll()，iterator()等等。

对于基本类型数据，集合使用自动装箱来减少编码工作量。但是，当处理固定大小的基本数据类型的时候，这种方式相对比较慢。

### ArrayList和LinkedList有什么区别？

ArrayList和LinkedList都实现了List接口，他们有以下的不同点：

ArrayList是基于索引的数据接口，它的底层是数组。它可以以O(1)时间复杂度对元素进行随机访问。与此对应，LinkedList是以元素列表的形式存储它的数据，每一个元素都和它的前一个和后一个元素链接在一起，在这种情况下，查找某个元素的时间复杂度是O(n)。

相对于ArrayList，LinkedList的插入，添加，删除操作速度更快，因为当元素被添加到集合任意位置的时候，不需要像数组那样重新计算大小或者是更新索引。

LinkedList比ArrayList更占内存，因为LinkedList为每一个节点存储了两个引用，一个指向前一个元素，一个指向下一个元素。

也可以参考ArrayList vs. LinkedList。

### Comparable和Comparator接口是干什么的？列出它们的区别?

Java提供了只包含一个compareTo()方法的Comparable接口。这个方法可以个给两个对象排序。具体来说，它返回负数，0，正数来表明已经存在的对象小于，等于，大于输入对象。

Java提供了包含compare()和equals()两个方法的Comparator接口。compare()方法用来给两个输入参数排序，返回负数，0，正数表明第一个参数是小于，等于，大于第二个参数。equals()方法需要一个对象作为参数，它用来决定输入参数是否和comparator相等。只有当输入参数也是一个comparator并且输入参数和当前comparator的排序结果是相同的时候，这个方法才返回true。

### 什么是Java优先级队列(Priority Queue)？

PriorityQueue是一个基于优先级堆的无界队列，它的元素是按照自然顺序(natural order)排序的。在创建的时候，我们可以给它提供一个负责给元素排序的比较器。PriorityQueue不允许null值，因为他们没有自然顺序，或者说他们没有任何的相关联的比较器。最后，PriorityQueue不是线程安全的，入队和出队的时间复杂度是O(log(n))。

### 你了解大O符号(big-O notation)么？你能给出不同数据结构的例子么？

大O符号描述了当数据结构里面的元素增加的时候，算法的规模或者是一个渐进上界 。

大O符号也可用来描述其他的行为，比如：内存消耗。因为集合类实际上是数据结构，我们一般使用大O符号基于时间，内存和性能来选择最好的实现。大O符号可以对大量数据的性能给出一个很好的说明。

### 如何权衡是使用无序的数组还是有序的数组？

有序数组最大的好处在于查找的时间复杂度是O(log n)，而无序数组是O(n)。有序数组的缺点是插入操作的时间复杂度是O(n)，因为值大的元素需要往后移动来给新元素腾位置。相反，无序数组的插入时间复杂度是常量O(1)。

### Java集合类框架的最佳实践有哪些？

根据应用的需要正确选择要使用的集合的类型对性能非常重要，比如：假如元素的数量是固定的，而且能事先知道，我们就应该用Array而不是ArrayList。

有些集合类允许指定初始容量。因此，如果我们能估计出存储的元素的数目，我们可以设置初始容量来避免重新计算hash值或者是扩容。

为了类型安全，可读性和健壮性的原因总是要使用泛型。同时，使用泛型还可以避免运行时的ClassCastException。

使用JDK提供的不变类(immutable class)作为Map的键可以避免为我们自己的类实现hashCode()和equals()方法。

编程的时候接口优于实现。

底层的集合实际上是空的情况下，返回长度是0的集合或者是数组，不要返回null。

### **说出几点 Java 中使用 Collections 的最佳实践**

这是我在使用 Java 中 Collectionc 类的一些最佳实践：

a）使用正确的集合类，例如，如果不需要同步列表，使用 ArrayList 而不是 Vector。

b）优先使用并发集合，而不是对集合进行同步。并发集合提供更好的可扩展性。

c）使用接口代表和访问集合，如使用List存储 ArrayList，使用 Map 存储 HashMap 等等。

d）使用迭代器来循环集合。

e）使用集合的时候使用泛型。

### Enumeration接口和Iterator接口的区别有哪些？

Enumeration速度是Iterator的2倍，同时占用更少的内存。但是，Iterator远远比Enumeration安全，因为其他线程不能够修改正在被iterator遍历的集合里面的对象。同时，Iterator允许调用者删除底层集合里面的元素，这对Enumeration来说是不可能的。

### HashSet和TreeSet有什么区别？

HashSet是由一个hash表来实现的，因此，它的元素是无序的。add()，remove()，contains()方法的时间复杂度是O(1)。

另一方面，TreeSet是由一个树形的结构来实现的，它里面的元素是有序的。因此，add()，remove()，contains()方法的时间复杂度是O(logn)。

### **List、Set、Map 和 Queue 之间的区别**

List 是一个有序集合，允许元素重复。它的某些实现可以提供基于下标值的常量访问时间，但是这不是 List 接口保证的。Set 是一个无序集合。

### **49）poll() 方法和 remove() 方法的区别？**

poll() 和 remove() 都是从队列中取出一个元素，但是 poll() 在获取元素失败的时候会返回空，但是 remove() 失败的时候会抛出异常。

### **50）Java 中 LinkedHashMap 和 PriorityQueue 的区别是什么？**

PriorityQueue 保证最高或者最低优先级的的元素总是在队列头部，但是 LinkedHashMap 维持的顺序是元素插入的顺序。当遍历一个 PriorityQueue 时，没有任何顺序保证，但是 LinkedHashMap 课保证遍历顺序是元素插入的顺序。

### **51）ArrayList 与 LinkedList 的不区别？**

最明显的区别是 ArrrayList 底层的数据结构是数组，支持随机访问，而 LinkedList 的底层数据结构书链表，不支持随机访问。使用下标访问一个元素，ArrayList 的时间复杂度是 O(1)，而 LinkedList 是 O(n)。更多细节的讨论参见答案。

### **52）用哪两种方式来实现集合的排序？**

你可以使用有序集合，如 TreeSet 或 TreeMap，你也可以使用有顺序的的集合，如 list，然后通过 Collections.sort() 来排序。

### **53）Java 中怎么打印数组？**

你可以使用 Arrays.toString() 和 Arrays.deepToString() 方法来打印数组。由于数组没有实现 toString() 方法，所以如果将数组传递给 System.out.println() 方法，将无法打印出数组的内容，但是 Arrays.toString() 可以打印每个元素。

### **54）Java 中的 LinkedList 是单向链表还是双向链表？**

是双向链表，你可以检查 JDK 的源码。在 Eclipse，你可以使用快捷键 Ctrl + T，直接在编辑器中打开该类。

### **55）Java 中的 TreeMap 是采用什么树实现的？**

Java 中的 TreeMap 是使用红黑树实现的。

### **56) Hashtable 与 HashMap 有什么不同之处？**

这两个类有许多不同的地方，下面列出了一部分：

a) Hashtable 是 JDK 1 遗留下来的类，而 HashMap 是后来增加的。

b）Hashtable 是同步的，比较慢，但 HashMap 没有同步策略，所以会更快。

c）Hashtable 不允许有个空的 key，但是 HashMap 允许出现一个 null key。

更多的不同之处参见答案。

### **57）Java 中的 HashSet，内部是如何工作的？**

HashSet 的内部采用 HashMap来实现。由于 Map 需要 key 和 value，所以所有 key 的都有一个默认 value。类似于 HashMap，HashSet 不允许重复的 key，只允许有一个null key，意思就是 HashSet 中只允许存储一个 null 对象。

### **58）写一段代码在遍历 ArrayList 时移除一个元素？**

该问题的关键在于面试者使用的是 ArrayList 的 remove() 还是 Iterator 的 remove()方法。这有一段示例代码，是使用正确的方式来实现在遍历的过程中移除元素，而不会出现 ConcurrentModificationException 异常的示例代码。

### **59）我们能自己写一个容器类，然后使用 for-each 循环码？**

可以，你可以写一个自己的容器类。如果你想使用 Java 中增强的循环来遍历，你只需要实现 Iterable 接口。如果你实现 Collection 接口，默认就具有该属性。

### **60）ArrayList 和 HashMap 的默认大小是多数？**

在 Java 7 中，ArrayList 的默认大小是 10 个元素，HashMap 的默认大小是16个元素（必须是2的幂）。这就是 Java 7 中 ArrayList 和 HashMap 类的代码片段：

```
// from ArrayList.java JDK 1.7
privatestaticfinalintDEFAULT_CAPACITY = 10;
//from HashMap.java JDK 7
staticfinalintDEFAULT_INITIAL_CAPACITY = 1<< 4; // aka 16
```

### **61）有没有可能两个不相等的对象有有相同的 hashcode？**

有可能，两个不相等的对象可能会有相同的 hashcode 值，这就是为什么在 hashmap 中会有冲突。相等 hashcode 值的规定只是说如果两个对象相等，必须有相同的hashcode 值，但是没有关于不相等对象的任何规定。

### **62）两个相同的对象会有不同的的 hash code 吗？**

不能，根据 hash code 的规定，这是不可能的。

### **63）我们可以在 hashcode() 中使用随机数字吗？**

不行，因为对象的 hashcode 值必须是相同的。参见答案获取更多关于 Java 中重写 hashCode() 方法的知识。

### **64）Java 中，Comparator 与 Comparable 有什么不同？**

Comparable 接口用于定义对象的自然顺序，而 comparator 通常用于定义用户定制的顺序。Comparable 总是只有一个，但是可以有多个 comparator 来定义对象的顺序。

### **65）为什么在重写 equals 方法的时候需要重写 hashCode 方法？**

因为有强制的规范指定需要同时重写 hashcode 与 equal 是方法，许多容器类，如 HashMap、HashSet 都依赖于 hashcode 与 equals 的规定。

### java中Collections框架是什么？？？


答：

Collection是整个集合框架的基础，它里面存储了一组对象，用于表示不同类型的Collections.主要有一下三种，其特点如下。


1）、set 主要特点集合中元素不能重复。
2）、list有序的Collection,按照对象的进入顺序保存对象，可以重复。
3）、map提供了从键映射到值得数据结构，值可以重复单键必须唯一。

### 9、java中ArrayList 、Vector 、LinkedList有什么区别？？？


答：

ArrayList 、Vector 、LinkedList类均在java.util包，均为可伸缩数组，即可以动态改变长度的数组。
ArrayList 、Vector 都是基于数组来实现的，数据存储是连续的，支持下标访问元素，查询快，插入慢。


区别在于：ArrayList提供的方法都不是同步的，且线程不安全，但效率高。Vector大部分方法都是同步的，且线程安全，效率低。
LinkedList 采用双向链表来实现，因此访问效率低，插入效率高，且该容器是非线性安全的。

### 10、java中HashTable与HashMap有什么区别？？？

答：
1、父类不同：
HashMap是继承自AbstractMap类，而HashTable是继承自Dictionary。但都是实现了Map方法。
2、null值不同：
HashMap可以允许存在一个为null的key和任意个null的value,但是HashTable中的key和value都不允许为null。
3、线程安全性：
hashtable是线程安全的，hashmap不之初线程同步，不是线程安全的

###  **java 容器都有哪些？**

常用容器的图录：

![](..\..\images\java\collection-1.jpg)



### **19. Collection 和 Collections 有什么区别？**

- java.util.Collection 是一个集合接口（集合类的一个顶级接口）。它提供了对集合对象进行基本操作的通用接口方法。Collection接口在Java 类库中有很多具体的实现。Collection接口的意义是为各种具体的集合提供了最大化的统一操作方式，其直接继承接口有List与Set。
- Collections则是集合类的一个工具类/帮助类，其中提供了一系列静态方法，用于对集合中元素进行排序、搜索以及线程安全等各种操作。

**20. List、Set、Map 之间的区别是什么？**

![](..\..\images\java\collection-2.jpg)



### 21. HashMap 和 Hashtable 有什么区别？

hashMap去掉了HashTable 的contains方法，但是加上了containsValue（）和containsKey（）方法。

hashTable同步的，而HashMap是非同步的，效率上逼hashTable要高。

hashMap允许空键值，而hashTable不允许。

### **22. 如何决定使用 HashMap 还是 TreeMap？**

对于在Map中插入、删除和定位元素这类操作，HashMap是最好的选择。然而，假如你需要对一个有序的key集合进行遍历，TreeMap是更好的选择。基于你的collection的大小，也许向HashMap中添加元素会更快，将map换为TreeMap进行有序key的遍历。

### **23. 说一下 HashMap 的实现原理？**

- HashMap概述： HashMap是基于哈希表的Map接口的非同步实现。此实现提供所有可选的映射操作，并允许使用null值和null键。此类不保证映射的顺序，特别是它不保证该顺序恒久不变。
- HashMap的数据结构： 在java编程语言中，最基本的结构就是两种，一个是数组，另外一个是模拟指针（引用），所有的数据结构都可以用这两个基本结构来构造的，HashMap也不例外。HashMap实际上是一个“链表散列”的数据结构，即数组和链表的结合体。

当我们往Hashmap中put元素时,首先根据key的hashcode重新计算hash值,根绝hash值得到这个元素在数组中的位置(下标),如果该数组在该位置上已经存放了其他元素,那么在这个位置上的元素将以链表的形式存放,新加入的放在链头,最先加入的放入链尾.如果数组中该位置没有元素,就直接将该元素放到数组的该位置上。

需要注意Jdk 1.8中对HashMap的实现做了优化,当链表中的节点数据超过八个之后,该链表会转为红黑树来提高查询效率,从原来的O(n)到O(logn)

### **24. 说一下 HashSet 的实现原理？**

- HashSet底层由HashMap实现
- HashSet的值存放于HashMap的key上
- HashMap的value统一为PRESENT

### **25. ArrayList 和 LinkedList 的区别是什么？**

最明显的区别是 ArrrayList底层的数据结构是数组，支持随机访问，而 LinkedList 的底层数据结构是双向循环链表，不支持随机访问。使用下标访问一个元素，ArrayList 的时间复杂度是 O(1)，而 LinkedList 是 O(n)。

### **26. 如何实现数组和 List 之间的转换？**

- List转换成为数组：调用ArrayList的toArray方法。
- 数组转换成为List：调用Arrays的asList方法。

### **27. ArrayList 和 Vector 的区别是什么？**

Vector是同步的，而ArrayList不是。然而，如果你寻求在迭代的时候对列表进行改变，你应该使用CopyOnWriteArrayList。

ArrayList比Vector快，它因为有同步，不会过载。

ArrayList更加通用，因为我们可以使用Collections工具类轻易地获取同步列表和只读列表。

### **28. Array 和 ArrayList 有何区别？**

Array可以容纳基本类型和对象，而ArrayList只能容纳对象。

Array是指定大小的，而ArrayList大小是固定的。

Array没有提供ArrayList那么多功能，比如addAll、removeAll和iterator等。

### **29. 在 Queue 中 poll()和 remove()有什么区别？**

poll() 和 remove() 都是从队列中取出一个元素，但是 poll() 在获取元素失败的时候会返回空，但是 remove() 失败的时候会抛出异常。

### **30. 哪些集合类是线程安全的？**

- vector：就比arraylist多了个同步化机制（线程安全），因为效率较低，现在已经不太建议使用。在web应用中，特别是前台页面，往往效率（页面响应速度）是优先考虑的。
- statck：堆栈类，先进后出。
- hashtable：就比hashmap多了个线程安全。
- enumeration：枚举，相当于迭代器。

### **31. 迭代器 Iterator 是什么？**

迭代器是一种设计模式，它是一个对象，它可以遍历并选择序列中的对象，而开发人员不需要了解该序列的底层结构。迭代器通常被称为“轻量级”对象，因为创建它的代价小。

### **32. Iterator 怎么使用？有什么特点？**

Java中的Iterator功能比较简单，并且只能单向移动：

(1) 使用方法iterator()要求容器返回一个Iterator。第一次调用Iterator的next()方法时，它返回序列的第一个元素。注意：iterator()方法是java.lang.Iterable接口,被Collection继承。

(2) 使用next()获得序列中的下一个元素。

(3) 使用hasNext()检查序列中是否还有元素。

(4) 使用remove()将迭代器新返回的元素删除。

Iterator是Java迭代器最简单的实现，为List设计的ListIterator具有更多的功能，它可以从两个方向遍历List，也可以从List中插入和删除元素。

### **33. Iterator 和 ListIterator 有什么区别？**

Iterator可用来遍历Set和List集合，但是ListIterator只能用来遍历List。

Iterator对集合只能是前向遍历，ListIterator既可以前向也可以后向。

ListIterator实现了Iterator接口，并包含其他的功能，比如：增加元素，替换元素，获取前一个和后一个元素的索引，等等。

## 4.多线程与并发

### 线程vs程序vs进程及关系？

**线程**与进程相似，但线程是一个比进程更小的执行单位。一个进程在其执行的过程中可以产生多个线程。与进程不同的是同类的多个线程共享同一块内存空间和一组系统资源，所以系统在产生一个线程，或是在各个线程之间作切换工作时，负担要比进程小得多，也正因为如此，线程也被称为轻量级进程。

**程序**是含有指令和数据的文件，被存储在磁盘或其他的数据存储设备中，也就是说程序是静态的代码。

**进程**是程序的一次执行过程，是系统运行程序的基本单位，因此进程是动态的。系统运行一个程序即是一个进程从创建，运行到消亡的过程。简单来说，一个进程就是一个执行中的程序，它在计算机中一个指令接着一个指令地执行着，同时，每个进程还占有某些系统资源如CPU时间，内存空间，文件，文件，输入输出设备的使用权等等。换句话说，当程序在执行时，将会被操作系统载入内存中。 线程是进程划分成的更小的运行单位。线程和进程最大的不同在于基本上各进程是独立的，而各线程则不一定，因为同一进程中的线程极有可能会相互影响。从另一角度来说，进程属于操作系统的范畴，主要是同一段时间内，可以同时执行一个以上的程序，而线程则是在同一程序内几乎同时执行一个以上的程序段。

### 什么是线程，什么是进程，它们之间的区别是什么 ？？？


**答：**
**线程：程序执行过程中，能够执行代码的一个执行单元。四种状态（运行、就绪、挂起、结束）**
**进程：是指一段正在执行的程序。**


**其关系如下：**
1）、一个线程只能属于一个进程，而一个进程可以有多个线程，但是至少有一个线程，线程是操作系统可识别的最小执行和调度单位。
2）、资源分配给进程，同一个进程中的所有线程共享该进程中的所有资源，同一个进程多个线程共享代码段（代码和常量），数据段（全局变量和静态变量），扩展段（堆存储）。但是每个线程用有独立的栈段，栈段用来存放所有的局部变量和临时变量。
3）、处理机分给线程，即真正的处理机上运行的是线程。
4）、线程在执行过程中，需要协作同步。不同的进程的线程间要利用通信的办法实现同步。

### 进程和线程的区别是什么？

进程是执行着的应用程序，而线程是进程内部的一个执行序列。一个进程可以有多个线程。线程又叫做轻量级进程。

线程与进程的区别归纳：

a.地址空间和其它资源：进程间相互独立，同一进程的各线程间共享。某进程内的线程在其它进程不可见。

b.通信：进程间通信IPC，线程间可以直接读写进程数据段（如全局变量）来进行通信——需要进程同步和互斥手段的辅助，以保证数据的一致性。

c.调度和切换：线程上下文切换比进程上下文切换要快得多。

d.在多线程OS中，进程不是一个可执行的实体。

### 11、同步与异步的区别？？？


答：

所谓的同步，就是发出一个功能调用时，在没有得到结果之前，该调用就不会放回，或继续执行后续操作。简单来说，同步就是必须一件一件的来做，等前一件事做完了，才能做下一件事。


异步，当异步过程调用发出后，调用者在没有得到结果之前就可以执行后续操作，
当这个调用完成之后，一般通过状态，通知和回调通知，调用者。对于异步调用，其返回并不受调用者控制。

### 线程5种基本状态及定义?

1. **新建(new)**：新创建了一个线程对象。

2. **可运行(runnable)**：线程对象创建后，其他线程(比如main线程）调用了该对象的start()方法。该状态的线程位于可运行线程池中，等待被线程调度选中，获 取cpu的使用权。

3. **运行(running)**：可运行状态(runnable)的线程获得了cpu时间片（timeslice），执行程序代码。

4. **阻塞(block)**：阻塞状态是指线程因为某种原因放弃了cpu使用权，也即让出了cpu timeslice，暂时停止运行。直到线程进入可运行(runnable)状态，才有 机会再次获得cpu timeslice转到运行(running)状态。阻塞的情况分三种： (一). 等待阻塞：运行(running)的线程执行o.wait()方法，JVM会把该线程放 入等待队列(waitting queue)中。 (二). 同步阻塞：运行(running)的线程在获取对象的同步锁时，若该同步锁 被别的线程占用，则JVM会把该线程放入锁池(lock pool)中。 (三). 其他阻塞: 运行(running)的线程执行Thread.sleep(long ms)或t.join()方法，或者发出了I/O请求时，JVM会把该线程置为阻塞状态。当sleep()状态超时join()等待线程终止或者超时、或者I/O处理完毕时，线程重新转入可运行(runnable)状态。

5. **死亡(dead)**：线程run()、main()方法执行结束，或者因异常退出了run()方法，则该线程结束生命周期。死亡的线程不可再次复生。

   ![](C:/Work/workspaces/xyzy/hexo/source/images/java/%E7%BA%BF%E7%A8%8B%E7%8A%B6%E6%80%81.jpg)

   备注： 可以用早起坐地铁来比喻这个过程：

   还没起床：sleeping

   起床收拾好了，随时可以坐地铁出发：Runnable

   等地铁来：Waiting

   地铁来了，但要排队上地铁：I/O阻塞

   上了地铁，发现暂时没座位：synchronized阻塞

   地铁上找到座位：Running

   到达目的地：Dead

### 创建线程有几种不同的方式？你喜欢哪一种？为什么？

有4种方式可以用来创建线程：

继承Thread类

实现Runnable接口

应用程序可以使用Executor框架来创建线程池

实现Runnable接口这种方式更受欢迎，因为这不需要继承Thread类。在应用设计中已经继承了别的对象的情况下，这需要多继承（而Java不支持多继承），只能实现接口。同时，线程池也是非常高效的，很容易实现和使用。

还有一种方式是实现Callable接口

### 概括的解释下线程的几种可用状态。

\1. 新建( new )：新创建了一个线程对象。

\2. 可运行( runnable

)：线程对象创建后，其他线程(比如 main 线程）调用了该对象 的 start ()方法。该状态的线程位于可运行线程池中，等待被线程调度选中，获 取 cpu 的使用权 。

\3. 运行( running )：可运行状态( runnable )的线程获得了 cpu 时间片（ timeslice ） ，执行程序代码。

\4. 阻塞( block )：阻塞状态是指线程因为某种原因放弃了 cpu 使用权，也即让出了 cpu timeslice ，暂时停止运行。直到线程进入可运行( runnable

)状态，才有 机会再次获得 cpu timeslice 转到运行( running )状态。阻塞的情况分三种：

(一). 等待阻塞：运行( running )的线程执行 o . wait ()方法， JVM 会把该线程放 入等待队列( waitting queue )中。

(二). 同步阻塞：运行( running )的线程在获取对象的同步锁时，若该同步锁 被别的线程占用，则 JVM 会把该线程放入锁池( lock pool )中。

(三). 其他阻塞: 运行( running )的线程执行 Thread . sleep ( long

ms )或 t . join

()方法，或者发出了 I / O 请求时， JVM 会把该线程置为阻塞状态。 当 sleep ()状态超时、 join ()等待线程终止或者超时、或者 I / O 处理完毕时，线程重新转入可运行( runnable

)状态。

\5. 死亡( dead )：线程 run ()、 main () 方法执行结束，或者因异常退出了 run ()方法，则该线程结束生命周期。死亡的线程不可再次复生。

### 同步方法和同步代码块的区别是什么？

区别：

同步方法默认用this或者当前类class对象作为锁；

同步代码块可以选择以什么来加锁，比同步方法要更细颗粒度，我们可以选择只同步会发生同步问题的部分代码而不是整个方法；

同步方法使用关键字

synchronized修饰方法，而同步代码块主要是修饰需要进行同步的代码，用 synchronized（object）{代码内容}进行修饰；

### 在监视器(Monitor)内部，是如何做线程同步的？程序应该做哪种级别的同步？

监视器和锁在Java虚拟机中是一块使用的。监视器监视一块同步代码块，确保一次只有一个线程执行同步代码块。每一个监视器都和一个对象引用相关联。线程在获取锁之前不允许执行同步代码。

### 什么是死锁(deadlock)？

所谓死锁是指多个进程因竞争资源而造成的一种僵局（互相等待），若无外力作用，这些进程都将无法向前推进。死锁产生的4个必要条件：

互斥条件：进程要求对所分配的资源（如打印机）进行排他性控制，即在一段时间内某 资源仅为一个进程所占有。此时若有其他进程请求该资源，则请求进程只能等待。

不剥夺条件：进程所获得的资源在未使用完毕之前，不能被其他进程强行夺走，即只能 由获得该资源的进程自己来释放（只能是主动释放)。

请求和保持条件：进程已经保持了至少一个资源，但又提出了新的资源请求，而该资源 已被其他进程占有，此时请求进程被阻塞，但对自己已获得的资源保持不放。

循环等待条件：存在一种进程资源的循环等待链，链中每一个进程已获得的资源同时被 链中下一个进程所请求。

### 如何确保N个线程可以访问N个资源同时又不导致死锁？

使用多线程的时候，一种非常简单的避免死锁的方式就是：指定获取锁的顺序，并强制线程按照指定的顺序获取锁。因此，如果所有的线程都是以同样的顺序加锁和释放锁，就不会出现死锁了。

### 线程同步，并发操作怎么控制

Java中可在方法名前加关键字syschronized来处理当有多个线程同时访问共享资源时候的问题

资源时，如果该资源没有被占用，那么将资源交付给这个申请者使用，在此期间，其他申请者只能申请而不能使用该资源，当该资源被使用完成后将释放该资源上的锁，其他申请者可申请使用。并发控制主要是为了多线程操作时带来的资源读写问题。如果不加以空间可能会出现死锁，读脏数据、不可重复读、丢失更新等异常。并发操作可以通过加锁的方式进行控制，锁又可分为乐观锁和悲观锁。悲观锁：悲观锁并发模式假定系统中存在足够多的数据修改操作，以致于任何确定的读操作都可能会受到由个别的用户所制造的数据修改的影响。也就是说悲观锁假定冲突总会发生，通过独占正在被读取的数据来避免冲突。但是独占数据会导致其他进程无法修改该数据，进而产生阻塞，读数据和写数据会相互阻塞。乐观锁：乐观锁假定系统的数据修改只会产生非常少的冲突，也就是说任何进程都不大可能修改别的进程正在访问的数据。乐观并发模式下，读数据和写数据之间不会发生冲突，只有写数据与写数据之间会发生冲突。即读数据不会产生阻塞，只有写数据才会产生阻塞。

### Java 中能创建 volatile 数组吗？

能，Java 中可以创建 volatile 类型数组，不过只是一个指向数组的引用，而不是整个数组。我的意思是，如果改变引用指向的数组，将会受到 volatile 的保护，但是如果多个线程同时改变数组的元素，volatile 标示符就不能起到之前的保护作用了。

### volatile 能使得一个非原子操作变成原子操作吗？

一个典型的例子是在类中有一个 long 类型的成员变量。如果你知道该成员变量会被多个线程访问，如计数器、价格等，你最好是将其设置为 volatile。为什么？因为 Java 中读取 long 类型变量不是原子的，需要分成两步，如果一个线程正在修改该 long 变量的值，另一个线程可能只能看到该值的一半（前 32 位）。但是对一个 volatile 型的 long 或 double 变量的读写是原子。

### volatile 修饰符的有过什么实践？

一种实践是用 volatile 修饰 long 和 double 变量，使其能按原子类型来读写。double 和 long 都是64位宽，因此对这两种类型的读是分为两部分的，第一次读取第一个 32 位，然后再读剩下的 32 位，这个过程不是原子的，但 Java 中 volatile 型的 long 或 double 变量的读写是原子的。volatile 修复符的另一个作用是提供内存屏障（memory barrier），例如在分布式框架中的应用。简单的说，就是当你写一个 volatile 变量之前，Java 内存模型会插入一个写屏障（write barrier），读一个 volatile 变量之前，会插入一个读屏障（read barrier）。意思就是说，在你写一个 volatile 域时，能保证任何线程都能看到你写的值，同时，在写之前，也能保证任何数值的更新对所有线程是可见的，因为内存屏障会将其他所有写的值更新到缓存。

### volatile 类型变量提供什么保证？

volatile 变量提供顺序和可见性保证，例如，JVM 或者 JIT为了获得更好的性能会对语句重排序，但是 volatile 类型变量即使在没有同步块的情况下赋值也不会与其他语句重排序。 volatile 提供 happens-before 的保证，确保一个线程的修改能对其他线程是可见的。某些情况下，volatile 还能提供原子性，如读 64 位数据类型，像 long 和 double 都不是原子的，但 volatile 类型的 double 和 long 就是原子的。

### 10 个线程和 2 个线程的同步代码，哪个更容易写？

从写代码的角度来说，两者的复杂度是相同的，因为同步代码与线程数量是相互独立的。但是同步策略的选择依赖于线程的数量，因为越多的线程意味着更大的竞争，所以你需要利用同步技术，如锁分离，这要求更复杂的代码和专业知识。

### 你是如何调用 wait（）方法的？使用 if 块还是循环？为什么？

wait() 方法应该在循环调用，因为当线程获取到 CPU 开始执行的时候，其他条件可能还没有满足，所以在处理前，循环检测条件是否满足会更好。下面是一段标准的使用 wait 和 notify 方法的代码：

```
// The standard idiom for using the wait method
synchronized(obj) {
while(condition does not hold)
obj.wait(); // (Releases lock, and reacquires on wakeup)
... // Perform action appropriate to condition
}
```

### 什么是多线程环境下的伪共享（false sharing）？

伪共享是多线程系统（每个处理器有自己的局部缓存）中一个众所周知的性能问题。伪共享发生在不同处理器的上的线程对变量的修改依赖于相同的缓存行，如下图所示：

![](..\..\images\java\thread-1.jpg)



有经验程序员的 Java 面试题

伪共享问题很难被发现，因为线程可能访问完全不同的全局变量，内存中却碰巧在很相近的位置上。如其他诸多的并发问题，避免伪共享的最基本方式是仔细审查代码，根据缓存行来调整你的数据结构。

### 什么是 Busy spin？我们为什么要使用它？

Busy spin 是一种在不释放 CPU 的基础上等待事件的技术。它经常用于避免丢失 CPU 缓存中的数据（如果线程先暂停，之后在其他CPU上运行就会丢失）。所以，如果你的工作要求低延迟，并且你的线程目前没有任何顺序，这样你就可以通过循环检测队列中的新消息来代替调用 sleep() 或 wait() 方法。它唯一的好处就是你只需等待很短的时间，如几微秒或几纳秒。LMAX 分布式框架是一个高性能线程间通信的库，该库有一个 BusySpinWaitStrategy 类就是基于这个概念实现的，使用 busy spin 循环 EventProcessors 等待屏障。

### Java 中怎么获取一份线程 dump 文件？

在 Linux 下，你可以通过命令 kill -3 PID （Java 进程的进程 ID）来获取 Java 应用的 dump 文件。在 Windows 下，你可以按下 Ctrl + Break 来获取。这样 JVM 就会将线程的 dump 文件打印到标准输出或错误文件中，它可能打印在控制台或者日志文件中，具体位置依赖应用的配置。如果你使用Tomcat。

### Swing 是线程安全的？

不是，Swing 不是线程安全的。你不能通过任何线程来更新 Swing 组件，如 JTable、JList 或 JPanel，事实上，它们只能通过 GUI 或 AWT 线程来更新。这就是为什么 Swing 提供 invokeAndWait() 和 invokeLater() 方法来获取其他线程的 GUI 更新请求。这些方法将更新请求放入 AWT 的线程队列中，可以一直等待，也可以通过异步更新直接返回结果。你也可以在参考答案中查看和学习到更详细的内容。

### 什么是线程局部变量？

线程局部变量是局限于线程内部的变量，属于线程自身所有，不在多个线程间共享。Java 提供 ThreadLocal 类来支持线程局部变量，是一种实现线程安全的方式。但是在管理环境下（如 web 服务器）使用线程局部变量的时候要特别小心，在这种情况下，工作线程的生命周期比任何应用变量的生命周期都要长。任何线程局部变量一旦在工作完成后没有释放，Java 应用就存在内存泄露的风险。

### 用 wait-notify 写一段代码来解决生产者-消费者问题？

请参考答案中的示例代码。只要记住在同步块中调用 wait() 和 notify()方法，如果阻塞，通过循环来测试等待条件。

### 用 Java 写一个线程安全的单例模式（Singleton）？

请参考答案中的示例代码，这里面一步一步教你创建一个线程安全的 Java 单例类。当我们说线程安全时，意思是即使初始化是在多线程环境中，仍然能保证单个实例。Java 中，使用枚举作为单例类是最简单的方式来创建线程安全单例模式的方式。

### Java 中 sleep 方法和 wait 方法的区别？

虽然两者都是用来暂停当前运行的线程，但是 sleep() 实际上只是短暂停顿，因为它不会释放锁，而 wait() 意味着条件等待，这就是为什么该方法要释放锁，因为只有这样，其他等待的线程才能在满足条件时获取到该锁。

### 什么是不可变对象（immutable object）？Java 中怎么创建一个不可变对象？

不可变对象指对象一旦被创建，状态就不能再改变。任何修改都会创建一个新的对象，如 String、Integer及其它包装类。详情参见答案，一步一步指导你在 Java 中创建一个不可变的类。

### 我们能创建一个包含可变对象的不可变对象吗？

是的，我们是可以创建一个包含可变对象的不可变对象的，你只需要谨慎一点，不要共享可变对象的引用就可以了，如果需要变化时，就返回原对象的一个拷贝。最常见的例子就是对象中包含一个日期对象的引用。





### **Java 中，编写多线程程序的时候你会遵循哪些最佳实践？**

这是我在写Java 并发程序的时候遵循的一些最佳实践：

a）给线程命名，这样可以帮助调试。

b）最小化同步的范围，而不是将整个方法同步，只对关键部分做同步。

c）如果可以，更偏向于使用 volatile 而不是 synchronized。

d）使用更高层次的并发工具，而不是使用 wait() 和 notify() 来实现线程间通信，如 BlockingQueue，CountDownLatch 及 Semeaphore。

e）优先使用并发集合，而不是对集合进行同步。并发集合提供更好的可扩展性。

### **5. 并行和并发有什么区别？**

并行是指两个或者多个事件在同一时刻发生；而并发是指两个或多个事件在同一时间间隔发生。

并行是在不同实体上的多个事件，并发是在同一实体上的多个事件。

在一台处理器上“同时”处理多个任务，在多台处理器上同时处理多个任务。如hadoop分布式集群。

所以并发编程的目标是充分的利用处理器的每一个核，以达到最高的处理性能。

### **36. 线程和进程的区别？**

简而言之，进程是程序运行和资源分配的基本单位，一个程序至少有一个进程，一个进程至少有一个线程。进程在执行过程中拥有独立的内存单元，而多个线程共享内存资源，减少切换次数，从而效率更高。线程是进程的一个实体，是cpu调度和分派的基本单位，是比程序更小的能独立运行的基本单位。同一进程中的多个线程之间可以并发执行。

### **37. 守护线程是什么？**

守护线程（即daemon thread），是个服务线程，准确地来说就是服务其他的线程。

### **38. 创建线程有哪几种方式？**

①. 继承Thread类创建线程类

定义Thread类的子类，并重写该类的run方法，该run方法的方法体就代表了线程要完成的任务。因此把run()方法称为执行体。

创建Thread子类的实例，即创建了线程对象。

调用线程对象的start()方法来启动该线程。

②. 通过Runnable接口创建线程类

定义runnable接口的实现类，并重写该接口的run()方法，该run()方法的方法体同样是该线程的线程执行体。

创建 Runnable实现类的实例，并依此实例作为Thread的target来创建Thread对象，该Thread对象才是真正的线程对象。

调用线程对象的start()方法来启动该线程。

③. 通过Callable和Future创建线程

创建Callable接口的实现类，并实现call()方法，该call()方法将作为线程执行体，并且有返回值。

创建Callable实现类的实例，使用FutureTask类来包装Callable对象，该FutureTask对象封装了该Callable对象的call()方法的返回值。

使用FutureTask对象作为Thread对象的target创建并启动新线程。

调用FutureTask对象的get()方法来获得子线程执行结束后的返回值。

### **39. 说一下 runnable 和 callable 有什么区别？**

有点深的问题了，也看出一个Java程序员学习知识的广度。

Runnable接口中的run()方法的返回值是void，它做的事情只是纯粹地去执行run()方法中的代码而已；

Callable接口中的call()方法是有返回值的，是一个泛型，和Future、FutureTask配合可以用来获取异步执行的结果。

### **40. 线程有哪些状态？**

线程通常都有五种状态，创建、就绪、运行、阻塞和死亡。

- 创建状态。在生成线程对象，并没有调用该对象的start方法，这是线程处于创建状态。
- 就绪状态。当调用了线程对象的start方法之后，该线程就进入了就绪状态，但是此时线程调度程序还没有把该线程设置为当前线程，此时处于就绪状态。在线程运行之后，从等待或者睡眠中回来之后，也会处于就绪状态。
- 运行状态。线程调度程序将处于就绪状态的线程设置为当前线程，此时线程就进入了运行状态，开始运行run函数当中的代码。
- 阻塞状态。线程正在运行的时候，被暂停，通常是为了等待某个时间的发生(比如说某项资源就绪)之后再继续运行。sleep,suspend，wait等方法都可以导致线程阻塞。
- 死亡状态。如果一个线程的run方法执行结束或者调用stop方法后，该线程就会死亡。对于已经死亡的线程，无法再使用start方法令其进入就绪 　　

### **41. sleep() 和 wait() 有什么区别？**

- sleep()：方法是线程类（Thread）的静态方法，让调用线程进入睡眠状态，让出执行机会给其他线程，等到休眠时间结束后，线程进入就绪状态和其他线程一起竞争cpu的执行时间。因为sleep() 是static静态的方法，他不能改变对象的机锁，当一个synchronized块中调用了sleep() 方法，线程虽然进入休眠，但是对象的机锁没有被释放，其他线程依然无法访问这个对象。
- wait()：wait()是Object类的方法，当一个线程执行到wait方法时，它就进入到一个和该对象相关的等待池，同时释放对象的机锁，使得其他线程能够访问，可以通过notify，notifyAll方法来唤醒等待的线程。

### **42. notify()和 notifyAll()有什么区别？**

如果线程调用了对象的 wait()方法，那么线程便会处于该对象的等待池中，等待池中的线程不会去竞争该对象的锁。

当有线程调用了对象的 notifyAll()方法（唤醒所有 wait 线程）或 notify()方法（只随机唤醒一个 wait 线程），被唤醒的的线程便会进入该对象的锁池中，锁池中的线程会去竞争该对象锁。也就是说，调用了notify后只要一个线程会由等待池进入锁池，而notifyAll会将该对象等待池内的所有线程移动到锁池中，等待锁竞争。

优先级高的线程竞争到对象锁的概率大，假若某线程没有竞争到该对象锁，它还会留在锁池中，唯有线程再次调用 wait()方法，它才会重新回到等待池中。而竞争到对象锁的线程则继续往下执行，直到执行完了 synchronized 代码块，它会释放掉该对象锁，这时锁池中的线程会继续竞争该对象锁。

### **43. 线程的 run()和 start()有什么区别？**

每个线程都是通过某个特定Thread对象所对应的方法run()来完成其操作的，方法run()称为线程体。通过调用Thread类的start()方法来启动一个线程。

- start()方法来启动一个线程，真正实现了多线程运行。这时无需等待run方法体代码执行完毕，可以直接继续执行下面的代码； 这时此线程是处于就绪状态， 并没有运行。 然后通过此Thread类调用方法run()来完成其运行状态， 这里方法run()称为线程体，它包含了要执行的这个线程的内容， Run方法运行结束， 此线程终止。然后CPU再调度其它线程。
- run()方法是在本线程里的，只是线程里的一个函数,而不是多线程的。 如果直接调用run(),其实就相当于是调用了一个普通函数而已，直接待用run()方法必须等待run()方法执行完毕才能执行下面的代码，所以执行路径还是只有一条，根本就没有线程的特征，所以在多线程执行时要使用start()方法而不是run()方法。

### **44. 创建线程池有哪几种方式？**

①. newFixedThreadPool(int nThreads)

创建一个固定长度的线程池，每当提交一个任务就创建一个线程，直到达到线程池的最大数量，这时线程规模将不再变化，当线程发生未预期的错误而结束时，线程池会补充一个新的线程。

②. newCachedThreadPool()

创建一个可缓存的线程池，如果线程池的规模超过了处理需求，将自动回收空闲线程，而当需求增加时，则可以自动添加新线程，线程池的规模不存在任何限制。

③. newSingleThreadExecutor()

这是一个单线程的Executor，它创建单个工作线程来执行任务，如果这个线程异常结束，会创建一个新的来替代它；它的特点是能确保依照任务在队列中的顺序来串行执行。

④. newScheduledThreadPool(int corePoolSize)

创建了一个固定长度的线程池，而且以延迟或定时的方式来执行任务，类似于Timer。

\45. 线程池都有哪些状态？

线程池有5种状态：Running、ShutDown、Stop、Tidying、Terminated。

线程池各个状态切换框架图：

![](..\..\images\java\thread-2.jpg)



### **46. 线程池中 submit()和 execute()方法有什么区别？**

- 接收的参数不一样
- submit有返回值，而execute没有
- submit方便Exception处理

### **47. 在 java 程序中怎么保证多线程的运行安全？**

线程安全在三个方面体现：

- 原子性：提供互斥访问，同一时刻只能有一个线程对数据进行操作，（atomic,synchronized）；
- 可见性：一个线程对主内存的修改可以及时地被其他线程看到，（synchronized,volatile）；
- 有序性：一个线程观察其他线程中的指令执行顺序，由于指令重排序，该观察结果一般杂乱无序，（happens-before原则）。

- \48. 多线程锁的升级原理是什么？

在Java中，锁共有4种状态，级别从低到高依次为：无状态锁，偏向锁，轻量级锁和重量级锁状态，这几个状态会随着竞争情况逐渐升级。锁可以升级但不能降级。

锁升级的图示过程：

![](..\..\images\java\thread-3.jpg)



### **49. 什么是死锁？**

死锁是指两个或两个以上的进程在执行过程中，由于竞争资源或者由于彼此通信而造成的一种阻塞的现象，若无外力作用，它们都将无法推进下去。此时称系统处于死锁状态或系统产生了死锁，这些永远在互相等待的进程称为死锁进程。是操作系统层面的一个错误，是进程死锁的简称，最早在 1965 年由 Dijkstra 在研究银行家算法时提出的，它是计算机操作系统乃至整个并发程序设计领域最难处理的问题之一。

### **50. 怎么防止死锁？**

死锁的四个必要条件：

- 互斥条件：进程对所分配到的资源不允许其他进程进行访问，若其他进程访问该资源，只能等待，直至占有该资源的进程使用完成后释放该资源
- 请求和保持条件：进程获得一定的资源之后，又对其他资源发出请求，但是该资源可能被其他进程占有，此事请求阻塞，但又对自己获得的资源保持不放
- 不可剥夺条件：是指进程已获得的资源，在未完成使用之前，不可被剥夺，只能在使用完后自己释放
- 环路等待条件：是指进程发生死锁后，若干进程之间形成一种头尾相接的循环等待资源关系

这四个条件是死锁的必要条件，只要系统发生死锁，这些条件必然成立，而只要上述条件之 一不满足，就不会发生死锁。

理解了死锁的原因，尤其是产生死锁的四个必要条件，就可以最大可能地避免、预防和 解除死锁。

所以，在系统设计、进程调度等方面注意如何不让这四个必要条件成立，如何确 定资源的合理分配算法，避免进程永久占据系统资源。

此外，也要防止进程在处于等待状态的情况下占用资源。因此，对资源的分配要给予合理的规划。

### **51. ThreadLocal 是什么？有哪些使用场景？**

线程局部变量是局限于线程内部的变量，属于线程自身所有，不在多个线程间共享。Java提供ThreadLocal类来支持线程局部变量，是一种实现线程安全的方式。但是在管理环境下（如 web 服务器）使用线程局部变量的时候要特别小心，在这种情况下，工作线程的生命周期比任何应用变量的生命周期都要长。任何线程局部变量一旦在工作完成后没有释放，Java 应用就存在内存泄露的风险。

### **52.说一下 synchronized 底层实现原理？**

synchronized可以保证方法或者代码块在运行时，同一时刻只有一个方法可以进入到临界区，同时它还可以保证共享变量的内存可见性。

Java中每一个对象都可以作为锁，这是synchronized实现同步的基础：

- 普通同步方法，锁是当前实例对象
- 静态同步方法，锁是当前类的class对象
- 同步方法块，锁是括号里面的对象

### **53. synchronized 和 volatile 的区别是什么？**

volatile本质是在告诉jvm当前变量在寄存器（工作内存）中的值是不确定的，需要从主存中读取； synchronized则是锁定当前变量，只有当前线程可以访问该变量，其他线程被阻塞住。

- volatile仅能使用在变量级别；synchronized则可以使用在变量、方法、和类级别的。
- volatile仅能实现变量的修改可见性，不能保证原子性；而synchronized则可以保证变量的修改可见性和原子性。
- volatile不会造成线程的阻塞；synchronized可能会造成线程的阻塞。
- volatile标记的变量不会被编译器优化；synchronized标记的变量可以被编译器优化。

### **54. synchronized 和 Lock 有什么区别？**

首先synchronized是java内置关键字，在jvm层面，Lock是个java类；

synchronized无法判断是否获取锁的状态，Lock可以判断是否获取到锁；

synchronized会自动释放锁(a 线程执行完同步代码会释放锁 ；b 线程执行过程中发生异常会释放锁)，Lock需在finally中手工释放锁（unlock()方法释放锁），否则容易造成线程死锁；

用synchronized关键字的两个线程1和线程2，如果当前线程1获得锁，线程2线程等待。如果线程1阻塞，线程2则会一直等待下去，而Lock锁就不一定会等待下去，如果尝试获取不到锁，线程可以不用一直等待就结束了；

synchronized的锁可重入、不可中断、非公平，而Lock锁可重入、可判断、可公平（两者皆可）；

Lock锁适合大量同步的代码的同步问题，synchronized锁适合代码少量的同步问题。

### **55. synchronized 和 ReentrantLock 区别是什么？**

synchronized是和if、else、for、while一样的关键字，ReentrantLock是类，这是二者的本质区别。既然ReentrantLock是类，那么它就提供了比synchronized更多更灵活的特性，可以被继承、可以有方法、可以有各种各样的类变量，ReentrantLock比synchronized的扩展性体现在几点上：

- ReentrantLock可以对获取锁的等待时间进行设置，这样就避免了死锁
- ReentrantLock可以获取各种锁的信息
- ReentrantLock可以灵活地实现多路通知

另外，二者的锁机制其实也是不一样的:ReentrantLock底层调用的是Unsafe的park方法加锁，synchronized操作的应该是对象头中mark word。

### **56. 说一下 atomic 的原理？**

Atomic包中的类基本的特性就是在多线程环境下，当有多个线程同时对单个（包括基本类型及引用类型）变量进行操作时，具有排他性，即当多个线程同时对该变量的值进行更新时，仅有一个线程能成功，而未成功的线程可以向自旋锁一样，继续尝试，一直等到执行成功。

Atomic系列的类中的核心方法都会调用unsafe类中的几个本地方法。我们需要先知道一个东西就是Unsafe类，全名为：sun.misc.Unsafe，这个类包含了大量的对C代码的操作，包括很多直接内存分配以及原子操作的调用，而它之所以标记为非安全的，是告诉你这个里面大量的方法调用都会存在安全隐患，需要小心使用，否则会导致严重的后果，例如在通过unsafe分配内存的时候，如果自己指定某些区域可能会导致一些类似C++一样的指针越界到其他进程的问题。

### **说出至少 5 点在 Java 中使用线程的最佳实践。**

这个问题与之前的问题类似，你可以使用上面的答案。对线程来说，你应该：

a）对线程命名

b）将线程和任务分离，使用线程池执行器来执行 Runnable 或 Callable。

c）使用线程池

## 5.异常

### Java中的两种异常类型是什么？他们有什么区别？

Java中有两种异常：受检查的(checked)异常和不受检查的(unchecked)异常。不受检查的异常不需要在方法或者是构造函数上声明，就算方法或者是构造函数的执行可能会抛出这样的异常，并且不受检查的异常可以传播到方法或者是构造函数的外面。相反，受检查的异常必须要用throws语句在方法或者是构造函数上声明。这里有Java异常处理的一些小建议。

### **74. throw 和 throws 的区别？**

throws是用来声明一个方法可能抛出的所有异常信息，throws是将异常声明但是不处理，而是将异常往上传，谁调用我就交给谁处理。而throw则是指抛出的一个具体的异常类型。

### **75. final、finally、finalize 有什么区别？**

- final可以修饰类、变量、方法，修饰类表示该类不能被继承、修饰方法表示该方法不能被重写、修饰变量表示该变量是一个常量不能被重新赋值。
- finally一般作用在try-catch代码块中，在处理异常的时候，通常我们将一定要执行的代码方法finally代码块中，表示不管是否出现异常，该代码块都会执行，一般用来存放一些关闭资源的代码。
- finalize是一个方法，属于Object类的一个方法，而Object类是所有类的父类，该方法一般由垃圾回收器来调用，当我们调用System的gc()方法的时候，由垃圾回收器调用finalize(),回收垃圾。

### **76. try-catch-finally 中哪个部分可以省略？**

答：catch 可以省略

原因：

更为严格的说法其实是：try只适合处理运行时异常，try+catch适合处理运行时异常+普通异常。也就是说，如果你只用try去处理普通异常却不加以catch处理，编译是通不过的，因为编译器硬性规定，普通异常如果选择捕获，则必须用catch显示声明以便进一步处理。而运行时异常在编译时没有如此规定，所以catch可以省略，你加上catch编译器也觉得无可厚非。

理论上，编译器看任何代码都不顺眼，都觉得可能有潜在的问题，所以你即使对所有代码加上try，代码在运行期时也只不过是在正常运行的基础上加一层皮。但是你一旦对一段代码加上try，就等于显示地承诺编译器，对这段代码可能抛出的异常进行捕获而非向上抛出处理。如果是普通异常，编译器要求必须用catch捕获以便进一步处理；如果运行时异常，捕获然后丢弃并且+finally扫尾处理，或者加上catch捕获以便进一步处理。

至于加上finally，则是在不管有没捕获异常，都要进行的“扫尾”处理。

### **77. try-catch-finally 中，如果 catch 中 return 了，finally 还会执行吗？**

答：会执行，在 return 前执行。

```

```

执行结果：30

**代码示例2：**

```

```

执行结果：40

### **78. 常见的异常类有哪些？**

- NullPointerException：当应用程序试图访问空对象时，则抛出该异常。
- SQLException：提供关于数据库访问错误或其他错误信息的异常。
- IndexOutOfBoundsException：指示某排序索引（例如对数组、字符串或向量的排序）超出范围时抛出。
- NumberFormatException：当应用程序试图将字符串转换成一种数值类型，但该字符串不能转换为适当格式时，抛出该异常。
- FileNotFoundException：当试图打开指定路径名表示的文件失败时，抛出此异常。
- IOException：当发生某种I/O异常时，抛出此异常。此类是失败或中断的I/O操作生成的异常的通用类。
- ClassCastException：当试图将对象强制转换为不是实例的子类时，抛出该异常。
- ArrayStoreException：试图将错误类型的对象存储到一个对象数组时抛出的异常。
- IllegalArgumentException：抛出的异常表明向方法传递了一个不合法或不正确的参数。
- ArithmeticException：当出现异常的运算条件时，抛出此异常。例如，一个整数“除以零”时，抛出此类的一个实例。
- NegativeArraySizeException：如果应用程序试图创建大小为负的数组，则抛出该异常。
- NoSuchMethodException：无法找到某一特定方法时，抛出该异常。
- SecurityException：由安全管理器抛出的异常，指示存在安全侵犯。
- UnsupportedOperationException：当不支持请求的操作时，抛出该异常。
- RuntimeExceptionRuntimeException：是那些可能在Java虚拟机正常运行期间抛出的异常的超类。

## 6.IO

###  **java 中 IO 流分为几种？**

按功能来分：输入流（input）、输出流（output）。

按类型来分：字节流和字符流。

字节流和字符流的区别是：字节流按 8 位传输以字节为单位输入输出数据，字符流按 16 位传输以字符为单位输入输出数据。

### **16. BIO、NIO、AIO 有什么区别？**

- BIO：Block IO 同步阻塞式 IO，就是我们平常使用的传统 IO，它的特点是模式简单使用方便，并发处理能力低。
- NIO：New IO 同步非阻塞 IO，是传统 IO 的升级，客户端和服务器端通过 Channel（通道）通讯，实现了多路复用。
- AIO：Asynchronous IO 是 NIO 的升级，也叫 NIO2，实现了异步非堵塞 IO ，异步 IO 的操作基于事件和回调机制。

### **17. Files的常用方法都有哪些？**

- Files.exists()：检测文件路径是否存在。
- Files.createFile()：创建文件。
- Files.createDirectory()：创建文件夹。
- Files.delete()：删除一个文件或目录。
- Files.copy()：复制文件。
- Files.move()：移动文件。
- Files.size()：查看文件个数。
- Files.read()：读取文件。
- Files.write()：写入文件。

### **说出 5 条 IO 的最佳实践**

IO 对 Java 应用的性能非常重要。理想情况下，你不应该在你应用的关键路径上避免 IO 操作。下面是一些你应该遵循的 Java IO 最佳实践：

a）使用有缓冲区的 IO 类，而不要单独读取字节或字符。

b）使用 NIO 和 NIO2

c）在 finally 块中关闭流，或者使用 try-with-resource 语句。

d）使用内存映射文件获取更快的 IO。

## 7.JVM

### 什么是 JVM？

JVM（Java Virtual Machine）俗称 Java 虚拟机。之所以称为虚拟机，是因为它实际上并不存在。它提供了一种运行环境，可供Java 字节码在上面运行。

JVM 提供了以下操作：

- 加载字节码
- 验证字节码
- 执行字节码
- 提供运行时环境

JVM 定义了以下内容：

- 存储区
- 类文件格式
- 寄存器组
- 垃圾回收堆
- 致命错误报告等

我们来尝试理解一下 JVM 的内部结构，它包含了类加载器（Class Loader）、运行时数据区（Runtime Data Areas）和执行引擎（Excution Engine）。

![](C:/Work/workspaces/xyzy/hexo/source/images/java/31-2.jpg)

**1）类加载器**

类加载器是 JVM 的一个子系统，用于加载类文件。每当我们运行一个 Java 程序，它都会由类加载器首先加载。Java 中有三个内置的类加载器：

- 启动类加载器（Bootstrap Class-Loader），加载 jre/lib 包下面的 jar 文件，比如说常见的 rt.jar（包含了 Java 标准库下的所有类文件，比如说 java.lang 包下的类，java.net 包下的类，java.util 包下的类，java.io 包下的类，java.sql 包下的类）。
- 扩展类加载器（Extension or Ext Class-Loader），加载 jre/lib/ext 包下面的 jar 文件。
- 应用类加载器（Application or App Clas-Loader），根据程序的类路径（classpath）来加载 Java 类。

一般来说，Java 程序员并不需要直接同类加载器进行交互。JVM 默认的行为就已经足够满足大多数情况的需求了。不过，如果遇到了需要和类加载器进行交互的情况，而对类加载器的机制又不是很了解的话，就不得不花大量的时间去调试

ClassNotFoundException 和 NoClassDefFoundError 等异常。

对于任意一个类，都需要由它的类加载器和这个类本身一同确定其在 JVM 中的唯一性。也就是说，如果两个类的加载器不同，即使两个类来源于同一个字节码文件，那这两个类就必定不相等（比如两个类的 Class 对象不 equals）。

是不是有点晕，来来来，通过一段简单的代码了解下。

```java
public class Test {
    public static void main(String[] args) {
        ClassLoader loader = Test.class.getClassLoader;
        while (loader != ) {
            System.out.println(loader.toString);loader = loader.getParent;
        }
    }
}
```

每个Java 类都维护着一个指向定义它的类加载器的引用，通过 类名.class.getClassLoader 可以获取到此引用；然后通过 loader.getParent 可以获取类加载器的上层类加载器。

上面这段代码的输出结果如下：

```powershell
sun.misc.Launcher$AppClassLoader@18b4aac2
sun.misc.Launcher$ExtClassLoader@4617c264
```

第一行输出为 Test 的类加载器，即应用类加载器，它是 sun.misc.Launcher$AppClassLoader 类的实例；

第二行输出为扩展类加载器，是 sun.misc.Launcher$ExtClassLoader 类的实例。那启动类加载器呢？

按理说，扩展类加载器的上层类加载器是启动类加载器，但在我这个版本的 JDK 中， 扩展类加载器的 getParent 返回 。所以没有输出。

**2）运行时数据区**

运行时数据区又包含以下内容：

![](C:/Work/workspaces/xyzy/hexo/source/images/java/31-2.jpg)

- PC寄存器（PC Register），也叫程序计数器（Program Counter Register），是一块较小的内存空间，它的作用可以看做是当前线程所执行的字节码的信号指示器。
- JVM 栈（Java Virtual Machine Stack），与 PC 寄存器一样，JVM 栈也是线程私有的。每一个 JVM 线程都有自己的 JVM 栈，这个栈与线程同时创建，它的生命周期与线程相同。
- 本地方法栈（Native Method Stack），JVM 可能会使用到传统的栈来支持 Native 方法（使用 Java 语言以外的其它语言［C语言］编写的方法）的执行，这个栈就是本地方法栈。
- 堆（Heap），在 JVM 中，堆是可供各条线程共享的运行时内存区域，也是供所有类实例和数据对象分配内存的区域。
- 方法区（Method area），在 JVM 中，被加载类型的信息都保存在方法区中。包括类型信息（Type Information）和方法列表（Method Tables）。方法区是所有线程共享的，所以访问方法区信息的方法必须是线程安全的。
- 运行时常量池（Runtime Constant Pool），运行时常量池是每一个类或接口的常量池在运行时的表现形式，它包括了编译器可知的数值字面量，以及运行期解析后才能获得的方法或字段的引用。简而言之，当一个方法或者变量被引用时，JVM 通过运行时常量区来查找方法或者变量在内存里的实际地址。

**3）执行引擎**

执行引擎包含了：

- 解释器：读取字节码流，然后执行指令。因为它一条一条地解释和执行指令，所以它可以很快地解释字节码，但是执行起来会比较慢。
- 即时（Just-In-Time，JIT）编译器：即时编译器用来弥补解释器的缺点，提高性能。执行引擎首先按照解释执行的方式来执行，然后在合适的时候，即时编译器把整段字节码编译成本地代码。然后，执行引擎就没有必要再去解释执行方法了，它可以直接通过本地代码去执行。执行本地代码比一条一条进行解释执行的速度快很多。编译后的代码可以执行的很快，因为本地代码是保存在缓存里的。

### Java中垃圾回收有什么目的？什么时候进行垃圾回收？

垃圾回收是在内存中存在没有引用的对象或超过作用域的对象时进行。

垃圾回收的目的是识别并且丢弃应用不再使用的对象来释放和重用资源。

### System.gc()和Runtime.gc()会做什么事情？

这两个方法用来提示JVM要进行垃圾回收。但是，立即开始还是延迟进行垃圾回收是取决于JVM的。

### finalize()方法什么时候被调用？析构函数(finalization)的目的是什么？

垃圾回收器(garbage collector)决定回收某对象时，就会运行该对象的finalize()方法 但是在Java中很不幸，如果内存总是充足的，那么垃圾回收可能永远不会进行，也就是说filalize()可能永远不被执行，显然指望它做收尾工作是靠不住的。 那么finalize()究竟是做什么的呢？它最主要的用途是回收特殊渠道申请的内存。Java程序有垃圾回收器，所以一般情况下内存问题不用程序员操心。但有一种JNI(Java Native Interface)调用non-Java程序（C或C++），finalize()的工作就是回收这部分的内存。

### 如果对象的引用被置为null，垃圾收集器是否会立即释放对象占用的内存？

不会，在下一个垃圾回收周期中，这个对象将是可被回收的。

### Java堆的结构是什么样子的？什么是堆中的永久代(Perm Genspace)?

JVM的堆是运行时数据区，所有类的实例和数组都是在堆上分配内存。它在JVM启动的时候被创建。对象所占的堆内存是由自动内存管理系统也就是垃圾收集器回收。

堆内存是由存活和死亡的对象组成的。存活的对象是应用可以访问的，不会被垃圾回收。死亡的对象是应用不可访问尚且还没有被垃圾收集器回收掉的对象。一直到垃圾收集器把这些对象回收掉之前，他们会一直占据堆内存空间。

永久代是用于存放静态文件，如Java类、方法等。持久代对垃圾回收没有显著影响，但是有些应用可能动态生成或者调用一些class，例如Hibernate 等，在这种时候需要设置一个比较大的持久代空间来存放这些运行过程中新增的类，永久代中一般包含：

· 类的方法(字节码...)

· 类名(Sring对象)

· .class文件读到的常量信息

· class对象相关的对象列表和类型列表 (e.g., 方法对象的array).

· JVM创建的内部对象

· JIT编译器优化用的信息

### 串行(serial)收集器和吞吐量(throughput)收集器的区别是什么？

吞吐量收集器使用并行版本的新生代垃圾收集器，它用于中等规模和大规模数据的应用程序。而串行收集器对大多数的小应用(在现代处理器上需要大概100M左右的内存)就足够了。

### 在Java中，对象什么时候可以被垃圾回收？

当对象对当前使用这个对象的应用程序变得不可触及的时候，这个对象就可以被回收了。

### JVM的永久代中会发生垃圾回收么？

垃圾回收不会发生在永久代，如果永久代满了或者是超过了临界值，会触发完全垃圾回收(Full GC)。如果你仔细查看垃圾收集器的输出信息，就会发现永久代也是被回收的。这就是为什么正确的永久代大小对避免Full GC是非常重要的原因。请参考下Java8：从永久代到元数据区

(注：Java8中已经移除了永久代，新加了一个叫做元数据区的native内存区)

### JVM垃圾回收算法？

基本回收算法

\1. 引用计数（Reference Counting） 比较古老的回收算法。原理是此对象有一个引用，即增加一个计数，删除一个引用则减少一个计数。垃圾回收时，只用收集计数为0的对象。此算法最致命的是无法处理循环引用的问题。

\2. 标记-清除（Mark-Sweep） 此算法执行分两阶段。第一阶段从引用根节点开始标记所有被引用的对象，第二阶段遍历整个堆，把未标记的对象清除。此算法需要暂停整个应用，同时，会产生内存碎片。

\3. 复制（Copying） 此算法把内存空间划为两个相等的区域，每次只使用其中一个区域。垃圾回收时，遍历当前使用区域，把正在使用中的对象复制到另外一个区域中。次算法每次只处理正在使用中的对象，因此复制成本比较小，同时复制过去以后还能进行相应的内存整理，不过出现“碎片”问题。当然，此算法的缺点也是很明显的，就是需要两倍内存空间。

\4. 标记-整理（Mark-Compact） 此算法结合了 “标记-清除”和“复制”两个算法的优点。也是分两阶段，第一阶段从根节点开始标记所有被引用对象，第二阶段遍历整个堆，把清除未标记对象并且把存活对象 “压缩”到堆的其中一块，按顺序排放。此算法避免了“标记-清除”的碎片问题，同时也避免了“复制”算法的空间问题。

\5. 增量收集（Incremental Collecting） 实施垃圾回收算法，即：在应用进行的同时进行垃圾回收。。

\6. 分代（Generational Collecting） 基于对对象生命周期分析后得出的垃圾回收算法。把对象分为年青代、年老代、持久代，对不同生命周期的对象使用不同的算法（上述方式中的一个）进行回收。现在的垃圾回收器（从J2SE1.2开始）都是使用此算法的。

### **解释 Java 堆空间及 GC？**

当通过 Java 命令启动 Java 进程的时候，会为它分配内存。内存的一部分用于创建堆空间，当程序中创建对象的时候，就从对空间中分配内存。GC 是 JVM 内部的一个进程，回收无效对象的内存用于将来的分配。

![](..\..\images\java\jvm-1.jpg)



JVM 底层面试题及答案

### **41）你能保证 GC 执行吗？**

不能，虽然你可以调用 System.gc() 或者 Runtime.gc()，但是没有办法保证 GC 的执行。

### **42）怎么获取 Java 程序使用的内存？堆使用的百分比？**

可以通过 java.lang.Runtime 类中与内存相关方法来获取剩余的内存，总内存及最大堆内存。通过这些方法你也可以获取到堆使用的百分比及堆内存的剩余空间。Runtime.freeMemory() 方法返回剩余空间的字节数，Runtime.totalMemory() 方法总内存的字节数，Runtime.maxMemory() 返回最大内存的字节数。

### **43）Java 中堆和栈有什么区别？**

JVM 中堆和栈属于不同的内存区域，使用目的也不同。栈常用于保存方法帧和局部变量，而对象总是在堆上分配。栈通常都比堆小，也不会在多个线程之间共享，而堆被整个 JVM 的所有线程共享。

![](..\..\images\java\jvm-2.jpg)



## 四、反射

### **57. 什么是反射？**

反射主要是指程序可以访问、检测和修改它本身状态或行为的一种能力

Java反射：

在Java运行时环境中，对于任意一个类，能否知道这个类有哪些属性和方法？对于任意一个对象，能否调用它的任意一个方法

Java反射机制主要提供了以下功能：

- 在运行时判断任意一个对象所属的类。
- 在运行时构造任意一个类的对象。
- 在运行时判断任意一个类所具有的成员变量和方法。
- 在运行时调用任意一个对象的方法。

### **58. 什么是 java 序列#化？什么情况下需要序列化？**

简单说就是为了保存在内存中的各种对象的状态（也就是实例变量，不是方法），并且可以把保存的对象状态再读出来。虽然你可以用你自己的各种各样的方法来保存object states，但是Java给你提供一种应该比你自己好的保存对象状态的机制，那就是序列化。

什么情况下需要序列化：

a）当你想把的内存中的对象状态保存到一个文件中或者数据库中时候；

b）当你想用套接字在网络上传送对象的时候；

c）当你想通过RMI传输对象的时候；

### **59. 动态代理#是什么？有哪些应用？**

动态代理：

当想要给实现了某个接口的类中的方法，加一些额外的处理。比如说加日志，加事务等。可以给这个类创建一个代理，故名思议就是创建一个新的类，这个类不仅包含原来类方法的功能，而且还在原来的基础上添加了额外处理的新类。这个代理类并不是定义好的，是动态生成的。具有解耦意义，灵活，扩展性强。

动态代理的应用：

- Spring的AOP
- 加事务
- 加权限
- 加日志

### **60. 怎么实现动态代理？**

首先必须定义一个接口，还要有一个InvocationHandler(将实现接口的类的对象传递给它)处理类。再有一个工具类Proxy(习惯性将其称为代理类，因为调用他的newInstance()可以产生代理对象,其实他只是一个产生代理对象的工具类）。利用到InvocationHandler，拼接代理类源码，将其编译生成代理类的二进制码，利用加载器加载，并将其实例化产生代理对象，最后返回。

## 设计模式

### **你能解释一下里氏替换原则吗?**

### **107) 什么情况下会违反迪米特法则？为什么会有这个问题？**

迪米特法则建议“只和朋友说话，不要陌生人说话”，以此来减少类之间的耦合。

### **108）适配器模式是什么？什么时候使用？**

适配器模式提供对接口的转换。如果你的客户端使用某些接口，但是你有另外一些接口，你就可以写一个适配去来连接这些接口。

### **109）什么是“依赖注入”和“控制反转”？为什么有人使用？**

### **110）抽象类是什么？它与接口有什么区别？你为什么要使用过抽象类？**

### **111）构造器注入和 setter 依赖注入，那种方式更好？**

每种方式都有它的缺点和优点。构造器注入保证所有的注入都被初始化，但是 setter 注入提供更好的灵活性来设置可选依赖。如果使用 XML 来描述依赖，Setter 注入的可读写会更强。经验法则是强制依赖使用构造器注入，可选依赖使用 setter 注入。

### **112）依赖注入和工程模式之间有什么不同？**

虽然两种模式都是将对象的创建从应用的逻辑中分离，但是依赖注入比工程模式更清晰。通过依赖注入，你的类就是 POJO，它只知道依赖而不关心它们怎么获取。使用工厂模式，你的类需要通过工厂来获取依赖。因此，使用 DI 会比使用工厂模式更容易测试。关于这个话题的更详细讨论请参见答案。

### **113）适配器模式和装饰器模式有什么区别？**

虽然适配器模式和装饰器模式的结构类似，但是每种模式的出现意图不同。适配器模式被用于桥接两个接口，而装饰模式的目的是在不修改类的情况下给类增加新的功能。

### **114）适配器模式和代理模式之前有什么不同？**

这个问题与前面的类似，适配器模式和代理模式的区别在于他们的意图不同。由于适配器模式和代理模式都是封装真正执行动作的类，因此结构是一致的，但是适配器模式用于接口之间的转换，而代理模式则是增加一个额外的中间层，以便支持分配、控制或智能访问。

### **115）什么是模板方法模式？**

模板方法提供算法的框架，你可以自己去配置或定义步骤。例如，你可以将排序算法看做是一个模板。它定义了排序的步骤，但是具体的比较，可以使用 Comparable 或者其语言中类似东西，具体策略由你去配置。列出算法概要的方法就是众所周知的模板方法。

### **116）什么时候使用访问者模式？**

访问者模式用于解决在类的继承层次上增加操作，但是不直接与之关联。这种模式采用双派发的形式来增加中间层。

### **117）什么时候使用组合模式？**

组合模式使用树结构来展示部分与整体继承关系。它允许客户端采用统一的形式来对待单个对象和对象容器。当你想要展示对象这种部分与整体的继承关系时采用组合模式。

### **118）继承和组合之间有什么不同？**

虽然两种都可以实现代码复用，但是组合比继承共灵活，因为组合允许你在运行时选择不同的实现。用组合实现的代码也比继承测试起来更加简单。

### **119）描述 Java 中的重载和重写？**

重载和重写都允许你用相同的名称来实现不同的功能，但是重载是编译时活动，而重写是运行时活动。你可以在同一个类中重载方法，但是只能在子类中重写方法。重写必须要有继承。

### **120）Java 中，嵌套公共静态类与顶级类有什么不同？**

类的内部可以有多个嵌套公共静态类，但是一个 Java 源文件只能有一个顶级公共类，并且顶级公共类的名称与源文件名称必须一致。

### **121) OOP 中的 组合、聚合和关联有什么区别？**

如果两个对象彼此有关系，就说他们是彼此相关联的。组合和聚合是面向对象中的两种形式的关联。组合是一种比聚合更强力的关联。组合中，一个对象是另一个的拥有者，而聚合则是指一个对象使用另一个对象。如果对象 A 是由对象 B 组合的，则 A 不存在的话，B一定不存在，但是如果 A 对象聚合了一个对象 B，则即使 A 不存在了，B 也可以单独存在。

### **122）给我一个符合开闭原则的设计模式的例子？**

开闭原则要求你的代码对扩展开放，对修改关闭。这个意思就是说，如果你想增加一个新的功能，你可以很容易的在不改变已测试过的代码的前提下增加新的代码。有好几个设计模式是基于开闭原则的，如策略模式，如果你需要一个新的策略，只需要实现接口，增加配置，不需要改变核心逻辑。一个正在工作的例子是 Collections.sort() 方法，这就是基于策略模式，遵循开闭原则的，你不需为新的对象修改 sort() 方法，你需要做的仅仅是实现你自己的 Comparator 接口。

### **123）抽象工厂模式和原型模式之间的区别？**

### **124）什么时候使用享元模式？**

享元模式通过共享对象来避免创建太多的对象。为了使用享元模式，你需要确保你的对象是不可变的，这样你才能安全的共享。JDK 中 String 池、Integer 池以及 Long 池都是很好的使用了享元模式的例子。

**说一下你熟悉的设计模式？**

参考：常用的设计模式汇总，超详细！

**89. 简单工厂和抽象工厂有什么区别？**

**简单工厂模式：**

这个模式本身很简单而且使用在业务较简单的情况下。一般用于小项目或者具体产品很少扩展的情况（这样工厂类才不用经常更改）。

它由三种角色组成：

1. 工厂类角色：这是本模式的核心，含有一定的商业逻辑和判断逻辑，根据逻辑不同，产生具体的工厂产品。如例子中的Driver类。
2. 抽象产品角色：它一般是具体产品继承的父类或者实现的接口。由接口或者抽象类来实现。如例中的Car接口。
3. 具体产品角色：工厂类所创建的对象就是此角色的实例。在java中由一个具体类实现，如例子中的Benz、Bmw类。

来用类图来清晰的表示下的它们之间的关系：

![](..\..\images\java\design-1.jpg)



**抽象工厂模式：**

先来认识下什么是产品族： 位于不同产品等级结构中，功能相关联的产品组成的家族。



![](..\..\images\java\design-2.jpg)



图中的BmwCar和BenzCar就是两个产品树（产品层次结构）；而如图所示的BenzSportsCar和BmwSportsCar就是一个产品族。他们都可以放到跑车家族中，因此功能有所关联。同理BmwBussinessCar和BenzBusinessCar也是一个产品族。

可以这么说，它和工厂方法模式的区别就在于需要创建对象的复杂程度上。而且抽象工厂模式是三个里面最为抽象、最具一般性的。抽象工厂模式的用意为：给客户端提供一个接口，可以创建多个产品族中的产品对象。

而且使用抽象工厂模式还要满足一下条件：

系统中有多个产品族，而系统一次只可能消费其中一族产品

同属于同一个产品族的产品以其使用。

来看看抽象工厂模式的各个角色（和工厂方法的如出一辙）：

1. 抽象工厂角色： 这是工厂方法模式的核心，它与应用程序无关。是具体工厂角色必须实现的接口或者必须继承的父类。在java中它由抽象类或者接口来实现。
2. 具体工厂角色：它含有和具体业务逻辑有关的代码。由应用程序调用以创建对应的具体产品的对象。在java中它由具体的类来实现。
3. 抽象产品角色：它是具体产品继承的父类或者是实现的接口。在java中一般有抽象类或者接口来实现。
4. 具体产品角色：具体工厂角色所创建的对象就是此角色的实例。在java中由具体的类来实现。