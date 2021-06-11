---
title: Java Web技术与实践
date: 2021-05-12 17:50:10.000
updated: 2021-05-13 14:31:25.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/116716911
description: 按照MVC思想，Ajax 与json 技术。
servlet与jsp技术体系
JDBC DAO设计
SSH框架
web项目经典问题
web 应用概述
分类
B/S
http协议
静态与动态
web服务器与应用服务器
ASP 与ASP.net
servlet/jsp技术
web技术比较
servlet 、jsp 基础
servlet 基础
历史，特点
功能，运行过程，生命周期
主要功能
servlet 生命周期与运行过程
jsp 技术基础
MVC
内置对象技术
request
response
session
tags: Javaweb概述,web技术,spring
categories: javaweb
article_id: 116716911
---
﻿[toc]
# web 应用概述
## 分类
-  单机应用
- c/s
- b/s
## B/S
### http协议
无状态。
### 静态与动态
动态：需要服务器支撑。

### web服务器与应用服务器
1. web服务器：对浏览器请求的提供文档（html）。是一种被动程序。如apache
2. 应用服务器：作为服务器执行共享业务应用程序 的底层的系统软件。可以让多个用户使用一个用户应用。处理非常规性的动态web页面。
3. 两者兼具：如Tomcat。login.html->servlet,接收与响应 ->业务Login类。->DataBase

### ASP 与ASP.net
asp。由微软牵头，90年代流行技术。active server page。vbscript为开发语言
asp.net 。2002年。完全不同开发模式。与net framework。
### servlet/jsp技术
由sun公司牵头
servlet部署在浏览器与服务器的中间层。由web服务器加载，这个web服务器就得支持servlet的java虚拟机。

servlet是用java写的。
servlet是用java servlet api 写的统一接口。。所有的servlet实现javax，servlet，servlet接口。大多数servlet是针对http的web服务器。因此，通用的开发servlet的办法就是使用javax.servlet.http.httpservlet类。
httpservlet 类通过扩展GenericServlet基类继承Servlet接口，提供处理http协议功能。它的service()方法支持标准http1.1，用于处理htttp响应请求。
servlet 优点在于提供了大量的实用工具例程，如自动解码处理cookie等。

原来是在
```java
public void  doGet(请求对象，响应对象){
printwriter out =response.getWriter();
out.println("<htlm代码")；
}
```
写大多html代码了。后面，sun弄了个jsp 来代替out.println这样的写法。
jsp 不但继承了全部servlet功能，还增加了功能。html中插入java程序片段scriptlet 和jsp标记tag 形成jsp文件。
当时的优势：到处运行。移植。可伸缩性，集群和负载均衡。支持服务器组件，jsp可以使用javabeans组件来实现业务逻辑。

弱势：与asp一样，优势也是弱势。跨平台和伸缩力，导致复杂度。常驻内存，硬盘存储java文件，class文件。

### web技术比较 

| 指标         | servlt/jsp | asp.net | php      |
| ------------ | ---------- | ------- | -------- |
| speed        | fast       | 较fast  | 较fast   |
| 难度         | 容易吧     | 简单    | 简单     |
| platform     | 大部分     | window  | win/unix |
| 扩展         | 好         | 较好    | 差       |
| 安全性       | 好         | 较差    | 好       |
| 厂商支持     | 多         | 较少    | 多       |
| 组件         | y          | y       | n        |
| 分布式       | y          | y       | n        |
| 项目大小     | L M S      | L M S   | M S      |
| 服务器性价比 | 较贵       | 便宜    | 便宜     |
| 支持框架     | 多         | 少      | 少       |


# servlet 、jsp 基础
## servlet 基础
### 历史，特点
jsp 最终会被服务器转换为一个servlet。==在该技术出现以前== 服务器采用CGI技术。Common Gateway Interface公共网关界面，实际上是http服务器与计算机其它技术“交谈”的一种工具，是最早的动态网页技术之一。当时被用来处理表单输入，反馈信息，等这样交互功能，主要用perl shell script 或者c++写。

http->服务器->CGI->返回结果->服务器->用户（浏览器）
CGI技术开启了动态网页技术。
当时缺点：1. 开发困难，参数传递知识，这在当时不是通用技能。2. 不可移植。3. 在用户请求后激活，会话结束后被卸载，导致开销。

