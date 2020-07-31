---
title: Java面试题
date: 2020-07-20 22:55:42
tags:java
---

# spring

## spring+mvc核心

### **1、一般问题**

#### **1.1. 不同版本的 Spring Framework 有哪些主要功能？**

VersionFeatureSpring 2.5发布于 2007 年。这是第一个支持注解的版本。Spring 3.0发布于 2009 年。它完全利用了 Java5 中的改进，并为 JEE6 提供了支持。Spring 4.0发布于 2013 年。这是第一个完全支持 JAVA8 的版本。

#### **1.2. 什么是 Spring Framework？**

- Spring 是一个开源应用框架，旨在降低应用程序开发的复杂度。
- 它是轻量级、松散耦合的。
- 它具有分层体系结构，允许用户选择组件，同时还为 J2EE 应用程序开发提供了一个有凝聚力的框架。
- 它可以集成其他框架，如 Structs、Hibernate、EJB 等，所以又称为框架的框架。

#### **1.3. 列举 Spring Framework 的优点。**

- 由于 Spring Frameworks 的分层架构，用户可以自由选择自己需要的组件。
- Spring Framework 支持 POJO(Plain Old Java Object) 编程，从而具备持续集成和可测试性。
- 由于依赖注入和控制反转，JDBC 得以简化。
- 它是开源免费的。

#### **1.4. Spring Framework 有哪些不同的功能？**

- **轻量级** - Spring 在代码量和透明度方面都很轻便。
- **IOC** - 控制反转
- **AOP** - 面向切面编程可以将应用业务逻辑和系统服务分离，以实现高内聚。
- **容器** - Spring 负责创建和管理对象（Bean）的生命周期和配置。
- **MVC** - 对 web 应用提供了高度可配置性，其他框架的集成也十分方便。
- **事务管理** - 提供了用于事务管理的通用抽象层。Spring 的事务支持也可用于容器较少的环境。
- **JDBC 异常** - Spring 的 JDBC 抽象层提供了一个异常层次结构，简化了错误处理策略。

#### **1.5. Spring Framework 中有多少个模块，它们分别是什么？**

![](C:/Work/workspaces/xyzy/hexo/source/images/spring/spring-11.jpg)



- **Spring 核心容器** – 该层基本上是 Spring Framework 的核心。它包含以下模块：
- Spring Core
- Spring Bean
- SpEL (Spring Expression Language)
- Spring Context
- **数据访问/集成** – 该层提供与数据库交互的支持。它包含以下模块：
- JDBC (Java DataBase Connectivity)
- ORM (Object Relational Mapping)
- OXM (Object XML Mappers)
- JMS (Java Messaging Service)
- Transaction
- **Web** – 该层提供了创建 Web 应用程序的支持。它包含以下模块：
- Web
- Web – Servlet
- Web – Socket
- Web – Portlet
- **AOP** – 该层支持面向切面编程
- **Instrumentation** – 该层为类检测和类加载器实现提供支持。
- **Test** – 该层为使用 JUnit 和 TestNG 进行测试提供支持。
- **几个杂项模块:**
- Messaging – 该模块为 STOMP 提供支持。它还支持注解编程模型，该模型用于从 WebSocket 客户端路由和处理 STOMP 消息。
- Aspects – 该模块为与 AspectJ 的集成提供支持。

#### **1.6. 什么是 Spring 配置文件？**

Spring 配置文件是 XML 文件。该文件主要包含类信息。它描述了这些类是如何配置以及相互引入的。但是，XML 配置文件冗长且更加干净。如果没有正确规划和编写，那么在大项目中管理变得非常困难。

#### **1.7. Spring 应用程序有哪些不同组件？**

Spring 应用一般有以下组件：

- **接口** - 定义功能。
- **Bean 类** - 它包含属性，setter 和 getter 方法，函数等。
- **Spring 面向切面编程（AOP）** - 提供面向切面编程的功能。
- **Bean 配置文件** - 包含类的信息以及如何配置它们。
- **用户程序** - 它使用接口。

#### **1.8. 使用 Spring 有哪些方式？**

使用 Spring 有以下方式：

- 作为一个成熟的 Spring Web 应用程序。
- 作为第三方 Web 框架，使用 Spring Frameworks 中间层。
- 用于远程使用。
- 作为企业级 Java Bean，它可以包装现有的 POJO（Plain Old Java Objects）。

### **2、依赖注入（Ioc）**

#### **2.1. 什么是 Spring IOC 容器？**

Spring 框架的核心是 Spring 容器。容器创建对象，将它们装配在一起，配置它们并管理它们的完整生命周期。Spring 容器使用依赖注入来管理组成应用程序的组件。容器通过读取提供的配置元数据来接收对象进行实例化，配置和组装的指令。该元数据可以通过 XML，Java 注解或 Java 代码提供。

![](C:/Work/workspaces/xyzy/hexo/source/images/spring/spring-12.jpg)



#### **2.2. 什么是依赖注入？**

在依赖注入中，您不必创建对象，但必须描述如何创建它们。您不是直接在代码中将组件和服务连接在一起，而是描述配置文件中哪些组件需要哪些服务。由 IoC 容器将它们装配在一起。

#### **2.3. 可以通过多少种方式完成依赖注入？**

通常，依赖注入可以通过三种方式完成，即：

- 构造函数注入
- setter 注入
- 接口注入

在 Spring Framework 中，仅使用构造函数和 setter 注入。

#### **2.4. 区分构造函数注入和 setter 注入。**

构造函数注入setter 注入没有部分注入有部分注入不会覆盖 setter 属性会覆盖 setter 属性任意修改都会创建一个新实例任意修改不会创建一个新实例适用于设置很多属性适用于设置少量属性

#### **2.5. spring 中有多少种 IOC 容器？**

- BeanFactory - BeanFactory 就像一个包含 bean 集合的工厂类。它会在客户端要求时实例化 bean。
- ApplicationContext - ApplicationContext 接口扩展了 BeanFactory 接口。它在 BeanFactory 基础上提供了一些额外的功能。

#### **2.6. 区分 BeanFactory 和 ApplicationContext。**

BeanFactoryApplicationContext它使用懒加载它使用即时加载它使用语法显式提供资源对象它自己创建和管理资源对象不支持国际化支持国际化不支持基于依赖的注解支持基于依赖的注解

#### **2.7. 列举 IoC 的一些好处。**

IoC 的一些好处是：

- 它将最小化应用程序中的代码量。
- 它将使您的应用程序易于测试，因为它不需要单元测试用例中的任何单例或 JNDI 查找机制。
- 它以最小的影响和最少的侵入机制促进松耦合。
- 它支持即时的实例化和延迟加载服务。

#### **2.8. Spring IoC 的实现机制。**

Spring 中的 IoC 的实现原理就是工厂模式加反射机制。

示例：

![](C:/Work/workspaces/xyzy/hexo/source/images/spring/spring-13.jpg)



### **3. Beans**

#### 3.1. 什么是 spring bean？

- 它们是构成用户应用程序主干的对象。
- Bean 由 Spring IoC 容器管理。
- 它们由 Spring IoC 容器实例化，配置，装配和管理。
- Bean 是基于用户提供给容器的配置元数据创建。

#### 3.2. spring 提供了哪些配置方式？

- 基于 xml 配置

bean 所需的依赖项和服务在 XML 格式的配置文件中指定。这些配置文件通常包含许多 bean 定义和特定于应用程序的配置选项。它们通常以 bean 标签开头。例如：

<bean id="studentbean" class="org.edureka.firstSpring.StudentBean">

<property name="name" value="Edureka"></property>

</bean>

- 基于注解配置

您可以通过在相关的类，方法或字段声明上使用注解，将 bean 配置为组件类本身，而不是使用 XML 来描述 bean 装配。默认情况下，Spring 容器中未打开注解装配。因此，您需要在使用它之前在 Spring 配置文件中启用它。例如：

<beans>

<context:annotation-config/>

<!-- bean definitions go here -->

</beans>

- 基于 Java API 配置

Spring 的 Java 配置是通过使用 @Bean 和 @Configuration 来实现。

1. @Bean 注解扮演与 <bean /> 元素相同的角色。
2. @Configuration 类允许通过简单地调用同一个类中的其他 @Bean 方法来定义 bean 间依赖关系。

例如：

@Configuration

public class StudentConfig {

@Bean

public StudentBean myStudent() {

return new StudentBean();

}

}

#### **3.3. spring 支持集中 bean scope？**

Spring bean 支持 5 种 scope：

- **Singleton** - 每个 Spring IoC 容器仅有一个单实例。
- **Prototype** - 每次请求都会产生一个新的实例。
- **Request** - 每一次 HTTP 请求都会产生一个新的实例，并且该 bean 仅在当前 HTTP 请求内有效。
- **Session** - 每一次 HTTP 请求都会产生一个新的 bean，同时该 bean 仅在当前 HTTP session 内有效。
- **Global-session** - 类似于标准的 HTTP Session 作用域，不过它仅仅在基于 portlet 的 web 应用中才有意义。Portlet 规范定义了全局 Session 的概念，它被所有构成某个 portlet web 应用的各种不同的 portlet 所共享。在 global session 作用域中定义的 bean 被限定于全局 portlet Session 的生命周期范围内。如果你在 web 中使用 global session 作用域来标识 bean，那么 web 会自动当成 session 类型来使用。

仅当用户使用支持 Web 的 ApplicationContext 时，最后三个才可用。

#### **3.4. spring bean 容器的生命周期是什么样的？**

spring bean 容器的生命周期流程如下：

1. Spring 容器根据配置中的 bean 定义中实例化 bean。
2. Spring 使用依赖注入填充所有属性，如 bean 中所定义的配置。
3. 如果 bean 实现 BeanNameAware 接口，则工厂通过传递 bean 的 ID 来调用 setBeanName()。
4. 如果 bean 实现 BeanFactoryAware 接口，工厂通过传递自身的实例来调用 setBeanFactory()。
5. 如果存在与 bean 关联的任何 BeanPostProcessors，则调用 preProcessBeforeInitialization() 方法。
6. 如果为 bean 指定了 init 方法（<bean> 的 init-method 属性），那么将调用它。
7. 最后，如果存在与 bean 关联的任何 BeanPostProcessors，则将调用 postProcessAfterInitialization() 方法。
8. 如果 bean 实现 DisposableBean 接口，当 spring 容器关闭时，会调用 destory()。
9. 如果为 bean 指定了 destroy 方法（<bean> 的 destroy-method 属性），那么将调用它。

![](C:/Work/workspaces/xyzy/hexo/source/images/spring/spring-14.jpg)



#### **3.5. 什么是 spring 的内部 bean？**

只有将 bean 用作另一个 bean 的属性时，才能将 bean 声明为内部 bean。为了定义 bean，Spring 的基于 XML 的配置元数据在 <property> 或 <constructor-arg>中提供了 <bean> 元素的使用。内部 bean 总是匿名的，它们总是作为原型。

例如，假设我们有一个 Student 类，其中引用了 Person 类。这里我们将只创建一个 Person 类实例并在 Student 中使用它。

Student.java

public class Student {

private Person person;

//Setters and Getters

}

public class Person {

private String name;

private String address;

//Setters and Getters

}

bean.xml

<bean id=“StudentBean" class="com.edureka.Student">

<property name="person">

<!--This is inner bean -->

<bean class="com.edureka.Person">

<property name="name" value=“Scott"></property>

<property name="address" value=“Bangalore"></property>

</bean>

</property>

</bean>

#### **3.6. 什么是 spring 装配**

当 bean 在 Spring 容器中组合在一起时，它被称为装配或 bean 装配。 Spring 容器需要知道需要什么 bean 以及容器应该如何使用依赖注入来将 bean 绑定在一起，同时装配 bean。

#### **3.7. 自动装配有哪些方式？**

Spring 容器能够自动装配 bean。也就是说，可以通过检查 BeanFactory 的内容让 Spring 自动解析 bean 的协作者。

自动装配的不同模式：

- **no** - 这是默认设置，表示没有自动装配。应使用显式 bean 引用进行装配。
- **byName** - 它根据 bean 的名称注入对象依赖项。它匹配并装配其属性与 XML 文件中由相同名称定义的 bean。
- **byType** - 它根据类型注入对象依赖项。如果属性的类型与 XML 文件中的一个 bean 名称匹配，则匹配并装配属性。
- **构造函数** - 它通过调用类的构造函数来注入依赖项。它有大量的参数。
- **autodetect** - 首先容器尝试通过构造函数使用 autowire 装配，如果不能，则尝试通过 byType 自动装配。

**3.8. 自动装配有什么局限？**

- 覆盖的可能性 - 您始终可以使用 <constructor-arg> 和 <property> 设置指定依赖项，这将覆盖自动装配。
- 基本元数据类型 - 简单属性（如原数据类型，字符串和类）无法自动装配。
- 令人困惑的性质 - 总是喜欢使用明确的装配，因为自动装配不太精确。

### **4、注解**

#### **4.1. 什么是基于注解的容器配置**

不使用 XML 来描述 bean 装配，开发人员通过在相关的类，方法或字段声明上使用注解将配置移动到组件类本身。它可以作为 XML 设置的替代方案。例如：

Spring 的 Java 配置是通过使用 @Bean 和 @Configuration 来实现。

- @Bean 注解扮演与
- 元素相同的角色。
- @Configuration 类允许通过简单地调用同一个类中的其他 @Bean 方法来定义 bean 间依赖关系。

例如：

@Configuration

public class StudentConfig {

@Bean

public StudentBean myStudent() {

return new StudentBean();

}

}

#### **4.2. 如何在 spring 中启动注解装配？**

默认情况下，Spring 容器中未打开注解装配。因此，要使用基于注解装配，我们必须通过配置<context：annotation-config /> 元素在 Spring 配置文件中启用它。

**4.3. @Component, @Controller, @Repository, @Service 有何区别？**

- @Component：这将 java 类标记为 bean。它是任何 Spring 管理组件的通用构造型。spring 的组件扫描机制现在可以将其拾取并将其拉入应用程序环境中。
- @Controller：这将一个类标记为 Spring Web MVC 控制器。标有它的 Bean 会自动导入到 IoC 容器中。
- @Service：此注解是组件注解的特化。它不会对 @Component 注解提供任何其他行为。您可以在服务层类中使用 @Service 而不是 @Component，因为它以更好的方式指定了意图。
- @Repository：这个注解是具有类似用途和功能的 @Component 注解的特化。它为 DAO 提供了额外的好处。它将 DAO 导入 IoC 容器，并使未经检查的异常有资格转换为 Spring DataAccessException。

#### **4.4. @Required 注解有什么用？**

@Required 应用于 bean 属性 setter 方法。此注解仅指示必须在配置时使用 bean 定义中的显式属性值或使用自动装配填充受影响的 bean 属性。如果尚未填充受影响的 bean 属性，则容器将抛出 BeanInitializationException。

示例：

public class Employee {

private String name;

@Required

public void setName(String name){

this.name=name;

}

public string getName(){

return name;

}

}

#### **4.5. @Autowired 注解有什么用？**

@Autowired 可以更准确地控制应该在何处以及如何进行自动装配。此注解用于在 setter 方法，构造函数，具有任意名称或多个参数的属性或方法上自动装配 bean。默认情况下，它是类型驱动的注入。

public class Employee {

private String name;

@Autowired

public void setName(String name) {

this.name=name;

}

public string getName(){

return name;

}

}

#### **4.6. @Qualifier 注解有什么用？**

当您创建多个相同类型的 bean 并希望仅使用属性装配其中一个 bean 时，您可以使用@Qualifier 注解和 @Autowired 通过指定应该装配哪个确切的 bean 来消除歧义。

例如，这里我们分别有两个类，Employee 和 EmpAccount。在 EmpAccount 中，使用@Qualifier 指定了必须装配 id 为 emp1 的 bean。

Employee.java

public class Employee {

private String name;

@Autowired

public void setName(String name) {

this.name=name;

}

public string getName() {

return name;

}

}

EmpAccount.java

public class EmpAccount {

private Employee emp;

@Autowired

@Qualifier(emp1)

public void showName() {

System.out.println(“Employee name : ”+emp.getName);

}

}

#### **4.7. @RequestMapping 注解有什么用？**

@RequestMapping 注解用于将特定 HTTP 请求方法映射到将处理相应请求的控制器中的特定类/方法。此注释可应用于两个级别：

- 类级别：映射请求的 URL
- 方法级别：映射 URL 以及 HTTP 请求方法

### **5、数据访问**

#### **5.1. spring DAO 有什么用？**

Spring DAO 使得 JDBC，Hibernate 或 JDO 这样的数据访问技术更容易以一种统一的方式工作。这使得用户容易在持久性技术之间切换。它还允许您在编写代码时，无需考虑捕获每种技术不同的异常。

#### **5.2. 列举 Spring DAO 抛出的异常。**

![](C:/Work/workspaces/xyzy/hexo/source/images/spring/spring-15.jpg)



#### **5.3. spring JDBC API 中存在哪些类？**

- JdbcTemplate
- SimpleJdbcTemplate
- NamedParameterJdbcTemplate
- SimpleJdbcInsert
- SimpleJdbcCall

#### **5.4. 使用 Spring 访问 Hibernate 的方法有哪些？**

我们可以通过两种方式使用 Spring 访问 Hibernate：

1. 使用 Hibernate 模板和回调进行控制反转
2. 扩展 HibernateDAOSupport 并应用 AOP 拦截器节点

#### **5.5. 列举 spring 支持的事务管理类型**

Spring 支持两种类型的事务管理：

1. 程序化事务管理：在此过程中，在编程的帮助下管理事务。它为您提供极大的灵活性，但维护起来非常困难。
2. 声明式事务管理：在此，事务管理与业务代码分离。仅使用注解或基于 XML 的配置来管理事务。

#### **5.6. spring 支持哪些 ORM 框架**

- Hibernate
- iBatis
- JPA
- JDO
- OJB

### **6、AOP**

#### **6.1. 什么是 AOP？**

AOP(Aspect-Oriented Programming), 即 **面向切面编程**, 它与 OOP( Object-Oriented Programming, 面向对象编程) 相辅相成, 提供了与 OOP 不同的抽象软件结构的视角.

在 OOP 中, 我们以类(class)作为我们的基本单元, 而 AOP 中的基本单元是 **Aspect(切面)**

#### **6.2. 什么是 Aspect？**

aspect 由 pointcount 和 advice 组成, 它既包含了横切逻辑的定义, 也包括了连接点的定义. Spring AOP 就是负责实施切面的框架, 它将切面所定义的横切逻辑编织到切面所指定的连接点中.

AOP 的工作重心在于如何将增强编织目标对象的连接点上, 这里包含两个工作:

1. 如何通过 pointcut 和 advice 定位到特定的 joinpoint 上
2. 如何在 advice 中编写切面代码.

**可以简单地认为, 使用 @Aspect 注解的类就是切面.**

![](C:/Work/workspaces/xyzy/hexo/source/images/spring/spring-16.jpg)



#### **6.3. 什么是切点（JoinPoint）**

程序运行中的一些时间点, 例如一个方法的执行, 或者是一个异常的处理.

在 Spring AOP 中, join point 总是方法的执行点。

#### **6.4. 什么是通知（Advice）？**

特定 JoinPoint 处的 Aspect 所采取的动作称为 Advice。Spring AOP 使用一个 Advice 作为拦截器，在 JoinPoint “周围”维护一系列的拦截器。

#### **6.5. 有哪些类型的通知（Advice）？**

- **Before** - 这些类型的 Advice 在 joinpoint 方法之前执行，并使用 @Before 注解标记进行配置。
- **After Returning** - 这些类型的 Advice 在连接点方法正常执行后执行，并使用@AfterReturning 注解标记进行配置。
- **After Throwing** - 这些类型的 Advice 仅在 joinpoint 方法通过抛出异常退出并使用 @AfterThrowing 注解标记配置时执行。
- **After (finally)** - 这些类型的 Advice 在连接点方法之后执行，无论方法退出是正常还是异常返回，并使用 @After 注解标记进行配置。
- **Around** - 这些类型的 Advice 在连接点之前和之后执行，并使用 @Around 注解标记进行配置。

#### **6.6. 指出在 spring aop 中 concern 和 cross-cutting concern 的不同之处。**

concern 是我们想要在应用程序的特定模块中定义的行为。它可以定义为我们想要实现的功能。

cross-cutting concern 是一个适用于整个应用的行为，这会影响整个应用程序。例如，日志记录，安全性和数据传输是应用程序几乎每个模块都需要关注的问题，因此它们是跨领域的问题。

#### **6.7. AOP 有哪些实现方式？**

实现 AOP 的技术，主要分为两大类：

- 静态代理 - 指使用 AOP 框架提供的命令进行编译，从而在编译阶段就可生成 AOP 代理类，因此也称为编译时增强；
- 编译时编织（特殊编译器实现）
- 类加载时编织（特殊的类加载器实现）。
- 动态代理 - 在运行时在内存中“临时”生成 AOP 动态代理类，因此也被称为运行时增强。
- JDK 动态代理
- CGLIB

#### **6.8. Spring AOP and AspectJ AOP 有什么区别？**

Spring AOP 基于动态代理方式实现；AspectJ 基于静态代理方式实现。

Spring AOP 仅支持方法级别的 PointCut；提供了完全的 AOP 支持，它还支持属性级别的 PointCut。

#### **6.9. 如何理解 Spring 中的代理？**

将 Advice 应用于目标对象后创建的对象称为代理。在客户端对象的情况下，目标对象和代理对象是相同的。

Advice + Target Object = Proxy

#### **6.10. 什么是编织（Weaving）？**

为了创建一个 advice 对象而链接一个 aspect 和其它应用类型或对象，称为编织（Weaving）。在 Spring AOP 中，编织在运行时执行。请参考下图：

![](C:/Work/workspaces/xyzy/hexo/source/images/spring/spring-17.jpg)



### **7、MVC**

#### **7.1. Spring MVC 框架有什么用？**

Spring Web MVC 框架提供 **模型-视图-控制器** 架构和随时可用的组件，用于开发灵活且松散耦合的 Web 应用程序。 MVC 模式有助于分离应用程序的不同方面，如输入逻辑，业务逻辑和 UI 逻辑，同时在所有这些元素之间提供松散耦合。

#### **7.2. 描述一下 DispatcherServlet 的工作流程**

DispatcherServlet 的工作流程可以用一幅图来说明：

![](C:/Work/workspaces/xyzy/hexo/source/images/spring/spring-18.jpg)



1. 向服务器发送 HTTP 请求，请求被前端控制器 DispatcherServlet 捕获。
2. DispatcherServlet 根据 **-servlet.xml** 中的配置对请求的 URL 进行解析，得到请求资源标识符（URI）。然后根据该 URI，调用 HandlerMapping 获得该 Handler 配置的所有相关的对象（包括 Handler 对象以及 Handler 对象对应的拦截器），最后以HandlerExecutionChain 对象的形式返回。
3. DispatcherServlet 根据获得的Handler，选择一个合适的HandlerAdapter。（附注：如果成功获得HandlerAdapter后，此时将开始执行拦截器的 preHandler(...)方法）。
4. 提取Request中的模型数据，填充Handler入参，开始执行Handler（Controller)。 在填充Handler的入参过程中，根据你的配置，Spring 将帮你做一些额外的工作：

- HttpMessageConveter： 将请求消息（如 Json、xml 等数据）转换成一个对象，将对象转换为指定的响应信息。
- 数据转换：对请求消息进行数据转换。如String转换成Integer、Double等。
- 数据根式化：对请求消息进行数据格式化。 如将字符串转换成格式化数字或格式化日期等。
- 数据验证： 验证数据的有效性（长度、格式等），验证结果存储到BindingResult或Error中。

1. Handler(Controller)执行完成后，向 DispatcherServlet 返回一个ModelAndView 对象；
2. 根据返回的ModelAndView，选择一个适合的 ViewResolver（必须是已经注册到 Spring 容器中的ViewResolver)返回给DispatcherServlet。
3. ViewResolver 结合Model和View，来渲染视图。
4. 视图负责将渲染结果返回给客户端。

#### **7.3. 介绍一下 WebApplicationContext**

WebApplicationContext 是 ApplicationContext 的扩展。它具有 Web 应用程序所需的一些额外功能。它与普通的 ApplicationContext 在解析主题和决定与哪个 servlet 关联的能力方面有所不同。

### 10项系列

#### 1.Spring IoC、AOP 原理

**1.1.定义**

**1.1.1.IoC**

Inversion of Control，控制反转。是面向对象编程中的一种设计原则，可以用来减低计算机代码之间的耦合度。其中最常见的方式叫做依赖注入（DependencyInjection，简称 DI），这也是 Spring 的实现方式。通过控制反转，对象在被创建的时候，由一个调控系统内所有对象的外界实体将其所依赖的对象的引用传递给它。也可以说，依赖被注入到对象中。

**1.1.2.AOP**

Aspect Oriented Programming，面向切面编程。通过预编译方式和运行期动态代理实现程序功能的统一维护的一种技术。AOP 是 OOP 的延续，是软件开发中的一个热点，也是 Spring框架中的一个重要内容，是函数式编程的一种衍生范型。利用 AOP 可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重用性，同时提高了开发的效率。其中，最常用的使用场景一般有日志模块、权限模块、事物模块。

**1.2.原理**

**1.2.1.IoC**

IoC 内部核心原理就是反射技术，当然这里面还涉及到 Bean 对象的初始化构建等步骤，这个在后面的生命周期中讲，这里我们需要了解 Java 中反射是如何做的就好。这里主要说明下主要的相关类和可能面试问题转向，具体的 API 实现需要自己去看。

![](..\..\images\spring\spring-1.jpg)



还有其他的类不一一列举出来，都在 java.lang.reflect 包下。说到这个模块的时候，那么面试官可能会考察相关的知识，主要是考察你是否真的有去了解过反射的使用。**举两个例子： **

利用反射获取实例的私有属性值怎么做

这里其实就是里面的重要考察点就是反射对私有属性的处理。

```
/**
 * 通过反射获取私有的成员变量.
 */
private Object getPrivateValue(Person person, String fieldName)
{
    try
    {
        Field field = person.getClass().getDeclaredField(fieldName);
        // 主要就是这里，需要将属性的 accessible 设置为 true 
        field.setAccessible(true);
        return field.get(person);
    }
    catch(Exception e)
    {
        e.printStackTrace();
    }
    return null;
}
```

