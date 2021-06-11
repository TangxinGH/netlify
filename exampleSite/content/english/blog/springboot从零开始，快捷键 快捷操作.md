###### 首先建一个maven 工程
idea main方法的快捷键是psvm 回车。
maven 导入包，官方网站有
创建一个启动类。用注解。
ctrl alt L 是代码修改快捷键。
/在创建类的时候输入包名。加文件名，可以自动创建该包
也可用restController 即restful 嘛， 这相当于 controller 加 ResponseBody  json 写在body里嘛， 如果又要返回html 文件呢？ 自己百度。
因为从零开始，没有配置文件，我这里端口冲突了，因为spring 会扫描 res下的yml文件，所以我新建一个文件。
1.内容格式比较：
.properties文件，通过.来连接，通过=来赋值，结构上，没有分层的感觉，但比较直接。
.yml文件，通过：来分层，结构上，有比较明显的层次感，最后key赋值的：后需要留一个空格

2.执行顺序
如果工程中同时存在application.properties文件和 application.yml文件，yml文件会先加载，而后加载的properties文件会覆盖yml文件。所以建议工程中，只使用其中一种类型的文件即可。

打包部署： 
 			 maven 导入官方推荐的plugin 点击maven 找到lifecycle 双击package 即可在target中看到jar
 			如果error 试试配置 setting.xml文件，可能配置标签不配对。详见百度。cmd中java -jar 后 输入前几个字符，
 			tab    	   		 一下可以 补全。
 如果你的maven 一直是从repo下载，那么你的setting.xml可能有错误，导致IDEA 默认下载了
 
 starter parent 中进入源码中看，一堆版本。，仲裁中心，以后导入依赖说明是不用写版本的。如mysql，但有一些是没有的。
ｓｐｒｉｎｇ　ｂｏｏｔstart web 也叫场景启动器。已经导入了web 模块。如果你要做什么场景如 redis 啊，只需要在maven 中导入spring 的 相关场景启动器即可。版本由spring 控制。可以在github 中看到不同场景所需要的依赖示例子。


快捷键：  shift +空格  半角全角。


配置文件类，spring 注解标明是哪一个。
autoconfiguration  开启自动配置。，加上这个注解就会自动配置，就会自动配置。@import是底层的注解，导入组件到容器中。Registrar 类中，导入一些注解元数据，一个方法得到包名，debug一下，可以发现这是自己的项目中的包名，所以扫描包下面的包、类等，也就是那个SpringBootApplication注解的类那个包名。包下所有组件扫描出来 。


目前IDEA都支持初始化项目，new project 的时候可以dependencies 组件，就是上面pom中的web模块。IDEA中res 中是网页 ，templates 可以使用模板引擎 freemarker、thymeleaf。


		全局配置文件，修改默认值。yml 以数据为中心。xml 浪费了大量标签。yml 省标签，数据直观。yml 使用k : v 
		空格必须有！！！，
		空格来控制层级 关系。
		属性和值大小写敏感。
		值的写法：普通、对象、Map (k,v)、数组(list、set)。注：普通值如果是字符串，双引号不转义，单引号转义（原样输出）。
==快捷键：alt +Insert  自动生成 get set 代码，dao pojo 的时候很有用，如，返回或设置属性。== 不用手写。！！！！！也可以alt insert 重写to string 方法。
			

