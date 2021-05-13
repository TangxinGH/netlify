参考：[https://www.cnblogs.com/mq0036/p/8522150.html](https://www.cnblogs.com/mq0036/p/8522150.html)
![在这里插入图片描述](http://img.yayi.site/csdn/20191024170834972.png-watermaskStyle)
[https://blog.csdn.net/engerla/article/details/81298645](https://blog.csdn.net/engerla/article/details/81298645)
util.Date与sql.Date的相互转换


Could not locate cfg.xml resource [hibernate.cfg.xml]，也有src下的
![在这里插入图片描述](http://img.yayi.site/csdn/20191024193440267.png-watermaskStyle)


 Recognized obsolete hibernate namespace http://hibernate.sourceforge.net/hibernate-configuration. Use namespace http://www.hibernate.org/dtd/hibernate-configuration instead.  Support for obsolete DTD/XSD namespaces may be removed at any time.
![在这里插入图片描述](http://img.yayi.site/csdn/20191024193950279.png-watermaskStyle)

一个是hibernate.cfg.xml 是与你数据库相关的：xx.hbm.xml  这是配置 
一个是与表相关的：table.hbm.xml 这是映射
这两个不是一样的，怎么区分与定义：
![在这里插入图片描述](http://img.yayi.site/csdn/20191024195200837.png-watermaskStyle)
map是这样的：![在这里插入图片描述](http://img.yayi.site/csdn/20191024195319239.png-watermaskStyle)
配置文件：
![在这里插入图片描述](http://img.yayi.site/csdn/20191024195454754.png-watermaskStyle)
xml文件类型定义;
![在这里插入图片描述](http://img.yayi.site/csdn/20191024195536606.png-watermaskStyle)
##### hibernate.cfg.xml找不到 ，放到resources中
###### .MappingNotFoundException: Mapping (RESOURCE) not found : example/pojo/UserinfoEntity.hbm.xml :
target结构![在这里插入图片描述](http://img.yayi.site/csdn/20191031135828152.png-watermaskStyle)
确定没有 ，都放resouces下又太乱
boot.MappingNotFoundException: Mapping (RESOURCE) not found : POJO/Student.hbm.xml : 因为是用maven，所以找不到，mappin 认为mapping 是资源文件？
[https://blog.csdn.net/u011731544/article/details/80020617](https://blog.csdn.net/u011731544/article/details/80020617)
pom 标签：位置，==pom.xml 的多级包是用斜杠的/ 而不是点==
[https://www.cnblogs.com/yangzhilong/p/4329336.html](https://www.cnblogs.com/yangzhilong/p/4329336.html)
复数包含单数：includes在前， include

这：。。

注意hibernate.cfg.xml改一下，
![在这里插入图片描述](http://img.yayi.site/csdn/20191024202829611.png-watermaskStyle)



一对多关系，创建关系：
[https://blog.csdn.net/weixin_39663138/article/details/87904784](https://blog.csdn.net/weixin_39663138/article/details/87904784)


url 连数据库中有 特殊符号：url参数中有+、空格、=、%、&、#等特殊符号的问题解决
[https://blog.csdn.net/duanliuchang/article/details/78739152](https://blog.csdn.net/duanliuchang/article/details/78739152)
xml中是这样转义
[https://www.cnblogs.com/z5337/p/9178712.html](https://www.cnblogs.com/z5337/p/9178712.html)
注意：在xml配置文件中配置数据库utl时，要使用&的转义字符也就是&amp;
==要加；分号！！！！==[https://blog.csdn.net/afgasdg/article/details/6941712](https://blog.csdn.net/afgasdg/article/details/6941712)


![在这里插入图片描述](http://img.yayi.site/csdn/20191031143733908.png-watermaskStyle)
转载：https://blog.csdn.net/qq_38728337/article/details/77926591
![在这里插入图片描述](http://img.yayi.site/csdn/20191031144141998.png-watermaskStyle)
实体类中的 hascode作用
[https://blog.csdn.net/s18579103565/article/details/56682369](https://blog.csdn.net/s18579103565/article/details/56682369)

/*更新操作
我们在快速入门中使用到了save(Objcet o)方法，调用了这个方法就把对象保存在数据库之中了。Session对象还提供着其他的方法来进行对数据库的更新

session.save(obj); 【保存一个对象】
session.update(obj); 【更新一个对象】
session.saveOrUpdate(obj); 【保存或者更新的方法】
没有设置主键，执行保存；
有设置主键，执行更新操作;
如果设置主键不存在报错！

主键查询
通过主键来查询数据库的记录，从而返回一个JavaBean对象

session.get(javaBean.class, int id); 【传入对应的class和id就可以查询】
session.load(javaBean.class, int id); 【支持懒加载】

HQL查询
HQL:hibernate query language 即hibernate提供的面向对象的查询语言

查询的是对象以及对象的属性【它查询的是对象以及属性，因此是区分大小写的！】。
SQL：Struct query language 结构化查询语言

查询的是表以及列【不区分大小写】
HQL是面向对象的查询语言，可以用来查询全部的数据！
QBC查询
QBC查询: query by criteria 完全面向对象的查询

从上面的HQL查询，我们就可以发现：HQL查询是需要SQL的基础的，因为还是要写少部分的SQL代码....QBC查询就是完全的面向对象查询.
//    https://www.w3cschool.cn/hibernate/ugov1ie8.html


    */
    
#### 要取字段值，如果你知道的话，可以告诉我，
我是多次查询来登录注册判断用户与密码的。

java.lang.NoClassDefFoundError: org/hibernate/criterion/Criterion | Spring Hibernate
![在这里插入图片描述](http://img.yayi.site/csdn/2019103119481954.png-watermaskStyle)
我maven导包，别无他法