如何通过反射构建对象实例？

使用默认构造函数（无参）创建的话：

```
Class.newInstance() Constroctor constroctor = clazz.getConstructor(String.class,Integer.class); Object obj = constroctor.newInstance("name", 18);
```

**1.2.2.AOP**

AOP 的内部原理其实就是动态代理和反射了。主要涉及到的反射类：

![](..\..\images\spring\spring-2.jpg)



动态代理相关原理的话，你需要了解什么是代理模式、静态代理的不足、动态代理的实现原理。Spring 中实现动态代理有两种方式可选，这两种动态代理的实现方式的一个对比也是面试中常问的。

**JDK 动态代理**

必须实现 InvocationHandler 接口，然后通过 Proxy.newProxyInstance(ClassLoader

loader, Class<?>[] interfaces, InvocationHandler h) 获得动态代理对象。

**CGLIB 动态代理**

使用 CGLIB 动态代理，被代理类不需要强制实现接口。CGLIB 不能对声明为 final的方法进行代理，因为 CGLIB 原理是动态生成被代理类的子类。

OK，AOP 讲了。其实讲到这里，可能会有一个延伸的面试问题。我们知道，Spring事物也是 通 过 AOP 来 实 现的 ， 我们使用的时候 一 般就是在方法上 加@Tranactional 注解，那么你有没有遇到过事物不生效的情况呢？这是为什么？这个问题我们在后面的面试题中会讲。

#### 2.Spring Bean 生命周期

![](..\..\images\spring\spring-3.jpg)



这只是个大体流程，内部的具体行为太多，需要自行去看看代码。

#### 3.Spring Bean 注入是如何解决循环依赖问题的

**3.1. 什么是循环依赖，有啥问题？**

循环依赖就是 N 个类中循环嵌套引用，这样会导致内存溢出。循环依赖主要分两种：

- 构造器循环依赖
- setter 循环依赖

**3.2. Spring 解决循环依赖问题**

- 构造器循环依赖问题

无解，直接抛出 BeanCurrentlyInCreatingException 异常。

- setter 循环依赖问题

单例模式下，通过“三级缓存”来处理。非单例模式的话，问题无解。

Spring 初始化单例对象大体是分为如下三个步骤的：

- createBeanInstance：调用构造函数创建对象
- populateBean：调用类的 setter 方法填充对象属性
- initializeBean：调用定义的 Bean 初始化 init 方法

可以看出，循环依赖主要发生在 1、2 步，当然如果发生在第一步的话，Spring 也是无法解决该问题的。那么就剩下第二步 populateBean 中出现的循环依赖问题。通过“三级缓存”来处理，三级缓存如下：

- singletonObjects：Cache of singleton objects: bean name --> bean instance，完成初始化的单例对象的 cache（一级缓存）
- earlySingletonObjects：Cache of early singleton objects: bean name--> bean instance ，完成实例化但是尚未初始化的，提前暴光的单例对象的 cache （二级缓存）
- singletonFactories ： Cache of singleton factories: bean name -->ObjectFactory，进入实例化阶段的单例对象工厂的 cache （三级缓存）

我们看下获取单例对象的方法：

```
protected Object getSingleton(String beanName, boolean allowEarlyReference)
{
    Object singletonObject = this.singletonObjects.get(beanName);
    // isSingletonCurrentlyInCreation：判断当前单例 bean 是否正在创建中 
    if(singletonObject == null && isSingletonCurrentlyInCreation(beanName))
    {
        synchronized(this.singletonObjects)
        {
            singletonObject = this.earlySingletonObjects.get(beanName);
            // allowEarlyReference：是否允许从 singletonFactories 中通过 getObject 拿到 
            对象
            if(singletonObject == null && allowEarlyReference)
            {
                ObjectFactory <? > singletonFactory = this.singletonFactories.get(beanName);
                if(singletonFactory != null)
                {
                    singletonObject = singletonFactory.getObject();
                    this.earlySingletonObjects.put(beanName, singletonObject);
                    this.singletonFactories.remove(beanName);
                }
            }
        }
    }
    return(singletonObject != NULL_OBJECT ? singletonObject : null);
}
```

其中解决循环依赖问题的关键点就在 singletonFactory.getObject() 这一步，getObject 这是 ObjectFactory<T> 接口的方法。Spring 通过对该方法的实现，在createBeanInstance 之后，populateBean 之前，通过将创建好但还没完成属性设置和初始化的对象提前曝光，然后再获取 Bean 的时候去看是否有提前曝光的对象实例来判断是否要走创建流程。

```
protected void addSingletonFactory(String beanName, ObjectFactory <? > singletonFactory)
{
    Assert.notNull(singletonFactory, "Singleton factory must not be null");
    synchronized(this.singletonObjects)
    {
        if(!this.singletonObjects.containsKey(beanName))
        {
            this.singletonFactories.put(beanName, singletonFactory);
            this.earlySingletonObjects.remove(beanName);
            this.registeredSingletons.add(beanName);
        }
    }
}
```

#### 4.Spring 事务为何失效了

可能的原因：

1. MySQL 使用的是 MyISAM 引擎，而 MyISAM 是不支持事务的。需要支持使用可以使用 InnoDB 引擎
2. 如果使用了 Spring MVC ，context:component-scan 重复扫描问题可能会引起事务失败
3. @Transactional 注解开启配置放到 DispatcherServlet 的配置里了。
4. @Transactional 注解只能应用到 public 可见度的方法上。 在其他可见类型上声明，事务会失效。
5. 在接口上使用 @Transactional 注解，只能当你设置了基于接口的代理时它才生效。所以如果强制使用了 CGLIB，那么事物会实效。
6. @Transactional 同一个类中无事务方法 a() 内部调用有事务方法 b()，那么此时事物不生效。

按 理 说 ， 如 果 按 照 Spring 说 的 事 物 传 播 级 别 去 配 置 其 事 物 级 别 为REQUIRES_NEW 的话，那么应该是在调用 b() 的时候会新生成一个事物。实际上却没有。

![](..\..\images\spring\spring-4.jpg)







NOT_SUPPORTED 总是非事务地执行，并挂起任何存在的事务其实，这是由于 Spring 的事物实现是通过 AOP 来实现的。此时，当这个有注解的方法 b() 被调用的时候，实际上是由代理类来调用的，代理类在调用之前就会启动 transaction。然而，如果这个有注解的方法是被同一个类中的其他方法 a() 调用的，那么该方法的调用并没有通过代理类，而是直接通过原来的那个 bean，所以就不会启动 transaction，我们看到的现象就是 @Transactional 注解无效。

#### 5.怎样用注解的方式配置 Spring？

Spring 在 2.5 版本以后开始支持用注解的方式来配置依赖注入。可以用注解的方式来替代XML 方式的 bean 描述，可以将 bean 描述转移到组件类的内部，只需要在相关类上、方法上或者字段声明上使用注解即可。注解注入将会被容器在 XML 注入之前被处理，所以后者会覆盖掉前者对于同一个属性的处理结果。注解装配在 Spring 中是默认关闭的。所以需要在 Spring 文件中配置一下才能使用基于注解的装配模式。如果你想要在你的应用程序中使用关于注解的方法的话，请参考如下的配置。

```
<beans>
    <context:annotation-config/>
    <!-- bean definitions go here -->
</beans>
```

在标签配置完成以后，就可以用注解的方式在 Spring 中向属性、方法和构造方法中自动装配变量。

下面是几种比较重要的注解类型：

- @Required：该注解应用于设值方法。
- @Autowired：该注解应用于有值设值方法、非设值方法、构造方法和变量。
- @Qualifier：该注解和@Autowired 注解搭配使用，用于消除特定 bean 自动装配的歧义。
- JSR-250 Annotations：Spring 支持基于 JSR-250 注解的以下注解，@Resource、@PostConstruct 和@PreDestroy。

#### 6、SpringMVC 的流程？

1. 用户发送请求至前端控制器 DispatcherServlet；
2. DispatcherServlet 收到请求后，调用 HandlerMapping 处理器映射器，请求获取Handle
3. 处理器映射器根据请求 url 找到具体的处理器，生成处理器对象及处理器拦截器(如果有则生成)一并返回给 DispatcherServlet；
4. DispatcherServlet 调用 HandlerAdapter 处理器适配器；
5. HandlerAdapter 经过适配调用 具体处理器(Handler，也叫后端控制器)；
6. Handler 执行完成返回 ModelAndView；
7. HandlerAdapter 将 Handler 执 行 结 果 ModelAndView 返 回 给DispatcherServlet ；
8. DispatcherServlet 将 ModelAndView 传 给ViewResolver 视图解析器进行解析；
9. ViewResolver 解析后返回具体View；
10. DispatcherServlet 对 View 进行渲染视图（即将模型数据填充至视图中）
11. DispatcherServlet 响应用户。

![](..\..\images\spring\spring-5.jpg)



#### 7、Springmvc 的优点:

1. 可以支持各种视图技术,而不仅仅局限于 JSP；
2. 与 Spring 框架集成（如 IoC 容器、AOP 等）；
3. 清 晰 的 角 色 分 配 ： 前 端 控 制 器 (dispatcherServlet) , 请 求 到处理器映射（handlerMapping), 处理器适配器（HandlerAdapter), 视图解析器（ViewResolver）。
4. 支持各种请求资源的映射策略。

#### 8. Spring 通知类型使用场景分别有哪些？

![](..\..\images\spring\spring-6.jpg)



#### 9.IoC 控制反转设计原理？

**具体设计原理如下图：**

![](..\..\images\spring\spring-7.jpg)



#### 10.Spring 如何处理线程并发问题？

Spring 使用 ThreadLocal 解决线程安全问题。我们知道在一般情况下，只有无状态的 Bean 才可以在多线程环境下共享，在Spring 中，绝大部分 Bean 都可以声明为 singleton 作用域。就是因为Spring 对 一 些 Bean （ 如 RequestContextHolder 、

TransactionSynchronizationManager、LocaleContextHolder 等）中非线程安全状态采用 ThreadLocal 进行处理，让它们也成为线程安全的状态，因为有状态的 Bean 就可以在多线程中共享了。

ThreadLocal 和线程同步机制都是为了解决多线程中相同变量的访问冲突问题。在同步机制中，通过对象的锁机制保证同一时间只有一个线程访问变量。这时该变量是多个线程共享的，使用同步机制要求程序慎密地分析什么时候对变量进行读写，什么时候需要锁定某个对象，什么时候释放对象锁等繁杂的问题，程序设计和编写难度相对较大。而 ThreadLocal 则从另一个角度来解决多线程的并发访问。 ThreadLocal 会为每一个线程提供一个独立的变量副本，从而隔离了多个线程对数据的访问冲突。因为每一个线程都拥有自己的变量副本，从而也就没有必要对该变量进行同步了。 ThreadLocal 提供了线程安全的共享对象，在编写多线程代码时，可以把不安全的变量封装进 ThreadLocal。

由于 ThreadLocal 中可以持有任何类型的对象，低版本 JDK 所提供的 get()返回的是 Object 对象，需要强制类型转换。但 JDK 5.0 通过泛型很好的解决了这个问题，在一定程度地简化 ThreadLocal 的使用。概括起来说，**<u>对于多线程资源共享的问题，同步机制采用了“以时间换空间”的方式，而 ThreadLocal采用了“以空间换时间”的方式。前者仅提供一份变量，让不同的线程排队访问，而后者为每一个线程都提供了一份变量，因此可以同时访问而互不影响。</u>**

### 23道系列

#### **1、什么是Spring？**

Spring是一个开源的Java EE开发框架。Spring框架的核心功能可以应用在任何Java应用程序中，但对Java EE平台上的Web应用程序有更好的扩展性。Spring框架的目标是使得Java EE应用程序的开发更加简捷，通过使用POJO为基础的编程模型促进良好的编程风格。

#### **2、Spring有哪些优点？**

轻量级：Spring在大小和透明性方面绝对属于轻量级的，基础版本的Spring框架大约只有2MB。

控制反转(IOC)：Spring使用控制反转技术实现了松耦合。依赖被注入到对象，而不是创建或寻找依赖对象。

面向切面编程(AOP)： Spring支持面向切面编程，同时把应用的业务逻辑与系统的服务分离开来。

容器：Spring包含并管理应用程序对象的配置及生命周期。

MVC框架：Spring的web框架是一个设计优良的web MVC框架，很好的取代了一些web框架。

事务管理：Spring对下至本地业务上至全局业务(JAT)提供了统一的事务管理接口。

异常处理：Spring提供一个方便的API将特定技术的异常(由JDBC, Hibernate, 或JDO抛出)转化为一致的、Unchecked异常。

#### **3、Spring 事务实现方式**

- 编程式事务管理：这意味着你可以通过编程的方式管理事务，这种方式带来了很大的灵活性，但很难维护。声明式事务管理：这种方式意味着你可以将事务管理和业务代码分离。你只需要通过注解或者XML配置管理事务。

#### **4、Spring框架的事务管理有哪些优点**

- 它为不同的事务API(如JTA, JDBC, Hibernate, JPA, 和JDO)提供了统一的编程模型。它为编程式事务管理提供了一个简单的API而非一系列复杂的事务API(如JTA).它支持声明式事务管理。它可以和Spring 的多种数据访问技术很好的融合。

#### **5、spring事务定义的传播规则**

- PROPAGATION_REQUIRED: 支持当前事务，如果当前没有事务，就新建一个事务。这是最常见的选择。PROPAGATION_SUPPORTS: 支持当前事务，如果当前没有事务，就以非事务方式执行。PROPAGATION_MANDATORY: 支持当前事务，如果当前没有事务，就抛出异常。PROPAGATION_REQUIRES_NEW: 新建事务，如果当前存在事务，把当前事务挂起。PROPAGATION_NOT_SUPPORTED: 以非事务方式执行操作，如果当前存在事务，就把当前事务挂起。PROPAGATION_NEVER: 以非事务方式执行，如果当前存在事务，则抛出异常。PROPAGATION_NESTED: 如果当前存在事务，则在嵌套事务内执行。如果当前没有事务，则进行与PROPAGATION_REQUIRED类似的操作。

#### **6、Spring 事务底层原理**

- 划分处理单元——IoC

由于spring解决的问题是对单个数据库进行局部事务处理的，具体的实现首先用spring中的IoC划分了事务处理单元。并且将对事务的各种配置放到了ioc容器中（设置事务管理器，设置事务的传播特性及隔离机制）。

- AOP拦截需要进行事务处理的类

Spring事务处理模块是通过AOP功能来实现声明式事务处理的，具体操作（比如事务实行的配置和读取，事务对象的抽象），用TransactionProxyFactoryBean接口来使用AOP功能，生成proxy代理对象，通过TransactionInterceptor完成对代理方法的拦截，将事务处理的功能编织到拦截的方法中。读取ioc容器事务配置属性，转化为spring事务处理需要的内部数据结构（TransactionAttributeSourceAdvisor），转化为TransactionAttribute表示的数据对象。

- 对事务处理实现（事务的生成、提交、回滚、挂起）

spring委托给具体的事务处理器实现。实现了一个抽象和适配。适配的具体事务处理器：DataSource数据源支持、hibernate数据源事务处理支持、JDO数据源事务处理支持，JPA、JTA数据源事务处理支持。这些支持都是通过设计PlatformTransactionManager、AbstractPlatforTransaction一系列事务处理的支持。 为常用数据源支持提供了一系列的TransactionManager。

- 结合

PlatformTransactionManager实现了TransactionInterception接口，让其与TransactionProxyFactoryBean结合起来，形成一个Spring声明式事务处理的设计体系。

#### **7、Spring MVC 运行流程**

第一步：发起请求到前端控制器(DispatcherServlet)

第二步：前端控制器请求HandlerMapping查找 Handler（ 可以根据xml配置、注解进行查找）

第三步：处理器映射器HandlerMapping向前端控制器返回Handler

第四步：前端控制器调用处理器适配器去执行Handler

第五步：处理器适配器去执行Handler

第六步：Handler执行完成给适配器返回ModelAndView

第七步：处理器适配器向前端控制器返回ModelAndView（ModelAndView是springmvc框架的一个底层对象，包括Model和view）

第八步：前端控制器请求视图解析器去进行视图解析（根据逻辑视图名解析成真正的视图(jsp)）

第九步：视图解析器向前端控制器返回View

第十步：前端控制器进行视图渲染（ 视图渲染将模型数据(在ModelAndView对象中)填充到request域）

第十一步：前端控制器向用户响应结果

#### **8、BeanFactory和ApplicationContext有什么区别？**

ApplicationContext提供了一种解决文档信息的方法，一种加载文件资源的方式(如图片)，他们可以向监听他们的beans发送消息。另外，容器或者容器中beans的操作，这些必须以bean工厂的编程方式处理的操作可以在应用上下文中以声明的方式处理。应用上下文实现了MessageSource，该接口用于获取本地消息，实际的实现是可选的。

相同点：两者都是通过xml配置文件加载bean,ApplicationContext和BeanFacotry相比,提供了更多的扩展功能。

不同点：BeanFactory是延迟加载,如果Bean的某一个属性没有注入，BeanFacotry加载后，直至第一次使用调用getBean方法才会抛出异常；而ApplicationContext则在初始化自身是检验，这样有利于检查所依赖属性是否注入；所以通常情况下我们选择使用ApplicationContext。

#### **9、什么是Spring Beans？**

Spring Beans是构成Spring应用核心的Java对象。这些对象由Spring IOC容器实例化、组装、管理。这些对象通过容器中配置的元数据创建，例如，使用XML文件中定义的创建。

在Spring中创建的beans都是单例的beans。在bean标签中有一个属性为”singleton”,如果设为true，该bean是单例的，如果设为false，该bean是原型bean。Singleton属性默认设置为true。因此，spring框架中所有的bean都默认为单例bean。

#### **10、说一下Spring中支持的bean作用域**

Spring框架支持如下五种不同的作用域：

- singleton：在Spring IOC容器中仅存在一个Bean实例，Bean以单实例的方式存在。prototype：一个bean可以定义多个实例。request：每次HTTP请求都会创建一个新的Bean。该作用域仅适用于WebApplicationContext环境。session：一个HTTP Session定义一个Bean。该作用域仅适用于WebApplicationContext环境。globalSession：同一个全局HTTP Session定义一个Bean。该作用域同样仅适用于WebApplicationContext环境。

bean默认的scope属性是"singleton"。

#### **11、Spring 的单例实现原理**

Spring框架对单例的支持是采用单例注册表的方式进行实现的，而这个注册表的缓存是HashMap对象，如果配置文件中的配置信息不要求使用单例，Spring会采用新建实例的方式返回对象实例。

#### **12、解释Spring框架中bean的生命周期**

ApplicationContext容器中，Bean的生命周期流程如上图所示，流程大致如下：

![](..\..\images\spring\spring-20.jpg)



1.首先容器启动后，会对scope为singleton且非懒加载的bean进行实例化，

2.按照Bean定义信息配置信息，注入所有的属性，

3.如果Bean实现了BeanNameAware接口，会回调该接口的setBeanName()方法，传入该Bean的id，此时该Bean就获得了自己在配置文件中的id，

4.如果Bean实现了BeanFactoryAware接口,会回调该接口的setBeanFactory()方法，传入该Bean的BeanFactory，这样该Bean就获得了自己所在的BeanFactory，

5.如果Bean实现了ApplicationContextAware接口,会回调该接口的setApplicationContext()方法，传入该Bean的ApplicationContext，这样该Bean就获得了自己所在的ApplicationContext，

6.如果有Bean实现了BeanPostProcessor接口，则会回调该接口的postProcessBeforeInitialzation()方法，

7.如果Bean实现了InitializingBean接口，则会回调该接口的afterPropertiesSet()方法，

8.如果Bean配置了init-method方法，则会执行init-method配置的方法，

9.如果有Bean实现了BeanPostProcessor接口，则会回调该接口的postProcessAfterInitialization()方法，

10.经过流程9之后，就可以正式使用该Bean了,对于scope为singleton的Bean,Spring的ioc容器中会缓存一份该bean的实例，而对于scope为prototype的Bean,每次被调用都会new一个新的对象，期生命周期就交给调用方管理了，不再是Spring容器进行管理了

11.容器关闭后，如果Bean实现了DisposableBean接口，则会回调该接口的destroy()方法，

12.如果Bean配置了destroy-method方法，则会执行destroy-method配置的方法，至此，整个Bean的生命周期结束

#### **13、Resource 是如何被查找、加载的？**

Resource 接口是 Spring 资源访问策略的抽象，它本身并不提供任何资源访问实现，具体的资源访问由该接口的实现类完成——每个实现类代表一种资源访问策略。 Spring 为 Resource 接口提供了如下实现类：

- UrlResource：访问网络资源的实现类。ClassPathResource：访问类加载路径里资源的实现类。FileSystemResource：访问文件系统里资源的实现类。ServletContextResource：访问相对于 ServletContext 路径里的资源的实现类：InputStreamResource：访问输入流资源的实现类。ByteArrayResource：访问字节数组资源的实现类。 这些 Resource 实现类，针对不同的的底层资源，提供了相应的资源访问逻辑，并提供便捷的包装，以利于客户端程序的资源访问。

#### **14、解释自动装配的各种模式？**

自动装配提供五种不同的模式供Spring容器用来自动装配beans之间的依赖注入:

no：默认的方式是不进行自动装配，通过手工设置ref 属性来进行装配bean。

byName：通过参数名自动装配，Spring容器查找beans的属性，这些beans在XML配置文件中被设置为byName。之后容器试图匹配、装配和该bean的属性具有相同名字的bean。

byType：通过参数的数据类型自动自动装配，Spring容器查找beans的属性，这些beans在XML配置文件中被设置为byType。之后容器试图匹配和装配和该bean的属性类型一样的bean。如果有多个bean符合条件，则抛出错误。

constructor：这个同byType类似，不过是应用于构造函数的参数。如果在BeanFactory中不是恰好有一个bean与构造函数参数相同类型，则抛出一个严重的错误。

autodetect：如果有默认的构造方法，通过 construct的方式自动装配，否则使用 byType的方式自动装配。

#### **15、Spring中的依赖注入是什么？**

依赖注入作为控制反转(IOC)的一个层面，可以有多种解释方式。在这个概念中，你不用创建对象而只需要描述如何创建它们。你不必通过代码直接的将组件和服务连接在一起，而是通过配置文件说明哪些组件需要什么服务。之后IOC容器负责衔接。

#### **16、有哪些不同类型的IOC(依赖注入)？**

构造器依赖注入：构造器依赖注入在容器触发构造器的时候完成，该构造器有一系列的参数，每个参数代表注入的对象。

Setter方法依赖注入：首先容器会触发一个无参构造函数或无参静态工厂方法实例化对象，之后容器调用bean中的setter方法完成Setter方法依赖注入。

#### **17、你推荐哪种依赖注入？构造器依赖注入还是Setter方法依赖注入？**

你可以同时使用两种方式的依赖注入，最好的选择是使用构造器参数实现强制依赖注入，使用setter方法实现可选的依赖关系。

#### **18、Spring IOC 如何实现**

Spring中的 org.springframework.beans 包和 org.springframework.context包构成了Spring框架IoC容器的基础。

BeanFactory 接口提供了一个先进的配置机制，使得任何类型的对象的配置成为可能。ApplicationContex接口对BeanFactory（是一个子接口）进行了扩展，在BeanFactory的基础上添加了其他功能，比如与Spring的AOP更容易集成，也提供了处理message resource的机制（用于国际化）、事件传播以及应用层的特别配置，比如针对Web应用的WebApplicationContext。

org.springframework.beans.factory.BeanFactory 是Spring IoC容器的具体实现，用来包装和管理前面提到的各种bean。BeanFactory接口是Spring IoC 容器的核心接口。

#### **19、Spring IoC容器是什么？**

Spring IOC负责创建对象、管理对象(通过依赖注入)、整合对象、配置对象以及管理这些对象的生命周期。

#### **20、IoC有什么优点？**

IOC或依赖注入减少了应用程序的代码量。它使得应用程序的测试很简单，因为在单元测试中不再需要单例或JNDI查找机制。简单的实现以及较少的干扰机制使得松耦合得以实现。IOC容器支持勤性单例及延迟加载服务。

#### **21、解释AOP模块**

AOP模块用来开发Spring应用程序中具有切面性质的部分。该模块的大部分服务由AOP Aliance提供，这就保证了Spring框架和其他AOP框架之间的互操作性。另外，该模块将元数据编程引入到了Spring。

#### **22、Spring面向切面编程(AOP)**

面向切面编程（AOP）：允许程序员模块化横向业务逻辑，或定义核心部分的功能，例如日志管理和事务管理。

切面(Aspect) ：AOP的核心就是切面，它将多个类的通用行为封装为可重用的模块。该模块含有一组API提供 cross-cutting功能。例如,日志模块称为日志的AOP切面。根据需求的不同，一个应用程序可以有若干切面。在Spring AOP中，切面通过带有@Aspect注解的类实现。

通知(Advice)：通知表示在方法执行前后需要执行的动作。实际上它是Spring AOP框架在程序执行过程中触发的一些代码。Spring切面可以执行一下五种类型的通知:

- before(前置通知)：在一个方法之前执行的通知。after(最终通知)：当某连接点退出的时候执行的通知（不论是正常返回还是异常退出）。after-returning(后置通知)：在某连接点正常完成后执行的通知。after-throwing(异常通知)：在方法抛出异常退出时执行的通知。around(环绕通知)：在方法调用前后触发的通知。

切入点(Pointcut)：切入点是一个或一组连接点，通知将在这些位置执行。可以通过表达式或匹配的方式指明切入点。

引入：引入允许我们在已有的类上添加新的方法或属性。

目标对象：被一个或者多个切面所通知的对象。它通常是一个代理对象。也被称做被通知（advised）对象。

代理：代理是将通知应用到目标对象后创建的对象。从客户端的角度看，代理对象和目标对象是一样的。有以下几种代理：