1997年，java 流行，servlet也成为主要动态网页开发技术。

与普通java程序不同，没有main方法，由如tomcat这样的容器来管理。==实际上是按照servlet规范来编写一个java类。==。

serlet 可以完成CGI相同功能，优点：
1.  使用内置对象，的支持，不需要处理参数传递及解析，开发容易。这也是解决CGI的缺点。
2. 因为是java ，移植。
3. 比CGI好的是，被 第一个请求激活后，能够继续在后台运行，每个请求一个线程。同时服务。也是解决了CGI的缺点。当时 （现在2021年了，CGI应该没有这个缺点了）

### 功能，运行过程，生命周期
#### 主要功能
用户创建的servlet是通过httpservlet派生的。httpservlet 拥有B/S服务功能，所以，没有特殊功能要求，没有必要扩展，只要对父类doGet做一些扩展即可。
主要方法有：
1. init().在servlet 生命周期中，仅执行一次。它是在服务器装入servelt时运行的。
2. destroy方法。仅运行一次，卸下servlet方法时执行。
3. service()。每当用户请求一个httpservlet对象，该对象service()被调用。且传递request 和response传给它。
4. doGet与doPost() 。由用户重写。

#### servlet 生命周期与运行过程
servlet没有main方法，受控于一个被称为容器的java应用程序 。如tomcat。当web服务器收到一个指向Servlet请求时，是交给容器先的，由容器管理了，
servlet容器：
1. 负责套接字，创建流。轻松让servlet与web服务器对话。
2. 控制 servlet生命周期。
3. 多线程功能，每个请求。
4. xml 配置容器。
5. 将jsp 转换servelt。
---

运行过程以tomcat为例：
1. tomcat 对web 应用服务器（其实是内置了）转发来的请求做出响应，并创建两个对象：httpservlet  request与response对象。
2. 根据url 找到正确的servlet（依据系统的配置文件完成），tomcat创建/分配一个线程（第一次请求该servlet是创建，以后是分配）（这里是线程重用，~~还是servlet重用？servlet 会只创建一次吗？~~ ），同时将1中两个对象传递给线程。 
3. 调用servlet 的service（）方法。
4. do方法
5. 返回response 。结束。



### jsp 技术基础
界面与业务功能
运行原理：首次访问时，jsp 转为servlet。其中提供相应内置对象。
语法见百度

javabean 组件，jsp通过<jsp:usebean》来实现。
而serlet本身就是java类，无缝集成组件 

### MVC
70年代就出现了计划。详见百度
详见百度。
实践出优势。
说下缺点：
1. 增加了复杂性。过多的更新操作，运行效率
2. v 与c 连接紧密。虽然分离，但实际联系交流紧密，v没有c是没有用的。反之亦然。
3. c 对m 访问效率低。当时是要多次访问，多次刷新。不过现在有ajax技术解决这个问题
4. 目前一此高级工具不支持mvc

其实，过去的问题都在补。起码2021年，mvc还是流行技术。对于程序 员来说，哪个好用，用哪个，哪个写代码少用哪个。对企业好，对自己不好，有什么用呢？

# 内置对象技术
## request
百度方法。主要是get 得到信息。
## response
response 主要是修改，设置，增加，删除。详见百度。

## session 
session与cookie的发展历程，我懂了，就不写了，不懂详见百度。

常用技术：
1. 多页面共享技术
	，登录后，保存数据共享区，给其它servlet 提供便利。
		在特定的情形下，多页面共享数据，是电子商务的一种解决方案，页面多货架，cart是多页面数据共享。现在可能不是这种方案了。
2. 安全控制技术
	绕过登录 
	设置时限
	安全退出 。
## application
实现了用户之间数据的共享。区别与session对象存放一个用户的共享数据，application存放所有用户的共享数据，开始于服务器启动，结束于服务器关闭。
applicatoin对象是servletContext的实例。

## out
代表向客户端发送数据。是printWrite类的实例。
## config 
一个servlet初始化时，jsp引擎向它传递信息用的。
## exception
异常处理对象，一个页面运行过程发生了异常，就产生了这个对象。iserrorpage
## page  与pagecontext
page指向jsp本身。有点像this指针
pageContext提供了对jsp页面内所有对象及名字空间的访问。比如访问本页所在的session对象。

