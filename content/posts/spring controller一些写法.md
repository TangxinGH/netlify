
```java
//@RestController 等于 @Controller + @ResponseBody  REST风格 
@Controller
@RequestMapping("/")
public class mainController {
    @RequestMapping("/")
public @ResponseBody    String Helloword(){//@ResponseBody 数据写进body里。
    return "helloworld. this is from controller";
}
    @GetMapping("/get")
public String word(){
        return "指定 get 方法";
}
    @RequestMapping(path = "/post" ,method = RequestMethod.POST)//REST风格的 PUT 等 指定。同样的可以指定 consumes 媒体类型 .produces 字段 对应http Accept 如applicatin/json
    public String word1(){
        return "指定 post 方法";
    }
    @GetMapping(value = "/param/{id}.json")
    public String param(@PathVariable("id") Long id){//匹配 id     还可以通配符/**/1.html    ${} 也可以  long id 改为 long userid 也是可以的。
        return "URL路径匹配，参数 匹配"+id;
    }
    @RequestMapping(value = "/consumes",consumes = "application/json")
    @ResponseBody
    public String consumes(){
        return "指定 consumes 方法";
    }
//    还可以热爱多种参数类型
@RequestMapping(value = "/var")
@ResponseBody
public String var(){
/*
      @pathvariable
      Model mvc 通用模型
      model and view
      javaBean  映射到bean 上 ，如 pojo
      multipartFile  文件上传
      @ModelAtrribute
      IO 流
      矩阵
      HTTPMesthod 枚举类型
      @RequestParam 对应HTTP 请示的参数
     @REQUESTHEADER  同上
     @ReauestBody 将请示内容转为指定对象
     @RequestPart 文件上传
     @sessionAttribute
     @RequestAttribute
     @InitBinder 会注册多个转化器，以便将http 请示参数转为对应java对象 。如 日期 ，float  javabean 等。实现 接口webbindinginitializer 实现 自定义

*/

    return "mutli var ";
}
    @RequestMapping(value = "/model")
    @ResponseBody
    public String model(Model model){
//        userid= Xx.getid();
//        model.addAllAttributes("user",userid);  一般用于视图之中 模板视图之中
        return "/model.html";//model.html 中的model 数据绑定之类的。
    }

    @RequestMapping(value = "/re")
    @ResponseBody
    public String re(@RequestParam(name = "id",required = true) Integer id,String name){ //required true  表示必须 没有会400 错误
//
        return "/ss.html";//model.html 中的model 数据绑定之类的。
    }
    @RequestMapping(value = "/javabean")
    @ResponseBody
    public String javabean(User name){ //required true  表示必须 没有会400 错误
//
        return "/ss.html";//model.html 中的model 数据绑定之类的。
    }

    @RequestMapping(value = "/JSON")
    @ResponseBody
    public String SAVEORDRBYJSON(@RequestBody User user){ //RequestBody的内容json??? 转为javabean
//
        return "/ss.html";//model.html 中的model 数据绑定之类的。
    }

    @RequestMapping(value = "/file")
    @ResponseBody
    public String handleFormUpload(String filename, MultipartFile file) throws IOException { //RequestBody的内容json??? 转为javabean
file.getInputStream();
        return "/sucess.html";//model.html 中的model 数据绑定之类的。
    }
//    InitBinder 可以自定义。将htpp参数 绑定到javaBean 中。

//    验证框架 jsr-303标准
/*
* @Null
* size
* min
* pattern
* 可以作用于javabean ｐｏｊｏ　之中。
* 但会有时候为空，有时候又不能为空。可以使用ｇｒｏｕｐ　加以区分。如下　
* 定义两个接口
* class A{
* interface add();
* interface update():
*
* ＠nonull(grooups={add.class})
* ＠nonull(grooups={update.class})
* Long id;
* }
* 当上下文不同时，校验效果不同。
* @RequestMapping(value = "/JSON")
@ResponseBody
public String addword(@Validated({A.add.class}) User user, BindingResult result){ //指定 为A类型
result.hasErrors();//判断绑定成功与否
    return "/ss.html";//model.html 中的model 数据绑定之类的。
}
* 当然你可以自己定义检验规则。
* */


//    拦截器
//    addinterceptors可以设置多个拦截器
//    自定义一个类实现handleinterceptor接口 来处理拦截
//     addinterceptors（你自定义的类实例化）。addpathpatterns（拦截的路径 ）

//    addCorsMappings 来实现跨域问题
//    json的处理  springboot 内置了jackjson

//    注意 redirect forward 两个是不同的，forward 可以链式处理。redirect 是发两次http的。


}
//还要错误处理
    @Controller
class  ErrorController extends AbstractErrorController{
 Log    log= (Log) LogFactory.getLog(ErrorController.class);
@Autowired
    ObjectMapper objectMapper;
    public ErrorController(ErrorAttributes errorAttributes) {
        super(errorAttributes);
    }
@RequestMapping("error")
@ResponseBody
public String error(){
//        处理异常

        return "erroeee";
}

    @Override
    public String getErrorPath() {
        return null;
    }
}
