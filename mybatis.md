### mybatis
1. 引入mybatis->org.mybatis
2. 引入mysql-connector-java
3. 配置mybatis->配置到类路径下，可以看官网
   <property name="driver" value="com.mysql.jdbc.Driver"/>
    <property name="url" value="jdbc:mysql://localhost:3305/smartx_car"/>
    <property name="username" value="root"/>
    <property name="password" value="123456"/>
    <mappers>
    <mapper resource="org/mybatis/example/BlogMapper.xml"/>
    </mappers>

5. 获取连接工厂
    String resource = "org/mybatis/example/mybatis-config.xml";
    InputStream inputStream = Resources.getResourceAsStream(resource);
    SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);

6. mapper配置文件
    可以看官网，注意namespace->id，共同作为唯一标志，