- BeanNameAutoProxyCreator：bean名称自动代理创建器DefaultAdvisorAutoProxyCreator：默认通知者自动代理创建器Metadata autoproxying：元数据自动代理

织入：将切面和其他应用类型或对象连接起来创建一个通知对象的过程。织入可以在编译、加载或运行时完成。

#### **23、Spring AOP 实现原理**

实现AOP的技术，主要分为两大类：

- 一是采用动态代理技术，利用截取消息的方式，对该消息进行装饰，以取代原有对象行为的执行；二是采用静态织入的方式，引入特定的语法创建“方面”，从而使得编译器可以在编译期间织入有关“方面”的代码。

Spring AOP 的实现原理其实很简单：AOP 框架负责动态地生成 AOP 代理类，这个代理类的方法则由 Advice和回调目标对象的方法所组成, 并将该对象可作为目标对象使用。AOP 代理包含了目标对象的全部方法，但AOP代理中的方法与目标对象的方法存在差异，AOP方法在特定切入点添加了增强处理，并回调了目标对象的方法。

Spring AOP使用动态代理技术在运行期织入增强代码。使用两种代理机制：基于JDK的动态代理（JDK本身只提供接口的代理）和基于CGlib的动态代理。

- (1) JDK的动态代理
- JDK的动态代理主要涉及java.lang.reflect包中的两个类：Proxy和InvocationHandler。其中InvocationHandler只是一个接口，可以通过实现该接口定义横切逻辑，并通过反射机制调用目标类的代码，动态的将横切逻辑与业务逻辑织在一起。而Proxy利用InvocationHandler动态创建一个符合某一接口的实例，生成目标类的代理对象。
- 其代理对象必须是某个接口的实现, 它是通过在运行期间创建一个接口的实现类来完成对目标对象的代理.只能实现接口的类生成代理,而不能针对类(2)CGLib
- CGLib采用底层的字节码技术，为一个类创建子类，并在子类中采用方法拦截的技术拦截所有父类的调用方法，并顺势织入横切逻辑.它运行期间生成的代理对象是目标类的扩展子类.所以无法通知final、private的方法,因为它们不能被覆写.是针对类实现代理,主要是为指定的类生成一个子类,覆盖其中方法.
- 在spring中默认情况下使用JDK动态代理实现AOP,如果proxy-target-class设置为true或者使用了优化策略那么会使用CGLIB来创建动态代理.Spring　AOP在这两种方式的实现上基本一样．以JDK代理为例，会使用JdkDynamicAopProxy来创建代理，在invoke()方法首先需要织入到当前类的增强器封装到拦截器链中，然后递归的调用这些拦截器完成功能的织入．最终返回代理对象．

### 源码系列30

#### 1.什么是Spring？

Spring是一个开源的Java EE开发框架。Spring框架的核心功能可以应用在任何Java应用程序中，但对Java EE平台上的Web应用程序有更好的扩展性。Spring框架的目标是使得Java EE应用程序的开发更加简捷，通过使用POJO为基础的编程模型促进良好的编程风格。

#### 2.Spring有哪些优点？

- 轻量级：Spring在大小和透明性方面绝对属于轻量级的，基础版本的Spring框架大约只有2MB。
- 控制反转(IOC)：Spring使用控制反转技术实现了松耦合。依赖被注入到对象，而不是创建或寻找依赖对象。
- 面向切面编程(AOP)： Spring支持面向切面编程，同时把应用的业务逻辑与系统的服务分离开来。
- 容器：Spring包含并管理应用程序对象的配置及生命周期。
- MVC框架：Spring的web框架是一个设计优良的web MVC框架，很好的取代了一些web框架。
- 事务管理：Spring对下至本地业务上至全局业务(JAT)提供了统一的事务管理接口。
- 异常处理：Spring提供一个方便的API将特定技术的异常(由JDBC, Hibernate, 或JDO抛出)转化为一致的、Unchecked异常。

#### 3. Spring 事务实现方式有哪些？

- 编程式事务管理：这意味着你可以通过编程的方式管理事务，这种方式带来了很大的灵活性，但很难维护。
- 声明式事务管理：这种方式意味着你可以将事务管理和业务代码分离。你只需要通过注解或者XML配置管理事务。

#### 4.Spring框架的事务管理有哪些优点？

- 它为不同的事务API(如JTA, JDBC, Hibernate, JPA, 和JDO)提供了统一的编程模型。
- 它为编程式事务管理提供了一个简单的API而非一系列复杂的事务API(如JTA). 它支持声明式事务管理。
- 它可以和Spring 的多种数据访问技术很好的融合。

#### 5.spring事务定义的传播规则

- PROPAGATION_REQUIRED: 支持当前事务，如果当前没有事务，就新建一个事务。这是最常见的选择。
- PROPAGATION_SUPPORTS: 支持当前事务，如果当前没有事务，就以非事务方式执行。
- PROPAGATION_MANDATORY: 支持当前事务，如果当前没有事务，就抛出异常。
- PROPAGATION_REQUIRES_NEW: 新建事务，如果当前存在事务，把当前事务挂起。
- PROPAGATION_NOT_SUPPORTED: 以非事务方式执行操作，如果当前存在事务，就把当前事务挂起。
- PROPAGATION_NEVER: 以非事务方式执行，如果当前存在事务，则抛出异常。
- PROPAGATION_NESTED:如果当前存在事务，则在嵌套事务内执行。如果当前没有事务，则进行与PROPAGATION_REQUIRED类似的操作。

#### 6.Spring 事务底层原理

- 划分处理单元——IoC

由于spring解决的问题是对单个数据库进行局部事务处理的，具体的实现首先用spring中的IoC划分了事务处理单元。并且将对事务的各种配置放到了ioc容器中（设置事务管理器，设置事务的传播特性及隔离机制）。

- AOP拦截需要进行事务处理的类

Spring事务处理模块是通过AOP功能来实现声明式事务处理的，具体操作（比如事务实行的配置和读取，事务对象的抽象），用TransactionProxyFactoryBean接口来使用AOP功能，生成proxy代理对象，通过TransactionInterceptor完成对代理方法的拦截，将事务处理的功能编织到拦截的方法中。读取ioc容器事务配置属性，转化为spring事务处理需要的内部数据结构（TransactionAttributeSourceAdvisor），转化为TransactionAttribute表示的数据对象。

- 对事务处理实现（事务的生成、提交、回滚、挂起）

spring委托给具体的事务处理器实现。实现了一个抽象和适配。适配的具体事务处理器：DataSource数据源支持、hibernate数据源事务处理支持、JDO数据源事务处理支持，JPA、JTA数据源事务处理支持。这些支持都是通过设计PlatformTransactionManager、AbstractPlatforTransaction一系列事务处理的支持。 为常用数据源支持提供了一系列的TransactionManager。

- 结合

PlatformTransactionManager实现了TransactionInterception接口，让其与TransactionProxyFactoryBean结合起来，形成一个Spring声明式事务处理的设计体系。

#### 7. Spring的单例实现原理

Spring框架对单例的支持是采用单例注册表的方式进行实现的，而这个注册表的缓存是HashMap对象，如果配置文件中的配置信息不要求使用单例，Spring会采用新建实例的方式返回对象实例。

#### 8. 有哪些不同类型的IOC(依赖注入)？

- 构造器依赖注入：构造器依赖注入在容器触发构造器的时候完成，该构造器有一系列的参数，每个参数代表注入的对象。
- Setter方法依赖注入：首先容器会触发一个无参构造函数或无参静态工厂方法实例化对象，之后容器调用bean中的setter方法完成Setter方法依赖注入。
- 注解注入：基于@Autowired的自动装配，默认是根据类型注入，可以用于构造器、字段、方法注入。

#### 9. 你推荐哪种依赖注入？构造器依赖注入还是Setter方法依赖注入？

你可以同时使用两种方式的依赖注入，最好的选择是使用构造器参数实现强制依赖注入，使用setter方法实现可选的依赖关系。

#### 10.简述一下Spring框架？

**概念**

- Spring致力于Java EE应用的各种解决方案，是一款轻量级框架，大大简化了Java企业级开发，提供了强大、稳定的功能。
- Spring主要有两个目标：一是让先有技术更易于使用，二是促进良好的编程习惯(或者称为最佳实践)

**优点**

- 轻量级：Spring在大小和透明性方面绝对属于轻量级的，基础版本的Spring框架大约只有2MB
- 控制反转(IOC)：Spring使用控制反转技术实现了松耦合。依赖被注入到对象，而不是创建或寻找依赖对象。
- 方便解耦，简化开发：Spring就是一个大工厂，可以将所有对象创建和依赖关系维护，交给Spring管理
- AOP编程的支持：Spring提供面向切面编程，可以方便的实现对程序进行权限拦截、运行监控等功能
- 声明式事务的支持：只需要通过配置就可以完成对事务的管理，而无需手动编程
- 方便集成各种优秀框架：Spring不排斥各种优秀的开源框架，其内部提供了对各种优秀框架（如：Struts2、Hibernate、MyBatis、Quartz等）的直接支持
- 降低JavaEE API的使用难度：Spring 对JavaEE开发中非常难用的一些API（JDBC、JavaMail、远程调用等），都提供了封装，使这些API应用难度大大降低

#### 11.简单介绍一下Spring七大模块？

- Spring Core：Core封装包是框架的最基础部分，提供IOC和依赖注入特性。这里的基础概念是BeanFactory，它提供对Factory模式的经典实现来消除对程序性单例模式的需要，并真正地允许你从程序逻辑中分离出依赖关系和配置。
- Spring Context：构建于Core封装包基础上的 Context封装包，提供了一种框架式的对象访问方法，有些象JNDI注册器。Context封装包的特性得自于Beans封装包，并添加了对国际化（I18N）的支持（例如资源绑定），事件传播，资源装载的方式和Context的透明创建，比如说通过Servlet容器。
- Spring DAO：DAO (Data Access Object)提供了JDBC的抽象层，它可消除冗长的JDBC编码和解析数据库厂商特有的错误代码。 并且，JDBC封装包还提供了一种比编程性更好的声明性事务管理方法，不仅仅是实现了特定接口，而且对所有的POJOs（plain old Java objects）都适用。
- Spring ORM：ORM 封装包提供了常用的“对象/关系”映射APIs的集成层。 其中包括JPA、JDO、Hibernate 和 iBatis 。利用ORM封装包，可以混合使用所有Spring提供的特性进行“对象/关系”映射，如前边提到的简单声明性事务管理。
- Spring AOP：Spring的 AOP 封装包提供了符合AOP Alliance规范的面向方面的编程实现，让你可以定义，例如方法拦截器（method-interceptors）和切点（pointcuts），从逻辑上讲，从而减弱代码的功能耦合，清晰的被分离开。而且，利用source-level的元数据功能，还可以将各种行为信息合并到你的代码中。
- Spring Web：Spring中的 Web 包提供了基础的针对Web开发的集成特性，例如多方文件上传，利用Servlet listeners进行IOC容器初始化和针对Web的ApplicationContext。当与WebWork或Struts一起使用Spring时，这个包使Spring可与其他框架结合。
- Spring Web MVC：Spring中的MVC封装包提供了Web应用的Model-View-Controller（MVC）实现。Spring的MVC框架并不是仅仅提供一种传统的实现，它提供了一种清晰的分离模型，在领域模型代码和Web Form之间。并且，还可以借助Spring框架的其他特性。

#### 12. Spring中的设计模式

spring中常用的设计模式达到九种，我们举例说明：

**第一种：简单工厂**

又叫做静态工厂方法（StaticFactory Method）模式，但不属于23种GOF设计模式之一。 简单工厂模式的实质是由一个工厂类根据传入的参数，动态决定应该创建哪一个产品类。 spring中的BeanFactory就是简单工厂模式的体现，根据传入一个唯一的标识来获得bean对象，但是否是在传入参数后创建还是传入参数前创建这个要根据具体情况来定。

**第二种：工厂方法（Factory Method）**

通常由应用程序直接使用new创建新的对象，为了将对象的创建和使用相分离，采用工厂模式,即应用程序将对象的创建及初始化职责交给工厂对象。一般情况下,应用程序有自己的工厂对象来创建bean.如果将应用程序自己的工厂对象交给Spring管理,那么Spring管理的就不是普通的bean,而是工厂Bean。

**第三种：单例模式（Singleton）**

保证一个类仅有一个实例，并提供一个访问它的全局访问点。
spring中的单例模式完成了后半句话，即提供了全局的访问点BeanFactory。但没有从构造器级别去控制单例，这是因为spring管理的是是任意的java对象。

**第四种：适配器（Adapter）**

在Spring的Aop中，使用的Advice（通知）来增强被代理类的功能。Spring实现这一AOP功能的原理就使用代理模式（1、JDK动态代理。2、CGLib字节码生成技术代理。）对类进行方法级别的切面增强，即，生成被代理类的代理类， 并在代理类的方法前，设置拦截器，通过执行拦截器重的内容增强了代理方法的功能，实现的面向切面编程。

**第五种：包装器（Decorator）**

在我们的项目中遇到这样一个问题：我们的项目需要连接多个数据库，而且不同的客户在每次访问中根据需要会去访问不同的数据库。我们以往在spring和hibernate框架中总是配置一个数据源，因而sessionFactory的dataSource属性总是指向这个数据源并且恒定不变，所有DAO在使用sessionFactory的时候都是通过这个数据源访问数据库。但是现在，由于项目的需要，我们的DAO在访问sessionFactory的时候都不得不在多个数据源中不断切换，问题就出现了：如何让sessionFactory在执行数据持久化的时候，根据客户的需求能够动态切换不同的数据源？我们能不能在spring的框架下通过少量修改得到解决？是否有什么设计模式可以利用呢？ 首先想到在spring的applicationContext中配置所有的dataSource。这些dataSource可能是各种不同类型的，比如不同的数据库：Oracle、SQL Server、MySQL等，也可能是不同的数据源：比如apache 提供的org.apache.commons.dbcp.BasicDataSource、spring提供的org.springframework.jndi.JndiObjectFactoryBean等。然后sessionFactory根据客户的每次请求，将dataSource属性设置成不同的数据源，以到达切换数据源的目的。
spring中用到的包装器模式在类名上有两种表现：一种是类名中含有Wrapper，另一种是类名中含有Decorator。基本上都是动态地给一个对象添加一些额外的职责。

**第六种：代理（Proxy）**

为其他对象提供一种代理以控制对这个对象的访问。 从结构上来看和Decorator模式类似，但Proxy是控制，更像是一种对功能的限制，而Decorator是增加职责。
spring的Proxy模式在aop中有体现，比如JdkDynamicAopProxy和Cglib2AopProxy。

**第七种：观察者（Observer）**

定义对象间的一种一对多的依赖关系，当一个对象的状态发生改变时，所有依赖于它的对象都得到通知并被自动更新。
spring中Observer模式常用的地方是listener的实现。如ApplicationListener。

**第八种：策略（Strategy）**

定义一系列的算法，把它们一个个封装起来，并且使它们可相互替换。本模式使得算法可独立于使用它的客户而变化。

**第九种：模板方法（Template Method）**

定义一个操作中的算法的骨架，而将一些步骤延迟到子类中。Template Method使得子类可以不改变一个算法的结构即可重定义该算法的某些特定步骤。
Template Method模式一般是需要继承的。这里想要探讨另一种对Template Method的理解。spring中的JdbcTemplate，在用这个类时并不想去继承这个类，因为这个类的方法太多，但是我们还是想用到JdbcTemplate已有的稳定的、公用的数据库连接，那么我们怎么办呢？我们可以把变化的东西抽出来作为一个参数传入JdbcTemplate的方法中。但是变化的东西是一段代码，而且这段代码会用到JdbcTemplate中的变量。怎么办？那我们就用回调对象吧。在这个回调对象中定义一个操纵JdbcTemplate中变量的方法，我们去实现这个方法，就把变化的东西集中到这里了。然后我们再传入这个回调对象到JdbcTemplate，从而完成了调用。这可能是Template Method不需要继承的另一种实现方式吧。

#### 13.ApplicationContext与BeanFactory的区别

两者都是通过xml配置文件加载bean,ApplicationContext和BeanFacotry相比,提供了更多的扩展功能，但其主要区别在于后者是延迟加载,如果Bean的某一个属性没有注入，BeanFacotry加载后，直至第一次使用调用getBean方法才会抛出异常；而ApplicationContext则在初始化自身是检验，这样有利于检查所依赖属性是否注入；所以通常情况下我们选择使用ApplicationContext。

BeanFactroy采用的是延迟加载形式来注入Bean的，即只有在使用到某个Bean时(调用getBean())，才对该Bean进行加载实例化，这样，我们就不能发现一些存在的Spring的配置问题。而ApplicationContext则相反，它是在容器启动时，一次性创建了所有的Bean。这样，在容器启动时，我们就可以发现Spring中存在的配置错误。

BeanFactory和ApplicationContext都支持BeanPostProcessor、BeanFactoryPostProcessor的使用，但两者之间的区别是：BeanFactory需要手动注册，而ApplicationContext则是自动注册

#### 14. 如何理解IoC和DI？

**IOC：**
IOC就是控制反转，通俗的说就是我们不用自己创建实例对象，这些都交给Spring的bean工厂帮我们创建管理。这也是Spring的核心思想，通过面向接口编程的方式来是实现对业务组件的动态依赖。这就意味着IOC是Spring针对解决程序耦合而存在的。在实际应用中，Spring通过配置文件（xml或者properties）指定需要实例化的java类（类名的完整字符串），包括这些java类的一组初始化值，通过加载读取配置文件，用Spring提供的方法（getBean()）就可以获取到我们想要的根据指定配置进行初始化的实例对象。

- 优点：IOC或依赖注入减少了应用程序的代码量。它使得应用程序的测试很简单，因为在单元测试中不再需要单例或JNDI查找机制。简单的实现以及较少的干扰机制使得松耦合得以实现。IOC容器支持勤性单例及延迟加载服务。

**DI：DI—Dependency** Injection，即“依赖注入”：组件之间依赖关系由容器在运行期决定，形象的说，即由容器动态的将某个依赖关系注入到组件之中。依赖注入的目的并非为软件系统带来更多功能，而是为了提升组件重用的频率，并为系统搭建一个灵活、可扩展的平台。通过依赖注入机制，我们只需要通过简单的配置，而无需任何代码就可指定目标需要的资源，完成自身的业务逻辑，而不需要关心具体的资源来自何处，由谁实现。

#### 15.介绍一下AOP相关术语？

- 切面（Aspect）：被抽取的公共模块，可能会横切多个对象。 在Spring AOP中，切面可以使用通用类（基于模式的风格） 或者在普通类中以 @AspectJ 注解来实现。
- 连接点（Join point）：指方法，在Spring AOP中，一个连接点 总是 代表一个方法的执行。
- 通知（Advice）：在切面的某个特定的连接点（Join point）上执行的动作。通知有各种类型，其中包括“around”、“before”和“after”等通知。许多AOP框架，包括Spring，都是以拦截器做通知模型， 并维护一个以连接点为中心的拦截器链。
- 切入点（Pointcut）：切入点是指 我们要对哪些Join point进行拦截的定义。通过切入点表达式，指定拦截的方法，比如指定拦截add、search。
- 引入（Introduction）：（也被称为内部类型声明（inter-type declaration））。声明额外的方法或者某个类型的字段。Spring允许引入新的接口（以及一个对应的实现）到任何被代理的对象。例如，你可以使用一个引入来使bean实现 IsModified 接口，以便简化缓存机制。
- 目标对象（Target Object）： 被一个或者多个切面（aspect）所通知（advise）的对象。也有人把它叫做 被通知（adviced） 对象。 既然Spring AOP是通过运行时代理实现的，这个对象永远是一个 被代理（proxied） 对象。
- 织入（Weaving）：指把增强应用到目标对象来创建新的代理对象的过程。Spring是在运行时完成织入。

切入点（pointcut）和连接点（join point）匹配的概念是AOP的关键，这使得AOP不同于其它仅仅提供拦截功能的旧技术。 切入点使得定位通知（advice）可独立于OO层次。 例如，一个提供声明式事务管理的around通知可以被应用到一组横跨多个对象中的方法上（例如服务层的所有业务操作）。

![](..\..\images\spring\spring-19.jpg)



#### 16.你是如何理解Spring AOP？

**概念**

面向切面编程。AOP是OOP的延续，是软件开发中的一个热点，也是Spring框架中的一个重要内容，利用AOP可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重用性，同时提高了开发的效率。

**核心思想**
可以在不修改源代码的前提下，对程序进行增强

**实现原理**
Spring框架的AOP技术底层也是采用的代理技术，所谓的动态代理就是说 AOP 框架不会去修改字节码，而是在内存中临时为方法生成一个 AOP 对象，这个 AOP 对象包含了目标对象的全部方法，并且在特定的切点做了增强处理，并回调原对象的方法 。Spring AOP 中的动态代理主要有两种方式， JDK 动态代理和 CGLIB 动态代理 。

- JDK 动态代理：通过反射来接收被代理的类，并且要求被代理的类必须实现一个接口 。JDK 动态代理的核心是 InvocationHandler 接口和 Proxy 类 。
- CGLIB动态代理： 如果目标类没有实现接口，那么 Spring AOP 会选择使用 CGLIB 来动态代理目标类 。CGLIB （ Code Generation Library ），是一个代码生成的类库，可以在运行时动态的生成某个类的子类，注意， CGLIB 是通过继承的方式做的动态代理，因此如果某个类被标记为 final ，那么它是无法使用 CGLIB 做动态代理的。

#### 17. Spring中有哪些增强处理，区别？

- 前置增强：org.springframework.aop.BeforeAdvice代表前置增强，表示在目标方法整形前实施增强
- 后置增强：org.springframework.aop.AfterReturningAdvice代表后置增强，表示在目标方法执行后实施增强
- 环绕增强：org.springframework.aop.MethodInterceptor代表环绕增强，表示在目标方法执行前后实施增强
- 异常抛出增强 ：org.springframework.aop.ThrowsAdvice代表抛出异常增强，表示在目标方法抛出异常后实施增强
- 引介增强：org.springframework.aop.IntroductionInterceptor代表引介增强，表示在目标类中添加一些新的方法和属性

#### 18. Spring中支持的Bean作用域有哪些？

支持如下五种不同的作用域

- Singleton（默认）：在Spring IOC容器中仅存在一个Bean实例，Bean以单实例的方式存在。
- Prototype：一个bean可以定义多个实例
- Request：每次HTTP请求都会创建一个新的Bean。该作用域仅适用于WebApplicationContext环境。
- Session：一个HTTP Session定义一个Bean。该作用域仅适用于WebApplicationContext环境.
- GolbalSession：同一个全局HTTP Session定义一个Bean。该作用域同样仅适用于WebApplicationContext环境.

#### 19.如何定义bean的作用域？

在Spring中创建一个bean的时候，我们可以声明它的作用域。只需要在bean定义的时候通过scope属性定义即可。例如，当Spring需要产生每次一个新的bean实例时，应该声明bean的scope属性为prototype。如果每次你希望Spring返回一个实例，应该声明bean的scope属性为singleton。

#### 20.说一说Spring框架中的bean的生命周期？

- Spring容器读取XML文件中bean的定义并实例化bean。
- Spring根据bean的定义设置属性值。
- 如果该Bean实现了BeanNameAware接口，Spring将bean的id传递给setBeanName()方法。
- 如果该Bean实现了BeanFactoryAware接口，Spring将beanfactory传递给setBeanFactory()方法。
- 如果任何bean BeanPostProcessors 和该bean相关，Spring调用postProcessBeforeInitialization()方法。
- 如果该Bean实现了InitializingBean接口，调用Bean中的afterPropertiesSet方法。如果bean有初始化函数声明，调用相应的初始化方法。
- 如果任何bean BeanPostProcessors 和该bean相关，调用postProcessAfterInitialization()方法。
- 如果该bean实现了DisposableBean，调用destroy()方法。

#### 21.哪些是最重要的bean生命周期方法，是否能重写它们？

有两个重要的bean生命周期方法。

- 第一个是setup方法，该方法在容器加载bean的时候被调用。
- 第二个是teardown方法，该方法在bean从容器中移除的时候调用。

bean标签有两个重要的属性(init-method 和 destroy-method)，你可以通过这两个属性定义自己的初始化方法和析构方法。
Spring也有相应的注解：@PostConstruct 和 @PreDestroy。

#### 22.有几种不同类型的自动代理？

BeanNameAutoProxyCreator
DefaultAdvisorAutoProxyCreator
Metadata autoproxying

#### 23. 什么是Spring的内部bean？

当一个bean仅被用作另一个bean的属性时，它能被声明为一个内部bean，为了定义inner bean，在Spring 的 基于XML的 配置元数据中，可以在 或 元素内使用 元素，内部bean通常是匿名的，它们的Scope一般是prototype。

#### 24. Spring中自动装配的方式有哪些？

- no：不进行自动装配，手动设置Bean的依赖关系。
- byName：根据Bean的名字进行自动装配。
- byType：根据Bean的类型进行自动装配。
- constructor：类似于byType，不过是应用于构造器的参数，如果正好有一个Bean与构造器的参数类型相同则可以自动装配，否则会导致错误。
- autodetect：如果有默认的构造器，则通过constructor的方式进行自动装配，否则使用byType的方式进行自动装配。

> 说明：自动装配没有自定义装配方式那么精确，而且不能自动装配简单属性（基本类型、字符串等），在使用时应注意。

#### 25.你可以在Spring中注入null或空字符串吗？

完全可以。

#### 26. 不同版本的 Spring Framework 有哪些主要功能？

VersionFeatureSpring 2.5发布于 2007 年。这是第一个支持注解的版本。Spring 3发布于 2009 年。它完全利用了 Java5 中的改进，并为 JEE6 提供了支持。Spring 4.0发布于 2013 年。这是第一个完全支持 JAVA8 的版本。。

#### 27.spring DAO 有什么用？

Spring DAO 使得 JDBC，Hibernate 或 JDO 这样的数据访问技术更容易以一种统一的方式工作。这使得用户容易在持久性技术之间切换。它还允许您在编写代码时，无需考虑捕获每种技术不同的异常。

#### 28. 列举 Spring DAO 抛出的异常。

spring-data-access-exception

#### 29. spring JDBC API 中存在哪些类？

