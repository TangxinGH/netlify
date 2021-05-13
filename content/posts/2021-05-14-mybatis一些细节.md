
### 项目过程记录
如果你要整合springboot 
你可能会去看中文官网 ，但是我建议看一下 英语版的，==或许有些不一样==的。
[http://mybatis.org/spring/mappers.html#scan](http://mybatis.org/spring/mappers.html#scan)

[https://mybatis.org/spring-boot-starter/mybatis-spring-boot-autoconfigure/](https://mybatis.org/spring-boot-starter/mybatis-spring-boot-autoconfigure/)

---
如果你是多模块的，要注意一下：
classpath:  和 classpath* 的区别 。加星的是包括lib的
你可以maven 打包看下 ，target目录下生成的jar 打开看看就知道了。
是maven打包不是idea的artifact打包。

[https://www.cnblogs.com/lujiango/p/9619524.html](https://www.cnblogs.com/lujiango/p/9619524.html)
使用MyBatis时为什么Dao层不需要@Repository：
[https://blog.csdn.net/hehyyoulan/article/details/98962138?utm_medium=distribute.wap_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.wap_blog_relevant_pic2&depth_1-utm_source=distribute.wap_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.wap_blog_relevant_pic2](https://blog.csdn.net/hehyyoulan/article/details/98962138?utm_medium=distribute.wap_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.wap_blog_relevant_pic2&depth_1-utm_source=distribute.wap_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.wap_blog_relevant_pic2)

---
这是官网springboot的一些配置application 属性说明 。
可以去这里找
[https://docs.spring.io/spring-boot/docs/current/reference/html/appendix-application-properties.html#devtools-properties](https://docs.spring.io/spring-boot/docs/current/reference/html/appendix-application-properties.html#devtools-properties)

如果你不清楚springboot帮你mybatis简化了什么，你可以从零开始建立 mybatis，再springboot。就知道了。

---

```java
@Controller("Bean的名称")

定义控制层Bean,如Action

 

@Service("Bean的名称")

定义业务层Bean

 

@Repository("Bean的名称")

定义DAO层Bean

 

@Component  

定义Bean, 不好归类时使用.

```
Could not autowire.No beans of ‘CategoryMapper’ type found.
解决@Autowired注解Mapper报错问题
你应该子解一下下面的：

[https://blog.csdn.net/wqh0830/article/details/96109587
](https://blog.csdn.net/wqh0830/article/details/96109587)

[https://blog.csdn.net/vivinchenleaf/article/details/100125646
](https://blog.csdn.net/vivinchenleaf/article/details/100125646)

---