# ajax技术
## 同步与异步通信
1. 同步：等待对方回应
2. 反之。

现在一般用json 交换数据异步。
Asynchronous JavaScript and XML
它是当时现有技术结合，不是新技术
3. css 与xhtml（2021年现在是html5）网页内容
4. dom 交互动态显示
5. xmlhttprequest请求
6. javascript来绑定与调用。

当时是直接写一个xmlhttpreques对象的。后面jquery 实现了封装。成了主流。现在2021年，有很多其它库，js。 现在，浏览器本身就有promise 异步支持。

使用方法见百度。我就不写重复的东西了。

# json 
见百度。 
要了解的是：
json 的数据类型有几咱。null是空。
语法规则 。
js下的json操作。
java下的json操作。好像现在是使用第三方库。起码java1.8（java8）是这样的。java14就不知道了.
# servlet进阶
百度一下serlet 架构图
## 常用类与接口
1. servlet 接口 interface。重写方法
2. 请求响应接口。interface httpservletrequest。
3. 会话跟踪接口
4. 上下文接口
5. requestDispatcher。这个是用于将请求转发给另一个servlet 或者jsp。forward（转发到另一个服务器资源 。）方法与include（把另一个服务器资源包括进来）方法。
## servlet配置
web.xml 文件
<seervlet-mapping > url上映射
## 过滤器技术
### 基本概念
filter是小型的web组件 
安全。
并不是标准的servlet。不能处理请求与响应
只能预处理httpservletrequest

拦截，修改，授权，日志，解码
### 生命周期与配置，部署，主要方法
#### 主要方法
所有实现了javax.servlet。filter接口的类被称为过滤器类。
init
dofilter
destroy
#### 生命周期
启动服务器
第一次请求只调用dofilter
停止服务器
#### 配置部署
web.xml
filter节点
### 过滤链
在web.xml定义的先后顺序 。如编码过滤器与安全过滤器

### 字符集转换及安全过滤器的开发。
用过滤器技术处理编码问题
new一个字符集，转换。设置htpp的头部。
安全器，则如登录 问题。accept 过滤一静态方法不作处理。

## 监听器技术
Listener 用于监听java web程序中的各类事件，是servlet规范中的特殊类，也需要在web.xml文件中注册配置才可以使用。Listerner监听着servletContext,HttpSession和ServletRequest等对象创建与销毁事件，以及这些域对象中属性发生了修改的事件。
有8种Listerner接口。6个Event类别。
Listener对应的Event详见百度。
被监听器对象,要实现的监听器接口，触发的 监听器事件。
1. 监听对象的创建和销毁事件。servletContextLIstener。
2. 监听对象的属性被修改。servletcontexattributelistener.
3. 监听对象本身状态的监听器。HttpSessionBindindin Listener 和HttpSessionActonListener。

使用示例：统计在线总人数。

# JDBC
详见百度吧。
## jdbc 接口和类介绍
### Driver接口
加载驱动类，注册该实例，

### DriverManager类
驱动路加载后，由它来管理了，静态方法。建立连接。
### statement preparedStatement和callableStatement
.statement是一个接口，。然后一堆的执行方法。
preparedstatement接口，是statement的子接口。占位符。
callableStatement是prepareStatement的子接口。
### ResultSet结果集
保存查询结果。
默认的Result结果集对象不可更新。当然，你可以生成可滚动可更新的结果集对象。这样比较强大点。
因为结果集与数据库相关联，所以与源表相关的，所以修改结果对象，达到同步更新数据库的目的。实际这种很少用。最好也不要用。
# 数据库访问层设计
## DAO
Data Access Object
从MVC中M 层分出来。
设计理念。常用的封装。
主要有两种思路：
第一种是可以针对 每一张表设计一个服务类。缺点耦合性强
第二种是不针对具体的表，目标是整个数据库。
目前好像是第一种多，如hibernate

面向抽象 面向接口
接口是不变的，实现的类（对象）变化 ，程序 去选择。甚至动态加载（比如spring框架）。

## DBUtil 
用于管理连接池。
思想：复用。
自己实现并不复杂。最好理解一下。虽然有大把现在的工具。实际情况，自己不会去开发连接池。

