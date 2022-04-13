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
2. 可以传出 String->(匹配视图),ViewModel
3. 可以传入HttpServletRequest HttpServletResponse
4. 可以传出 String->(显示字符串 @ResponseBody),json 也是String
5. 可以传出任意对象，输出json,配置handleadapter(RequestMappingHandlerAdapter.messageConverters.MappingJackson2HttpMessageConverter) @ResponseBody
### 注解
@RequestMapping，uri<=>controller.action，映射地址和方法对应
   value就是地址
   method 指定请求方式
   params，参数限定条件
