fastjson
因为json中即有对象也有数组
{imgurl:xxx, [{}]}

```java
 JSONObject json = JSON.parseObject(jsonStr);
     String  newslist = json.getString("newslist");//因为对象中有数组
    JSONArray jsonArr = JSON.parseArray(newslist);//数组中再取

    String first = jsonArr.get(0).toString();// 第一个  原因是：改提取出来的对象不能转为String，而要通过它的方法 toString 来转化：
    JSONObject imgurljson = JSON.parseObject(first);
    String imgurl = imgurljson.getString("imgurl");
    String date=json.getString("date");
```
多转一次就行，取对象中newslist转数组，再转jsonstring,再取值