### 连接池的初始化
其实就是静态连接池。初始化的时候就分配好。
java中可以使用容器类。如Vector ，Stack等作。在init初始化好。
### 连接池的管理
管理策略。合理分配
很有名的设计模式：Reference Counting 。引用计数。==在利用资源方面有着非常广泛的应用==。它的基本思想是：为第一个数据库连接保留一个引用计数，用来记录该连接的使用者个数。：
1. 当客户请求连接时，看是否有空闲连接，有，则把该连接分配给它，连接的引用加一 。没有空闲，看是否达到了最大连接数。没达到则开一个新的连接到数据库，达到则等待，直至超时。
2. 如果在客户结束后，先判断引用次数是否超过了预定的规定值，超过了就删除该连接。并判断池内总连接数是否小于mincount，若小于则将连接池充满；如果 没有超过规定值，则将该连接标记为开放状态，可供利用。

保证了有效复用，避免频繁建立、释放，

### 连接池关闭
程序退出 时，要关闭连接池。

## 数据源与JNDI技术
数据源可以说是数据库的一种代替。一种引用，
DataSource代表一个数据源实体对象。
有了数据源技术，
与DriverMannager获取数据库连接相比，还是有优势的。比如不用像DriverManager那样硬编码。而是像在tomcat中配置web.xml文件，起一个别名，在JNDI中注册，该别名，最后，客户利用JNDI中找到这个别名绑定的数据源对象，这个对象可以连接实体数据库。
第二个优势是分布式事务与连接池。tomcat默认就有了连接池。
一般数据源与JNDI技术一起使用。
## JNDI
用于向Java程序程序提供目录与命令功能的API，被 设计于独立特定的目录服务，所以各种各样的目录都可以通过相同的方式进行访问。
可以简单的理解为一种将对象与名字绑定的技术。JNDI对象工厂负责生产对象，对象与名字绑定，外部可以通过名字获取对某个对象的引用。

目录服务用人类的理解来刻画各种各样的实体关系，。
从用户角度看，这是由于不同命名方案构成的复合名称。如URL就是这样。
> 在web 开发中，JNDI技术主要的作用是：通过表征数据源对象的逻辑名在JNDI的注册，利用名字与对象绑定功能。找到数据源对象，从而实现对数据库的访问。

## 配置数据源与连接池
web.xml 与context.xml
resource节点。

DBUtil ，有利于扩展，或者使用ORM框架，
## ORM 技术
Object Relational Mapping 对象映射技术。用于面向对象不同编程语言的数据类型转换。
面向对象是软件建模方法。
关系数据库是关系代数理论发展而来。
它们是不同的，因此解决不匹配问题，所以有了ORM。
从效果来说，可以说是创建了一个可以在编程语言里使用的虚拟对象数据库。
也就是说，可以直接在编程语言里使用update方法一样操作数据库。
Hibernate的出现代替了java原生的ORM与烦琐的EJB模型。。

### 核心思想
ORM核心思想是：需要解决的核心问题是对象数据与表数据之间的相互转换。java下转换对象成sql的相应字段，反之 ，xxx

其实之前 有说json 是解决了html与java 的问题。也是这种思想。

视角不一样，形态不一样。
### UserDao的设计
理论是来说与表的结构相对应。
但实际上可以与相应业务对应。返回的类型不一样。
### 分页处理技术
1. 传统的是结果缓存在HttpSession或者有状的JavaBean中。响应快。但数据量大的 时候，就内存多。。。。存在过期数据（数据库也是不断更新的）。
2. 二是，每次翻页都查一遍数据库，从ResultSet里取一页出来，但，如果每次都查数据库遍历整个数据库，速度就跟不上。
3. 第三种方法是：每次翻页时，只从数据库里检索出与页面大小一样的数据块。这样做，虽然每次翻页还是要查询数据库，但查询出记录少，因此速度快，。而且数据库查询是有优化的。
4. 还有一种是数据库有分页的功能，但是这种看数据库的，移植性差，重用性差。

主要还是利用数据库本身的一种查询方法优化。

### 文件上传与下载技术

jsp有这个功能

# SSH
spring spring MVC Hibernate