- JdbcTemplate
- SimpleJdbcTemplate
- NamedParameterJdbcTemplate
- SimpleJdbcInsert
- SimpleJdbcCall

#### 30.Spring AOP and AspectJ AOP 有什么区别？

Spring AOP 基于动态代理方式实现；AspectJ 基于静态代理方式实现。
Spring AOP 仅支持方法级别的 PointCut；提供了完全的 AOP 支持，它还支持属性级别的 PointCut。



### 21道spring mvc

#### **1、什么是Spring MVC ？简单介绍下你对springMVC的理解?**

Spring MVC是一个基于Java的实现了MVC设计模式的请求驱动类型的轻量级Web框架，通过把Model，View，Controller分离，将web层进行职责解耦，把复杂的web应用分成逻辑清晰的几部分，简化开发，减少出错，方便组内开发人员之间的配合。

#### **2、SpringMVC的流程？**

1. 用户发送请求至前端控制器DispatcherServlet；
2. DispatcherServlet收到请求后，调用HandlerMapping处理器映射器，请求获取Handle；
3. 处理器映射器根据请求url找到具体的处理器，生成处理器对象及处理器拦截器(如果有则生成)一并返回给DispatcherServlet；
4. DispatcherServlet 调用 HandlerAdapter处理器适配器；
5. HandlerAdapter 经过适配调用 具体处理器(Handler，也叫后端控制器)；
6. Handler执行完成返回ModelAndView；
7. HandlerAdapter将Handler执行结果ModelAndView返回给DispatcherServlet；
8. DispatcherServlet将ModelAndView传给ViewResolver视图解析器进行解析；
9. ViewResolver解析后返回具体View；
10. DispatcherServlet对View进行渲染视图（即将模型数据填充至视图中）
11. DispatcherServlet响应用户。





#### **3、Springmvc的优点:**

1. 可以支持各种视图技术,而不仅仅局限于JSP；
2. 与Spring框架集成（如IoC容器、AOP等）；
3. 清晰的角色分配：前端控制器(dispatcherServlet) , 请求到处理器映射（handlerMapping), 处理器适配器（HandlerAdapter), 视图解析器（ViewResolver）。
4. 支持各种请求资源的映射策略。

#### **4、Spring MVC的主要组件？**

1. 前端控制器 DispatcherServlet（不需要程序员开发）
2. **作用** ：接收请求、响应结果，相当于转发器，有了DispatcherServlet 就减少了其它组件之间的耦合度。
3. 理器映射器HandlerMapping（不需要程序员开发）
4. **作用** ：根据请求的URL来查找Handler
5. 处理器适配器HandlerAdapter
6. **注意** ：在编写Handler的时候要按照HandlerAdapter要求的规则去编写，这样适配器HandlerAdapter才可以正确的去执行Handler。
7. 处理器Handler（需要程序员开发）
8. 视图解析器 ViewResolver（不需要程序员开发）
9. **作用** ：进行视图的解析，根据视图逻辑名解析成真正的视图（view）
10. 视图View（需要程序员开发jsp）
11. View是一个接口， 它的实现类支持不同的视图类型（jsp，freemarker，pdf等等）

#### **5、springMVC和struts2的区别有哪些?**

1. springmvc的入口是一个servlet即前端控制器（DispatchServlet），而struts2入口是一个filter过虑器（StrutsPrepareAndExecuteFilter）。
2. springmvc是基于方法开发(一个url对应一个方法)，请求参数传递到方法的形参，可以设计为单例或多例(建议单例)，struts2是基于类开发，传递参数是通过类的属性，只能设计为多例。
3. Struts采用值栈存储请求和响应的数据，通过OGNL存取数据，springmvc通过参数解析器是将request请求内容解析，并给方法形参赋值，将数据和视图封装成ModelAndView对象，最后又将ModelAndView中的模型数据通过reques域传输到页面。Jsp视图解析器默认使用jstl。

#### **6、SpringMVC怎么样设定重定向和转发的？**

1. 转发：在返回值前面加"forward:"，譬如"forward:user.do?name=method4"
2. 重定向：在返回值前面加"redirect:"，譬如"redirect:http://www.baidu.com"

#### **7、SpringMvc怎么和AJAX相互调用的？**

通过Jackson框架就可以把Java里面的对象直接转化成Js可以识别的Json对象。具体步骤如下 ：

1. 加入Jackson.jar
2. 在配置文件中配置json的映射
3. 在接受Ajax方法里面可以直接返回Object,List等,但方法前面要加上@ResponseBody注解。





#### **8、如何解决POST请求中文乱码问题，GET的又如何处理呢？**

1. 解决post请求乱码问题：
2. 在web.xml中配置一个CharacterEncodingFilter过滤器，设置成utf-8；

```
<filter>
<filter-name>CharacterEncodingFilter</filter-name>
<filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
<init-param>
<param-name>encoding</param-name>
<param-value>utf-8</param-value>
</init-param>
</filter>
<filter-mapping>
<filter-name>CharacterEncodingFilter</filter-name>
<url-pattern>
/*</url-pattern>
</filter-mapping>
```

1. get请求中文参数出现乱码解决方法有两个：

- 修改tomcat配置文件添加编码与工程编码一致，如下：

```
<ConnectorURIEncoding="utf-8" connectionTimeout="20000" port="8080" protocol="HTTP/1.1" redirectPort="8443"/>
```

- 另外一种方法对参数进行重新编码：

```
String userName = new String(request.getParamter("userName").getBytes("ISO8859-1"),"utf-8")
```

ISO8859-1是tomcat默认编码，需要将tomcat编码后的内容按utf-8编码。

#### **9、Spring MVC的异常处理 ？**

答：可以将异常抛给Spring框架，由Spring框架来处理；我们只需要配置简单的异常处理器，在异常处理器中添视图页面即可。

#### **10、SpringMvc的控制器是不是单例模式,如果是,有什么问题,怎么解决？**

答：是单例模式,所以在多线程访问的时候有线程安全问题,不要用同步,会影响性能的,解决方案是在控制器里面不能写字段。

#### **11、 SpringMVC常用的注解有哪些？**

- @RequestMapping：用于处理请求 url 映射的注解，可用于类或方法上。用于类上，则表示类中的所有响应请求的方法都是以该地址作为父路径。
- @RequestBody：注解实现接收http请求的json数据，将json转换为java对象。
- @ResponseBody：注解实现将conreoller方法返回对象转化为json对象响应给客户。

#### **12、SpingMvc中的控制器的注解一般用那个,有没有别的注解可以替代？**

答：一般用@Conntroller注解,表示是表现层,不能用别的注解代替。

#### **13、如果在拦截请求中，我想拦截get方式提交的方法,怎么配置？**

答：可以在@RequestMapping注解里面加上method=RequestMethod.GET。

#### **14、怎样在方法里面得到Request,或者Session？**

答：直接在方法的形参中声明request,SpringMvc就自动把request对象传入。

#### **15、如果想在拦截的方法里面得到从前台传入的参数,怎么得到？**

答：直接在形参里面声明这个参数就可以,但必须名字和传过来的参数一样。

#### **16、如果前台有很多个参数传入,并且这些参数都是一个对象的,那么怎么样快速得到这个对象？**

答：直接在方法中声明这个对象,SpringMvc就自动会把属性赋值到这个对象里面。

#### **17、SpringMvc中函数的返回值是什么？**

答：返回值可以有很多类型,有String, ModelAndView。ModelAndView类把视图和数据都合并的一起的，但一般用String比较好。

#### **18、SpringMvc用什么对象从后台向前台传递数据的？**

答：通过ModelMap对象,可以在这个对象里面调用put方法,把对象加到里面,前台就可以通过el表达式拿到。

#### **19、怎么样把ModelMap里面的数据放入Session里面？**

答：可以在类上面加上@SessionAttributes注解,里面包含的字符串就是要放入session里面的key。

#### **20、SpringMvc里面拦截器是怎么写的：**

有两种写法,一种是实现HandlerInterceptor接口，另外一种是继承适配器类，接着在接口方法当中，实现处理逻辑；然后在SpringMvc的配置文件中配置拦截器即可：

```
<!-- 配置SpringMvc的拦截器 -->
<mvc:interceptors>
<!-- 配置一个拦截器的Bean就可以了 默认是对所有请求都拦截 -->
<bean id="myInterceptor" class="com.zwp.action.MyHandlerInterceptor"></bean>
<!-- 只针对部分请求拦截 -->
<mvc:interceptor>
<mvc:mapping path="/modelMap.do" />
<bean class="com.zwp.action.MyHandlerInterceptorAdapter" />
</mvc:interceptor>
</mvc:interceptors>
```

#### **21、注解原理：**

注解本质是一个继承了Annotation的特殊接口，其具体实现类是Java运行时生成的动态代理类。我们通过反射获取注解时，返回的是Java运行时生成的动态代理对象。通过代理对象调用自定义注解的方法，会最终调用AnnotationInvocationHandler的invoke方法。该方法会从memberValues这个Map中索引出对应的值。而memberValues的来源是Java常量池。

## spring boot

### 概述

#### 什么是 Spring Boot？

Spring Boot 是 Spring 开源组织下的子项目，是 Spring 组件一站式解决方案，主要是简化了使用 Spring 的难度，简省了繁重的配置，提供了各种启动器，开发者能快速上手。

#### Spring Boot 有哪些优点？

##### Spring Boot 主要有如下优点：

1. 容易上手，提升开发效率，为 Spring 开发提供一个更快、更广泛的入门体验。
2. 开箱即用，远离繁琐的配置。
3. 提供了一系列大型项目通用的非业务性功能，例如：内嵌服务器、安全管理、运行数据监控、运行状况检查和外部化配置等。
4. 没有代码生成，也不需要XML配置。
5. 避免大量的 Maven 导入和各种版本冲突。

**Spring Boot 的核心注解是哪个？它主要由哪几个注解组成的？**

启动类上面的注解是@SpringBootApplication，它也是 Spring Boot 的核心注解，主要组合包含了以下 3 个注解：

启动类上面的注解是@SpringBootApplication，它也是 Spring Boot 的核心注解，主要组合包含了以下 3 个注解：

@SpringBootConfiguration：组合了 @Configuration 注解，实现配置文件的功能。

@EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置功能：@SpringBootApplication(exclude{DataSourceAutoConfiguration.class})

@ComponentScan：Spring组件扫描。

### 配置

#### 什么是 JavaConfig？

Spring JavaConfig 是 Spring 社区的产品，它提供了配置 Spring IoC 容器的纯Java 方法。因此它有助于避免使用 XML 配置。使用 JavaConfig 的优点在于：

（1）面向对象的配置。由于配置被定义为 JavaConfig 中的类，因此用户可以充分利用 Java 中的面向对象功能。一个配置类可以继承另一个，重写它的@Bean 方法等。

（2）减少或消除 XML 配置。基于依赖注入原则的外化配置的好处已被证明。但是，许多开发人员不希望在 XML 和 Java 之间来回切换。JavaConfig 为开发人员提供了一种纯 Java 方法来配置与 XML 配置概念相似的 Spring 容器。从技术角度来讲，只使用 JavaConfig 配置类来配置容器是可行的，但实际上很多人认为将JavaConfig 与 XML 混合匹配是理想的。

（3）类型安全和重构友好。JavaConfig 提供了一种类型安全的方法来配置 Spring容器。由于 Java 5.0 对泛型的支持，现在可以按类型而不是按名称检索 bean，不需要任何强制转换或基于字符串的查找。

#### Spring Boot 自动配置原理是什么？

注解 @EnableAutoConfiguration, @Configuration, @ConditionalOnClass 就是自动配置的核心，

@EnableAutoConfiguration 给容器导入META-INF/spring.factories 里定义的自动配置类。

筛选有效的自动配置类。

每一个自动配置类结合对应的 xxxProperties.java 读取配置文件进行自动配置功能

#### 你如何理解 Spring Boot 配置加载顺序？

在 Spring Boot 里面，可以使用以下几种方式来加载配置。

1）properties文件；

2）YAML文件；

3）系统环境变量；

4）命令行参数；

等等……

#### 什么是 YAML？

YAML 是一种人类可读的数据序列化语言。它通常用于配置文件。与属性文件相比，如果我们想要在配置文件中添加复杂的属性，YAML 文件就更加结构化，而且更少混淆。可以看出 YAML 具有分层配置数据。

**YAML 配置的优势在哪里 ?**

YAML 现在可以算是非常流行的一种配置文件格式了，无论是前端还是后端，都可以见到 YAML 配置。那么 YAML 配置和传统的 properties 配置相比到底有哪些优势呢？

1. 配置有序，在一些特殊的场景下，配置有序很关键
2. 支持数组，数组中的元素可以是基本数据类型也可以是对象
3. 简洁

相比 properties 配置文件，YAML 还有一个缺点，就是不支持@PropertySource 注解导入自定义的 YAML 配置。

#### Spring Boot 是否可以使用 XML 配置 ?

Spring Boot 推荐使用 Java 配置而非 XML 配置，但是 Spring Boot 中也可以使用 XML 配置，通过 @ImportResource 注解可以引入一个 XML 配置。

#### spring boot 核心配置文件是什么？bootstrap.properties 和 application.properties 有何区别 ?

单纯做 Spring Boot 开发，可能不太容易遇到 bootstrap.properties 配置文件，但是在结合 Spring Cloud 时，这个配置就会经常遇到了，特别是在需要加载一些远程配置文件的时侯。

spring boot 核心的两个配置文件：

- bootstrap (. yml 或者 . properties)：boostrap 由父 ApplicationContext 加载的，比 applicaton 优先加载，配置在应用程序上下文的引导阶段生效。一般来说我们在 Spring Cloud Config 或者 Nacos 中会用到它。且 boostrap 里面的属性不能被覆盖；
- application (. yml 或者 . properties)：由ApplicatonContext 加载，用于 spring boot 项目的自动化配置。

#### 什么是 Spring Profiles？

Spring Profiles 允许用户根据配置文件（dev，test，prod 等）来注册 bean。因此，当应用程序在开发中运行时，只有某些 bean 可以加载，而在 PRODUCTION中，某些其他 bean 可以加载。假设我们的要求是 Swagger 文档仅适用于 QA 环境，并且禁用所有其他文档。这可以使用配置文件来完成。Spring Boot 使得使用配置文件非常简单。

#### 如何在自定义端口上运行 Spring Boot 应用程序？

为了在自定义端口上运行 Spring Boot 应用程序，您可以在application.properties 中指定端口。server.port = 8090

### 安全

#### 如何实现 Spring Boot 应用程序的安全性？

为了实现 Spring Boot 的安全性，我们使用 spring-boot-starter-security 依赖项，并且必须添加安全配置。它只需要很少的代码。配置类将必须扩展WebSecurityConfigurerAdapter 并覆盖其方法。

#### 比较一下 Spring Security 和 Shiro 各自的优缺点 ?

由于 Spring Boot 官方提供了大量的非常方便的开箱即用的 Starter ，包括 Spring Security 的 Starter ，使得在 Spring Boot 中使用 Spring Security 变得更加容易，甚至只需要添加一个依赖就可以保护所有的接口，所以，如果是 Spring Boot 项目，一般选择 Spring Security 。当然这只是一个建议的组合，单纯从技术上来说，无论怎么组合，都是没有问题的。Shiro 和 Spring Security 相比，主要有如下一些特点：

1. Spring Security 是一个重量级的安全管理框架；Shiro 则是一个轻量级的安全管理框架
2. Spring Security 概念复杂，配置繁琐；Shiro 概念简单、配置简单
3. Spring Security 功能强大；Shiro 功能简单

**Spring Boot 中如何解决跨域问题 ?**

跨域可以在前端通过 JSONP 来解决，但是 JSONP 只可以发送 GET 请求，无法发送其他类型的请求，在 RESTful 风格的应用中，就显得非常鸡肋，因此我们推荐在后端通过 （CORS，Cross-origin resource sharing） 来解决跨域问题。这种解决方案并非 Spring Boot 特有的，在传统的 SSM 框架中，就可以通过 CORS 来解决跨域问题，只不过之前我们是在 XML 文件中配置 CORS ，现在可以通过实现WebMvcConfigurer接口然后重写addCorsMappings方法解决跨域问题。

> @Configuration
>
> public class CorsConfig implements WebMvcConfigurer {
>
> @Override
>
> public void addCorsMappings(CorsRegistry registry) {
>
> registry.addMapping("/**")
>
> .allowedOrigins("*")
>
> .allowCredentials(true)
>
> .allowedMethods("GET", "POST", "PUT", "DELETE", "OPTIONS")
>
> .maxAge(3600);
>
> }
>
> }

项目中前后端分离部署，所以需要解决跨域的问题。

我们使用cookie存放用户登录的信息，在spring拦截器进行权限控制，当权限不符合时，直接返回给用户固定的json结果。

当用户登录以后，正常使用；当用户退出登录状态时或者token过期时，由于拦截器和跨域的顺序有问题，出现了跨域的现象。

我们知道一个http请求，先走filter，到达servlet后才进行拦截器的处理，如果我们把cors放在filter里，就可以优先于权限拦截器执行。

> @Configuration
>
> public class CorsConfig {
>
> @Bean
>
> public CorsFilter corsFilter() {
>
> CorsConfiguration corsConfiguration = new CorsConfiguration();
>
> corsConfiguration.addAllowedOrigin("*");
>
> corsConfiguration.addAllowedHeader("*");
>
> corsConfiguration.addAllowedMethod("*");
>
> corsConfiguration.setAllowCredentials(true);
>
> UrlBasedCorsConfigurationSource urlBasedCorsConfigurationSource = new UrlBasedCorsConfigurationSource();
>
> urlBasedCorsConfigurationSource.registerCorsConfiguration("/**", corsConfiguration);
>
> return new CorsFilter(urlBasedCorsConfigurationSource);
>
> }
>
> }

#### 什么是 CSRF 攻击？

CSRF 代表跨站请求伪造。这是一种攻击，迫使最终用户在当前通过身份验证的Web 应用程序上执行不需要的操作。CSRF 攻击专门针对状态改变请求，而不是数据窃取，因为攻击者无法查看对伪造请求的响应。

### 监视器

#### Spring Boot 中的监视器是什么？

Spring boot actuator 是 spring 启动框架中的重要功能之一。Spring boot 监视器可帮助您访问生产环境中正在运行的应用程序的当前状态。有几个指标必须在生产环境中进行检查和监控。即使一些外部应用程序可能正在使用这些服务来向相关人员触发警报消息。监视器模块公开了一组可直接作为 HTTP URL 访问的REST 端点来检查状态。

**如何在 Spring Boot 中禁用 Actuator 端点安全性？**

默认情况下，所有敏感的 HTTP 端点都是安全的，只有具有 ACTUATOR 角色的用户才能访问它们。安全性是使用标准的 HttpServletRequest.isUserInRole 方法实施的。我们可以使用来禁用安全性。只有在执行机构端点在防火墙后访问时，才建议禁用安全性。

**我们如何监视所有 Spring Boot 微服务？**

Spring Boot 提供监视器端点以监控各个微服务的度量。这些端点对于获取有关应用程序的信息（如它们是否已启动）以及它们的组件（如数据库等）是否正常运行很有帮助。但是，使用监视器的一个主要缺点或困难是，我们必须单独打开应用程序的知识点以了解其状态或健康状况。想象一下涉及 50 个应用程序的微服务，管理员将不得不击中所有 50 个应用程序的执行终端。为了帮助我们处理这种情况，我们将使用位于的开源项目。它建立在 Spring Boot Actuator 之上，它提供了一个 Web UI，使我们能够可视化多个应用程序的度量。

**整合第三方项目**

**什么是 WebSockets？**

WebSocket 是一种计算机通信协议，通过单个 TCP 连接提供全双工通信信道。

1、WebSocket 是双向的 -使用 WebSocket 客户端或服务器可以发起消息发送。

2、WebSocket 是全双工的 -客户端和服务器通信是相互独立的。

3、单个 TCP 连接 -初始连接使用 HTTP，然后将此连接升级到基于套接字的连接。然后这个单一连接用于所有未来的通信

4、Light -与 http 相比，WebSocket 消息数据交换要轻得多。

### 什么是 Spring Data ?

Spring Data 是 Spring 的一个子项目。用于简化数据库访问，支持NoSQL 和 关系数据存储。其主要目标是使数据库的访问变得方便快捷。Spring Data 具有如下特点：

SpringData 项目支持 NoSQL 存储：

1. MongoDB （文档数据库）
2. Neo4j（图形数据库）
3. Redis（键/值存储）
4. Hbase（列族数据库）

SpringData 项目所支持的关系数据存储技术：

1. JDBC
2. JPA

Spring Data Jpa 致力于减少数据访问层 (DAO) 的开发量. 开发者唯一要做的，就是声明持久层的接口，其他都交给 Spring Data JPA 来帮你完成！Spring Data JPA 通过规范方法的名字，根据符合规范的名字来确定方法需要实现什么样的逻辑。

**什么是 Spring Batch？**

Spring Boot Batch 提供可重用的函数，这些函数在处理大量记录时非常重要，包括日志/跟踪，事务管理，作业处理统计信息，作业重新启动，跳过和资源管理。它还提供了更先进的技术服务和功能，通过优化和分区技术，可以实现极高批量和高性能批处理作业。简单以及复杂的大批量批处理作业可以高度可扩展的方式利用框架处理重要大量的信息。

**什么是 FreeMarker 模板？**

FreeMarker 是一个基于 Java 的模板引擎，最初专注于使用 MVC 软件架构进行动态网页生成。使用 Freemarker 的主要优点是表示层和业务层的完全分离。程序员可以处理应用程序代码，而设计人员可以处理 html 页面设计。最后使用freemarker 可以将这些结合起来，给出最终的输出页面。

### 如何集成 Spring Boot 和 ActiveMQ？

对于集成 Spring Boot 和 ActiveMQ，我们使用依赖关系。它只需要很少的配置，并且不需要样板代码。

### 什么是 Apache Kafka？

Apache Kafka 是一个分布式发布 - 订阅消息系统。它是一个可扩展的，容错的发布 - 订阅消息系统，它使我们能够构建分布式应用程序。这是一个 Apache 顶级项目。Kafka 适合离线和在线消息消费。

**什么是 Swagger？你用 Spring Boot 实现了它吗？**

Swagger 广泛用于可视化 API，使用 Swagger UI 为前端开发人员提供在线沙箱。Swagger 是用于生成 RESTful Web 服务的可视化表示的工具，规范和完整框架实现。它使文档能够以与服务器相同的速度更新。当通过 Swagger 正确定义时，消费者可以使用最少量的实现逻辑来理解远程服务并与其进行交互。因此，Swagger消除了调用服务时的猜测。

**前后端分离，如何维护接口文档 ?**

前后端分离开发日益流行，大部分情况下，我们都是通过 Spring Boot 做前后端分离开发，前后端分离一定会有接口文档，不然会前后端会深深陷入到扯皮中。一个比较笨的方法就是使用 word 或者 md 来维护接口文档，但是效率太低，接口一变，所有人手上的文档都得变。在 Spring Boot 中，这个问题常见的解决方案是 Swagger ，使用 Swagger 我们可以快速生成一个接口文档网站，接口一旦发生变化，文档就会自动更新，所有开发工程师访问这一个在线网站就可以获取到最新的接口文档，非常方便。

### 其他

#### 如何重新加载 Spring Boot 上的更改，而无需重新启动服务器？Spring Boot项目如何热部署？

这可以使用 DEV 工具来实现。通过这种依赖关系，您可以节省任何更改，嵌入式tomcat 将重新启动。Spring Boot 有一个开发工具（DevTools）模块，它有助于提高开发人员的生产力。Java 开发人员面临的一个主要挑战是将文件更改自动部署到服务器并自动重启服务器。开发人员可以重新加载 Spring Boot 上的更改，而无需重新启动服务器。这将消除每次手动部署更改的需要。Spring Boot 在发布它的第一个版本时没有这个功能。这是开发人员最需要的功能。DevTools 模块完全满足开发人员的需求。该模块将在生产环境中被禁用。它还提供 H2 数据库控制台以更好地测试应用程序。

> <dependency>
>
> <groupId>org.springframework.boot</groupId>
>
> <artifactId>spring-boot-devtools</artifactId>
>
> </dependency>

#### 您使用了哪些 starter maven 依赖项？

使用了下面的一些依赖项

spring-boot-starter-activemq

spring-boot-starter-security

这有助于增加更少的依赖关系，并减少版本的冲突。

**Spring Boot 中的 starter 到底是什么 ?**

首先，这个 Starter 并非什么新的技术点，基本上还是基于 Spring 已有功能来实现的。首先它提供了一个自动化配置类，一般命名为 XXXAutoConfiguration ，在这个配置类中通过条件注解来决定一个配置是否生效（条件注解就是 Spring 中原本就有的），然后它还会提供一系列的默认配置，也允许开发者根据实际情况自定义相关配置，然后通过类型安全的属性注入将这些配置属性注入进来，新注入的属性会代替掉默认属性。正因为如此，很多第三方框架，我们只需要引入依赖就可以直接使用了。当然，开发者也可以自定义 Starter

#### spring-boot-starter-parent 有什么用 ?

我们都知道，新创建一个 Spring Boot 项目，默认都是有 parent 的，这个 parent 就是 spring-boot-starter-parent ，spring-boot-starter-parent 主要有如下作用：

1. 定义了 Java 编译版本为 1.8 。
2. 使用 UTF-8 格式编码。
3. 继承自 spring-boot-dependencies，这个里边定义了依赖的版本，也正是因为继承了这个依赖，所以我们在写依赖时才不需要写版本号。
4. 执行打包操作的配置。
5. 自动化的资源过滤。
6. 自动化的插件配置。
7. 针对 application.properties 和 application.yml 的资源过滤，包括通过 profile 定义的不同环境的配置文件，例如 application-dev.properties 和 application-dev.yml。

**Spring Boot 打成的 jar 和普通的 jar 有什么区别 ?**

Spring Boot 项目最终打包成的 jar 是可执行 jar ，这种 jar 可以直接通过 java -jar xxx.jar 命令来运行，这种 jar 不可以作为普通的 jar 被其他项目依赖，即使依赖了也无法使用其中的类。

