#### 错误解读
Exception encountered during context initialization - cancelling refresh attempt: （在创建context 初始化时错误 ）org.springframework.beans.factory.BeanCreationException:（创建beans错误） Error creating bean with name 'org.springframework.context.annotation.internalAsyncAnnotationProcessor' defined in class path resource（在xx类路径下错误） [org/springframework/scheduling/annotation/ProxyAsyncConfiguration.class]: Bean instantiation via factory method failed; nested exception is org.springframework.beans.BeanInstantiationException: Failed to instantiate [org.springframework.scheduling.annotation.AsyncAnnotationBeanPostProcessor]: Factory method 'asyncAdvisor' threw exception; nested exception is java.lang.IllegalArgumentException: @EnableAsync annotation metadata was not injected

---

@EnableAsync annotation metadata was not injected

查了一下，说[https://blog.csdn.net/pansanday/java/article/details/50365399](https://blog.csdn.net/pansanday/java/article/details/50365399)

我的情况是 maven ==只引入 context包==，使用

```java
 ApplicationContext context=new  AnnotationConfigApplicationContext(AppConfig.class);
```
 AnnotationConfigApplicationContext 传入的是一个配置类，有@Configuration 指定，
我用@ComponentScan 扫描注解的组件。可能把spring的一些注解的自带的也扫描进来了。
@ComponentScan 最好指定扫描哪些包，否则也会扫描spring的包，导致创建组件失败。


```java
@Configuration
@ComponentScan(value = "service")
```

#####或者不用@Configuration 和@ComponentScan
把`  ApplicationContext context=new  AnnotationConfigApplicationContext(AppConfig.class);`这 个创建容器上下文的东西换成，` ClassPathXmlApplicationContext classPathXmlApplicationContext=new ClassPathXmlApplicationContext("applicationContext.xml");` 这是从xml读取你指定要创建的组件。

###### 其它错误信息：
Caused by: org.springframework.beans.BeanInstantiationException: Failed to instantiate [org.springframework.scheduling.annotation.AsyncAnnotationBeanPostProcessor]: Factory method 'asyncAdvisor' threw exception; nested exception is java.lang.IllegalArgumentException: @EnableAsync annotation metadata was not injected
	
##### 2
Caused by: java.lang.IllegalArgumentException: @EnableAsync annotation metadata was not injected
#### 完整的：
```java
C:\Users\26284\.jdks\openjdk-14.0.1\bin\java.exe -ea -Didea.test.cyclic.buffer.size=1048576 "-javaagent:C:\Program Files\JetBrains\IntelliJ IDEA 2019.3\lib\idea_rt.jar=60751:C:\Program Files\JetBrains\IntelliJ IDEA 2019.3\bin" -Dfile.encoding=UTF-8 -classpath "C:\Program Files\JetBrains\IntelliJ IDEA 2019.3\lib\idea_rt.jar;C:\Users\26284\.m2\repository\org\junit\platform\junit-platform-launcher\1.7.0-M1\junit-platform-launcher-1.7.0-M1.jar;C:\Program Files\JetBrains\IntelliJ IDEA 2019.3\plugins\junit\lib\junit5-rt.jar;C:\Program Files\JetBrains\IntelliJ IDEA 2019.3\plugins\junit\lib\junit-rt.jar;E:\WorkSpaceIDEA\JAVALearn\SpringIoC_Context\target\test-classes;E:\WorkSpaceIDEA\JAVALearn\SpringIoC_Context\target\classes;C:\Users\26284\.m2\repository\org\springframework\spring-context\5.2.4.RELEASE\spring-context-5.2.4.RELEASE.jar;C:\Users\26284\.m2\repository\org\springframework\spring-aop\5.2.4.RELEASE\spring-aop-5.2.4.RELEASE.jar;C:\Users\26284\.m2\repository\org\springframework\spring-beans\5.2.4.RELEASE\spring-beans-5.2.4.RELEASE.jar;C:\Users\26284\.m2\repository\org\springframework\spring-core\5.2.4.RELEASE\spring-core-5.2.4.RELEASE.jar;C:\Users\26284\.m2\repository\org\springframework\spring-jcl\5.2.4.RELEASE\spring-jcl-5.2.4.RELEASE.jar;C:\Users\26284\.m2\repository\org\springframework\spring-expression\5.2.4.RELEASE\spring-expression-5.2.4.RELEASE.jar;C:\Users\26284\.m2\repository\org\junit\jupiter\junit-jupiter\5.7.0-M1\junit-jupiter-5.7.0-M1.jar;C:\Users\26284\.m2\repository\org\junit\jupiter\junit-jupiter-api\5.7.0-M1\junit-jupiter-api-5.7.0-M1.jar;C:\Users\26284\.m2\repository\org\apiguardian\apiguardian-api\1.1.0\apiguardian-api-1.1.0.jar;C:\Users\26284\.m2\repository\org\opentest4j\opentest4j\1.2.0\opentest4j-1.2.0.jar;C:\Users\26284\.m2\repository\org\junit\platform\junit-platform-commons\1.7.0-M1\junit-platform-commons-1.7.0-M1.jar;C:\Users\26284\.m2\repository\org\junit\jupiter\junit-jupiter-params\5.7.0-M1\junit-jupiter-params-5.7.0-M1.jar;C:\Users\26284\.m2\repository\org\junit\jupiter\junit-jupiter-engine\5.7.0-M1\junit-jupiter-engine-5.7.0-M1.jar;C:\Users\26284\.m2\repository\org\junit\platform\junit-platform-engine\1.7.0-M1\junit-platform-engine-1.7.0-M1.jar" com.intellij.rt.junit.JUnitStarter -ideVersion5 -junit5 test,ll

4月 21, 2020 8:02:54 下午 org.springframework.context.support.AbstractApplicationContext refresh
警告: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'org.springframework.context.annotation.internalAsyncAnnotationProcessor' defined in class path resource [org/springframework/scheduling/annotation/ProxyAsyncConfiguration.class]: Bean instantiation via factory method failed; nested exception is org.springframework.beans.BeanInstantiationException: Failed to instantiate [org.springframework.scheduling.annotation.AsyncAnnotationBeanPostProcessor]: Factory method 'asyncAdvisor' threw exception; nested exception is java.lang.IllegalArgumentException: @EnableAsync annotation metadata was not injected


org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'org.springframework.context.annotation.internalAsyncAnnotationProcessor' defined in class path resource [org/springframework/scheduling/annotation/ProxyAsyncConfiguration.class]: Bean instantiation via factory method failed; nested exception is org.springframework.beans.BeanInstantiationException: Failed to instantiate [org.springframework.scheduling.annotation.AsyncAnnotationBeanPostProcessor]: Factory method 'asyncAdvisor' threw exception; nested exception is java.lang.IllegalArgumentException: @EnableAsync annotation metadata was not injected

	at org.springframework.beans.factory.support.ConstructorResolver.instantiate(ConstructorResolver.java:656)
	at org.springframework.beans.factory.support.ConstructorResolver.instantiateUsingFactoryMethod(ConstructorResolver.java:484)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.instantiateUsingFactoryMethod(AbstractAutowireCapableBeanFactory.java:1338)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1177)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:557)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:517)
	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:323)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:321)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:207)
	at org.springframework.context.support.PostProcessorRegistrationDelegate.registerBeanPostProcessors(PostProcessorRegistrationDelegate.java:228)
	at org.springframework.context.support.AbstractApplicationContext.registerBeanPostProcessors(AbstractApplicationContext.java:722)
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:535)
	at org.springframework.context.annotation.AnnotationConfigApplicationContext.<init>(AnnotationConfigApplicationContext.java:89)
	at test.ll(test.java:47)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:564)
	at org.junit.platform.commons.util.ReflectionUtils.invokeMethod(ReflectionUtils.java:688)
	at org.junit.jupiter.engine.execution.MethodInvocation.proceed(MethodInvocation.java:60)
	at org.junit.jupiter.engine.execution.InvocationInterceptorChain$ValidatingInvocation.proceed(InvocationInterceptorChain.java:131)
	at org.junit.jupiter.engine.extension.TimeoutExtension.intercept(TimeoutExtension.java:149)
	at org.junit.jupiter.engine.extension.TimeoutExtension.interceptTestableMethod(TimeoutExtension.java:140)
	at org.junit.jupiter.engine.extension.TimeoutExtension.interceptTestMethod(TimeoutExtension.java:84)
	at org.junit.jupiter.engine.execution.ExecutableInvoker$ReflectiveInterceptorCall.lambda$ofVoidMethod$0(ExecutableInvoker.java:115)
	at org.junit.jupiter.engine.execution.ExecutableInvoker.lambda$invoke$0(ExecutableInvoker.java:105)
	at org.junit.jupiter.engine.execution.InvocationInterceptorChain$InterceptedInvocation.proceed(InvocationInterceptorChain.java:106)
	at org.junit.jupiter.engine.execution.InvocationInterceptorChain.proceed(InvocationInterceptorChain.java:64)
	at org.junit.jupiter.engine.execution.InvocationInterceptorChain.chainAndInvoke(InvocationInterceptorChain.java:45)
	at org.junit.jupiter.engine.execution.InvocationInterceptorChain.invoke(InvocationInterceptorChain.java:37)
	at org.junit.jupiter.engine.execution.ExecutableInvoker.invoke(ExecutableInvoker.java:104)
	at org.junit.jupiter.engine.execution.ExecutableInvoker.invoke(ExecutableInvoker.java:98)
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.lambda$invokeTestMethod$6(TestMethodTestDescriptor.java:212)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.invokeTestMethod(TestMethodTestDescriptor.java:208)
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.execute(TestMethodTestDescriptor.java:137)
	at org.junit.jupiter.engine.descriptor.TestMethodTestDescriptor.execute(TestMethodTestDescriptor.java:71)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$5(NodeTestTask.java:139)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$7(NodeTestTask.java:129)
	at org.junit.platform.engine.support.hierarchical.Node.around(Node.java:137)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$8(NodeTestTask.java:127)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.executeRecursively(NodeTestTask.java:126)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.execute(NodeTestTask.java:84)
	at java.base/java.util.ArrayList.forEach(ArrayList.java:1510)
	at org.junit.platform.engine.support.hierarchical.SameThreadHierarchicalTestExecutorService.invokeAll(SameThreadHierarchicalTestExecutorService.java:38)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$5(NodeTestTask.java:143)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$7(NodeTestTask.java:129)
	at org.junit.platform.engine.support.hierarchical.Node.around(Node.java:137)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$8(NodeTestTask.java:127)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.executeRecursively(NodeTestTask.java:126)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.execute(NodeTestTask.java:84)
	at java.base/java.util.ArrayList.forEach(ArrayList.java:1510)
	at org.junit.platform.engine.support.hierarchical.SameThreadHierarchicalTestExecutorService.invokeAll(SameThreadHierarchicalTestExecutorService.java:38)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$5(NodeTestTask.java:143)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$7(NodeTestTask.java:129)
	at org.junit.platform.engine.support.hierarchical.Node.around(Node.java:137)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.lambda$executeRecursively$8(NodeTestTask.java:127)
	at org.junit.platform.engine.support.hierarchical.ThrowableCollector.execute(ThrowableCollector.java:73)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.executeRecursively(NodeTestTask.java:126)
	at org.junit.platform.engine.support.hierarchical.NodeTestTask.execute(NodeTestTask.java:84)
	at org.junit.platform.engine.support.hierarchical.SameThreadHierarchicalTestExecutorService.submit(SameThreadHierarchicalTestExecutorService.java:32)
	at org.junit.platform.engine.support.hierarchical.HierarchicalTestExecutor.execute(HierarchicalTestExecutor.java:57)
	at org.junit.platform.engine.support.hierarchical.HierarchicalTestEngine.execute(HierarchicalTestEngine.java:51)
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.execute(EngineExecutionOrchestrator.java:107)
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.execute(EngineExecutionOrchestrator.java:87)
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.lambda$execute$0(EngineExecutionOrchestrator.java:53)
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.withInterceptedStreams(EngineExecutionOrchestrator.java:66)
	at org.junit.platform.launcher.core.EngineExecutionOrchestrator.execute(EngineExecutionOrchestrator.java:51)
	at org.junit.platform.launcher.core.DefaultLauncher.execute(DefaultLauncher.java:87)
	at org.junit.platform.launcher.core.DefaultLauncher.execute(DefaultLauncher.java:66)
	at com.intellij.junit5.JUnit5IdeaTestRunner.startRunnerWithArgs(JUnit5IdeaTestRunner.java:69)
	at com.intellij.rt.junit.IdeaTestRunner$Repeater.startRunnerWithArgs(IdeaTestRunner.java:33)
	at com.intellij.rt.junit.JUnitStarter.prepareStreamsAndStart(JUnitStarter.java:230)
	at com.intellij.rt.junit.JUnitStarter.main(JUnitStarter.java:58)
Caused by: org.springframework.beans.BeanInstantiationException: Failed to instantiate [org.springframework.scheduling.annotation.AsyncAnnotationBeanPostProcessor]: Factory method 'asyncAdvisor' threw exception; nested exception is java.lang.IllegalArgumentException: @EnableAsync annotation metadata was not injected
	at org.springframework.beans.factory.support.SimpleInstantiationStrategy.instantiate(SimpleInstantiationStrategy.java:185)
	at org.springframework.beans.factory.support.ConstructorResolver.instantiate(ConstructorResolver.java:651)
	... 79 more
Caused by: java.lang.IllegalArgumentException: @EnableAsync annotation metadata was not injected
	at org.springframework.util.Assert.notNull(Assert.java:198)
	at org.springframework.scheduling.annotation.ProxyAsyncConfiguration.asyncAdvisor(ProxyAsyncConfiguration.java:47)
	at org.springframework.scheduling.annotation.ProxyAsyncConfiguration$$EnhancerBySpringCGLIB$$fa6a2401.CGLIB$asyncAdvisor$0(<generated>)
	at org.springframework.scheduling.annotation.ProxyAsyncConfiguration$$EnhancerBySpringCGLIB$$fa6a2401$$FastClassBySpringCGLIB$$d47263e6.invoke(<generated>)
	at org.springframework.cglib.proxy.MethodProxy.invokeSuper(MethodProxy.java:244)
	at org.springframework.context.annotation.ConfigurationClassEnhancer$BeanMethodInterceptor.intercept(ConfigurationClassEnhancer.java:331)
	at org.springframework.scheduling.annotation.ProxyAsyncConfiguration$$EnhancerBySpringCGLIB$$fa6a2401.asyncAdvisor(<generated>)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:564)
	at org.springframework.beans.factory.support.SimpleInstantiationStrategy.instantiate(SimpleInstantiationStrategy.java:154)
	... 80 more



Process finished with exit code -1

```