## maven 与Gadle
一般java选maven
android选Gadle
IDE选IDEA。有免费版的。

## spring 
为了解决JavaEE的开发慢

POJO  plain Old Java Object 简单的Java对象。的这样一种编程模型来促进编程体验。
然后JavaEE也跟着引进。。。。无语
1. 可以使用POJO 开发企业应用，不需要使用类似应用服务器DJB容器产品，而是选择一个强大的servlet容器如tomcat
2. 模块化组织，可选择性选择包，与其他框架集成，。
3. 不是将JavaEE推倒重来，而是利用现有技术，如orm，日志框架，JEE，quartz,JDK timers及其他视图技术。
4. 测试简单。因为依赖环境的代码被移动到了spring框架中。使用JavaBean风格的的POJO，依赖注入进行测试变得简单
5. 有个web框架，比struts好用
6. 方便api转换特定技术异为一致的异常
7. 比EJB容器轻量。
8. 一致的事务管理接口，可以缩小到一个本地事务，如单一数据库，。也可以全局事务。

两个重要功能：依赖注入与面向切面编程。
具体百度。

### DI 与IOC
1.依赖注入和控制反转
        Spring框架最显著的技术特征便是依赖注入（DI和控制反转（Inversion Of Control，IOC），控制反转是一个普遍的概念，它可以用多种不同的方式表达。依赖注入只是控制反转的一个具体例子。在编写一个复杂的Jav应用程序时，一个应用程序类应尽量独立于其他java类，并尽可能地重用这些类，在进行单元测试时也应可以独立于其他类进行单独测试。依赖注入提供了上述功能，既有助于将这些类粘合在一起，也能够同时保持它们相对独立。

     在传统的程序设计中，通常由调用者来创建被调用者的实例，而在依赖注入或控制反转的定义中，调用者不负责被调用者的实例创建工作，该工作由 Spring框架中的容器来负责完成，它通过开发者的配置来判断实例的类型，创建后再注入调用者。由于Spring容器负责创建被调用者的实例，实例创建后又负责将该实例注入调用者，因此被称为依赖注人。而被调用者的实例创建工作不再由调用者来创建，而是由 Spring容器来创建，因此也被称为控制反转。依赖注入可以通过将参数传递给构造函数或者通过使用 setter方法进行后期构造来实现。依赖注入是 Spring框架的核心后面将用相关的例子来解释相关概念。

==主要是在UML图中，如果 一个图总是只有向下的箭头并不 太好，有时候要向上==
### AOP

2.面向切面编程

 Spring的关键组件之一是面向切面编程（AO），它是面向对象编程（OOP）的补充和完善。在OOP中，通过继承、封装和多态性等概念建立起了多个对象之间的次结构关系，但是当需要为这些分散的对象加入一些公共的行为时，OOP就显得力不从心了。换句话说，OOP擅长的是定义从上到下的关系，但是并不适用定义从左到右的关系以日志功能为例，日志代码往往分散地存在于所有的对象层次中，而这些代码又与其所属对象的核心功能没有任何关系。像日志代码这种分散在各处且与对象核心功能无关的代码就被称为横切Cross-cutting-）代码。在OOP中，正是横切代码的存在导致了大量的代码重复，而且增加了模块复用的难度。这些横切代码在概念上与应用程序的业务逻辑分离，在日志、声明性事务、安全性、缓存等方面有许多常见的例子。

  AOP的出现恰好解决了OOP技术的这种局限性，AOP利用了“横切”的技术，将封装好的对象，找出其中对多个对象产生影响的共行为，并将其封装为一个可重用的块，这个模块称为切面（ spect），切面将那些与业务无关却被业务模块共同调用的逻提取并封装起来，于是减少了系统中的重复代码，降低了模块间的耦合度，同时提高了系统的可维护性。

      因此，OOP中模块化的关键单元是类，而在AOP中块化的单元切面D帮助解应用程序对象，而AOP帮助将横切代码与它们影响的象解后面将详细讨论更多有关 Spring AOP概念的内容。

==横向切面==

### 基于POJO编程模型