Spring Boot 的 jar 无法被其他项目依赖，主要还是他和普通 jar 的结构不同。普通的 jar 包，解压后直接就是包名，包里就是我们的代码，而 Spring Boot 打包成的可执行 jar 解压后，在 \BOOT-INF\classes 目录下才是我们的代码，因此无法被直接引用。如果非要引用，可以在 pom.xml 文件中增加配置，将 Spring Boot 项目打包成两个 jar ，一个可执行，一个可引用。

#### 运行 Spring Boot 有哪几种方式？

1）打包用命令或者放到容器中运行

2）用 Maven/ Gradle 插件运行

3）直接执行 main 方法运行

#### Spring Boot 需要独立的容器运行吗？

可以不需要，内置了 Tomcat/ Jetty 等容器。

#### 开启 Spring Boot 特性有哪几种方式？

1）继承spring-boot-starter-parent项目

2）导入spring-boot-dependencies项目依赖

#### 如何使用 Spring Boot 实现异常处理？

Spring 提供了一种使用 ControllerAdvice 处理异常的非常有用的方法。我们通过实现一个 ControlerAdvice 类，来处理控制器类抛出的所有异常。

#### 如何使用 Spring Boot 实现分页和排序？

使用 Spring Boot 实现分页非常简单。使用 Spring Data-JPA 可以实现将可分页的传递给存储库方法。

**微服务中如何实现 session 共享 ?**

在微服务中，一个完整的项目被拆分成多个不相同的独立的服务，各个服务独立部署在不同的服务器上，各自的 session 被从物理空间上隔离开了，但是经常，我们需要在不同微服务之间共享 session ，常见的方案就是 Spring Session + Redis 来实现 session 共享。将所有微服务的 session 统一保存在 Redis 上，当各个微服务对 session 有相关的读写操作时，都去操作 Redis 上的 session 。这样就实现了 session 共享，Spring Session 基于 Spring 中的代理过滤器实现，使得 session 的同步操作对开发人员而言是透明的，非常简便。

**Spring Boot 中如何实现定时任务 ?**

定时任务也是一个常见的需求，Spring Boot 中对于定时任务的支持主要还是来自 Spring 框架。

在 Spring Boot 中使用定时任务主要有两种不同的方式，一个就是使用 Spring 中的 @Scheduled 注解，另一个则是使用第三方框架 Quartz。

使用 Spring 中的 @Scheduled 的方式主要通过 @Scheduled 注解来实现。

使用 Quartz ，则按照 Quartz 的方式，定义 Job 和 Trigger 即可。

### 8道专题

#### 1. 什么是spring boot？

> 多年来，随着新功能的增加，spring变得越来越复杂。只需访问页面https://spring.io/projects，我们将看到所有在应用程序中使用的不同功能的spring项目。**如果必须启动一个新的spring项目，我们必须添加构建路径或maven依赖项，配置application server，添加spring配置。因此，启动一个新的spring项目需要大量的工作，因为我们目前必须从头开始做所有事情**。Spring Boot是这个问题的解决方案。Spring boot构建在现有Spring框架之上。使用spring boot，我们可以避免以前必须执行的所有样板代码和配置。因此，Spring boot帮助我们更健壮地使用现有的Spring功能，并且只需最少的工作量。

#### 2.Spring Boot的优点是什么?

> 减少开发、测试的时间和工作量。使用JavaConfig有助于避免使用XML。避免大量maven导入和各种版本冲突。提供可选的开发方法。通过提供默认开发方式进行快速开发。不需要单独的Web服务器。这意味着您不再需要启动Tomcat、Glassfish或其他任何东西。

#### 3.什么是JavaConfig?

> **Spring JavaConfig是Spring社区的一个产品，它提供了一种纯java方法来配置Spring IoC容器。因此，它有助于避免使用XML配置。使用JavaConfig的优点是：**面向对象的配置。因为配置在JavaConfig中定义为类，所以用户可以充分利用Java中的面向对象特性。一个配置类可以子类化另一个配置类，覆盖它的@Bean方法，等等。减少或消除XML配置。已经证明了基于依赖注入原则的外部化配置的好处。然而，许多开发人员不愿意在XML和Java之间来回切换。JavaConfig为开发人员提供了一种纯java方法来配置Spring容器，这种方法在概念上类似于XML配置。从技术上讲，仅使用 JavaConfig配置类来配置容器是可行的，但是在实践中，许多人发现将JavaConfig与XML混合并匹配是理想的。类型安全的重构能力。JavaConfig提供了一种类型安全的配置Spring容器的方法。由于Java 5.0对泛型的支持，现在可以通过类型而不是名称检索bean，不需要进行任何基于类型转换或字符串的查找。

#### 4.如何在不重启服务器的情况下在Spring引导时重新加载我的更改?

> 这可以通过开发工具来实现。有了这个依赖项，您保存的任何更改都将重新启动嵌入的tomcat。Spring Boot有一个开发人员工具(DevTools)模块，它有助于提高开发人员的工作效率。**Java开发人员面临的关键挑战之一是将文件更改自动部署到服务器并自动重启服务器。开发人员可以在Spring引导时重新加载更改，而不必重新启动服务器。**这将消除每次手动部署更改的需要。Spring Boot在发布第一个版本时没有这个特性。这是开发人员最需要的特性。DevTools模块完全满足开发人员的需求。此模块将在生产环境中禁用。它还提供了H2-database控制台，以便更好地测试应用程序。使用以下依赖项<dependency><groupId>org.springframework.boot</groupId><artifactId>spring-boot-devtools</artifactId><optional>true</optional></dependency>

#### 5.什么是ELK堆栈?如何与Spring Boot一起使用?

ELK堆栈由三个开源产品组成——Elasticsearch、Logstash和Kibana from Elastic。

