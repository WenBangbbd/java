### 创建项目
1. 引入spring-webmvc，javax.servlet-api
2. 在 WEB-INF->web.xml中配置servlet
   1. servlet标签，配置DispatcherServlet
   2. servlet-mapping,配置映射
   3. 配置配置文件 <param-value>classpath:spring-mvc.xml</param-value>
3. 在resouces下建spring配置文件
   1. 配置视图解析器 InternalResourceViewResolver
   2. 配置头尾映射   <property name="prefix" value="/WEB-INF/"></property><property name="suffix" value=".jsp"></property>
4. 创建控制器HelloController 并注解未@Controller
5. 创建方法，注解@RequestMapping("\hello") 访问路径,返回字符串即可拼接为 /WEB-INF/viewName.jsp
6. 添加tomcat，然后部署项目
7. 如果报404，file-project structure->artifats->选择部署项目->WEB-INF->lib->add copy files->lib files
### 原理
1. http=>前端控制器(DispatcherServlet)<=>HandlerMapping(执行链路)
                                       <=>HandlerAdapter=>Controller(返回ViewModel)
                                       <=>ViewResolver(提供view)
       html <=
2. 组件
   1. 前端控制器 DispatcherServlet
   2. 处理器映射器 HandlerMapping
   3. 处理器适配器 handleradapter
   4. 处理器 controller
   5. 视图解析器 viewresolver
   6. 视图 view
   7. 默认配置在.webmvc包中的properies配置
3. 返回数据
   1. 返回页面，字符串 modelandview
   2. 返回文本，json,字符串
   3. 返回带前缀，forward(默认)，redirect重定向
### 方法
1. 可以传入Model,ViewModel
2. 可以传出 String->(匹配视图),ViewModel，未绑定模型，可能是web.xml配置错误
3. 可以传入HttpServletRequest HttpServletResponse，httpsession
4. 可以传出 String->(显示字符串 @ResponseBody),json 也是String
5. 可以传出任意对象，输出json
   1. 配置handleadapter(RequestMappingHandlerAdapter.messageConverters.MappingJackson2HttpMessageConverter) @ResponseBody
   2. 配置<mvc:annotation-driven /> 可替代上面
#### 数据映射
1. 映射get的请求的参数  action(params) action(input) action(String [] strs)<->(?strs=12&strs=24)
2. 映射post,请求体中的参数   在参数前注解 @RequestBody
3. @RequestParams，在参数前自定义映射，name表示输入名称，required，default
4. 自定义类型转换
   1. 实现Converter<S,T>
   2. 在配置文件中注册转换器工厂类，ConversionServiceFactory.converters.add(converter)
   3. 将工厂类注入到框架中，<mvc:annotation-driven conversion-service='converter'>
5. restful,/qui/{name} @PathVariable注解到参数前，
6. head,@RequestHeader,name requied
7. Cook,@CookValue, value
### 注解
@RequestMapping，uri<=>controller.action，映射地址和方法对应
   value就是地址
   method 指定请求方式
   params，参数限定条件

### 过滤器
1. 编码问题，可以配置过滤器
### 上传文件
1. 表单项 type='file'
2. 表单的提交方式 post
3. 表单enctyp multipart/form-data
4. postman 上传文件
   1. ContentType=multipart/form-data;
   2. Body->form-data->file
5. 引入 commons-io commons-fileupload 
6. 配置文件解析器 <class='CommonsMultipartResolver',id='multipartResolver'>,id是固定的
7. 传入参数CommonsMultipartFile 参数前面 注解RequestParam
8. 