3基于POJO的编程模型

      Java开发领域的一大特色就是有大量开源框架可供开发人员选择和使用通常情况下，使用任何一种开发框架，开发人员编写的业务类都需要继承框架提供的类或接口，如此才能使用框架提供的基础功能，而对于 Spring框架，只需通过POJO就能使用其强大的功能。 Spring不强制依赖于其特定的AP，这称为“非侵人式”开发，能够让代码更加简单且更容易复用。
    
      pojo是软件开发大师 Martin Fowler提出的一个概念，指的是一个普通的Java类就说，随便编写一个Java类，就可以称之为POO。之所以要提出这样一个专门的术语，是为了与基于重量级开发框架的代码相区分。例如，B编写的类一般都要求符合特定编码规范，实现特定接口，继承特定基类，而POJO可以说是没有禁忌，灵活方便。此外，另外两个概念 JavaBeans、Spring Bean和POJO的概念经常联系在一起，下面简单加以介绍
   1. JavaBeans是一种Java规范定义的一种组件模型它包含了一些类编码的约定。==简单地说，一个类如果拥有一个默认构造函数，访问内部属性且符合命名规范的 setter和 getter方法，同时实现了io. Serializable接口，就是一个JavaBean遵守上述约定==，在编写或者修改一个类的时候，就能很容易地在可视化的开发环境中进行操作，也可以方便地分发给其他开发人员。

 2. Spring Bean 是被Spring维护和管理的POjO. 最早 Spring只能管理符合 Java Bean规范的对象，这也是为什么称之为Spring Bean的原因。但是，现在只要是POJO就能被 Spring容器管理起来，而且这也是最为常见的情况。

###  Spring框架结构
  Spring是基于JAVA平台的轻量级框架。在基于web应用基础上，修改扩展。它解决的是业务逻辑层与其它各层的松耦问题。因此，它将面向接口思想贯穿整个应用。
  良好的抽象。因此容易 组合其它框架。
  架构图见百度
#### 核心容器
1. 核心容器
    位于 Spring结构图底层的是其核心容器 Core Container， Spring的核心容 Beans、ore、 Context和SpEL（Spring Expression Language）模块组成， Spring的其他模块都是建立在核心容器之上的。
    
     Beans和Core模块实现了 Spring框架的基本功能，规定了创建配置和管理Bean的方式，提供了控制反转和依赖注入的特性。核心容器中的主要组件是 BeanFactory类它是工厂模式的实现， JavaBean的管理就由它来负责。 BeanFactory通过控制反转将应用程序的配置以及依赖性规范与实际的应用程序代码相分离。
    
     Context模块建立在 Beans和Core模块上，该模块向 Spring框架提供了下文信息。它扩展了 BeanFactory，添加了国际化（18N）的支持，提供了国际化、资源加载和校验等功能，并支持与模块框架（如 Velocity、 Freemarker）的集成。
    
     SpEL模块提供了一种强大的表达式语言来访问和操纵运行时对象。该表达式语言是在JSP2.1中规定的统一表达式语言的延伸支持设置和获取属性值、方法调用、访问数组、集合和索引、逻辑和算术运算、命名变量以及根据名称从IOC容器中获取对象等功能也支持list投影、选择和list聚合功能。


2. 数据访问/集成模块
    数据访问集成（Data AcceIntegr ation模块由DBC、ORM、OXM、MS和 Transaction模块组成.在编写DBC代码时需要一套程序化的代码， Spring的DBC块将这些程序化的代码进行抽象，提供了一个JDBC的抽象层这样就大幅减少了开发过程中对数据库操作代码的编写同时也避免了开发者去面对复杂的 JDBC API以及因为释放数据库资源失败而引起的一系列问题
    
      ORM模块为主流的对象关系映射（Object-Relation- Mapping）AP提供了集成层这些主流的对象关系映射API包括JPAJDO、 HibernateM和 ORM模块可以将O映射框架与 Spring提供的特性进行组合来使用。

OxM模块为支持 Object/XML映射的实现提供了一个抽象层，这些支持 Object/xmL映射的实现包括JAXB、 Castor、 XMLLBeans、JiBX和 XStream.

   jMs（Java Messaging Service）模块包含发布和订阅消息的特性。

    Transaction模块使用了对声明式事务和编程事务的支持，这些事务类必须实现特定的接口，而且对所有的POO都适用。

