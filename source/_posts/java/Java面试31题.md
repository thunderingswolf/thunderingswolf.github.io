---
title: Java面试题整理
date: 2020-07-09 21:48:13
tags: java

---



![](..\..\images\java\1csdn.jpg)

**第一波**

**01、请说出 Java 14 版本中更新的重要功能。**

Java 14 发布于 2020 年 3 月 17 日，更新的重要功能有：

- switch表达式；
- instanceof增强表达式，预览功能；
- 文本块，第二次预览；
- Records，预览功能。

**02、请说出 Java 13 版本中更新的重要功能。**

Java 13 发布于 2019 年 9 月 17 日，更新的重要功能有：

- 文本块，预览功能；
- switch表达式，预览功能；
- JavaSocket 重新实现；
- FileSystems.newFileSystem 方法；
- 支持Unicode 12.1；
- 可伸缩、低延迟的垃圾收集器改进，用于返回未使用的内存。

**03、请说出 Java 12 版本中更新的重要功能。**

Java 12 发布于 2019 年 3 月 19 日，更新的重要功能有：

- JVM 更新；
- File.mismatch 方法；
- 紧凑型数字格式；
- String类新增了一些方法，比如说 indent。

**04、请说出 Java 11 版本中更新的重要功能。**

Java 11 是继 Java 8 之后的第二个商用版本，如果你下载的是 Oracle JDK，则需要进行付费；如果想继续使用免费版本，需要下载 OpenJDK。

![](..\..\images\java\31-1.jpg)

Oracle JDK 中会有一些 Open JDK 没有的、商用闭源的功能。

Java 11 更新的重要功能有：

- 可以直接使用 java 命令运行 Java 程序，源代码将会隐式编译和运行。
- String类新增了一些方法，比如说 isBlank、lines、strip 等等；
- Files类新增了两个读写方法，readString 和 writeString；
- 可以在 Lambda 表达式中使用 var 作为变量类型。

**05、请说出 Java 10 版本中更新的重要功能。**

Java 10 更新的重要功能有：

- 局部变量类型推断，举个例子，var list = newArrayList;，可以使用 var 来作为变量类型，Java 编译器知道 list 的类型为字符串的 ArrayList；
- 增强 java.util.Locale；
- 提供了一组默认的根证书颁发机构（CA）。

**06、请说出 Java 9 版本中更新的重要功能。**

Java 9 更新的重要功能有：

- 模块系统；
- 不可变的 List、Set、Map 的工厂方法；
- 接口中可以有私有方法；
- 垃圾收集器改进。

**07、请说出 Java 8 版本中更新的重要功能。**

Java 8 发布于 2014 年 3 月份，可以说是 Java 6 之后最重要的版本更新，深受开发者的喜爱。

- 函数式编程和 Lambda 表达式；
- Stream 流；
- JavaDate Time API；
- 接口中可以使用默认方法和静态方法。

**08、请说出 Java 面向对象编程中的一些重要概念。**

- 抽象

- 封装

- 多态

- 继承

  ![](..\..\images\java\2csdn.jpg)

**第二波**

**09、Java 声称的平台独立性指的是什么？**

常见的操作系统有 Windows、Linux、OS-X，那么平台独立性意味着我们可以在任何操作系统中运行相同源代码的 Java 程序，比如说我们可以在 Windows 上编写 Java 程序，然后在 Linux 上运行它。

**10、什么是 JVM？**

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

![](..\..\images\java\31-2.jpg)

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

![](..\..\images\java\31-2.jpg)

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

**11、JDK 和 JVM 有什么区别？**

JDK 是 Java Development Kit 的首字母缩写，是提供给 Java 开发人员的软件环境，包含 JRE 和一组开发工具。可分为以下版本：

- 标准版（大多数开发人员用的就是这个）
- 企业版
- 微型版

JDK 包含了一个私有的 JVM 和一些其他资源，比如说编译器（javac 命令）、解释器（java 命令）等，帮助 Java 程序员完成开发工作。

![](..\..\images\java\31-4.jpg)

**12、JVM 和 JRE 有什么区别？**

Java RuntimeEnvironment（JRE）是 JVM 的实现。JRE 由 JVM 和 Java 二进制文件以及其他类组成，可以执行任何程序。JRE 不包含 Java 编译器，调试器等任何开发工具。

![](..\..\images\java\31-5.jpg)

**13、哪个类是所有类的超类？**

java.lang.Object 是所有 Java 类的超类，我们不需要继承它，因为是隐式继承的。

**14、为什么 Java 不支持多重继承？**

如果有两个类共同继承（extends）一个有特定方法的父类，那么该方法会被两个子类重写。然后，如果你决定同时继承这两个子类，那么在你调用该重写方法时，编译器不能识别你要调用哪个子类的方法。这也正是著名的菱形问题，见下图。

![](..\..\images\java\31-6.jpg)

ClassC 同时继承了 ClassA 和ClassB，ClassC 的对象在调用 ClassA 和 ClassB 中重载的方法时，就不知道该调用 ClassA 的方法，还是 ClassB 的方法。

**15、为什么 Java 不是纯粹的面向对象编程语言？**