```bash
参照下面链接，
类从配置文件中获得值，注解configurationproperties。
其中 prefix 是指定要yml中那么多属性，是哪个装填。还是报错。
导入一个依赖可以在yml 中看到提示。
但还是报错。参照下面链接。
Not registered via @EnableConfigurationProperties or marked as Spring component
没有在自动装填中注册，或者标志为一个spring 组件。
添加后错误确实是没了，但是在SpringBoot的单元测试时会看到错误
 回到自定义的bean Person中，添加注解@Component，声明将这个组件添加至容器中，这样才可以被使用？
==“只有这个组件是容器中的组件，才能使用容器提供的@ConfigurationProperties功能,”==
？？？？ 组件元数据，类元数据，配置元数据，底层元数据。？？
```
[https://www.cnblogs.com/Guhongying/p/10848251.html](https://www.cnblogs.com/Guhongying/p/10848251.html)


```css
单元测试：
	 

 1. spring unit
  从零开始，所以要手动加，如果用IDEA创的话，就不用。
  pom.xml 引用test.
  RunWith（xxx.class） ：指定用xxx驱动器来跑。
  springBootTest 注解说明这个类是测试用。
  可以在测试期间方便像编码一样自动注入容器的功能。用AutoWired注入。
  可以进行局部测试，很方便。
 2. toString 
 	重写了这个方法，所以system.out.println 是不一样的。不重写输出的只是地址。
 	
 3. 总结
 	配置文件怎么写，
 	JAVABEAN：长得是什么样，像POJO，entiy之类的。
 	maven导入配置依赖，
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-configuration-processor</artifactId>
            <optional>true</optional>
        </dependency>
作用就是在yml中配置可以看到提示而已？自动补全之类的。驼峰写法，或者用-代替大写。
要加在容器中用component。
两个文件的配置的区别，先后覆盖情况，用一个就行了。properties文件可以设置编码。
```

``
除了用configurationpropeties 加prefix之外，另一种方法。用value注解，在以前，<bean>标签 class ,<property> 中写value，这里作用是差不多的，spring 底层的东西。以前值支持的写法（￥ #），现在也支持。 只不过要一个个指定。value不支持-的转化。（松散语法。） value 支持表达式语言。configuration 支持数据检验，复杂类型的取值。用validated 注解检验，与configurationproperties一起使用。对属性检验。
业务逻辑中，只取一个值，用value方便。专门的JavaBean来映射配置文件的话，就用configuration
``
```

 1. @PropertySource
 	加载指定配置文件，上面的configurationProperties 是全局的，文件太大。@propertySource可以指定文件，不会去默认的全局中寻找。指定类路径下的配置文件。
 	只能Properties 文件，
 	而且不能省掉@ConfigurationProperties，不然会报错。
 2. @ImportResouce
 	导入Spring 的配置文件，并让配置文件生效。如：bean中的xml 自己配置文件，测试单元中，看容器中有没有这个id 
 	@Autowired
    ApplicationContext ioc;

    @Test
    public void testHelloService() {
        boolean b = ioc.containsBean("helloWordService");
        System.out.println("容器中是否有bean 配置，id 为hellowordService的配置:" + b);


    }
以前是用Bean xml 之类的配置的，现在不知道。然而spring 不推荐怎么做。
spring 推荐给容器加组件的方式是：
	1、配置类 
				用注解的方式来加组件。
				新建一个类，用@Configuration 开标明这是一个配置类。
				以前是用<bean></bean>来添加组件的，现在配置类里，用@Bean注解一个方法。
				方法返回值做为组件添加到容器中。容器中的组件 默认的ID就是这个方法名。
				return 一个new xxx;
				
```
````

 3. 配置文件占位符
 		在配置文件中，用＄{random} 之类的，也可以取变量（变量不存在则原样表示，也可以冒号指定默认值 ）。
 		占位符是什么意思？
 		
````

 4. Profile
 

```c
profile 是在不同环境中，提供支持，方便切换环境，如开发，部署环境。
文件名规范： application-环境标识.yml/properties
如端口号。
sprig.profiles.active=dev 激活配置。 dev 是环境标识
yml 多文档模块 ： 在ymL 中使用 --- 三条杠，分成多个文档块。然后由上面那个的激活来看是谁激活的。
命令行也可以激活，在IDEA中的RunConfiguration 中的Program Arguments 输入--spring.profiles.active=dev
IDEA 中的RunConfiguration 虚拟vm options 配置也行，-Dspring.profile.active=dev
还可以打包完成后在cmd中 java -jar spring tab .jar --spring.profiles.active=dev 开启。
```
spring 配置文件可以 在file 路径下，也可以在file:/config/下，也可以在 classpath下，classpath:/config
优先从 xx:config 搜索，有优先级的。resouce 下是类路径？？？建一个config，下的，先搜索。 当前项目文件是file:  可以建一个config文件夹，
优先级： file:/config> file:>classpath:config>classpath:  优先级大的会覆盖优先级小的。全部加载，没有冲突就互补配置。
可以改变默认的配置文件位置：在配置文件中指定另一个位置： spring config.location ，类似上面手动写cmd 

==在实际项目中 当配置改变时，重新启动的时候cmd输入一个 配置路径，加载新的配置，旧的配置也会生效（互补）。==

外部的配置依然是有顺序的，同理。
命令行优先级高，带profiles 的优先高，外的大于内的。空格隔开多个配置 ，也可以外部，不用命令行输那么多。详情官方文档，百度。
```

 1. spring自动配置原理
  yml 能配置什么，看官方文档。
  EnableAutoConfiguration  扫描meta-inf/spring factory，返回组件加到组件 中，enableconfiguration 中的 class ，值加载进来。xxxautoconfiguration 类自动加载。
  以httpencodinATUOconfiguration  
  @configuration 配置类，
  enableconfiguration auto ，启动自动配置。properties.
  点击进去，conditionalonwebapplication 判断是不是web应用，配置生效，否则不生效。 条件判断，on 后面是条件
  
  如果配置生效就会添加组件，组件的属性是从对应的properties中获得的，这些类中，每一个属性又是和配置文件绑定的，所以我们能配置什么，主要看自动配置这个类有什么

```
 springboot 启动会加载大量自动配置类，我们需要的功能如果springboot 有默认写好的配置，
如果有， 我们看这个自动配置类中到底配置了那些组件，我们要用的组件，有的话，就不用配置，如果没有这个组件的配置，就自己配置，。
	  给容器中自动配置类添加组件的时候，会从properties 类中获取的属性，我们可以从配置文件中指定这些属性，
	  autoconfiguration 自动配置类，给容器添加组件，会有对应的xxxproperties封装文件中相关发属性。
	  conditional 扩展注解，百度，官方文档。
```bash
在yml 中打开debug=true 作用是在启动的时候会报告，使用了哪些自动配置类，控制台会输出哪些控制类生效了。
POSITIVE match 是匹配的， negetive match 是不匹配的。
```

## 3. **日志**
日志 代码 System.out.println(""); 大多控制台太乱，注释麻烦，更改到保存到文件也麻烦。
日志功能增加，高大上功能： 异步模式输出，而不是I/O中断，日志自动归档功能？ 
用框架.jar 。
哪天，这个框架不适合了，换新的框架，修改API，
那就，想想JDBC。 改为接口编程，不用修改API，日志抽象层.jar ；面向这个抽象层编程。在项目中导入日志。
框架常见的有、、、

日志门面：抽象层
日志实现：实现

这两个各选一个框架，门面选SLF4j ，实现是Logback (log4j2 暂时等多点人用先，好用，以后用这个，学习先用logback)。

```bash

 1. SLF4j使用
  日志调用应该调用门面类，而不是实现类。
  参考官方文档，import Logger. 官方有一张图，关于实现类的实现，不实现的话，输出的是空。导入Logback.jar SLF4j 会去自己调用。 log4j 还要适配器，适配层。
实现类的框架有配置文件，我们配置的是实现层的框架的配置文件。
 2. 问题
 	不同模块、不同框架，用的是不同日志框架，统一太难。即使，底层用的是不同日志框架。
 	通过统一使用某一框架进行输出 。看官方文档 legacy APIS 中。 统一使用，SLF4j 。那就要去/换掉其它日志框架的依赖，这会运行不起来。所以用一个狸猫换太子的方法，中有一个适配层 又调用了指向SLF4j来实现，
 	
 	
 3. 日志统一步骤
 	a、排除其它框架的日志框架。如spring ,
 	b、用中间包替换原有日志框架，
 	c、导入slf4j其它的实现。
 	
 4. IDEA中的maven
 	快捷键，pom.xml 中用右击 选Diagrams 可以看到依赖的关系图。
 	

```
![在这里插入图片描述](http://img.yayi.site/csdn/20200119162548993.png-watermaskStyle)
根据关系图，我们知道了springboot 使用slf4j+logback ,springboot 把其它日志替换成了slf4j
进入源码中，可以看到，apache的日志中，new 的却是slf4j , 这里就进行了替换。包名不变（不会not found）内部new 变化而已。

中间转变包：转换用的。

spring 已经做好了，
如果引入其它框架，移除掉原来日志框架的** 依赖 **，因为，因为包名类名相同会冲突。
spring 给出了排除的示例，在pom.xml中。
             

```clike
   <exclusion> 标签就是排除作用。
```
所以ｓｐｒｉｎｇｂｏｏｔ　自动适配了框架，要做排除的是引入其它框架的时候，要排除操作。

因为springboot 默认使用了slf4j logback 所以直接用就行了。
  //日志的级别 可以调整输出的信息，只看需要的信息
  //springboot 默认使用info及以后的级别，可以在配置文件中调整，
  logging:
  level:
    HelloWord: trace 指定到相应的包名。

也可以输出到相应的文件。而不是控制台。logging.file  logging.path

 1. logging.file 
 	在,好像是在项目的根目录下
 	可以用绝对路径。
 	比path 优先级高点
 2. logging.path
 	 相对路径。
 3. pattern  输出格式
 源码级别的修改》》
    
  自己配置文件的话，在类路径里放一个xxx.xml 或者 xxx-spring.xml参照官方文档springboot 了logg 章节，找到jar 复制一份改改。就行。
  xxx-spring.xml 命名,官方的话，可以进行一些高级功能，如指定环境使用。功能 springprofile。

```bash

 1. 切换日志框架
   在关系图中maven 选中logback-classic ，右击 exclude 排除掉logback
   log4j-to-slf4j 也去掉，因为这是要替换log4j用的，现在我们就需要切换为log4j，所以不用转换包。所以去掉这个。
   因为我是从零开始的，所以还要导入 log4j ，IDEA 自动创建的，就不用，反正看依赖图。
   
 2. 总结
  按照slf4j官方的网站的适配图，在maven 中 排除的排除，增加的增加。
  spring 官方支持log4j2 所以 按官方的走、切换。

```
![在这里插入图片描述](http://img.yayi.site/csdn/20200119190455363.png-watermaskStyle)
Please initialize the log4j system properly. 这个问题是没有初始化配置文件问题，在resoucre 下新建一个配置文件，初始化一下就行。
  
## springboot 开发
 

 1. IDEA 向导创建

 springboot 场景已经部署好了，只要在配置文件中配置一下就好。
 

 2. 自动配置
 	 这个之前已经学过了，springboot 帮我们配置了什么，现在，我们能改什么，不能改什么。
 	 在依赖jar 中 找一下AutoConfiguration 可以看到 配置了什么。

 3. 静态资源映射
  		
==快捷键ctrl+n是全局搜索，ctlr+f 是当前文件，不同的！！！==

 public void addResourceHandlers(ResourceHandlerRegistry registry) { 这个是资源映射配置类，自动配置类， 
 		其中有一个webjars的官网 将前端框架以maven的形式使用。 
/**  没有人处理的话，默认去classpath:下等等 找，看源码就知道。

 4. 模板引擎
   	因为不支持jsp，纯html开发，表达式之类的东西不能用。所以使用模板引擎。其它就是jsp差不多，最后渲染成html。
   	只是语法不一样而已。
   	thymeleaf:
   				a、引入thymeleaf,去spring 官方复制一下thymeleaf的依赖怎么写和配置。github搜索对应版本layout
   				b、看懂英文。spring中也自动装配了thymeleaf ，可以去源码看一下配置了什么东西。
   				c、在templates/html 中语法，会自动渲染，为什么会自动渲染，因为上面自动装填了。
   				d、==<html 标签中 xmlns:th="url"加了这个会有语法提示，url是官方网站？？==
   				e、th：可以替换原来的值。参照官方文档。可以使用内置对象。
   				

 5. SpringMVC 的自动配置
 	 springboot 官方文档：已经配置好了：
 	 		ViewResolver 视图解析器；根据方法返回值得到视图对象。这个对象决定如何渲染转发等。
 	 	自动可以定制解析器，自动的组合起来。仿照源码的方法。
 	 	 静态资源的配置
 	 	 还有 自动注册了Converter ：转换器。 如：public string hello( User user){} 如果发请求带的数据与user 一一对应，则封装好，因为提交是文本，要转换为类型，如18 变为 int 18 ; Converter也是一个组件。
 	 	 Formatter: 格式器。作用：数据格式 化。这些组件也自动注册了，在源码中的webmvcautoconfiguration.java 中，crtl + n 搜索。
 	 	 httpMessageConverters  ：spring mvc 用来转换http请求和响应的。 user 转换成json 写出去之类的。是从容器中确定的。
 	 	 定制的话，向容器注册自己的就行。官方文档有写。

 6. 修改springboot默认配置
 		@bean @conditionmissingxxx 没有就new 一个，其实，springboot是看有没有用户自己定义的，如果有，则不用springboot 自己自动配置的，没有，则用spring 自己的。或者 都用，或者互补。
 

 7. 扩展springMVC
 		 可以写一个配置类，用注解标明这是一个配置类。以前spring mvc 是xml中写<mvc:> 之类的.
 		 扩展wevmvc configureradapter 源码中有这个例子。所以会看源码？？
 		 注册 增加 之类 的。super...
 		 @enalbemvc 是自已全面接管springmvc ，不要springboot 帮我们配。知道就行。

8. 国际化
   国际化配置
   ResourceVundleMessageSource管理国际化资源文件。 
   在页面使用fmt:message取出国际化内容
因为springboot 做好了，我们要做的是配置国际化配置，抽取要国际化的元素。
写规范的文件名，IDEA就会识别你要做国际化，右击， 点进去，然后 加号 。下方 是resource Bundle。
在源码中看到，springboot 已经自动配置好了管理国际化资源文件的组件。只需要在配置文件中年指定配置文件夹就行。

去页面取，在模板引擎中 #号 就是国际化用的。 th: xx=#{}。 input 是自闭标签，所以用 模板引擎的 inlining 表达式。 即双中括号。注意properties 文件编码问题，在IDEA中设置编码保存，可以设置全局默认utf-8。

Locale(区域信息对象)；localeResolver 获取区域信息，源码自动配置中也有（从request中获取）。Accept-Language。所以可以在链接上带上区域语言？l=zh-CN  get 参数上带上，模板引擎用的是小括号，k v  会自动渲染的。然后写一个自己的区域解析器，从request获取，new locale 然后在自己的配置类中添加一个@Bean 作为组件添加

@requestmapping(value,method =xxpost限定post) 。spring 可以直接用postmapping限定post 就行，不用写这么长。
putmapping deletemaping 还有这种东西？？？

参数时可以 用@requestparam 限定，没有提交相关数据会报错。

```bash
stringuitls.isEmpty 这个是spring的工具，挺好用的，不用自己写null之类的。
```
==开发的时候，禁用模板缓存 spring.thymeleaf.cache=false，不然结果不能实时看到。==
  ==ctrl +F9 重新编译一下文件。不然浏览器看到的代码不一致。IDEA==
  模板引擎是可以在 控制器中方法参数作为设置变量，作为参数，这个配置 应该是spring自动帮我们配置的。
  
 注意： 重定向F5是不会重复提交表单的。springmvc 是加redirect 。默认的却不是重定向，重定向因为配置了路径映射，所以可以直接输入地址访问，。所以弄个拦截器。
 spring 中可以使用spring 带的 handlerInterceptor 实现这个接口即可。写个拦截类。session存个。这样就不用在控制器中判断。代码量多难看。未登录使用getRequestDispatcher 获得转发器，转加登录页。forward

 -  Restful风格
	*  一种风格： 如emp 不同的请求方式代表不同的意思 get 、post、put、delete。emp{id}。意思规范明了。
 ```
控制器方法参数中的变量都是放在请求域中共享的。
spring MVC 与入参参数 的javabean 对象的性情名一样就可以自动装填。
 ```

- 定制错误错误响应
	* 定制页面：源码中有配置，看看。
	
### Docker
 - 一个容器技术，
 - * 类似于window镜像，装好了各种东西，装好的环境，Docker支持将已经安装好的配置环境，打包成镜像，别人就可以用了。虚拟技术，软件编译成镜像，每个软件隔离开，启动速度快。环境的快速统一部署快，不用一个个配置，类似如window 的ghosts 镜像安装。
-
```
- 安装docker,  再安一个客户端来操作docker， docker仓库是用来保存镜像，仓库官方的是公共的，也可以使用自己的仓库，docker去镜像就是软件打包好的镜像。
- 运行一个镜像就会产生一个容器，如mysql 镜像，就会启动mysql 容器。
- 多运行几次同一镜像，就是多开应用了。关闭容器就是关闭应用了，启动同理。
- 随开机启动则要系统命令 不然重新就关掉了，因为是个软件嘛。
- 使用方法，百度。window linux 
- -d是后台运行，映射端口，容器内部端口。注：linux 防火墙要开放相应端口。
- docker logs ID 可以看相关日志。启动不了的时候。
- mysql run 的时候要指定 使用正确的命令。看官方文档。可以挂载外部配置文件。
```
### spring Data 
springboot 使用spring Data 管理，不管是关系型还是非关系型。
starter 启动器，starter data  官方文档有相关介绍。
- IDEA 向导中 选mysql 是加载驱动的，选JDBC 是连接的，实验先这个JDBC，后期再用JPA，mybatis之类的。看pom.xml 就知道向导不同选择引入了什么。
- 数据源： 在springboot 中的datasource 中看到了自动配置相关，当类路径下有 sql 或者schema-*.sql 、data- * 文件时，会执行该文件？？？这也是发布项目给别人的要注意地方。如果不是这种命令的话，可以，在 yml 里设置指定文件 schema -classpath:xx.sql 。2.2.x版本以上要 写initialization-mode:always
==只加一次sql文件就行了，不要多，因为每次启动都要执行，开发的时候不用，发布的时候用，或者加些条件语句阻止一下，一次性有效就行。==
- 操作数据库 在有数据源的情况下，SPRING 还配置了JDBCTemplate 相关，如果如果使用其它的而不是JDBC，spring 同理，配的也是其它了。
- 底层数据源。
	* Druid  实际开发中，数据源，看官方文档，现在应该已经配置很简单了。md,全是英文。。。
	* 因为Druid有一些高级功能。配置一些监控功能。等，spring有配置，还是要自己加组件？？加配置？
	* //配置一个后台管理的Servlet
	* ```
	光标定位到chrome浏览器地址栏有五种办法(不同浏览器快捷键不同，不过下面五种总有一种能帮到你)：

0)Alt+D;

1)Ctrl+L;

2)Ctrl+K;

3)Ctrl+E;

4)F6。

他们之间还有些小差异0、1会选中已有内容；2、3会替换内容为"?",你之后的输入会作为搜索关键词；而4)其实是控制窗口焦点的移动。


————————————————
版权声明：本文为CSDN博主「一个很酷的人」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/Hi_Boy_/article/details/95207365


一、Servlet简介
　　Servlet是sun公司提供的一门用于开发动态web资源的技术。
　　Sun公司在其API中提供了一个servlet接口，用户若想用发一个动态web资源(即开发一个Java程序向浏览器输出数据)，需要完成以下2个步骤：
　　1、编写一个Java类，实现servlet接口。
　　2、把开发好的Java类部署到web服务器中。
　　按照一种约定俗成的称呼习惯，通常我们也把实现了servlet接口的java程序，称之为Servlet

二、Servlet的运行过程
Servlet程序是由WEB服务器调用，web服务器收到客户端的Servlet访问请求后：
　　①Web服务器首先检查是否已经装载并创建了该Servlet的实例对象。如果是，则直接执行第④步，否则，执行第②步。
　　②装载并创建该Servlet的一个实例对象。 
　　③调用Servlet实例对象的init()方法。
　　④创建一个用于封装HTTP请求消息的HttpServletRequest对象和一个代表HTTP响应消息的HttpServletResponse对象，然后调用Servlet的service()方法并将请求和响应对象作为参数传递进去。
　　⑤WEB应用程序被停止或重新启动之前，Servlet引擎将卸载Servlet，并在卸载之前调用Servlet的destroy()方法。 
原来来自百度  
```
什么是servlet 实现了这个接口的，程序，去向浏览器输出数据，一个对象，
？？
```
IDEA 扩展屏幕，以浮动方式比较好，因为，点击IDEA ，所有的浮窗就会顶层显示，不在IDEA的时候，就是普通的窗口。
 1. Druid 配置一个后台监控servlet ，是可以/druid 访问的。![在这里插入图片描述](http://img.yayi.site/csdn/20200121215148763.png-watermaskStyle)
```
 2. 注解版Mybatis
 - 写一个接口，注解@Mapper 写明这是batis的一个操作数据库的Mapper
 - @Mapper //这个注解只有引入Mybatis才不会报错。可能是Mybatis里的 


```

```

 3. 配置版
 - 官方有配置例子全局。
- mapper.xml与命名空间 与接口 一致。
```

##### 整合ＪＰＡ
- springData 简化数据访问模块。官方文档。
- 提供统一接口， Repository ， crud 分页。模板类，访问。
- app 面向 springdata (里面的 repository、templates、object Mapping)，。
- jpa 是由springData 管理，jpa 关系性数据库，持久层api。
- jpa 的注解 有如： @entity , @id , jap 的底层是由hibernate 和其它一些实现。的。
- jpa 也是ORM(object relational mapping) 对象关系映射。
	- ：实体类bean 和数据表映射，并配置好映射关系。？
	- //配置映射关系，要使用JPA映射关系。
@Entity //告诉 JPA 这是一个实体类（和数据表映射的类
@table @id @generatedvalue 官方文档。省略值就是默认方法名，属性名。
	- 编写一个DAO接口来操作实体类对应的实体表。是一个接口？，JPA spring 为统一接口继承。所这个接口继承JAP 提供的接口就有基本的功能了。japrepository <实体类，主键类型>
	-  jpa:
    hibernate:
     更新或者创建数据表，没有就创建
      ddl-auto: update
      控制台显示sql语句
    show-sql: true
    基本的配置。
    
 ### Springboot 启动配置原理。
 	- 启动原理。
 		* run()
 			- 执行APPlicationContextInitializer.initalize();
 			- 监听器SpringApplicationRunListeer回调contexPrepared
 			- 加载主配置类定义信息
 			- 监听器，springapplicationrunlistener回调contexloaded 
 			说明：创建application对象， 调用initalize方法，保存主配置类，web环境类，现在2.x版本的已经不
 			一样了，meta-inf 配置类，spring factories。 从类路径下配置所有，找到listener ，找主方法类，可以
 			多个的，启动类多个，main方法，如多模块的时候会有用。
 			环境准备完成就会回调，开始创建容器，准备上下文，回调之前保存的initalize ，监听器，容器，
 			preparecontext完成后，回调，apprunlistener， 刷新容器，完成容器创建完，此时tomcata也启动
 			了。从容器中获得所有runner commandrunner进行回调。整个启动完成后，返回conetext。
 			回调机制，appcontextinitalizer springapprunlistener 在meta-inf factories 中，springruner 
 			commandlineruner 是要加在容器ioc中的。 refreshcontext 是扫描加载创建所有组件的地方。
	我们可以自己创建一个实现类开看看。泛型类？？
 		* springboot -starter场景启动器，配置好了，少量配置，自定义start场景。
 		 这个场景使用的依赖是什么，有了依赖需要自动配置是什么。参照以前的，使用configuration注解。onmissing
 		 条件成立生效，启动场景顺序，参照源码。
 		 @bean 组件。 
 		 @configurationProperties结合相关xxx.properties来绑定。
 		 @enableconfigurationproperties//让xxxproperties生效加入容器生效，自动配置。自动配置要生效要放在classpath 下的meta-inf/spring.factories文件。
 		 模式：启动器只用作依赖导入； 所以要专门来写一人自动配置模块； 别人引入starter就行。
 		 
 			
 ### 缓存
 	缓存规范：JSR107。
 	CachingProvider、CacheManager、 Cache（Map形式存储）、Entry （存储在Cache组件 中的key-value对）、Expiry（有效期）。
 	我们通过CacherProvider 来管理CacheManager 依次层次管理。可以多个提供者。

```bash
Spring使用了缓存 抽象 。兼容js1076有自己的注解。
Cache缓存接口。可以实现RedisCache 等，真正操作的。接口不同，技术不同。@Cacheable可缓存,针对方法配置。
@CxacheEvict清空缓存，@CachePut,方法被调用，结果还被调用，更新？@EnableCaching 开启基于注解的缓存。
serialize 序列化。
```
会有一堆的配置，点击源码看就知道。。缓存的自动配置类。
@cacheable运行流程：
	- 查询cache 组件，按照 cachenames 指定名字获取cacheManager先获取，没有就缓存 。
	- 去缓存中查询内容，用key ，默认是使用方法的参数。某种key生成策略。
	- 没有就调用方法，结果就缓存。下一次用。
	- 可以自己配置key 生成类。
@CachePut 既调用缓存方法，又更新数据缓存。	运行时机，先调用目标方法，方法结果缓存。
使用 统一key 才能覆盖 其它的 cacheable
@cacheEvit 缓存清除 
	-	allEntries 指定清除所有数据。
	-	beforeInvacation  是否在方法之前 调用。方法如果出错会不会执行操作
	

```bash
@cacheing 多个组合，复杂，点击源码。组合注解。也可以使用 cacheconfig配置
```
![在这里插入图片描述](http://img.yayi.site/csdn/20200212194530761.png-watermaskStyle)
	#### redis 
	之前使用的是ConcurrentManagercachemap 创建的xx 作为缓存，数据保存在 concurrentMap中的。
	开发中使用缓存中间件：redis\memcached等。springboot默认开启simplecacheconfiguration这个。
	···官方网站 可以docker 安装？？docker中国镜像 下载。或者阿里的。
	redis 管理软件下载一个，。命令行就行。看官方文档，有中国版的。
	注：手动安装的redis centos7 要 CONFIG SET protected-mode no 关闭保存模式，不然是连不上的。spring会有报错，管理软件好像没有报错。
	各种数据结构存储。
	-
	在spring 中引入 场景starter。官方文档。
	spring 提供了 stringredistemplate和redisTemplate两个。
	插入本地变量的快捷键 alt enter 
	序列化规则
自定义规则：spring 有自己的cache管理器。自动配置类。序列化保存。组件 放到容器中。定制一些规则。

### 消息
消息服务件
如：同步，异步。异步时间。
消息队列 ： 用户能更快的收到消息，剩下的工作异步做。
应用解耦 ： 调用接口还是慢，消息队列 发送与订阅，解耦度高
流量削峰：消息队列，队列，秒杀，再处理业务。

两个概念： 消息代理，目的地。
消息代理就是中间件，消息队列有两种形式的目的地：队列点对点，主题形式。
接受者可以有多个。点对点，消费是一次性的，拿了就没有了，
JMS ：java消息队列,基于JVM的消息规范。
AMQP: 高级消息队列,也是一个消息队列协议，兼容JMS
对比：
 - JMS 是java api 。AMQP 是网络级协议，跨平台和语言。消息模型多少。
 - JMS 有自己消息类型，AMQP 是序列化后发送。

spring rabbit 提供了对Amqp支持。也提供了Template。使用注解 在方法上监听消息代理发布的消息。开启支持@enablerabbit

```bash
RabbitMQ 简介
 - Message 
 	 消息头与消息体组成。消息头 属性如：路由健，优先权，持久化存储与否。
 - Publisher
 	 消息生产者，应用程序。
 - Exchange
   交换器，接收生产者发送的消息，并将这些消息级服务器中的队列。像路由器一样。有4处类型。
   direct:routing key 和 Binging key 一致，就会派发。
   fanout:不管路由器，是什么，只有绑定了队列，就广播发送，消息是最快的。
   Topic: 模糊发送，有选择性的发送。key #使用通配符。路由键，绑定键 匹配模糊。
 - Queue 
 	消息队列，保存消息，等待取走。
 -Binding
 	 queue与exchange的对应关系，关联，多对多，也可以。
 -connection
 	网络连接
 -Channel
 	 如：多个tcp费资源，在一个tcp里开多个信道，从信道虚拟发送。
 - Consumer
    消费者，
 - Virtual Host
   在一个服务器（消息中间件）里，多个rabbitMQ 多开，小号，独立运行。默认是/ 以路径区分。
 - Broker
  消息代理，消息队列服务器实体。
 
 以上的找个原理图会理解一点
```
 安装：
 	因为安装麻烦，所以采用了docker安装
 	https://hub.docker.com/_/rabbitmq
 	带management的是有web管理界面的

spring 自动配置：
 		-   连接工厂，
	-    RabbitTemplate ：给Rabbitmq发送和接收消息的。
	-   AmqpAdmin：Rabbitmq系统管理功能组件

```bash
点击 rabbitmq 的message的包，可以看到相关。
对象默认序列化 使用的是java

```
![在这里插入图片描述](http://img.yayi.site/csdn/20200205090948892.png-watermaskStyle)
可以自定义序列化规则，配置类里new 一个amp包里的json相关的就行。

@rabbitListener
@EnableRabbit  //开启基于注解的rabbit

使用amqbadmin 可以在程序中创建，而不是在先前就创建好。搜索一下就可以知道属性之类的。
源码中有方法。

### 检索
springboot 与 ElasticSearch

官方有中文文档
如果启动一会就关掉了的话，请，使用旧版本，要2g内存？？
[https://blog.csdn.net/ZPeng_CSDN/article/details/90340437](https://blog.csdn.net/ZPeng_CSDN/article/details/90340437)
5.3.1 试试，新版本指定内存都不行。
我是docker 对应的版本 docker 方便版本更换。直接安装太。。查看日志 docker log id.

ElasticSearch 看官方文档。put 方式请求，get方式请求执行不同的动作。相同的，版本会更新。按照官方文档操作即可。

spring 有两种方式操作elasticseacrh : jest  和spring elasticsearch .jest默认不生效。现在过时了？
==通过自动配置类内的@configuration 的preix 可以知道 在yml配置里要写什么。==

版本不适配。官方有相关介绍。
     main] o.s.d.e.c.TransportClientFactoryBean     : Adding transport node : 16.13.210.169:9300 成功
     在bean 中@Document 标明
     9300是tcp端口，java客户端是用tcp通信的，所以得配置9300, 9200是http端口，一般是用作rest接口的像curl之类的
     ==对镜像的配置文件的修改。==：
[https://blog.csdn.net/weixin_41799019/article/details/101319184](https://blog.csdn.net/weixin_41799019/article/details/101319184)
在springboot 中看版本应该是在 EXTERNAL Iibraries中看
elasticsearch jdk 要11 放在 elasticsearch/jdk/bin/java下
java.nio.file.AccessDeniedException: /data/wwwroot/elasticsearch-6.2.4/config/jvm.options
这里写图片描述
原因：当前用户没有执行权限
解决方法： chown linux用户名 elasticsearch安装目录 -R
例如：chown ealsticsearch /data/wwwroot/elasticsearch-6.2.4 -R
PS：其他Java软件报.AccessDeniedException错误也可以同样方式解决，给 执行用户相应的目录权限即可
————————————————
版权声明：本文为CSDN博主「一江黑白」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/w790634493/article/details/80081901
搭建es集群时，如果集群名字配置有误，会报错 node -name 我改为与master一样后就没
][o.e.c.c.ClusterFormationFailureHelper] [node2] master not discovered yet, this node has not previously joined a bootstrapped (v7+) cluster, and this node must discover master-eligible nodes [node-1] to bootstrap a cluster: have discovered [{node2}{C38r20R6Q7a7JxxNMgcVqQ}{VkF5NJ1yTLKoOb-T6OM65w}


springboot 启动原理：
[https://www.cnblogs.com/xiaoxi/p/7999885.html](https://www.cnblogs.com/xiaoxi/p/7999885.html)

- 异步任务： @EnableAsync 开启 异步，@Async  作用于方法，这个方法spring 会开线程池执行这个方法。
- 定时任务：@EnableScheduling @Scheduled 同理 也是一样。点进原码里会发现有属性和注释提示。用法见官方，枚举执行？ 每4 秒执行，区间， 任意，冲突匹配，
- 邮件任务： 场景spring 有支持。引入场景依赖在pom中

### 安全
- shiro 与 spring security
- 认证与授权
	可以在创建项目的时候选择 security
- 参考官网的写法
- 写配置类继承 参考 https://spring.io/guides/gs/securing-web/
- 控件请求的访问权限
- 快捷键：ctrl +o 打开可以重写的方法
- 在新的版本中要自己写在配置中增加控制器，见官方的文档例子，自己写模板.新版本已经不一样了
- 结合thyleaf 的加入依赖可以动态。
- 可以定制，要设置参数
### 分布式
需要一分布式框架来处理远程，和一些问题。注册中心，指挥中心。
Zookeeper: 注册中心
Dubbo：负责远程过程调用。
![在这里插入图片描述](http://img.yayi.site/csdn/20200207194314495.png-watermaskStyle)
流程图见官网。安装zooKeeper
//将服务提供者注册到注册中心，
引入 dubbo依赖 是spring 场景依赖

```bash
<!-- https://mvnrepository.com/artifact/com.github.sgroschupf/zkclient -->
<dependency>
    <groupId>com.github.sgroschupf</groupId>
    <artifactId>zkclient</artifactId>
    <version>0.1</version>
</dependency>

```

配置扫描包，注册中心
发布服务
@Service //注意是dubbo的servce
@Component //加入spring容器中？

使用spring Cloud 来做分布式：
- spring cloud 是一个整体解决方案，多种问题解决 
- 常用五大组件：Netflix Eureka(服务发 现相当于注册中心）、Netflix Ribbon(负载均衡）、等等，见官方。
- 关系有点微妙
- eureka server 访问的是server.port 8080 而不是eureka 的8761，

### 热部署
springboot 自己的 spring loaded
JRebel 收费
推荐 devtools  ，引入依赖即可或者在创建项目的时候选择比较好。
### 监控管理
spring boot starter actuator 场景 。审计，健康等。信息
 SBA 全称 Spring Boot Admin 是一个管理和监控 Spring Boot 应用程序的开源项目。分为admin-server 与 admin-client 两个组件，admin-server通过采集 actuator 端点数据，显示在 spring-boot-admin-ui 上，已知的端点几乎都有进行采集，通过 spring-boot-admin 可以动态切换日志级别、导出日志、导出heapdump、监控各项指标 等等….

Spring Boot Admin 在对单一应用服务监控的同时也提供了集群监控方案，支持通过eureka、consul、zookeeper等注册中心的方式实现多服务监控与管理…
[https://github.com/codecentric/spring-boot-admin](https://github.com/codecentric/spring-boot-admin)

定制端点：通过endpoints + 端点名+ 属性名来设置。
修改端点id 
定制一个健康状态指示器，实现healthIndicator 接口 指示器名字 xxxHealthIndicator 不能乱叫。

### 本文是学习视频时的笔记，资料在附件[https://www.bilibili.com/video/av38657363/?p=1](https://www.bilibili.com/video/av38657363/?p=1)
本文文章详见：
本文开始：2019/12/17 结束：2020/02/10