![8个经典spring boot面试问题](http://p6-tt.byteimg.com/large/pgc-image/dd7689a3d00c49a6b3119a0b23decc01?from=pc)

Elasticsearch是一个基于Lucene搜索引擎的NoSQL数据库。

> Logstash是一个日志管道工具，它接受来自不同来源的输入，执行不同的转换，并将数据导出到不同的目标。它是一个动态的数据收集管道，具有可扩展的插件生态系统和强大的弹性搜索协同作用 **Kibana是一个可视化UI层，工作在Elasticsearch之上。**这三个项目一起用于各种环境中的日志分析。因此Logstash收集和解析日志、弹性搜索索引并存储这些信息，而Kibana提供了一个UI层，提供可操作的可见性。Spring Boot + ELK stack

#### 6.什么是FreeMarker模板?如何使用Spring Boot实现它?

> FreeMarker是一个基于java的模板引擎，最初专注于使用MVC软件架构生成动态web页面。使用Freemarker的主要优势是完全分离了表示层和业务层。程序员可以处理应用程序代码，而设计人员可以处理html页面设计。最后，使用freemarker，这些可以组合在一起，给出最终的输出页面。Spring Boot + FreeMarker的例子

#### 7.你什么时候使用WebSockets?如何使用Spring Boot实现它?

WebSocket是一种计算机通信协议，通过单个TCP连接提供全双工通信通道。

![8个经典spring boot面试问题](http://p1-tt.byteimg.com/large/pgc-image/b25b80b6b1414569810dda98a6b715a6?from=pc)

> WebSocket是双向的——使用WebSocket客户端或服务器都可以发起发送消息。WebSocket是全双工的——客户端和服务器之间的通信是相互独立的。单个TCP连接——初始连接使用HTTP，然后将此连接升级为基于套接字的连接。然后，这个单一连接将用于未来的所有通信轻- WebSocket消息数据交换比http轻得多。Spring Boot + WebSockets的例子

#### 8.我们如何监视所有Spring Boot微服务?

> Spring Boot提供了actuator 端点来监控单个微服务的指标。这些端点对于获取关于应用程序的信息非常有帮助，比如应用程序是否启动，它们的组件(如数据库等)是否正常工作。但是，使用actuator 接口的一个主要缺点或困难是，我们必须逐个命中这些接口，以了解应用程序的状态或健康状况。假设微服务涉及50个应用程序，管理员将不得不命中所有50个应用程序的actuator 端点。为了帮助我们处理这种情况，我们将使用位于https://github.com/codecentric/springing-boot-admin的开源项目。它构建在Spring Boot Actuator之上，提供了一个web UI，使我们能够可视化多个应用程序的指标。Spring Boot Admin
>
> 

### 41道面试

#### **1 什么是springboot ？**

用来简化spring应用的初始搭建以及开发过程 使用特定的方式来进行配置（properties或yml文件）

创建独立的spring引用程序 main方法运行

嵌入的Tomcat 无需部署war文件

简化maven配置

自动配置spring添加对应功能starter自动化配置

答：spring boot来简化spring应用开发，约定大于配置，去繁从简，just run就能创建一个独立的，产品级别的应用

#### **2 Springboot 有哪些优点？**

-快速创建独立运行的spring项目与主流框架集成

-使用嵌入式的servlet容器，应用无需打包成war包

-starters自动依赖与版本控制

-大量的自动配置，简化开发，也可修改默认值

-准生产环境的运行应用监控

-与云计算的天然集成

#### **3 如何重新加载Spring Boot上的更改，而无需重新启动服务器？**

这可以使用DEV工具来实现。通过这种依赖关系，您可以节省任何更改，嵌入式tomcat将重新启动。

Spring Boot有一个开发工具（DevTools）模块，它有助于提高开发人员的生产力。Java开发人员面临的一个主要挑战是将文件更改自动部署到服务器并自动重启服务器。

开发人员可以重新加载Spring Boot上的更改，而无需重新启动服务器。这将消除每次手动部署更改的需要。Spring Boot在发布它的第一个版本时没有这个功能。

这是开发人员最需要的功能。DevTools模块完全满足开发人员的需求。该模块将在生产环境中被禁用。它还提供H2数据库控制台以更好地测试应用程序。

org.springframework.boot

spring-boot-devtools

true

#### **4 Spring Boot、Spring MVC 和 Spring 有什么区别？**

1、Spring

Spring最重要的特征是依赖注入。所有 SpringModules 不是依赖注入就是 IOC 控制反转。

当我们恰当的使用 DI 或者是 IOC 的时候，我们可以开发松耦合应用。松耦合应用的单元测试可以很容易的进行。

2、Spring MVC

Spring MVC 提供了一种分离式的方法来开发 Web 应用。通过运用像 DispatcherServelet，MoudlAndView 和 ViewResolver 等一些简单的概念，开发 Web 应用将会变的非常简单。

3、SpringBoot

Spring 和 SpringMVC 的问题在于需要配置大量的参数。

![](..\..\images\springboot\1.jpg)



Spring Boot 通过一个自动配置和启动的项来目解决这个问题。为了更快的构建产品就绪应用程序，Spring Boot 提供了一些非功能性特征。

#### **5 什么是自动配置？**

Spring 和 SpringMVC 的问题在于需要配置大量的参数。

![](..\..\images\springboot\2.jpg)



我们能否带来更多的智能？当一个 MVC JAR 添加到应用程序中的时候，我们能否自动配置一些 beans？

Spring 查看（CLASSPATH 上可用的框架）已存在的应用程序的配置。在此基础上，Spring Boot 提供了配置应用程序和框架所需要的基本配置。这就是自动配置。

#### **6 什么是 Spring Boot Stater ？**

启动器是一套方便的依赖没描述符，它可以放在自己的程序中。你可以一站式的获取你所需要的 Spring 和相关技术，而不需要依赖描述符的通过示例代码搜索和复制黏贴的负载。

例如，如果你想使用 Sping 和 JPA 访问数据库，只需要你的项目包含 spring-boot-starter-data-jpa 依赖项，你就可以完美进行。

#### **7 能否举一个例子来解释更多 Staters 的内容？**

让我们来思考一个 Stater 的例子 -Spring Boot Stater Web。

如果你想开发一个 web 应用程序或者是公开 REST 服务的应用程序。Spring Boot Start Web 是首选。让我们使用 Spring Initializr 创建一个 Spring Boot Start Web 的快速项目。

Spring Boot Start Web 的依赖项

![](..\..\images\springboot\3.jpg)



下面的截图是添加进我们应用程序的不同的依赖项

![](..\..\images\springboot\4.jpg)



依赖项可以被分为：

- Spring - core，beans，context，aop
- Web MVC - （Spring MVC）
- Jackson - for JSON Binding
- Validation - Hibernate,Validation API
- Enbedded Servlet Container - Tomcat
- Logging - logback,slf4j

任何经典的 Web 应用程序都会使用所有这些依赖项。Spring Boot Starter Web 预先打包了这些依赖项。

作为一个开发者，我不需要再担心这些依赖项和它们的兼容版本。

#### **8 Spring Boot 还提供了其它的哪些 Starter Project Options？**

Spring Boot 也提供了其它的启动器项目包括，包括用于开发特定类型应用程序的典型依赖项。

- spring-boot-starter-web-services - SOAP Web Services；
- spring-boot-starter-web - Web 和 RESTful 应用程序；
- spring-boot-starter-test - 单元测试和集成测试；
- spring-boot-starter-jdbc - 传统的 JDBC；
- spring-boot-starter-hateoas - 为服务添加 HATEOAS 功能；
- spring-boot-starter-security - 使用 SpringSecurity 进行身份验证和授权；
- spring-boot-starter-data-jpa - 带有 Hibeernate 的 Spring Data JPA；
- spring-boot-starter-data-rest - 使用 Spring Data REST 公布简单的 REST 服务；

#### **9 创建一个 Spring Boot Project 的最简单的方法是什么？**

Spring Initializr是启动 Spring Boot Projects 的一个很好的工具。

![](..\..\images\springboot\5.jpg)



就像上图中所展示的一样，我们需要做一下几步：

1、登录 Spring Initializr，按照以下方式进行选择：

2、选择 com.in28minutes.springboot 为组

3、选择 studet-services 为组件

4、选择下面的依赖项

Web

Actuator

DevTools

5、点击生 GenerateProject

6、将项目导入 Eclipse。文件 - 导入 - 现有的 Maven 项目

#### **10 Spring Initializr 是创建 Spring Boot Projects 的唯一方法吗？**

不是的。

Spring Initiatlizr 让创建 Spring Boot 项目变的很容易，但是，你也可以通过设置一个 maven 项目并添加正确的依赖项来开始一个项目。

在我们的 Spring 课程中，我们使用两种方法来创建项目。

第一种方法是 start.spring.io 。

另外一种方法是在项目的标题为“Basic Web Application”处进行手动设置。

手动设置一个 maven 项目

这里有几个重要的步骤：

1、在 Eclipse 中，使用文件 - 新建 Maven 项目来创建一个新项目

2、添加依赖项。

3、添加 maven 插件。

4、添加 Spring Boot 应用程序类。

到这里，准备工作已经做好！

#### **11 为什么我们需要 spring-boot-maven-plugin?**

spring-boot-maven-plugin 提供了一些像 jar 一样打包或者运行应用程序的命令。

1、spring-boot:run 运行你的 SpringBooty 应用程序。

2、spring-boot：repackage 重新打包你的 jar 包或者是 war 包使其可执行

3、spring-boot：start 和 spring-boot：stop 管理 Spring Boot 应用程序的生命周期（也可以说是为了集成测试）。

4、spring-boot:build-info 生成执行器可以使用的构造信息。

#### **12 如何使用 SpringBoot 自动重装我的应用程序？**

使用 Spring Boot 开发工具。

把 Spring Boot 开发工具添加进入你的项目是简单的。

把下面的依赖项添加至你的 Spring Boot Project pom.xml 中

![](..\..\images\springboot\6.jpg)



重启应用程序，然后就可以了。

同样的，如果你想自动装载页面，有可以看看 FiveReload

```
http://www.logicbig.com/tutorials/spring-framework/spring-boot/boot-live-reload/.
```

在我测试的时候，发现了 LiveReload 漏洞，如果你测试时也发现了，请一定要告诉我们。

#### **13 Spring Boot中的监视器是什么？**

Spring boot actuator是spring启动框架中的重要功能之一。Spring boot监视器可帮助您访问生产环境中正在运行的应用程序的当前状态。

有几个指标必须在生产环境中进行检查和监控。即使一些外部应用程序可能正在使用这些服务来向相关人员触发警报消息。监视器模块公开了一组可直接作为HTTP URL访问的REST端点来检查状态。

#### **14 什么是YAML？**

YAML是一种人类可读的数据序列化语言。它通常用于配置文件。

与属性文件相比，如果我们想要在配置文件中添加复杂的属性，YAML文件就更加结构化，而且更少混淆。可以看出YAML具有分层配置数据。

#### **15 springboot自动配置的原理**

在spring程序main方法中 添加@SpringBootApplication或者@EnableAutoConfiguration

会自动去maven中读取每个starter中的spring.factories文件 该文件里配置了所有需要被创建spring容器中的bean

#### **16 springboot读取配置文件的方式**

springboot默认读取配置文件为application.properties或者是application.yml

#### **17 springboot集成mybatis的过程**

添加mybatis的starter maven依赖

```
<dependency>
    <groupId>org.mybatis.spring.boot</groupId>
    <artifactId>mybatis-spring-boot-starter</artifactId>
    <version>1.3.2</version>
</dependency>
```

在mybatis的接口中 添加@Mapper注解

在application.yml配置数据源信息

#### **18 什么是嵌入式服务器？我们为什么要使用嵌入式服务器呢?**

思考一下在你的虚拟机上部署应用程序需要些什么。

第一步：安装 Java

第二步：安装 Web 或者是应用程序的服务器（Tomat/Wbesphere/Weblogic 等等）

第三步：部署应用程序 war 包

如果我们想简化这些步骤，应该如何做呢？

让我们来思考如何使服务器成为应用程序的一部分？

你只需要一个安装了 Java 的虚拟机，就可以直接在上面部署应用程序了，

这个想法是嵌入式服务器的起源。

当我们创建一个可以部署的应用程序的时候，我们将会把服务器（例如，tomcat）嵌入到可部署的服务器中。

例如，对于一个 Spring Boot 应用程序来说，你可以生成一个包含 Embedded Tomcat 的应用程序 jar。你就可以想运行正常 Java 应用程序一样来运行 web 应用程序了。

嵌入式服务器就是我们的可执行单元包含服务器的二进制文件（例如，tomcat.jar）。

#### **19 如何在 Spring Boot 中添加通用的 JS 代码？**

在源文件夹下，创建一个名为 static 的文件夹。然后，你可以把你的静态的内容放在这里面。

例如，myapp.js 的路径是 resources\static\js\myapp.js

你可以参考它在 jsp 中的使用方法：

![](..\..\images\springboot\7.jpg)



错误：HAL browser gives me unauthorized error - Full authenticaition is required to access this resource.

该如何来修复这个错误呢？

![](..\..\images\springboot\8.jpg)



两种方法：

方法 1：关闭安全验证

application.properties

```
management.security.enabled:FALSE
```

方法二：在日志中搜索密码并传递至请求标头中

#### **20 什么是 Spring Data？**

来自：//projects.spring.io/spring- data/

Spring Data 的使命是在保证底层数据存储特殊性的前提下，为数据访问提供一个熟悉的，一致性的，基于 Spring 的编程模型。这使得使用数据访问技术，关系数据库和非关系数据库，map-reduce 框架以及基于云的数据服务变得很容易。

为了让它更简单一些，Spring Data 提供了不受底层数据源限制的 Abstractions 接口。

下面来举一个例子:

![](..\..\images\springboot\9.jpg)



你可以定义一简单的库，用来插入，更新，删除和检索代办事项，而不需要编写大量的代码。

#### **21 什么是 Spring Data REST?**

Spring Data TEST 可以用来发布关于 Spring 数据库的 HATEOAS RESTful 资源。

下面是一个使用 JPA 的例子:

![](..\..\images\springboot\10.jpg)



不需要写太多代码，我们可以发布关于 Spring 数据库的 RESTful API。

下面展示的是一些关于 TEST 服务器的例子

```
POST:URL:http：//localhost：8080/todosUse Header:Content-Type:Type:application/jsonRequest Content
```

代码如下：

![](..\..\images\springboot\11.jpg)



响应内容：

![](..\..\images\springboot\12.jpg)



响应包含新创建资源的 href。

#### **22 path=”users”, collectionResourceRel=”users” 如何与 Spring Data Rest 一起使用？**

![](..\..\images\springboot\13.jpg)



path- 这个资源要导出的路径段。

collectionResourceRel- 生成指向集合资源的链接时使用的 rel 值。在生成 HATEOAS 链接时使用。

#### **23 当 Spring Boot 应用程序作为 Java 应用程序运行时，后台会发生什么？**

如果你使用 Eclipse IDE，Eclipse maven 插件确保依赖项或者类文件的改变一经添加，就会被编译并在目标文件中准备好！在这之后，就和其它的 Java 应用程序一样了。

当你启动 java 应用程序的时候，spring boot 自动配置文件就会魔法般的启用了。

当 Spring Boot 应用程序检测到你正在开发一个 web 应用程序的时候，它就会启动 tomcat。

#### **24 我们能否在 spring-boot-starter-web 中用 jetty 代替 tomcat？**

在 spring-boot-starter-web 移除现有的依赖项，并把下面这些添加进去。

![](..\..\images\springboot\14.jpg)



#### **25 如何使用 Spring Boot 生成一个 WAR 文件？**

推荐阅读:

https://spring.io/guides/gs/convert-jar-to-war/

下面有 spring 说明文档直接的链接地址：

```
https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#build-tool-plugins-maven-packaging
```

#### **26 如何使用 Spring Boot 部署到不同的服务器？**

你需要做下面两个步骤：

在一个项目中生成一个 war 文件。

将它部署到你最喜欢的服务器（websphere 或者 Weblogic 或者 Tomcat and so on）。

第一步：这本入门指南应该有所帮助：

https://spring.io/guides/gs/convert-jar-to-war/

第二步：取决于你的服务器。

#### **27 RequestMapping 和 GetMapping 的不同之处在哪里？**

RequestMapping 具有类属性的，可以进行 GET,POST,PUT 或者其它的注释中具有的请求方法。GetMapping 是 GET 请求方法中的一个特例。它只是 ResquestMapping 的一个延伸，目的是为了提高清晰度。

#### **28 为什么我们不建议在实际的应用程序中使用 Spring Data Rest?**

我们认为 Spring Data Rest 很适合快速原型制造！在大型应用程序中使用需要谨慎。

通过 Spring Data REST 你可以把你的数据实体作为 RESTful 服务直接发布。

当你设计 RESTful 服务器的时候，最佳实践表明，你的接口应该考虑到两件重要的事情：

你的模型范围。

你的客户。

通过 With Spring Data REST，你不需要再考虑这两个方面，只需要作为 TEST 服务发布实体。

这就是为什么我们建议使用 Spring Data Rest 在快速原型构造上面，或者作为项目的初始解决方法。对于完整演变项目来说，这并不是一个好的注意。

#### **29 在 Spring Initializer 中，如何改变一个项目的包名字？**

好消息是你可以定制它。点击链接“转到完整版本”。你可以配置你想要修改的包名称！

#### **30 JPA 和 Hibernate 有哪些区别？**

简而言之

JPA 是一个规范或者接口

Hibernate 是 JPA 的一个实现

当我们使用 JPA 的时候，我们使用 javax.persistence 包中的注释和接口时，不需要使用 hibernate 的导入包。

我们建议使用 JPA 注释，因为哦我们没有将其绑定到 Hibernate 作为实现。后来（我知道 - 小于百分之一的几率），我们可以使用另一种 JPA 实现。

#### **31 使用 Spring Boot 启动连接到内存数据库 H2 的 JPA 应用程序需要哪些依赖项？**

在 Spring Boot 项目中，当你确保下面的依赖项都在类路里面的时候，你可以加载 H2 控制台。

web 启动器

h2

jpa 数据启动器

其它的依赖项在下面：

![](..\..\images\springboot\15.jpg)

需要注意的一些地方：

一个内部数据内存只在应用程序执行期间存在。这是学习框架的有效方式。

这不是你希望的真是世界应用程序的方式。

在问题“如何连接一个外部数据库？”中，我们解释了如何连接一个你所选择的数据库。

#### **32 如何不通过任何配置来选择 Hibernate 作为 JPA 的默认实现？**

因为 Spring Boot 是自动配置的。

下面是我们添加的依赖项:

![](..\..\images\springboot\16.jpg)



spring-boot-stater-data-jpa 对于 Hibernate 和 JPA 有过渡依赖性。

当 Spring Boot 在类路径中检测到 Hibernate 中，将会自动配置它为默认的 JPA 实现。

#### **33 我们如何连接一个像 MySQL 或者Orcale 一样的外部数据库？**

让我们以 MySQL 为例来思考这个问题：

第一步 - 把 mysql 连接器的依赖项添加至 pom.xml

![](..\..\images\springboot\17.jpg)



第二步 - 从 pom.xml 中移除 H2 的依赖项

或者至少把它作为测试的范围。

![](..\..\images\springboot\18.jpg)



第三步 - 安装你的 MySQL 数据库

更多的来看看这里 -https://github.com/in28minutes/jpa-with-hibernate#installing-and-setting-up-mysql

第四步 - 配置你的 MySQL 数据库连接

配置 application.properties

```
spring.jpa.hibernate.ddl-auto=none spring.datasource.url=jdbc:mysql://localhost:3306/todo_example spring.datasource.username=todouser spring.datasource.password=YOUR_PASSWORD
```

第五步 - 重新启动，你就准备好了！

就是这么简单！

#### **34 你能否举一个以 ReadOnly 为事务管理的例子？**

当你从数据库读取内容的时候，你想把事物中的用户描述或者是其它描述设置为只读模式，以便于 Hebernate 不需要再次检查实体的变化。这是非常高效的。

#### **35 Spring Boot 的核心注解是哪个？它主要由哪几个注解组成的？**

启动类上面的注解是@SpringBootApplication，它也是 Spring Boot 的核心注解，主要组合包含了以下 3 个注解：

@SpringBootConfiguration：组合了 @Configuration 注解，实现配置文件的功能。

@EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置功能：

@SpringBootApplication(exclude = { DataSourceAutoConfiguration.class })。

@ComponentScan：Spring组件扫描。

#### **36 开启 Spring Boot 特性有哪几种方式？**

1）继承spring-boot-starter-parent项目

2）导入spring-boot-dependencies项目依赖

#### **37 Spring Boot 需要独立的容器运行吗？**

可以不需要，内置了 Tomcat/ Jetty 等容器。

#### **38 运行 Spring Boot 有哪几种方式？**

1）打包用命令或者放到容器中运行

2）用 Maven/ Gradle 插件运行

3）直接执行 main 方法运行

#### **39 你如何理解 Spring Boot 中的 Starters？**

Starters可以理解为启动器，它包含了一系列可以集成到应用里面的依赖包，你可以一站式集成 Spring 及其他技术，而不需要到处找示例代码和依赖包。如你想使用 Spring JPA 访问数据库，只要加入 spring-boot-starter-data-jpa 启动器依赖就能使用了。

#### **40 Spring Boot 支持哪些日志框架？推荐和默认的日志框架是哪个？**

Spring Boot 支持 Java Util Logging, Log4j2, Lockback 作为日志框架，如果你使用 Starters 启动器，Spring Boot 将使用 Logback 作为默认日志框架.

#### **41 SpringBoot 实现热部署有哪几种方式？**

主要有两种方式：

1、Spring Loaded

2、Spring-boot-devtools　　

### 10细节

#### **1. @SpringBootApplication 是做什么的？**

根据 Spring Boot 文档， @SpringBootApplication 注解相当于使用 @Configuration 、@EnableAutoConfiguration 和 @ComponentScan 及其默认属性。Spring Boot 允许开发人员使用单个注解而不是多个注解。但是，正如我们所知，Spring 提供了松散耦合的特性，我们可以根据项目的需要单独使用每个注解。

#### **2. 如何在不使用 basePackages 过滤器的情况下排除任何包？**

您可以通过不同方式过滤任意的包。但是，在不接触组件扫描的情况下，Spring Boot 为实现这个提供了一个复杂的选项。当您使用注解 @SpringApplication 时，可以使用 exclude 属性。请参考以下代码片段：

- 

```
@SpringBootApplication(exclude= {Employee.class})
public class FooAppConfiguration {}
```

#### **3. 如何禁用一个特定自动配置类？**

如果您不想要某个特定的自动配置类生效，您可以使用 @EnableAutoConfiguration 的 exclude 属性。

- 

```
//By using "exclude"
@EnableAutoConfiguration(exclude={DataSourceAutoConfiguration.class})
```

另一方面，如果类不在类路径上，您可以使用注解的 excludeName 属性并指定完全限定名称。

- 

```
//By using "excludeName"
@EnableAutoConfiguration(excludeName={Foo.class})
```

另外，Spring Boot 通过使用 spring.autoconfigure.exclude 属性来控制要排除的自动配置类列表的工具。您可以添加到 application.properties 中。并且您可以使用逗号分隔添加多个类。

- 

```
//By using property file
spring.autoconfigure.exclude=org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration
```

#### **4. 什么是Spring Actuator ？它的优势是什么？**

这是 Spring Boot 最常见的面试问题之一。根据 Spring 文档：

> “Actuator 是一个制造术语，指用于移动或控制某物的机械装置。Actuator 可以通过微小的变化产生大量的运动。”

正如我们所知，Spring Boot 提供了许多自动配置特性，帮助开发人员快速开发产品组件。但是，如果您考虑调试和如何调试，如果出了什么问题，我们总是需要分析日志并挖掘应用程序的数据流，以检查发生了什么。因此，Spring Actuator 提供了方便的访问这些类型的功能。它提供了许多特性，例如创建了什么bean、控制器中的映射、CPU 使用情况等等。然后可以将自动收集和审计健康状况（health）以及指标（metric）到您的应用程序中。

它提供了一种非常简单的方法来访问少数生产就绪的 REST 端点 并从 Web 获取各种信息。但是通过使用这些端点，您可以做很多事情来查看端点文档。无需担心安全性；如果存在 Spring Security ，那么默认情况下使用 Spring Security 的内容协商策略来保护这些端点。或者，我们可以通过 RequestMatcher 的帮助来配置自定义安全性。

#### **5. 如何启用/禁用 Actuator ？**

启用/禁用 Actuator 是很简单的。最简单的方法是启用功能，添加依赖项（Maven/Gradle）到 *spring-boot-starter-actuator* ，即 Starter 。如果你不想 Actuator 启动，则不添加依赖。

**Maven 依赖：**

- 

```
<dependencies>
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-actuator</artifactId>
	</dependency>
</dependencies>
```

#### **6. 什么是 Spring Initializer ？**

这可能不是一个很难的问题，但是面试官总是会检查应聘者的专业知识。通常你不能总是期待你已经准备好的问题。然而，这几乎一直是一个非常常见的问题。

Spring Initializer 是一个 Web 应用程序，它使用快速启动所需的一切来生成 Spring 启动项目。和往常一样，我们需要一个好的项目框架；它可以帮助您正确地创建项目结构/框架。您可以在这里了解关于 初始化器 的更多信息。

#### **7. Actuator 中的关闭是什么？**

关闭是一个端点，它允许应用程序优雅地关闭。默认情况下不启用此功能。您可以通过在应用程序中的 application.properties 文件使用 *management.endpoint.shutdown.enabled=true* 启用此功能。但是如果你用这个的话要小心。

#### **8. 能够在 Spring boot 中更改嵌入式 Tomcat 服务器的端口吗？**

是的，可以更改端口。您可以使用 application.properties 文件改变端口。但是需要提到“ *server.port* ”（即：*server.port=8081*）。确保在项目类路径中有 application.properties ；REST Spring 框架将处理其余部分。如果您提到 *server.port=0* ，那么它将自动分配任何可用的端口。

#### **9. 我们在 Spring Boot 中能覆盖或替换嵌入式 Tomcat 服务器吗？**

是的，我们可以使用 Starter 依赖项将嵌入式 Tomcat 替换为任何其他服务器。您可以根据需要使用 spring-boot-starter-jetty 或 spring-boot-start -undertow 作为每个项目的依赖项。

#### **10. 我们可以在 Spring Boot 应用程序中禁用默认 web 服务器吗？**

Spring 的主要优点是提供灵活性来构建松散耦合的应用程序。Spring 提供了在快速配置中禁用 Web 服务器的功能。是的，我们可以使用 application.properties 来配置 web 应用程序类型，即：spring.main.web-application-type=none 。

## spring cloud

见今日头条收藏

# doubo

# netty

## 1.Netty 是什么？

Netty是 一个异步事件驱动的网络应用程序框架，用于快速开发可维护的高性能协议服务器和客户端。Netty是基于nio的，它封装了jdk的nio，让我们使用起来更加方法灵活。

**2.Netty 的特点是什么？**

- 高并发：Netty 是一款基于 NIO（Nonblocking IO，非阻塞IO）开发的网络通信框架，对比于 BIO（Blocking I/O，阻塞IO），他的并发性能得到了很大提高。
- 传输快：Netty 的传输依赖于零拷贝特性，尽量减少不必要的内存拷贝，实现了更高效率的传输。
- 封装好：Netty 封装了 NIO 操作的很多细节，提供了易于使用调用接口。

## 3.Netty 的优势有哪些？

- 使用简单：封装了 NIO 的很多细节，使用更简单。
- 功能强大：预置了多种编解码功能，支持多种主流协议。
- 定制能力强：可以通过 ChannelHandler 对通信框架进行灵活地扩展。
- 性能高：通过与其他业界主流的 NIO 框架对比，Netty 的综合性能最优。
- 稳定：Netty 修复了已经发现的所有 NIO 的 bug，让开发人员可以专注于业务本身。
- 社区活跃：Netty 是活跃的开源项目，版本迭代周期短，bug 修复速度快。

## 4.Netty 的应用场景有哪些？

典型的应用有：阿里分布式服务框架 Dubbo，默认使用 Netty 作为基础通信组件，还有 RocketMQ 也是使用 Netty 作为通讯的基础。

## 5.Netty 高性能表现在哪些方面？

- IO 线程模型：同步非阻塞，用最少的资源做更多的事。
- 内存零拷贝：尽量减少不必要的内存拷贝，实现了更高效率的传输。
- 内存池设计：申请的内存可以重用，主要指直接内存。内部实现是用一颗二叉查找树管理内存分配情况。
- 串形化处理读写：避免使用锁带来的性能开销。
- 高性能序列化协议：支持 protobuf 等高性能序列化协议。

## 6.BIO、NIO和AIO的区别？

BIO：一个连接一个线程，客户端有连接请求时服务器端就需要启动一个线程进行处理。线程开销大。

伪异步IO：将请求连接放入线程池，一对多，但线程还是很宝贵的资源。

NIO：一个请求一个线程，但客户端发送的连接请求都会注册到多路复用器上，多路复用器轮询到连接有I/O请求时才启动一个线程进行处理。

AIO：一个有效请求一个线程，客户端的I/O请求都是由OS先完成了再通知服务器应用去启动线程进行处理，

BIO是面向流的，NIO是面向缓冲区的；BIO的各种流是阻塞的。而NIO是非阻塞的；BIO的Stream是单向的，而NIO的channel是双向的。

NIO的特点：事件驱动模型、单线程处理多任务、非阻塞I/O，I/O读写不再阻塞，而是返回0、基于block的传输比基于流的传输更高效、更高级的IO函数zero-copy、IO多路复用大大提高了Java网络应用的可伸缩性和实用性。基于Reactor线程模型。

在Reactor模式中，事件分发器等待某个事件或者可应用或个操作的状态发生，事件分发器就把这个事件传给事先注册的事件处理函数或者回调函数，由后者来做实际的读写操作。如在Reactor中实现读：注册读就绪事件和相应的事件处理器、事件分发器等待事件、事件到来，激活分发器，分发器调用事件对应的处理器、事件处理器完成实际的读操作，处理读到的数据，注册新的事件，然后返还控制权。

## 7.NIO的组成？

Buffer：与Channel进行交互，数据是从Channel读入缓冲区，从缓冲区写入Channel中的

flip方法 ：反转此缓冲区，将position给limit，然后将position置为0，其实就是切换读写模式

clear方法 ：清除此缓冲区，将position置为0，把capacity的值给limit。

rewind方法 ：重绕此缓冲区，将position置为0

DirectByteBuffer可减少一次系统空间到用户空间的拷贝。但Buffer创建和销毁的成本更高，不可控，通常会用内存池来提高性能。直接缓冲区主要分配给那些易受基础系统的本机I/O 操作影响的大型、持久的缓冲区。如果数据量比较小的中小应用情况下，可以考虑使用heapBuffer，由JVM进行管理。

Channel：表示 IO 源与目标打开的连接，是双向的，但不能直接访问数据，只能与Buffer 进行交互。通过源码可知，FileChannel的read方法和write方法都导致数据复制了两次！

Selector可使一个单独的线程管理多个Channel，open方法可创建Selector，register方法向多路复用器器注册通道，可以监听的事件类型：读、写、连接、accept。注册事件后会产生一个SelectionKey：它表示SelectableChannel 和Selector 之间的注册关系，wakeup方法：使尚未返回的第一个选择操作立即返回，唤醒的

原因是：注册了新的channel或者事件；channel关闭，取消注册；优先级更高的事件触发（如定时器事件），希望及时处理。

Selector在Linux的实现类是EPollSelectorImpl，委托给EPollArrayWrapper实现，其中三个native方法是对epoll的封装，而EPollSelectorImpl. implRegister方法，通过调用epoll_ctl向epoll实例中注册事件，还将注册的文件描述符(fd)与SelectionKey的对应关系添加到fdToKey中，这个map维护了文件描述符与SelectionKey的映射。

fdToKey有时会变得非常大，因为注册到Selector上的Channel非常多（百万连接）；过期或失效的Channel没有及时关闭。fdToKey总是串行读取的，而读取是在select方法中进行的，该方法是非线程安全的。

Pipe：两个线程之间的单向数据连接，数据会被写到sink通道，从source通道读取

NIO的服务端建立过程：Selector.open()：打开一个Selector；ServerSocketChannel.open()：创建服务端的Channel；bind()：绑定到某个端口上。并配置非阻塞模式；register()：注册Channel和关注的事件到Selector上；select()轮询拿到已经就绪的事件

## 8.Netty的线程模型？

Netty通过Reactor模型基于多路复用器接收并处理用户请求，内部实现了两个线程池，boss线程池和work线程池，其中boss线程池的线程负责处理请求的accept事件，当接收到accept事件的请求时，把对应的socket封装到一个NioSocketChannel中，并交给work线程池，其中work线程池负责请求的read和write事件，由对应的Handler处理。

单线程模型：所有I/O操作都由一个线程完成，即多路复用、事件分发和处理都是在一个Reactor线程上完成的。既要接收客户端的连接请求,向服务端发起连接，又要发送/读取请求或应答/响应消息。一个NIO 线程同时处理成百上千的链路，性能上无法支撑，速度慢，若线程进入死循环，整个程序不可用，对于高负载、大并发的应用场景不合适。

多线程模型：有一个NIO 线程（Acceptor） 只负责监听服务端，接收客户端的TCP 连接请求；NIO 线程池负责网络IO 的操作，即消息的读取、解码、编码和发送；1 个NIO 线程可以同时处理N 条链路，但是1 个链路只对应1 个NIO 线程，这是为了防止发生并发操作问题。但在并发百万客户端连接或需要安全认证时，一个Acceptor 线程可能会存在性能不足问题。

主从多线程模型：Acceptor 线程用于绑定监听端口，接收客户端连接，将SocketChannel 从主线程池的Reactor 线程的多路复用器上移除，重新注册到Sub 线程池的线程上，用于处理I/O 的读写等操作，从而保证mainReactor只负责接入认证、握手等操作；

## 9.TCP 粘包/拆包的原因及解决方法？

TCP是以流的方式来处理数据，一个完整的包可能会被TCP拆分成多个包进行发送，也可能把小的封装成一个大的数据包发送。

TCP粘包/分包的原因：

应用程序写入的字节大小大于套接字发送缓冲区的大小，会发生拆包现象，而应用程序写入数据小于套接字缓冲区大小，网卡将应用多次写入的数据发送到网络上，这将会发生粘包现象；

进行MSS大小的TCP分段，当TCP报文长度-TCP头部长度>MSS的时候将发生拆包

以太网帧的payload（净荷）大于MTU（1500字节）进行ip分片。

解决方法

消息定长：FixedLengthFrameDecoder类

包尾增加特殊字符分割：

- 行分隔符类：LineBasedFrameDecoder
- 或自定义分隔符类 ：DelimiterBasedFrameDecoder

将消息分为消息头和消息体：LengthFieldBasedFrameDecoder类。分为有头部的拆包与粘包、长度字段在前且有头部的拆包与粘包、多扩展头部的拆包与粘包。

## 10.什么是 Netty 的零拷贝？

Netty 的零拷贝主要包含三个方面：

- Netty 的接收和发送 ByteBuffer 采用 DIRECT BUFFERS，使用堆外直接内存进行 Socket 读写，不需要进行字节缓冲区的二次拷贝。如果使用传统的堆内存（HEAP BUFFERS）进行 Socket 读写，JVM 会将堆内存 Buffer 拷贝一份到直接内存中，然后才写入 Socket 中。相比于堆外直接内存，消息在发送过程中多了一次缓冲区的内存拷贝。
- Netty 提供了组合 Buffer 对象，可以聚合多个 ByteBuffer 对象，用户可以像操作一个 Buffer 那样方便的对组合 Buffer 进行操作，避免了传统通过内存拷贝的方式将几个小 Buffer 合并成一个大的 Buffer。
- Netty 的文件传输采用了 transferTo 方法，它可以直接将文件缓冲区的数据发送到目标 Channel，避免了传统通过循环 write 方式导致的内存拷贝问题。

## 11.Netty 中有哪种重要组件？

- Channel：Netty 网络操作抽象类，它除了包括基本的 I/O 操作，如 bind、connect、read、write 等。
- EventLoop：主要是配合 Channel 处理 I/O 操作，用来处理连接的生命周期中所发生的事情。
- ChannelFuture：Netty 框架中所有的 I/O 操作都为异步的，因此我们需要 ChannelFuture 的 addListener()注册一个 ChannelFutureListener 监听事件，当操作执行成功或者失败时，监听就会自动触发返回结果。
- ChannelHandler：充当了所有处理入站和出站数据的逻辑容器。ChannelHandler 主要用来处理各种事件，这里的事件很广泛，比如可以是连接、数据接收、异常、数据转换等。
- ChannelPipeline：为 ChannelHandler 链提供了容器，当 channel 创建时，就会被自动分配到它专属的 ChannelPipeline，这个关联是永久性的。

## 12.Netty 发送消息有几种方式？

Netty 有两种发送消息的方式：

- 直接写入 Channel 中，消息从 ChannelPipeline 当中尾部开始移动；
- 写入和 ChannelHandler 绑定的 ChannelHandlerContext 中，消息从 ChannelPipeline 中的下一个 ChannelHandler 中移动。

## 13.默认情况 Netty 起多少线程？何时启动？

Netty 默认是 CPU 处理器数的两倍，bind 完之后启动。

## 14.了解哪几种序列化协议？

序列化（编码）是将对象序列化为二进制形式（字节数组），主要用于网络传输、数据持久化等；而反序列化（解码）则是将从网络、磁盘等读取的字节数组还原成原始对象，主要用于网络传输对象的解码，以便完成远程调用。

影响序列化性能的关键因素：序列化后的码流大小（网络带宽的占用）、序列化的性能（CPU资源占用）；是否支持跨语言（异构系统的对接和开发语言切换）。

Java默认提供的序列化：无法跨语言、序列化后的码流太大、序列化的性能差

XML，优点：人机可读性好，可指定元素或特性的名称。缺点：序列化数据只包含数据本身以及类的结构，不包括类型标识和程序集信息；只能序列化公共属性和字段；不能序列化方法；文件庞大，文件格式复杂，传输占带宽。适用场景：当做配置文件存储数据，实时数据转换。

JSON，是一种轻量级的数据交换格式，优点：兼容性高、数据格式比较简单，易于读写、序列化后数据较小，可扩展性好，兼容性好、与XML相比，其协议比较简单，解析速度比较快。缺点：数据的描述性比XML差、不适合性能要求为ms级别的情况、额外空间开销比较大。适用场景（可替代ＸＭＬ）：跨防火墙访问、可调式性要求高、基于Web browser的Ajax请求、传输数据量相对小，实时性要求相对低（例如秒级别）的服务。

Fastjson，采用一种“假定有序快速匹配”的算法。优点：接口简单易用、目前java语言中最快的json库。缺点：过于注重快，而偏离了“标准”及功能性、代码质量不高，文档不全。适用场景：协议交互、Web输出、Android客户端

Thrift，不仅是序列化协议，还是一个RPC框架。优点：序列化后的体积小, 速度快、支持多种语言和丰富的数据类型、对于数据字段的增删具有较强的兼容性、支持二进制压缩编码。缺点：使用者较少、跨防火墙访问时，不安全、不具有可读性，调试代码时相对困难、不能与其他传输层协议共同使用（例如HTTP）、无法支持向持久层直接读写数据，即不适合做数据持久化序列化协议。适用场景：分布式系统的RPC解决方案

Avro，Hadoop的一个子项目，解决了JSON的冗长和没有IDL的问题。优点：支持丰富的数据类型、简单的动态语言结合功能、具有自我描述属性、提高了数据解析速度、快速可压缩的二进制数据形式、可以实现远程过程调用RPC、支持跨编程语言实现。缺点：对于习惯于静态类型语言的用户不直观。适用场景：在Hadoop中做Hive、Pig和MapReduce的持久化数据格式。

Protobuf，将数据结构以.proto文件进行描述，通过代码生成工具可以生成对应数据结构的POJO对象和Protobuf相关的方法和属性。优点：序列化后码流小，性能高、结构化数据存储格式（XML JSON等）、通过标识字段的顺序，可以实现协议的前向兼容、结构化的文档更容易管理和维护。缺点：需要依赖于工具生成代码、支持的语言相对较少，官方只支持Java 、C++ 、python。适用场景：对性能要求高的RPC调用、具有良好的跨防火墙的访问属性、适合应用层对象的持久化

**其它**

protostuff 基于protobuf协议，但不需要配置proto文件，直接导包即可

Jboss marshaling 可以直接序列化java类， 无须实java.io.Serializable接口

Message pack 一个高效的二进制序列化格式

Hessian 采用二进制协议的轻量级remoting onhttp工具

kryo 基于protobuf协议，只支持java语言,需要注册（Registration），然后序列化（Output），反序列化（Input）

## 15.如何选择序列化协议？

具体场景

对于公司间的系统调用，如果性能要求在100ms以上的服务，基于XML的SOAP协议是一个值得考虑的方案。

基于Web browser的Ajax，以及Mobile app与服务端之间的通讯，JSON协议是首选。对于性能要求不太高，或者以动态类型语言为主，或者传输数据载荷很小的的运用场景，JSON也是非常不错的选择。

对于调试环境比较恶劣的场景，采用JSON或XML能够极大的提高调试效率，降低系统开发成本。

当对性能和简洁性有极高要求的场景，Protobuf，Thrift，Avro之间具有一定的竞争关系。

对于T级别的数据的持久化应用场景，Protobuf和Avro是首要选择。如果持久化后的数据存储在hadoop子项目里，Avro会是更好的选择。

对于持久层非Hadoop项目，以静态类型语言为主的应用场景，Protobuf会更符合静态类型语言工程师的开发习惯。由于Avro的设计理念偏向于动态类型语言，对于动态语言为主的应用场景，Avro是更好的选择。

如果需要提供一个完整的RPC解决方案，Thrift是一个好的选择。

如果序列化之后需要支持不同的传输层协议，或者需要跨防火墙访问的高性能场景，Protobuf可以优先考虑。

protobuf的数据类型有多种：bool、double、float、int32、int64、string、bytes、enum、message。protobuf的限定符：required: 必须赋值，不能为空、optional:字段可以赋值，也可以不赋值、repeated: 该字段可以重复任意次数（包括0次）、枚举；只能用指定的常量集中的一个值作为其值；

protobuf的基本规则：每个消息中必须至少留有一个required类型的字段、包含0个或多个optional类型的字段；repeated表示的字段可以包含0个或多个数据；[1,15]之内的标识号在编码的时候会占用一个字节（常用），[16,2047]之内的标识号则占用2个字节，标识号一定不能重复、使用消息类型，也可以将消息嵌套任意多层，可用嵌套消息类型来代替组。

protobuf的消息升级原则：不要更改任何已有的字段的数值标识；不能移除已经存在的required字段，optional和repeated类型的字段可以被移除，但要保留标号不能被重用。新添加的字段必须是optional或repeated。因为旧版本程序无法读取或写入新增的required限定符的字段。

编译器为每一个消息类型生成了一个.java文件，以及一个特殊的Builder类（该类是用来创建消息类接口的）。如：UserProto.User.Builder builder = UserProto.User.newBuilder();builder.build()；

Netty中的使用：ProtobufVarint32FrameDecoder 是用于处理半包消息的解码类；ProtobufDecoder(UserProto.User.getDefaultInstance())这是创建的UserProto.java文件中的解码类；ProtobufVarint32LengthFieldPrepender 对protobuf协议的消息头上加上一个长度为32的整形字段，用于标志这个消息的长度的类；ProtobufEncoder 是编码类

将StringBuilder转换为ByteBuf类型：copiedBuffer()方法

## 16.Netty 支持哪些心跳类型设置？

- readerIdleTime：为读超时时间（即测试端一定时间内未接受到被测试端消息）。
- writerIdleTime：为写超时时间（即测试端一定时间内向被测试端发送消息）。
- allIdleTime：所有类型的超时时间。

## 17.Netty 和 Tomcat 的区别？

- 作用不同：Tomcat 是 Servlet 容器，可以视为 Web 服务器，而 Netty 是异步事件驱动的网络应用程序框架和工具用于简化网络编程，例如TCP和UDP套接字服务器。
- 协议不同：Tomcat 是基于 http 协议的 Web 服务器，而 Netty 能通过编程自定义各种协议，因为 Netty 本身自己能编码/解码字节流，所有 Netty 可以实现，HTTP 服务器、FTP 服务器、UDP 服务器、RPC 服务器、WebSocket 服务器、Redis 的 Proxy 服务器、MySQL 的 Proxy 服务器等等。

## 18.NIOEventLoopGroup源码？

NioEventLoopGroup(其实是MultithreadEventExecutorGroup) 内部维护一个类型为 EventExecutor children [], 默认大小是处理器核数 * 2, 这样就构成了一个线程池，初始化EventExecutor时NioEventLoopGroup重载newChild方法，所以children元素的实际类型为NioEventLoop。

线程启动时调用SingleThreadEventExecutor的构造方法，执行NioEventLoop类的run方法，首先会调用hasTasks()方法判断当前taskQueue是否有元素。如果taskQueue中有元素，执行 selectNow() 方法，最终执行selector.selectNow()，该方法会立即返回。如果taskQueue没有元素，执行 select(oldWakenUp) 方法

select ( oldWakenUp) 方法解决了 Nio 中的 bug，selectCnt 用来记录selector.select方法的执行次数和标识是否执行过selector.selectNow()，若触发了epoll的空轮询bug，则会反复执行selector.select(timeoutMillis)，变量selectCnt 会逐渐变大，当selectCnt 达到阈值（默认512），则执行rebuildSelector方法，进行selector重建，解决cpu占用100%的bug。

rebuildSelector方法先通过openSelector方法创建一个新的selector。然后将old selector的selectionKey执行cancel。最后将old selector的channel重新注册到新的selector中。rebuild后，需要重新执行方法selectNow，检查是否有已ready的selectionKey。

接下来调用processSelectedKeys 方法（处理I/O任务），当selectedKeys != null时，调用processSelectedKeysOptimized方法，迭代 selectedKeys 获取就绪的 IO 事件的selectkey存放在数组selectedKeys中, 然后为每个事件都调用 processSelectedKey 来处理它，processSelectedKey 中分别处理OP_READ；OP_WRITE；OP_CONNECT事件。

最后调用runAllTasks方法（非IO任务），该方法首先会调用fetchFromScheduledTaskQueue方法，把scheduledTaskQueue中已经超过延迟执行时间的任务移到taskQueue中等待被执行，然后依次从taskQueue中取任务执行，每执行64个任务，进行耗时检查，如果已执行时间超过预先设定的执行时间，则停止执行非IO任务，避免非IO任务太多，影响IO任务的执行。

每个NioEventLoop对应一个线程和一个Selector，NioServerSocketChannel会主动注册到某一个NioEventLoop的Selector上，NioEventLoop负责事件轮询。

Outbound 事件都是请求事件, 发起者是 Channel，处理者是 unsafe，通过 Outbound 事件进行通知，传播方向是 tail到head。Inbound 事件发起者是 unsafe，事件的处理者是 Channel, 是通知事件，传播方向是从头到尾。

内存管理机制，首先会预申请一大块内存Arena，Arena由许多Chunk组成，而每个Chunk默认由2048个page组成。Chunk通过AVL树的形式组织Page，每个叶子节点表示一个Page，而中间节点表示内存区域，节点自己记录它在整个Arena中的偏移地址。当区域被分配出去后，中间节点上的标记位会被标记，这样就表示这个中间节点以下的所有节点都已被分配了。大于8k的内存分配在poolChunkList中，而PoolSubpage用于分配小于8k的内存，它会把一个page分割成多段，进行内存分配。

ByteBuf的特点：支持自动扩容（4M），保证put方法不会抛出异常、通过内置的复合缓冲类型，实现零拷贝（zero-copy）；不需要调用flip()来切换读/写模式，读取和写入索引分开；方法链；引用计数基于AtomicIntegerFieldUpdater用于内存回收；PooledByteBuf采用二叉树来实现一个内存池，集中管理内存的分配和释放，不用每次使用都新建一个缓冲区对象。UnpooledHeapByteBuf每次都会新建一个缓冲区对象。

## Netty简介





Netty是 一个异步事件驱动的网络应用程序框架，用于快速开发可维护的高性能协议服务器和客户端。

### JDK原生NIO程序的问题

JDK原生也有一套网络应用程序API，但是存在一系列问题，主要如下：

- NIO的类库和API繁杂，使用麻烦，你需要熟练掌握Selector、ServerSocketChannel、SocketChannel、ByteBuffer等
- 需要具备其它的额外技能做铺垫，例如熟悉Java多线程编程，因为NIO编程涉及到Reactor模式，你必须对多线程和网路编程非常熟悉，才能编写出高质量的NIO程序
- 可靠性能力补齐，开发工作量和难度都非常大。例如客户端面临断连重连、网络闪断、半包读写、失败缓存、网络拥塞和异常码流的处理等等，NIO编程的特点是功能开发相对容易，但是可靠性能力补齐工作量和难度都非常大
- JDK NIO的BUG，例如臭名昭著的epoll bug，它会导致Selector空轮询，最终导致CPU 100%。官方声称在JDK1.6版本的update18修复了该问题，但是直到JDK1.7版本该问题仍旧存在，只不过该bug发生概率降低了一些而已，它并没有被根本解决

### Netty的特点

Netty的对JDK自带的NIO的API进行封装，解决上述问题，主要特点有：

- 设计优雅 适用于各种传输类型的统一API - 阻塞和非阻塞Socket 基于灵活且可扩展的事件模型，可以清晰地分离关注点 高度可定制的线程模型 - 单线程，一个或多个线程池 真正的无连接数据报套接字支持（自3.1起）
- 使用方便 详细记录的Javadoc，用户指南和示例 没有其他依赖项，JDK 5（Netty 3.x）或6（Netty 4.x）就足够了
- 高性能 吞吐量更高，延迟更低 减少资源消耗 最小化不必要的内存复制
- 安全 完整的SSL / TLS和StartTLS支持
- 社区活跃，不断更新 社区活跃，版本迭代周期短，发现的BUG可以被及时修复，同时，更多的新功能会被加入

### Netty常见使用场景

Netty常见的使用场景如下：

- 互联网行业 在分布式系统中，各个节点之间需要远程服务调用，高性能的RPC框架必不可少，Netty作为异步高新能的通信框架,往往作为基础通信组件被这些RPC框架使用。典型的应用有：阿里分布式服务框架Dubbo的RPC框架使用Dubbo协议进行节点间通信，Dubbo协议默认使用Netty作为基础通信组件，用于实现各进程节点之间的内部通信。
- 游戏行业 无论是手游服务端还是大型的网络游戏，Java语言得到了越来越广泛的应用。Netty作为高性能的基础通信组件，它本身提供了TCP/UDP和HTTP协议栈。非常方便定制和开发私有协议栈，账号登录服务器，地图服务器之间可以方便的通过Netty进行高性能的通信
- 大数据领域 经典的Hadoop的高性能通信和序列化组件Avro的RPC框架，默认采用Netty进行跨界点通信，它的Netty Service基于Netty框架二次封装实现

**Netty高性能设计**

Netty作为异步事件驱动的网络，高性能之处主要来自于其I/O模型和线程处理模型，前者决定如何收发数据，后者决定如何处理数据

**I/O模型**

用什么样的通道将数据发送给对方，BIO、NIO或者AIO，I/O模型在很大程度上决定了框架的性能

**阻塞I/O**

传统阻塞型I/O(BIO)可以用下图表示：

![](..\..\images\netty\1.jpg)



特点

- 每个请求都需要独立的线程完成数据read，业务处理，数据write的完整操作

问题

- 当并发数较大时，需要创建大量线程来处理连接，系统资源占用较大
- 连接建立后，如果当前线程暂时没有数据可读，则线程就阻塞在read操作上，造成线程资源浪费

#### I/O复用模型

![](..\..\images\netty\2.jpg)



在I/O复用模型中，会用到select，这个函数也会使进程阻塞，但是和阻塞I/O所不同的的，这两个函数可以同时阻塞多个I/O操作，而且可以同时对多个读操作，多个写操作的I/O函数进行检测，直到有数据可读或可写时，才真正调用I/O操作函数

Netty的非阻塞I/O的实现关键是基于I/O复用模型，这里用Selector对象表示：

![](..\..\images\netty\3.jpg)



Netty的IO线程NioEventLoop由于聚合了多路复用器Selector，可以同时并发处理成百上千个客户端连接。当线程从某客户端Socket通道进行读写数据时，若没有数据可用时，该线程可以进行其他任务。线程通常将非阻塞 IO 的空闲时间用于在其他通道上执行 IO 操作，所以单独的线程可以管理多个输入和输出通道。

由于读写操作都是非阻塞的，这就可以充分提升IO线程的运行效率，避免由于频繁I/O阻塞导致的线程挂起，一个I/O线程可以并发处理N个客户端连接和读写操作，这从根本上解决了传统同步阻塞I/O一连接一线程模型，架构的性能、弹性伸缩能力和可靠性都得到了极大的提升。

#### 基于buffer

传统的I/O是面向字节流或字符流的，以流式的方式顺序地从一个Stream 中读取一个或多个字节, 因此也就不能随意改变读取指针的位置。

在NIO中, 抛弃了传统的 I/O流, 而是引入了Channel和Buffer的概念. 在NIO中, 只能从Channel中读取数据到Buffer中或将数据 Buffer 中写入到 Channel。

基于buffer操作不像传统IO的顺序操作, NIO 中可以随意地读取任意位置的数据

### 线程模型

数据报如何读取？读取之后的编解码在哪个线程进行，编解码后的消息如何派发，线程模型的不同，对性能的影响也非常大。

#### 事件驱动模型

通常，我们设计一个事件处理模型的程序有两种思路

- 轮询方式 线程不断轮询访问相关事件发生源有没有发生事件，有发生事件就调用事件处理逻辑。
- 事件驱动方式 发生事件，主线程把事件放入事件队列，在另外线程不断循环消费事件列表中的事件，调用事件对应的处理逻辑处理事件。事件驱动方式也被称为消息通知方式，其实是设计模式中观察者模式的思路。

以GUI的逻辑处理为例，说明两种逻辑的不同：

- 轮询方式 线程不断轮询是否发生按钮点击事件，如果发生，调用处理逻辑
- 事件驱动方式 发生点击事件把事件放入事件队列，在另外线程消费的事件列表中的事件，根据事件类型调用相关事件处理逻辑

这里借用O’Reilly 大神关于事件驱动模型解释图

![](..\..\images\netty\4.jpg)



主要包括4个基本组件：

- 事件队列（event queue）：接收事件的入口，存储待处理事件
- 分发器（event mediator）：将不同的事件分发到不同的业务逻辑单元
- 事件通道（event channel）：分发器与处理器之间的联系渠道
- 事件处理器（event processor）：实现业务逻辑，处理完成后会发出事件，触发下一步操作

可以看出，相对传统轮询模式，事件驱动有如下优点：

- 可扩展性好，分布式的异步架构，事件处理器之间高度解耦，可以方便扩展事件处理逻辑
- 高性能，基于队列暂存事件，能方便并行异步处理事件

**Reactor线程模型**

Reactor是反应堆的意思，Reactor模型，是指通过一个或多个输入同时传递给服务处理器的服务请求的事件驱动处理模式。服务端程序处理传入多路请求，并将它们同步分派给请求对应的处理线程，Reactor模式也叫Dispatcher模式，即I/O多了复用统一监听事件，收到事件后分发(Dispatch给某进程)，是编写高性能网络服务器的必备技术之一。

**Reactor模型中有2个关键组成：**

- Reactor Reactor在一个单独的线程中运行，负责监听和分发事件，分发给适当的处理程序来对IO事件做出反应。它就像公司的电话接线员，它接听来自客户的电话并将线路转移到适当的联系人
- Handlers 处理程序执行I/O事件要完成的实际事件，类似于客户想要与之交谈的公司中的实际官员。Reactor通过调度适当的处理程序来响应I/O事件，处理程序执行非阻塞操作

![](..\..\images\netty\5.jpg)



取决于Reactor的数量和Hanndler线程数量的不同，Reactor模型有3个变种

- 单Reactor单线程
- 单Reactor多线程
- 主从Reactor多线程

可以这样理解，Reactor就是一个执行while (true) { selector.select(); …}循环的线程，会源源不断的产生新的事件，称作反应堆很贴切。

篇幅关系，这里不再具体展开Reactor特性、优缺点比较，有兴趣的读者可以参考我之前另外一篇文章：《理解高性能网络模型》https://www.jianshu.com/p/2965fca6bb8f

#### Netty线程模型

Netty主要基于主从Reactors多线程模型（如下图）做了一定的修改，其中主从Reactor多线程模型有多个Reactor：MainReactor和SubReactor：

- MainReactor负责客户端的连接请求，并将请求转交给SubReactor
- SubReactor负责相应通道的IO读写请求
- 非IO请求（具体逻辑处理）的任务则会直接写入队列，等待worker threads进行处理

这里引用Doug Lee大神的Reactor介绍：Scalable IO in Java里面关于主从Reactor多线程模型的图

![](..\..\images\netty\6.jpg)



特别说明的是：虽然Netty的线程模型基于主从Reactor多线程，借用了MainReactor和SubReactor的结构，但是实际实现上，SubReactor和Worker线程在同一个线程池中：

```
EventLoopGroup bossGroup = new NioEventLoopGroup();EventLoopGroup workerGroup = new NioEventLoopGroup();ServerBootstrap server = new ServerBootstrap();server.group(bossGroup, workerGroup) .channel(NioServerSocketChannel.class)
```

上面代码中的bossGroup 和workerGroup是Bootstrap构造方法中传入的两个对象，这两个group均是线程池

- bossGroup线程池则只是在bind某个端口后，获得其中一个线程作为MainReactor，专门处理端口的accept事件，每个端口对应一个boss线程
- workerGroup线程池会被各个SubReactor和worker线程充分利用

**异步处理**

异步的概念和同步相对。当一个异步过程调用发出后，调用者不能立刻得到结果。实际处理这个调用的部件在完成后，通过状态、通知和回调来通知调用者。

Netty中的I/O操作是异步的，包括bind、write、connect等操作会简单的返回一个ChannelFuture，调用者并不能立刻获得结果，通过Future-Listener机制，用户可以方便的主动获取或者通过通知机制获得IO操作结果。

当future对象刚刚创建时，处于非完成状态，调用者可以通过返回的ChannelFuture来获取操作执行的状态，注册监听函数来执行完成后的操，常见有如下操作：

- 通过isDone方法来判断当前操作是否完成
- 通过isSuccess方法来判断已完成的当前操作是否成功
- 通过getCause方法来获取已完成的当前操作失败的原因
- 通过isCancelled方法来判断已完成的当前操作是否被取消
- 通过addListener方法来注册监听器，当操作已完成(isDone方法返回完成)，将会通知指定的监听器；如果future对象已完成，则理解通知指定的监听器

例如下面的的代码中绑定端口是异步操作，当绑定操作处理完，将会调用相应的监听器处理逻辑

```
    serverBootstrap.bind(port).addListener(future -> {        if (future.isSuccess()) {            System.out.println(new Date() + ": 端口[" + port + "]绑定成功!");        } else {            System.err.println("端口[" + port + "]绑定失败!");        }    });
```

相比传统阻塞I/O，执行I/O操作后线程会被阻塞住, 直到操作完成；异步处理的好处是不会造成线程阻塞，线程在I/O操作期间可以执行别的程序，在高并发情形下会更稳定和更高的吞吐量。

## Netty架构设计

前面介绍完Netty相关一些理论介绍，下面从功能特性、模块组件、运作过程来介绍Netty的架构设计

### 功能特性

![](..\..\images\netty\7.jpg)



- 传输服务 支持BIO和NIO
- 容器集成 支持OSGI、JBossMC、Spring、Guice容器
- 协议支持 HTTP、Protobuf、二进制、文本、WebSocket等一系列常见协议都支持。还支持通过实行编码解码逻辑来实现自定义协议
- Core核心 可扩展事件模型、通用通信API、支持零拷贝的ByteBuf缓冲对象

### 模块组件

#### Bootstrap、ServerBootstrap

Bootstrap意思是引导，一个Netty应用通常由一个Bootstrap开始，主要作用是配置整个Netty程序，串联各个组件，Netty中Bootstrap类是客户端程序的启动引导类，ServerBootstrap是服务端启动引导类。

**Future、ChannelFuture**

正如前面介绍，在Netty中所有的IO操作都是异步的，不能立刻得知消息是否被正确处理，但是可以过一会等它执行完成或者直接注册一个监听，具体的实现就是通过Future和ChannelFutures，他们可以注册一个监听，当操作执行成功或失败时监听会自动触发注册的监听事件。

#### Channel

Netty网络通信的组件，能够用于执行网络I/O操作。Channel为用户提供：

- 当前网络连接的通道的状态（例如是否打开？是否已连接？）
- 网络连接的配置参数 （例如接收缓冲区大小）
- 提供异步的网络I/O操作(如建立连接，读写，绑定端口)，异步调用意味着任何I / O调用都将立即返回，并且不保证在调用结束时所请求的I / O操作已完成。调用立即返回一个ChannelFuture实例，通过注册监听器到ChannelFuture上，可以I / O操作成功、失败或取消时回调通知调用方。
- 支持关联I/O操作与对应的处理程序

不同协议、不同的阻塞类型的连接都有不同的 Channel 类型与之对应，下面是一些常用的 Channel 类型

- NioSocketChannel，异步的客户端 TCP Socket 连接
- NioServerSocketChannel，异步的服务器端 TCP Socket 连接
- NioDatagramChannel，异步的 UDP 连接
- NioSctpChannel，异步的客户端 Sctp 连接
- NioSctpServerChannel，异步的 Sctp 服务器端连接 这些通道涵盖了 UDP 和 TCP网络 IO以及文件 IO.

**Selector**

Netty基于Selector对象实现I/O多路复用，通过 Selector, 一个线程可以监听多个连接的Channel事件, 当向一个Selector中注册Channel 后，Selector 内部的机制就可以自动不断地查询(select) 这些注册的Channel是否有已就绪的I/O事件(例如可读, 可写, 网络连接完成等)，这样程序就可以很简单地使用一个线程高效地管理多个 Channel 。

#### NioEventLoop

NioEventLoop中维护了一个线程和任务队列，支持异步提交执行任务，线程启动时会调用NioEventLoop的run方法，执行I/O任务和非I/O任务：

- I/O任务 即selectionKey中ready的事件，如accept、connect、read、write等，由processSelectedKeys方法触发。
- 非IO任务 添加到taskQueue中的任务，如register0、bind0等任务，由runAllTasks方法触发。

两种任务的执行时间比由变量ioRatio控制，默认为50，则表示允许非IO任务执行的时间与IO任务的执行时间相等。

#### NioEventLoopGroup

NioEventLoopGroup，主要管理eventLoop的生命周期，可以理解为一个线程池，内部维护了一组线程，每个线程(NioEventLoop)负责处理多个Channel上的事件，而一个Channel只对应于一个线程。

**ChannelHandler**

ChannelHandler是一个接口，处理I / O事件或拦截I / O操作，并将其转发到其ChannelPipeline(业务处理链)中的下一个处理程序。

ChannelHandler本身并没有提供很多方法，因为这个接口有许多的方法需要实现，方便使用期间，可以继承它的子类：

- ChannelInboundHandler用于处理入站I / O事件
- ChannelOutboundHandler用于处理出站I / O操作

或者使用以下适配器类：

- ChannelInboundHandlerAdapter用于处理入站I / O事件
- ChannelOutboundHandlerAdapter用于处理出站I / O操作
- ChannelDuplexHandler用于处理入站和出站事件

#### ChannelHandlerContext

保存Channel相关的所有上下文信息，同时关联一个ChannelHandler对象

**ChannelPipline**

保存ChannelHandler的List，用于处理或拦截Channel的入站事件和出站操作。ChannelPipeline实现了一种高级形式的拦截过滤器模式，使用户可以完全控制事件的处理方式，以及Channel中各个的ChannelHandler如何相互交互。

下图引用Netty的Javadoc4.1中ChannelPipline的说明，描述了ChannelPipeline中ChannelHandler通常如何处理I/O事件。I/O事件由ChannelInboundHandler或ChannelOutboundHandler处理，并通过调用ChannelHandlerContext中定义的事件传播方法（例如ChannelHandlerContext.fireChannelRead（Object）和ChannelOutboundInvoker.write（Object））转发到其最近的处理程序。

```
                                                 I/O Request                                            via Channel or                                        ChannelHandlerContext                                                      |  +---------------------------------------------------+---------------+  |                           ChannelPipeline         |               |  |                                                  \|/              |  |    +---------------------+            +-----------+----------+    |  |    | Inbound Handler  N  |            | Outbound Handler  1  |    |  |    +----------+----------+            +-----------+----------+    |  |              /|\                                  |               |  |               |                                  \|/              |  |    +----------+----------+            +-----------+----------+    |  |    | Inbound Handler N-1 |            | Outbound Handler  2  |    |  |    +----------+----------+            +-----------+----------+    |  |              /|\                                  .               |  |               .                                   .               |  | ChannelHandlerContext.fireIN_EVT() ChannelHandlerContext.OUT_EVT()|  |        [ method call]                       [method call]         |  |               .                                   .               |  |               .                                  \|/              |  |    +----------+----------+            +-----------+----------+    |  |    | Inbound Handler  2  |            | Outbound Handler M-1 |    |  |    +----------+----------+            +-----------+----------+    |  |              /|\                                  |               |  |               |                                  \|/              |  |    +----------+----------+            +-----------+----------+    |  |    | Inbound Handler  1  |            | Outbound Handler  M  |    |  |    +----------+----------+            +-----------+----------+    |  |              /|\                                  |               |  +---------------+-----------------------------------+---------------+                  |                                  \|/  +---------------+-----------------------------------+---------------+  |               |                                   |               |  |       [ Socket.read() ]                    [ Socket.write() ]     |  |                                                                   |  |  Netty Internal I/O Threads (Transport Implementation)            |  +-------------------------------------------------------------------+
```

入站事件由自下而上方向的入站处理程序处理，如图左侧所示。入站Handler处理程序通常处理由图底部的I / O线程生成的入站数据。通常通过实际输入操作（例如SocketChannel.read（ByteBuffer））从远程读取入站数据。

出站事件由上下方向处理，如图右侧所示。出站Handler处理程序通常会生成或转换出站传输，例如write请求。I/O线程通常执行实际的输出操作，例如SocketChannel.write（ByteBuffer）。

在 Netty 中每个 Channel 都有且仅有一个 ChannelPipeline 与之对应, 它们的组成关系如下:

![](..\..\images\netty\8.jpg)



一个 Channel 包含了一个 ChannelPipeline, 而 ChannelPipeline 中又维护了一个由 ChannelHandlerContext 组成的双向链表, 并且每个 ChannelHandlerContext 中又关联着一个 ChannelHandler。入站事件和出站事件在一个双向链表中，入站事件会从链表head往后传递到最后一个入站的handler，出站事件会从链表tail往前传递到最前一个出站的handler，两种类型的handler互不干扰。

### 工作原理架构

初始化并启动Netty服务端过程如下：

```
    public static void main(String[] args) {        // 创建mainReactor        NioEventLoopGroup boosGroup = new NioEventLoopGroup();        // 创建工作线程组        NioEventLoopGroup workerGroup = new NioEventLoopGroup();        final ServerBootstrap serverBootstrap = new ServerBootstrap();        serverBootstrap                  // 组装NioEventLoopGroup                 .group(boosGroup, workerGroup)                 // 设置channel类型为NIO类型                .channel(NioServerSocketChannel.class)                // 设置连接配置参数                .option(ChannelOption.SO_BACKLOG, 1024)                .childOption(ChannelOption.SO_KEEPALIVE, true)                .childOption(ChannelOption.TCP_NODELAY, true)                // 配置入站、出站事件handler                .childHandler(new ChannelInitializer<NioSocketChannel>() {                    @Override                    protected void initChannel(NioSocketChannel ch) {                        // 配置入站、出站事件channel                        ch.pipeline().addLast(...);                        ch.pipeline().addLast(...);                    }    });        // 绑定端口        int port = 8080;        serverBootstrap.bind(port).addListener(future -> {            if (future.isSuccess()) {                System.out.println(new Date() + ": 端口[" + port + "]绑定成功!");            } else {                System.err.println("端口[" + port + "]绑定失败!");            }        });}
```

基本过程如下：

- 1 初始化创建2个NioEventLoopGroup，其中boosGroup用于Accetpt连接建立事件并分发请求， workerGroup用于处理I/O读写事件和业务逻辑
- 2 基于ServerBootstrap(服务端启动引导类)，配置EventLoopGroup、Channel类型，连接参数、配置入站、出站事件handler
- 3 绑定端口，开始工作

结合上面的介绍的Netty Reactor模型，介绍服务端Netty的工作架构图：

![](..\..\images\netty\9.jpg)



server端包含1个Boss NioEventLoopGroup和1个Worker NioEventLoopGroup，NioEventLoopGroup相当于1个事件循环组，这个组里包含多个事件循环NioEventLoop，每个NioEventLoop包含1个selector和1个事件循环线程。

每个Boss NioEventLoop循环执行的任务包含3步：

- 1 轮询accept事件
- 2 处理accept I/O事件，与Client建立连接，生成NioSocketChannel，并将NioSocketChannel注册到某个Worker NioEventLoop的Selector上
- 3 处理任务队列中的任务，runAllTasks。任务队列中的任务包括用户调用eventloop.execute或schedule执行的任务，或者其它线程提交到该eventloop的任务。

每个Worker NioEventLoop循环执行的任务包含3步：

- 1 轮询read、write事件；
- 2 处I/O事件，即read、write事件，在NioSocketChannel可读、可写事件发生时进行处理
- 3 处理任务队列中的任务，runAllTasks。

其中任务队列中的task有3种典型使用场景

- 1 用户程序自定义的普通任务

```
ctx.channel().eventLoop().execute(new Runnable() {    @Override    public void run() {        //...    }});
```

- 2 非当前reactor线程调用channel的各种方法 例如在推送系统的业务线程里面，根据用户的标识，找到对应的channel引用，然后调用write类方法向该用户推送消息，就会进入到这种场景。最终的write会提交到任务队列中后被异步消费。
- 3 用户自定义定时任务

```
ctx.channel().eventLoop().schedule(new Runnable() {    @Override    public void run() {    }}, 60, TimeUnit.SECONDS);
```

**总结**

现在稳定推荐使用的主流版本还是Netty4，Netty5 中使用了 ForkJoinPool，增加了代码的复杂度，但是对性能的改善却不明显，所以这个版本不推荐使用，官网也没有提供下载链接。

Netty 入门门槛相对较高，其实是因为这方面的资料较少，并不是因为他有多难，大家其实都可以像搞透 Spring 一样搞透 Netty。在学习之前，建议先理解透整个框架原理结构，运行过程，可以少走很多弯路。

## 11条

#### 1.Netty 是什么？

Netty 是一款基于 NIO（Nonblocking I/O，非阻塞IO）开发的网络通信框架，对比于 BIO（Blocking I/O，阻塞IO），他的并发性能得到了很大提高。难能可贵的是，在保证快速和易用性的同时，并没有丧失可维护性和性能等优势。

#### 2.Netty 的特点是什么？

高并发：Netty 是一款基于 NIO（Nonblocking IO，非阻塞IO）开发的网络通信框架，对比于 BIO（Blocking I/O，阻塞IO），他的并发性能得到了很大提高。

传输快：Netty 的传输依赖于零拷贝特性，尽量减少不必要的内存拷贝，实现了更高效率的传输。

封装好：Netty 封装了 NIO 操作的很多细节，提供了易于使用调用接口。

#### 3.什么是 Netty 的零拷贝？

Netty 的零拷贝主要包含三个方面：

Netty 的接收和发送 ByteBuffer 采用 DIRECT BUFFERS，使用堆外直接内存进行 Socket 读写，不需要进行字节缓冲区的二次拷贝。如果使用传统的堆内存（HEAP BUFFERS）进行 Socket 读写，JVM 会将堆内存 Buffer 拷贝一份到直接内存中，然后才写入 Socket 中。相比于堆外直接内存，消息在发送过程中多了一次缓冲区的内存拷贝。

Netty 提供了组合 Buffer 对象，可以聚合多个 ByteBuffer 对象，用户可以像操作一个 Buffer 那样方便的对组合 Buffer 进行操作，避免了传统通过内存拷贝的方式将几个小 Buffer 合并成一个大的 Buffer。

Netty 的文件传输采用了 transferTo 方法，它可以直接将文件缓冲区的数据发送到目标 Channel，避免了传统通过循环 write 方式导致的内存拷贝问题。

#### 4.Netty 的优势有哪些？

使用简单：封装了 NIO 的很多细节，使用更简单。

功能强大：预置了多种编解码功能，支持多种主流协议。

定制能力强：可以通过 ChannelHandler 对通信框架进行灵活地扩展。

性能高：通过与其他业界主流的 NIO 框架对比，Netty 的综合性能最优。

稳定：Netty 修复了已经发现的所有 NIO 的 bug，让开发人员可以专注于业务本身。

社区活跃：Netty 是活跃的开源项目，版本迭代周期短，bug 修复速度快。

#### 5.Netty 的应用场景有哪些？

典型的应用有：阿里分布式服务框架 Dubbo，默认使用 Netty 作为基础通信组件，还有 RocketMQ 也是使用 Netty 作为通讯的基础。

#### 6.Netty 高性能表现在哪些方面？

IO 线程模型：同步非阻塞，用最少的资源做更多的事。

内存零拷贝：尽量减少不必要的内存拷贝，实现了更高效率的传输。

内存池设计：申请的内存可以重用，主要指直接内存。内部实现是用一颗二叉查找树管理内存分配情况。

串形化处理读写：避免使用锁带来的性能开销。

高性能序列化协议：支持 protobuf 等高性能序列化协议。

#### 7.Netty 和 Tomcat 的区别？

作用不同：Tomcat 是 Servlet 容器，可以视为 Web 服务器，而 Netty 是异步事件驱动的网络应用程序框架和工具用于简化网络编程，例如TCP和UDP套接字服务器。

协议不同：Tomcat 是基于 http 协议的 Web 服务器，而 Netty 能通过编程自定义各种协议，因为 Netty 本身自己能编码/解码字节流，所有 Netty 可以实现，HTTP 服务器、FTP 服务器、UDP 服务器、RPC 服务器、WebSocket 服务器、Redis 的 Proxy 服务器、MySQL 的 Proxy 服务器等等。

#### 8.Netty 中有那种重要组件？

Channel：Netty 网络操作抽象类，它除了包括基本的 I/O 操作，如 bind、connect、read、write 等。

EventLoop：主要是配合 Channel 处理 I/O 操作，用来处理连接的生命周期中所发生的事情。

ChannelFuture：Netty 框架中所有的 I/O 操作都为异步的，因此我们需要 ChannelFuture 的 addListener()注册一个 ChannelFutureListener 监听事件，当操作执行成功或者失败时，监听就会自动触发返回结果。

ChannelHandler：充当了所有处理入站和出站数据的逻辑容器。ChannelHandler 主要用来处理各种事件，这里的事件很广泛，比如可以是连接、数据接收、异常、数据转换等。

ChannelPipeline：为 ChannelHandler 链提供了容器，当 channel 创建时，就会被自动分配到它专属的 ChannelPipeline，这个关联是永久性的。

#### 9.Netty 发送消息有几种方式？

Netty 有两种发送消息的方式：

直接写入 Channel 中，消息从 ChannelPipeline 当中尾部开始移动；

写入和 ChannelHandler 绑定的 ChannelHandlerContext 中，消息从 ChannelPipeline 中的下一个 ChannelHandler 中移动。

#### 10.默认情况 Netty 起多少线程？何时启动？

Netty 默认是 CPU 处理器数的两倍，bind 完之后启动。

#### 11.Netty 支持哪些心跳类型设置？

readerIdleTime：为读超时时间（即测试端一定时间内未接受到被测试端消息）。

writerIdleTime：为写超时时间（即测试端一定时间内向被测试端发送消息）。

allIdleTime：所有类型的超时时间。

# mybitis

## 10条

### 1. #{}和${}的区别是什么？

\#{}是预编译处理，${}是字符串替换。

Mybatis在处理#{}时，会将sql中的#{}替换为?号，调用PreparedStatement的set方法来赋值；

Mybatis在处理${}时，就是把${}替换成变量的值。

使用#{}可以有效的防止SQL注入，提高系统安全性。

### 2. 通常一个Xml映射文件，都会写一个Dao接口与之对应，请问，这个Dao接口的工作原理是什么？Dao接口里的方法，参数不同时，方法能重载吗？

Dao接口，就是人们常说的Mapper接口，接口的全限名，就是映射文件中的namespace的值，接口的方法名，就是映射文件中MappedStatement的id值，接口方法内的参数，就是传递给sql的参数。Mapper接口是没有实现类的，当调用接口方法时，接口全限名+方法名拼接字符串作为key值，可唯一定位一个MappedStatement，举例：com.mybatis3.mappers.StudentDao.findStudentById，可以唯一找到namespace为com.mybatis3.mappers.StudentDao下面id = findStudentById的MappedStatement。在Mybatis中，每一个<select>、<insert>、<update>、<delete>标签，都会被解析为一个MappedStatement对象。

Dao接口里的方法，是不能重载的，因为是全限名+方法名的保存和寻找策略。

Dao接口的工作原理是JDK动态代理，Mybatis运行时会使用JDK动态代理为Dao接口生成代理proxy对象，代理对象proxy会拦截接口方法，转而执行MappedStatement所代表的sql，然后将sql执行结果返回。

### 3. Mybatis是如何进行分页的？分页插件的原理是什么？

Mybatis使用RowBounds对象进行分页，它是针对ResultSet结果集执行的内存分页，而非物理分页，可以在sql内直接书写带有物理分页的参数来完成物理分页功能，也可以使用分页插件来完成物理分页。

分页插件的基本原理是使用Mybatis提供的插件接口，实现自定义插件，在插件的拦截方法内拦截待执行的sql，然后重写sql，根据dialect方言，添加对应的物理分页语句和物理分页参数。

### 4. Mybatis是如何将sql执行结果封装为目标对象并返回的？都有哪些映射形式？

第一种是使用<resultMap>标签，逐一定义列名和对象属性名之间的映射关系。第二种是使用sql列的别名功能，将列别名书写为对象属性名，比如T_NAME AS NAME，对象属性名一般是name，小写，但是列名不区分大小写，Mybatis会忽略列名大小写，智能找到与之对应对象属性名，你甚至可以写成T_NAME AS NaMe，Mybatis一样可以正常工作。

有了列名与属性名的映射关系后，Mybatis通过反射创建对象，同时使用反射给对象的属性逐一赋值并返回，那些找不到映射关系的属性，是无法完成赋值的。

### 5. Xml映射文件中，除了常见的select|insert|update|delete标签之外，还有哪些标签？

注：这道题出自京东面试官。

还有很多其他的标签，加上动态sql的9个标签，trim|where|set|foreach|if|choose|when|otherwise|bind等，其中为sql片段标签，通过标签引入sql片段，为不支持自增的主键生成策略标签。

### 6. 简述Mybatis的插件运行原理，以及如何编写一个插件

Mybatis仅可以编写针对ParameterHandler、ResultSetHandler、StatementHandler、Executor这4种接口的插件，Mybatis使用JDK的动态代理，为需要拦截的接口生成代理对象以实现接口方法拦截功能，每当执行这4种接口对象的方法时，就会进入拦截方法，具体就是InvocationHandler的invoke()方法，当然，只会拦截那些你指定需要拦截的方法。实现Mybatis的Interceptor接口并复写intercept()方法，然后在给插件编写注解，指定要拦截哪一个接口的哪些方法即可，记住，还需要在配置文件中配置你编写的插件。

### 7. 一级、二级缓存

1）一级缓存: 基于 PerpetualCache 的 HashMap 本地缓存，其存储作用域为 Session，当 Session flush 或 close 之后，该 Session 中的所有 Cache 就将清空。

2）二级缓存与一级缓存其机制相同，默认也是采用 PerpetualCache，HashMap 存储，不同在于其存储作用域为 Mapper(Namespace)，并且可自定义存储源，如 Ehcache。要开启二级缓存，你需要在你的 SQL 映射文件中添加一行：<cache/>

3）对于缓存数据更新机制，当某一个作用域(一级缓存 Session/二级缓存Namespaces)的进行了C/U/D 操作后，默认该作用域下所有 select 中的缓存将被 clear。

### 8. Mybatis是否支持延迟加载？如果支持，它的实现原理是什么？

Mybatis仅支持association关联对象和collection关联集合对象的延迟加载，association指的就是一对一，collection指的就是一对多查询。在Mybatis配置文件中，可以配置是否启用延迟加载lazyLoadingEnabled=true|false。

它的原理是，使用CGLIB创建目标对象的代理对象，当调用目标方法时，进入拦截器方法，比如调用a.getB().getName()，拦截器invoke()方法发现a.getB()是null值，那么就会单独发送事先保存好的查询关联B对象的sql，把B查询上来，然后调用a.setB(b)，于是a的对象b属性就有值了，接着完成a.getB().getName()方法的调用。这就是延迟加载的基本原理。

### 9. Mybatis映射文件中，如果A标签通过include引用了B标签的内容，请问，B标签能否定义在A标签的后面，还是说必须定义在A标签的前面？

虽然Mybatis解析Xml映射文件是按照顺序解析的，但是，被引用的B标签依然可以定义在任何地方，Mybatis都可以正确识别。

原理是，Mybatis解析A标签，发现A标签引用了B标签，但是B标签尚未解析到，尚不存在，此时，Mybatis会将A标签标记为未解析状态，然后继续解析余下的标签，包含B标签，待所有标签解析完毕，Mybatis会重新解析那些被标记为未解析的标签，此时再解析A标签时，B标签已经存在，A标签也就可以正常解析完成了。

### 10. 简述Mybatis的Xml映射文件和Mybatis内部数据结构之间的映射关系？

Mybatis将所有Xml配置信息都封装到All-In-One重量级对象Configuration内部。在Xml映射文件中，<parameterMap>标签会被解析为ParameterMap对象，其每个子元素会被解析为ParameterMapping对象。<resultMap>标签会被解析为ResultMap对象，其每个子元素会被解析为ResultMapping对象。每一个<select>、<insert>、<update>、<delete>标签均会被解析为MappedStatement对象，标签内的sql会被解析为BoundSql对象。

## 虫手20

## **MyBatis简介MyBatis是什么？**

MyBatis 是一款优秀的持久层框架，一个半 ORM（对象关系映射）框架，它支持定制化 SQL、存储过程以及高级映射。MyBatis 避免了几乎所有的 JDBC 代码和手动设置参数以及获取结果集。MyBatis 可以使用简单的 XML 或注解来配置和映射原生类型、接口和 Java 的 POJO（Plain Old Java Objects，普通老式 Java 对象）为数据库中的记录。

## **ORM是什么**

ORM（Object Relational Mapping），对象关系映射，是一种为了解决关系型数据库数据与简单Java对象（POJO）的映射关系的技术。简单的说，ORM是通过使用描述对象和数据库之间映射的元数据，将程序中的对象自动持久化到关系型数据库中。

## **为什么说Mybatis是半自动ORM映射工具？它与全自动的区别在哪里？**

Hibernate属于全自动ORM映射工具，使用Hibernate查询关联对象或者关联集合对象时，可以根据对象关系模型直接获取，所以它是全自动的。

而Mybatis在查询关联对象或关联集合对象时，需要手动编写sql来完成，所以，称之为半自动ORM映射工具。

## **传统JDBC开发存在的问题**

频繁创建数据库连接对象、释放，容易造成系统资源浪费，影响系统性能。可以使用连接池解决这个问题。但是使用jdbc需要自己实现连接池。

sql语句定义、参数设置、结果集处理存在硬编码。实际项目中sql语句变化的可能性较大，一旦发生变化，需要修改java代码，系统需要重新编译，重新发布。不好维护。

使用preparedStatement向占有位符号传参数存在硬编码，因为sql语句的where条件不一定，可能多也可能少，修改sql还要修改代码，系统不易维护。

结果集处理存在重复代码，处理麻烦。如果可以映射成Java对象会比较方便。

## **JDBC编程有哪些不足之处，MyBatis是如何解决这些问题的？**

1、数据库链接创建、释放频繁造成系统资源浪费从而影响系统性能，如果使用数据库连接池可解决此问题。解决：在mybatis-config.xml中配置数据链接池，使用连接池管理数据库连接。

2、Sql语句写在代码中造成代码不易维护，实际应用sql变化的可能较大，sql变动需要改变java代码。解决：将Sql语句配置在XXXXmapper.xml文件中与java代码分离。

3、向sql语句传参数麻烦，因为sql语句的where条件不一定，可能多也可能少，占位符需要和参数一一对应。解决：Mybatis自动将java对象映射至sql语句。

4、对结果集解析麻烦，sql变化导致解析代码变化，且解析前需要遍历，如果能将数据库记录封装成pojo对象解析比较方便。

解决：Mybatis自动将sql执行结果映射至java对象。

## **Mybatis优缺点**

**优点**

与传统的数据库访问技术相比，ORM有以下优点：

基于SQL语句编程，相当灵活，不会对应用程序或者数据库的现有设计造成任何影响，SQL写在XML里，解除sql与程序代码的耦合，便于统一管理；提供XML标签，支持编写动态SQL语句，并可重用

与JDBC相比，减少了50%以上的代码量，消除了JDBC大量冗余的代码，不需要手动开关连接很好的与各种数据库兼容（因为MyBatis使用JDBC来连接数据库，所以只要JDBC支持的数据库MyBatis都支持）

提供映射标签，支持对象与数据库的ORM字段关系映射；提供对象关系映射标签，支持对象关系组件维护

能够与Spring很好的集成

**缺点**

SQL语句的编写工作量较大，尤其当字段多、关联表多时，对开发人员编写SQL语句的功底有一定要求

SQL语句依赖于数据库，导致数据库移植性差，不能随意更换数据库

**MyBatis框架适用场景**

MyBatis专注于SQL本身，是一个足够灵活的DAO层解决方案。

对性能的要求很高，或者需求变化较多的项目，如互联网项目，MyBatis将是不错的选择。

**Hibernate 和 MyBatis 的区别**

**相同点**

都是对jdbc的封装，都是持久层的框架，都用于dao层的开发。

**映射关系**

MyBatis 是一个半自动映射的框架，配置Java对象与sql语句执行结果的对应关系，多表关联关系配置简单

Hibernate 是一个全表映射的框架，配置Java对象与数据库表的对应关系，多表关联关系配置复杂SQL优化和移植性

Hibernate 对SQL语句封装，提供了日志、缓存、级联（级联比 MyBatis 强大）等特性，此外还提供 HQL（Hibernate Query Language）操作数据库，数据库无关性支持好，但会多消耗性能。如果项目需要支持多种数据库，代码开发量少，但SQL语句优化困难。

MyBatis 需要手动编写 SQL，支持动态 SQL、处理列表、动态生成表名、支持存储过程。开发工作量相对大些。直接使用SQL语句操作数据库，不支持数据库无关性，但sql语句优化容易。开发难易程度和学习成本

Hibernate 是重量级框架，学习使用门槛高，适合于需求相对稳定，中小型的项目，比如：办公自动化系统

MyBatis 是轻量级框架，学习使用门槛低，适合于需求变化频繁，大型的项目，比如：互联网电子商务系统

**总结**

MyBatis 是一个小巧、方便、高效、简单、直接、半自动化的持久层框架，Hibernate 是一个强大、方便、高效、复杂、间接、全自动化的持久层框架。

## **MyBatis的解析和运行原理MyBatis编程步骤是什么样的？**

1、 创建SqlSessionFactory

2、 通过SqlSessionFactory创建SqlSession

3、 通过sqlsession执行数据库操作

4、 调用session.commit()提交事务

5、 调用session.close()关闭会话

## **请说说MyBatis的工作原理**

在学习 MyBatis 程序之前，需要了解一下 MyBatis 工作原理，以便于理解程序。

1）读取 MyBatis 配置文件：mybatis-config.xml 为 MyBatis 的全局配置文件，配置了 MyBatis 的运行环境等信息，例如数据库连接信息。

2）加载映射文件。映射文件即 SQL 映射文件，该文件中配置了操作数据库的 SQL 语句，需要在 MyBatis 配置文件 mybatis-config.xml 中加载。mybatis-config.xml 文件可以加载多个映射文件，每个文件对应数据库中的一张表。

3）构造会话工厂：通过 MyBatis 的环境等配置信息构建会话工厂 SqlSessionFactory。

4）创建会话对象：由会话工厂创建 SqlSession 对象，该对象中包含了执行 SQL 语句的所有方法。

5）Executor 执行器：MyBatis 底层定义了一个 Executor 接口来操作数据库，它将根据 SqlSession 传递的参数动态地生成需要执行的 SQL 语句，同时负责查询缓存的维护。

6）MappedStatement 对象：在 Executor 接口的执行方法中有一个 MappedStatement 类型的参数，该参数是对映射信息的封装，用于存储要映射的 SQL 语句的 id、参数等信息。

7）输入参数映射：输入参数类型可以是 Map、List 等集合类型，也可以是基本数据类型和 POJO 类型。输入参数映射过程类似于 JDBC 对 preparedStatement 对象设置参数的过程。

8）输出结果映射：输出结果类型可以是 Map、 List 等集合类型，也可以是基本数据类型和 POJO 类型。输出结果映射过程类似于 JDBC 对结果集的解析过程。

**MyBatis的功能架构是怎样的**

![](..\..\images\mybatis\1.jpg)



我们把Mybatis的功能架构分为三层：

API接口层：提供给外部使用的接口API，开发人员通过这些本地API来操纵数据库。接口层一接收到调用请求就会调用数据处理层来完成具体的数据处理。

数据处理层：负责具体的SQL查找、SQL解析、SQL执行和执行结果映射处理等。它主要的目的是根据调用的请求完成一次数据库操作。

基础支撑层：负责最基础的功能支撑，包括连接管理、事务管理、配置加载和缓存处理，这些都是共用的东西，将他们抽取出来作为最基础的组件。为上层的数据处理层提供最基础的支撑。

## **Mybatis都有哪些Executor执行器？它们之间的区别是什么？**

Mybatis有三种基本的Executor执行器，SimpleExecutor、ReuseExecutor、BatchExecutor。

SimpleExecutor：每执行一次update或select，就开启一个Statement对象，用完立刻关闭Statement对象。

ReuseExecutor：执行update或select，以sql作为key查找Statement对象，存在就使用，不存在就创建，用完后，不关闭Statement对象，而是放置于Map<String, Statement>内，供下一次使用。简言之，就是重复使用Statement对象。

BatchExecutor：执行update（没有select，JDBC批处理不支持select），将所有sql都添加到批处理中（addBatch()），等待统一执行（executeBatch()），它缓存了多个Statement对象，每个Statement对象都是addBatch()完毕后，等待逐一执行executeBatch()批处理。与JDBC批处理相同。

作用范围：Executor的这些特点，都严格限制在SqlSession生命周期范围内。

## **Mybatis中如何指定使用哪一种Executor执行器？**

在Mybatis配置文件中，在设置（settings）可以指定默认的ExecutorType执行器类型，也可以手动给DefaultSqlSessionFactory的创建SqlSession的方法传递ExecutorType类型参数，如SqlSession openSession(ExecutorType execType)。

配置默认的执行器。SIMPLE 就是普通的执行器；REUSE 执行器会重用预处理语句（prepared statements）；BATCH 执行器将重用语句并执行批量更新。

## **Mybatis是否支持延迟加载？如果支持，它的实现原理是什么？**

Mybatis仅支持association关联对象和collection关联集合对象的延迟加载，association指的就是一对一，collection指的就是一对多查询。在Mybatis配置文件中，可以配置是否启用延迟加载lazyLoadingEnabled=true|false。

它的原理是，使用CGLIB创建目标对象的代理对象，当调用目标方法时，进入拦截器方法，比如调用a.getB().getName()，拦截器invoke()方法发现a.getB()是null值，那么就会单独发送事先保存好的查询关联B对象的sql，把B查询上来，然后调用a.setB(b)，于是a的对象b属性就有值了，接着完成a.getB().getName()方法的调用。这就是延迟加载的基本原理。

当然了，不光是Mybatis，几乎所有的包括Hibernate，支持延迟加载的原理都是一样的。

## **映射器**#{}和${}的区别

\#{}是占位符，预编译处理；${}是拼接符，字符串替换，没有预编译处理。

Mybatis在处理#{}时，#{}传入参数是以字符串传入，会将SQL中的#{}替换为?号，调用PreparedStatement的set方法来赋值。

Mybatis在处理时，是原值传入，就是把{}时，是原值传入，就是把时，是原值传入，就是把{}替换成变量的值，相当于JDBC中的Statement编译

变量替换后，#{} 对应的变量自动加上单引号 ‘’；变量替换后，${} 对应的变量不会加上单引号 ‘’
\#{} 可以有效的防止SQL注入，提高系统安全性；${} 不能防止SQL 注入
\#{} 的变量替换是在DBMS 中；${} 的变量替换是在 DBMS 外
<在mapper中如何传递多个参数

方法1：顺序传参法

> public User selectUser(String name, int deptId);<select id="selectUser" resultMap="UserResultMap"> select * from user where user_name = #{0} and dept_id = #{1}</select>#{}

里面的数字代表传入参数的顺序。这种方法不建议使用，sql层表达不直观，且一旦顺序调整容易出错。

方法2：@Param注解传参法

> public User selectUser(@Param("userName") String name, int @Param("deptId") deptId);<select id="selectUser" resultMap="UserResultMap"> select * from user where user_name = #{userName} and dept_id = #{deptId}</select>#{}

里面的名称对应的是注解@Param括号里面修饰的名称。这种方法在参数不多的情况还是比较直观的，推荐使用。如何获取生成的主键对于支持主键自增的数据库（MySQL）

> <insert id="insertUser" useGeneratedKeys="true" keyProperty="userId" > insert into user( user_name, user_password, create_time) values(#{userName}, #{userPassword} , #{createTime, jdbcType= TIMESTAMP})</insert>

parameterType 可以不写，Mybatis可以推断出传入的数据类型。如果想要访问主键，那么应当parameterType 应当是java实体或者Map。这样数据在插入之后 可以通过ava实体或者Map 来获取主键值。通过 getUserId获取主键

## **不支持主键自增的数据库（Oracle）**

对于像Oracle这样的数据，没有提供主键自增的功能，而是使用序列的方式获取自增主键。

可以使用＜selectKey＞标签来获取主键的值，这种方式不仅适用于不提供主键自增功能的数据库，也适用于提供主键自增功能的数据库

＜selectKey＞一般的用法

<selectKey keyColumn="id" resultType="long" keyProperty="id" order="BEFORE">

</selectKey>

## **Mapper 编写有哪几种方式？**

第一种：接口实现类继承 SqlSessionDaoSupport：使用此种方法需要编写mapper 接口，mapper 接口实现类、mapper.xml 文件。

（1）在 sqlMapConfig.xml 中配置 mapper.xml 的位置

<mappers> <mapper resource="mapper.xml 文件的地址" /> <mapper resource="mapper.xml 文件的地址" /></mappers>

（2）定义 mapper 接口

（3）实现类集成 SqlSessionDaoSupport

mapper 方法中可以 this.getSqlSession()进行数据增删改查。

（4）spring 配置<bean id=" " class="mapper 接口的实现"> <property name="sqlSessionFactory" ref="sqlSessionFactory"></property></bean>

## **什么是MyBatis的接口绑定？有哪些实现方式？**

接口绑定，就是在MyBatis中任意定义接口，然后把接口里面的方法和SQL语句绑定，我们直接调用接口方法就可以，这样比起原来了SqlSession提供的方法我们可以有更加灵活的选择和设置。

## **接口绑定有两种实现方式**

通过注解绑定，就是在接口的方法上面加上 @Select、@Update等注解，里面包含Sql语句来绑定；

通过xml里面写SQL来绑定， 在这种情况下，要指定xml映射文件里面的namespace必须为接口的全路径名。当Sql语句比较简单时候，用注解绑定， 当SQL语句比较复杂时候，用xml绑定，一般用xml绑定的比较多。

## **使用MyBatis的mapper接口调用时有哪些要求？**

1、Mapper接口方法名和mapper.xml中定义的每个sql的id相同。

2、Mapper接口方法的输入参数类型和mapper.xml中定义的每个sql 的parameterType的类型相同。

3、Mapper接口方法的输出参数类型和mapper.xml中定义的每个sql的resultType的类型相同。

4、Mapper.xml文件中的namespace即是mapper接口的类路径。

## **最佳实践中，通常一个Xml映射文件，都会写一个Dao接口与之对应，请问，这个Dao接口的工作原理是什么？Dao接口里的方法，参数不同时，方法能重载吗**

Dao接口，就是人们常说的Mapper接口，接口的全限名，就是映射文件中的namespace的值，接口的方法名，就是映射文件中MappedStatement的id值，接口方法内的参数，就是传递给sql的参数。Mapper接口是没有实现类的，当调用接口方法时，接口全限名+方法名拼接字符串作为key值，可唯一定位一个MappedStatement，


举例：com.mybatis3.mappers.StudentDao.findStudentById，


可以唯一找到namespace为com.mybatis3.mappers.StudentDao


下面id = findStudentById的MappedStatement。


在Mybatis中，每一个<select>、<insert>、<update>、<delete>标签，都会被解析为一个MappedStatement对象。
Dao接口里的方法，是不能重载的，因为是全限名+方法名的保存和寻找策略。


Dao接口的工作原理是JDK动态代理，Mybatis运行时会使用JDK动态代理为Dao接口生成代理proxy对象，代理对象proxy会拦截接口方法，转而执行MappedStatement所代表的sql，然后将sql执行结果返回。

# mysql

# redis

# 消息中间件

## kafka

## MQ

## RabbitMQ

# zookeeper

# linux

# nginx

# tomcat

# hadoop

# es

# 设计模式

# 总结

# 参考

[spring-55](<https://www.toutiao.com/a6586253099294261764/>)

[spring-10](<https://www.toutiao.com/a6775869522067849732/>)