之所以不能说 Java 是纯粹的面向对象编程语言，是因为 Java 支持基本数据类型，比如说 int、short、long、double 等，尽管它们有自己的包装器类型，但它们的确不能算是对象。

**16、path 和 classpath 之间有什么区别？**

path 是操作系统用来查找可执行文件的环境变量，我的电脑上就定义了下图这些 path 变量，比如 Java 和 Maven 的。

![](..\..\images\java\31-7.jpg)

classpath 是针对 Java 而言的，用于指定 Java 虚拟机载入的字节码文件路径。

![](..\..\images\java\3csdn.jpg)

**第三波**

17、Java 中 `main` 方法的重要性是什么？

每个程序都需要一个入口，对于 Java 程序来说，入口就是 main 方法。

```java
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

**18、Java 的重写（Override）和重载（Overload）有什么区别？**

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

![](..\..\images\java\31-8.jpg)

- 如果在一个类中有多个相同名字的方法，但参数不同，则称为方法重载。
- 父类中有一个方法，子类中有另外一个和它有相同签名（方法名相同，参数相同、修饰符相同）的方法时，则称为方法重写。子类在重写父类方法的时候可以加一个@Override 注解。

**19、`main` 方法可以重载吗？**

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

**20、一个 Java 源文件中有多个 public 类吗？**

一个 Java 源文件中不能有多个 public 类。

![](..\..\images\java\31-9.jpg)

**21、什么是 Java 的 package（包）？**

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

**22、什么是访问权限修饰符？**

访问权限修饰符对于 Java 来说，非常重要，目前共有四种：public、private、protected和 default（缺省）。

一个类只能使用 public 或者 default 修饰，public 修饰的类你之前已经见到过了，现在我来定义一个缺省权限修饰符的类给你欣赏一下。

```java
class Dog {
    
}
```

哈哈，其实也没啥可以欣赏的。缺省意味着这个类可以被同一个包下的其他类进行访问；而 public 意味着这个类可以被所有包下的类进行访问。

假如硬要通过 private 和 protected 来修饰类的话，编译器会生气的，它不同意。

![](..\..\images\java\31-10.jpg)

private 可以用来修饰类的构造方法、字段和方法，只能被当前类进行访问。protected 也可以用来修饰类的构造方法、字段和方法，但它的权限范围更宽一些，可以被同一个包中的类进行访问，或者当前类的子类。

可以通过下面这张图来对比一下四个权限修饰符之间的差别：

![](..\..\images\java\31-11.jpg)

- 同一个类中，不管是哪种权限修饰符，都可以访问；
- 同一个包下，private 修饰的无法访问；
- 子类可以访问 public 和 protected 修饰的；
- public修饰符面向世界，哈哈，可以被所有的地方访问到。

**23、什么是 final 关键字？**

final 关键字修饰类的时候，表示该类无法被继承。比如，String 类就是 final 的，无法被继承。

final 关键字修饰方法的时候，表示子类无法覆盖它。

final 关键字修饰变量的时候，表示该变量只能被赋值一次，尽管变量的状态可以更改。

**24、什么是 static 关键字？**

static 关键字可以用来修饰类变量，使其具有全局性，即所有对象将共享同一个变量。

static 关键字可以用来修饰方法，该方法称为静态方法，只可以访问类的静态变量，并且只能调用类的静态方法。

![](..\..\images\java\4csdn.jpg)

**第四波**

**25、finally 和 finalize 有什么区别？**

finally 通常与 try-catch 块一起使用，即使 try-catch 块引发了异常，finally 块中的代码也会被执行，用于释放 try 块中创建的资源。

finalize 是 Object 类的一个特殊方法，当对象正在被垃圾回收时，垃圾收集器将会调用该方法。可以重写该方法用于释放系统资源。

**26、可以将一个类声明为 static 的吗？**

不能将一个外部类声明为 static 的，但可以将一个内部类声明为 static 的——称为静态内部类。

**27、什么是静态导入？**

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

**28、什么是 try-with-resources？**

try-with-resources 是 Java 7 时引入的一个自动资源管理语句，在此之前，我们必须通过 try-catch-finally 的方式手动关闭资源，当我们忘记关闭资源的时候，就容易导致内存泄漏。

**29、什么是 multi-catch？**

Java 7 改进的另外一个地方就是 multi-catch，可以在单个 catch 中捕获多个异常，当一个 try 块抛出多个类似的异常时，这种写法更短，更清晰。

```java
catch(IOException | SQLException ex){
    logger.error(ex);
    throw new MyException(ex.getMessage);
}
```

当有多个异常的时候，可以使用管道表示符“|”隔开。

**30、什么是 static 块？**

static 块是由 Java ClassLoader 将类加载到内存中时执行的代码块。通常用于初始化类的静态变量或者创建静态资源。

**31、什么是接口？**

接口是 Java 编程语言中的一个核心概念，不仅在 JDK 源码中使用很多，还在 Java 设计模式、框架和工具中使用很多。接口提供了一种在 Java 中实现抽象的方法，用于定义子类的行为约定。

说句实在话，这 31 道 Java 核心面试题在面试的过程中还是很常见的，值得好好复习一遍。

关键是还有下一波，同样 31 道，望眼欲穿吧？