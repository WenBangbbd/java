### spring-framwork
1. core，其他组件的核心
2. bean,依赖注入
3. context,注解和springconfig
#### bean-factory
1. id，唯一标签，取bean的时候用
2. class,类指定初始化的类，默认无参构造函数
3. scope,范围sing-单例，加载配置文件的时候创建，prototype-每次都创建，getbean的时候创建
4. init-method，在构造函数之后,destory-method,初始化和销毁时调用
5. 工厂构造，factory-method，指定静态类构造创建实例方法，factory-bean，指定实例工厂bean的id,配置factory-method
6. ApplicationConext container=new ClassPathXmlApplicationContext("xml");container.getBean("id");container.getBean(class)
#### di
1. set和构造函数注入
2. set 注入，<property>子标签，name=属性（小写，set后面的），ref=id，value=value
3. 构造函数注入，<constructor-arg>子标签，name=变量名，ref=id，value=value
4. p属性，不用写<property>子标签，xmlns:p="http://www.springframework.org/schema/p"，p:_user-ref="user"->set注入
5. 传入集合，在property中使用map和list等子标签
#### 分层配置
1. <import>标签，引入子配置文件
#### 加载配置文件位置
1. 默认resources下的文件编译后都会被复制到classes目录下，称为类路径，所以ClassPathXmlApplicationContext可以加载配置文件
2. FileSystemXmlApplicationContext ->文件路径加载
3. AnnotationConfigApplicationContext->注解配置
#### 注解 在spring-context里面
1. 标记bean,component,controller,service,repository
2. 依赖注入，autowired,qualifier,resource
3. 值，value
4. 范围，scope,
5. 初始销毁，postconstruct,predestroy
6. 配置文件里面要配置<context:component-scan base-package="org.example"/>,地址也要增加，在文档里面查component-scan即可
##### 扩展注解
1. 标记配置文件 configruation
2. 导入子配置文件 import
3. 编辑方法返回值为bean  bean
4. 标记扫描包 componentscan
5. 加载properity配置文件 PropertySource 
#### 在spring配置文件中引入键值对配置
1. 使用标签<context:property-placeholder location="UserService"></context:property-placeholder>，可以在spring文档中收索
2. 在resource下面创建UserService文件，使用key=value配置
3. 然后使用@Value("${key}")来取值、
#### 测试中使用配置依赖注入
1. 引入 spring-test依赖
2. 注解@RunWith(SpringJUnit4ClassRunner.class),运行时
3. 注解配置@ContextConfiguration(classes = {ApplicationCfg.class})和@ContextConfiguration("classpath:application.xml")
4. 引入@Autowired
5. 