3. Web模块
     Web模块包括Web、 Servlet、 Struts和 Portlet4个模块。

     Web模块提供了基本的面向Web的集成功能，例如多文件上传、使用 Servlet监听器初始化IOC容器和面向Web的应用上下文，还包含 Spring的远程支持中与Web相关的部分
     
     Servlet模块也称为Web-M模块，提供了 Spring的web应用的模型视图控制器（M）实现，包含 Spring的MVC框架和用于Web应用程 Rest序的 Web服务的实现 Spring的MVC框架在域模型代码和Web表达之间提供了清晰的边界，并且还集成了 Spring框架的所有其他功能。
     
   WebSocket模块为基于 WebSocket的开发提供了支持，而且在eb应用程序中提供了客户端和服务器端之间通信的两种方式。
   
    PoletPortlet模块提供了在环境中使用Web-MVC的实现。
4. AoP Aspects、 Instrumentation和 Messaging模块
      AOP模块提供了在AOP联盟标准的面向切面编程的实现，使用该模块可以定义方法拦截器和切点
5. Test模块
Test模块支持使用 JUnit和 TestNG对Spri件进行单儿测试和集成测试它供了一致的Application Contexts并存上下文它还供了muck对象使得开发以独立地测试代码。

#### 依赖注入 

当开发一个复杂的Java应用程序时，每个v应用都会有很多对象起工作依赖注入有助于将这些类整合到一起，同时保它们相对独立假设一个应用程序有一个本编辑器组件，并且希望提供一个拼写检查功能标准代码如下
```java
public class TextEditor
 private Spellchecker spellcheckeri
 public TextEditor（）
 spellchecker＝new SpellChecker（）
```

代码中创建了一个文本编辑器和拼写检查之间的相关性，并且在文编辑器的构造函数中创建了一个拼写检查功能的实例。而在利用控制反转的情况下，代码如下:
```java
 public class TextEditor
 private Spellchecker spellchecker；
 public TextEditor （SpellChecker spellchecker）（
 this. spellchecker＝spellchecker；
```
  在这里，一个文本编辑器并没有考虑拼写检查的实现，拼写检查程序被独立实现，在一个文本编辑器实例化的时候提供给文本编辑器，整个过程由 Spring框架控制。上述代码已经从文本编辑器中去除了拼写检查功能的全部控制功能，并在其他地方对其进行配置（如XML文件），依赖性（即拼写检查器类）是通过一个的构造函数注到文本编辑器类中的因此，控制流已经被依赖注人“反转”A因为依赖关系已经被有效地授权到一些外部系统。这种依赖注入的方式是在文本编辑器的构造函数中进行的。

   目前主要的注入依赖方式是通过文本编辑器类的注解方式来实现的。从 Spring2.5开始，使用注解配置依赖注入是可行的。因此，可以使有关类方法或字段声明的注解将bean配置移动到组件类本身，而不再使用XMl来进行描述于注解的依赖注入在xML注入方式之前执行，因此，后一种配置将覆盖前者。
默认情况下， Spring容器中没有打开注解配置方式因此在使用于注解的配置之前，需要在 Spring配置文件中启用它，具体代码可以参考下面的配置文件。
`<context:annotation-config/>`


一旦＜ context: annotation-config-/＞被配置，应用程序就可以开始支持基于注解的代码，以指示 Spring自动将值连接到属性方法和构造函数中。下面的代码以注解的方式通过构造函数进行依赖注入，通过该代码可以理解它们是如何工作的，＠ Autowired注解提供了细粒度的控制，可以实现在哪里以及如何完成自动绑定当 Spring发现了一个使用＠ Autowired注解的方法后，它试图执行按类型自动绑定的方法。使用＠ Autowired注解到构造函数，当创建bean时构造函数仍将自动对参数进行绑定

### aop
这些术语不是针对spring的。而是与aop有关的。
![在这里插入图片描述](http://img.yayi.site/csdn/20210513142303806.png-watermaskStyle)
![五种通知![\](https://img-blog.csdnimg.cn/20210513142523110.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzUzMTk0MA==,size_16,color_FFFFFF,t_70)](http://img.yayi.site/csdn/20210513142526192.png-watermaskStyle)

### spring mvc 运行原理
 ![在这里插入图片描述](http://img.yayi.site/csdn/20210513142813755.png-watermaskStyle)

