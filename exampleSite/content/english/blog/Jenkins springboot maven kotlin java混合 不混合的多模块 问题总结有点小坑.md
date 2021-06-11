### 搞了一天，心累。
idea 打包没有问题。
难道idea 这么智能吗？

---
#### 错误
> /var/jenkins_home/workspace/kunpengshetuan/app/src/main/java/kunpeng/App.java:[7,19] package POJO does not exist
[ERROR] /var/jenkins_home/workspace/kunpengshetuan/app/src/main/java/kunpeng/App.java:[7,1] static import only from classes and interfaces
[ERROR] /var/jenkins_home/workspace/kunpengshetuan/app/src/main/java/kunpeng/App.java:[16,9] cannot find symbol
[ERROR]   symbol:   method dao()
[ERROR]   location: class kunpeng.App

### 依赖关系 
这个pojo是另一个moudle A的kotlin类。

moudle app 依赖于 A 。 使用了A的kotlin类。然后就提使找不了。

---
### idea 下
一开始 也是失败运行和失败打包的。
idea 先mvn install A 到本地仓库中，这样可以找到依赖。。然后mvn package app 得到app.jar 可以运行。
mvn 命令在：
![在这里插入图片描述](http://img.yayi.site/csdn/20201007095822843.png-watermaskStyle)

---
当前了jenkins中就不行了。
找不到这个类。
我找到了个个命令：
>mvn clean kotlin:compile package -Dmaven.test.skip=true

命令的意思是：清理target目录下的，使用kotlin 编译，打包，跳过测试。
==强烈建议开启-X 进行详细debug 信息输出 == mvn -X

然后对于我没有什么用。因为
它这个是 在 kotlin java 混合 开发的时候才会使用的先编译kotlin 再编译java 。
==但问题是我的app中只有java类，没有kotlin.kt类。。。== 所以这个不叫混合！！
有kotlin类的是我的moudle A 。我是**多模块开发**的。A 与app只是**调用关系** 而已。
**而且我的moudle A中只有kotlin 类**

混合是一个模块中都有java 和kotlin类。

---

在jenkins中找到了这个==info==类型的输出，看来连info的信息都要看。
>O] --- kotlin-maven-plugin:1.4.10:compile (default-cli) @ kotlin ---
[WARNING] No sources found skipping Kotlin compile

kotlin插件编译==模块== kotlin（也就是上面说的moudle A）时，没有souces跳过编译

---
到下面 一个warning
>[INFO] --- maven-jar-plugin:3.2.0:jar (default-jar) @ kotlin ---
[WARNING] JAR will be empty - no content was marked for inclusion!

==maven 发现它打包好的 moudle A 是个空的jar ！！！==

嗯？？

---
所以应该是moudle A 的pom.xml出了问题
```xml
<build>
        <plugins>
            <plugin>
                <groupId>org.jetbrains.kotlin</groupId>
                <artifactId>kotlin-maven-plugin</artifactId>
                <version>${kotlin.version}</version>
                <executions>
                    <execution>
                        <id>compile</id>
                        <goals>
                            <goal>compile</goal>
                        </goals>
                    </execution>

                    <execution>
                        <id>test-compile</id>
                        <goals>
                            <goal>test-compile</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
```
好像没什么问题
百度了一下。kotlin 的官网：
[https://www.kotlincn.net/docs/reference/using-maven.html](https://www.kotlincn.net/docs/reference/using-maven.html)

```java
编译只有 Kotlin 的源代码
要编译源代码，请在 <build> 标签中指定源代码目录：

<build>
    <sourceDirectory>${project.basedir}/src/main/kotlin</sourceDirectory>
    <testSourceDirectory>${project.basedir}/src/test/kotlin</testSourceDirectory>
</build>
<build>
    <sourceDirectory>${project.basedir}/src/main/kotlin</sourceDirectory>
    <testSourceDirectory>${project.basedir}/src/test/kotlin</testSourceDirectory>
</build>

![在这里插入图片描述](http://img.yayi.site/csdn/20201007102206381.png-watermaskStyle)
哦，==还要指定目录的啊==，这么不智能，看来我的idea应该是我装了插件。
```


---
在bulid点加上：
```xml
 <configuration>
                    <sourceDirs>
                        <sourceDir>${project.basedir}/src/main/kotlin</sourceDir>
                        <sourceDir>${project.basedir}/src/main/java</sourceDir>
                    </sourceDirs>
                </configuration>
               
   ```
   这样A.jar 就不为空了

---
### 总结
还有一个spring boot多模块 指定mainclass 启动类：
在app模块的pom.xml中： 只需要打包启动类所在的模块就行。其它模块作为依赖模块。
```xml
  <plugin>
                <!--该插件主要用途：构建可执行的JAR -->
<!--                在父项目下有的子项目在首次运行clean 和install前应该先运行父项目的clean和install-->
<!--                使用maven 打包 而不是 idea  在 target 目录下。-->
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <configuration>
                    <mainClass>kunpeng.App</mainClass> <!--主类 包含main-->
                    <layout>JAR</layout>
                </configuration>
            </plugin>
```

---
顺便说一下jenkins要配置镜像。不然慢。。。。
使用阿里云的比较好，
pipeline {


    agent {
        docker { //dokcer 中运行在
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2'  //挂载仓库到宿主机，所以在这里配镜像。
        }
    }
  
  好像到[这个直接进jenkins的数据目录里改也行。](https://www.jianshu.com/p/7883c251eb09)
