---
title: Java面试题
date: 2020-07-20 22:55:42
tags:java
---

# spring

## spring核心

### 1.Spring IoC、AOP 原理

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

### 2.Spring Bean 生命周期

![](..\..\images\spring\spring-3.jpg)



这只是个大体流程，内部的具体行为太多，需要自行去看看代码。

### 3.Spring Bean 注入是如何解决循环依赖问题的

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

### 4.Spring 事务为何失效了

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

### 5.怎样用注解的方式配置 Spring？

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

### 6、SpringMVC 的流程？

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



### 7、Springmvc 的优点:

1. 可以支持各种视图技术,而不仅仅局限于 JSP；
2. 与 Spring 框架集成（如 IoC 容器、AOP 等）；
3. 清 晰 的 角 色 分 配 ： 前 端 控 制 器 (dispatcherServlet) , 请 求 到处理器映射（handlerMapping), 处理器适配器（HandlerAdapter), 视图解析器（ViewResolver）。
4. 支持各种请求资源的映射策略。

### 8. Spring 通知类型使用场景分别有哪些？

![](..\..\images\spring\spring-6.jpg)



### 9.IoC 控制反转设计原理？

**具体设计原理如下图：**

![](..\..\images\spring\spring-7.jpg)



### 10.Spring 如何处理线程并发问题？

Spring 使用 ThreadLocal 解决线程安全问题。我们知道在一般情况下，只有无状态的 Bean 才可以在多线程环境下共享，在Spring 中，绝大部分 Bean 都可以声明为 singleton 作用域。就是因为Spring 对 一 些 Bean （ 如 RequestContextHolder 、

TransactionSynchronizationManager、LocaleContextHolder 等）中非线程安全状态采用 ThreadLocal 进行处理，让它们也成为线程安全的状态，因为有状态的 Bean 就可以在多线程中共享了。

ThreadLocal 和线程同步机制都是为了解决多线程中相同变量的访问冲突问题。在同步机制中，通过对象的锁机制保证同一时间只有一个线程访问变量。这时该变量是多个线程共享的，使用同步机制要求程序慎密地分析什么时候对变量进行读写，什么时候需要锁定某个对象，什么时候释放对象锁等繁杂的问题，程序设计和编写难度相对较大。而 ThreadLocal 则从另一个角度来解决多线程的并发访问。 ThreadLocal 会为每一个线程提供一个独立的变量副本，从而隔离了多个线程对数据的访问冲突。因为每一个线程都拥有自己的变量副本，从而也就没有必要对该变量进行同步了。 ThreadLocal 提供了线程安全的共享对象，在编写多线程代码时，可以把不安全的变量封装进 ThreadLocal。

由于 ThreadLocal 中可以持有任何类型的对象，低版本 JDK 所提供的 get()返回的是 Object 对象，需要强制类型转换。但 JDK 5.0 通过泛型很好的解决了这个问题，在一定程度地简化 ThreadLocal 的使用。概括起来说，对于多线程资源共享的问题，同步机制采用了“以时间换空间”的方式，而 ThreadLocal采用了“以空间换时间”的方式。前者仅提供一份变量，让不同的线程排队访问，而后者为每一个线程都提供了一份变量，因此可以同时访问而互不影响。

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

![](..\..\images\spring\spring-11.jpg)



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

![](..\..\images\spring\spring-12.jpg)



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

![](..\..\images\spring\spring-13.jpg)



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

![](..\..\images\spring\spring-14.jpg)



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

![](..\..\images\spring\spring-15.jpg)



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

![](..\..\images\spring\spring-16.jpg)



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

![](..\..\images\spring\spring-17.jpg)





## spring mvc

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

## spring cloud

# doubo

# netty

# mybitis

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