### Progouard 
开始压缩 ，release版有问题。数据没显示	

1. ` buildTypes {
        release {
            minifyEnabled true
            shrinkResources true//减小apk包大小
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
        debug{
            minifyEnabled true
            shrinkResources true//减小apk包大小
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }`
于是 在debug 中也加了 同样的代码 。==这样就可以在窗口看到调试信息了==。

2. 去官方okhttp 找了下progouard 的规则文件 
    	加入 规则 ：
	If you use OkHttp as a dependency in an Android project which uses R8 as a default compiler you don’t have to do anything. The specific rules are already bundled into the JAR which can be interpreted by R8 automatically.意思是不用加
3. 好像 是不用加的 。R8 编译器是不用加的， AS.34  默认R8 。所以加了规则也没有用。
### 然后 检查我自己的代码 
 1. 异步回调是官方照写的。
 2. 我使用了pojo 。可以 在转为beans时（用的是第三方框架转的） progouard 将属性名 被改变了a,bc 。
 3. 于是在proguard-rules.pro 加入 规则    --keep class com.my.package.beans.** { *; }  ==注意保持类==
