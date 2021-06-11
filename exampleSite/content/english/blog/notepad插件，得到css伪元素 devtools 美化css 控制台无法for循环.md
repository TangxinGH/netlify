# 安装插件
![在这里插入图片描述](http://img.yayi.site/csdn/20210316162556434.png-watermaskStyle)

## 抓取伪元素
原理见百度

window.getComputedStyle(document.querySelector('.zp-jobNavigater__item--txt'),':after').getPropertyValue('content')
## 美化css
f12 
![在这里插入图片描述](http://img.yayi.site/csdn/20210316170820919.png-watermaskStyle)
![在这里插入图片描述](http://img.yayi.site/csdn/20210316170839278.png-watermaskStyle) 
点进去
![在这里插入图片描述](http://img.yayi.site/csdn/20210316170920918.png-watermaskStyle)
有个方括号

## js 元素下所有指定类元素

```javascript
zp-jobNavigater__item.querySelectorAll("div.xxlist")
```
jobNavigater__item 元素下的div 标签下的xxlist类

## 控制台无法for循环（未解决）
浏览器console for undefid

foreach 可以？是我不会用. 以下代码是使用函数立即执行加foreach 。不然还是用油猴插件吧。

元素children是集合而不数组
```javascript
(function() {

 Array.from(document.querySelector("#root > div.zp-main.zp-main-container-1 > div.zp-container.zp-main__container > div.zp-jobNavigater.zp-main__jobnav > ol").children).forEach((typelist,i) => {
    //类别分类 type一共九个

    var type = Array.from(document.querySelector("#root > div.zp-main.zp-main-container-1 > div.zp-container.zp-main__container > div.zp-jobNavigater.zp-main__jobnav > ol").children)[i];

    //type标题
    var jobtitle = type.querySelector("div.zp-jobNavigater__pop > div.zp-jobNavigater__pop--container > div.zp-jobNavigater__pop--title").textContent;//标题

    console.log("#" + jobtitle);
    //类型，二级
    var genre_list = type.querySelectorAll("div.zp-jobNavigater__pop--list");
    //职位名称
   Array.from( genre_list).forEach((a_tag_list, j) => {
        //职位
         Array.from(a_tag_list.children).forEach((position,j) =>
                                        {console.log(position.text);})
    });
}

);

})();
```




