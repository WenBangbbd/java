### json
1. jackson-core，jackson-databind,jackson-annotations
2. ObjectMapper .writeValueAsString 序列化
### date
1. 日期转换，使用 SimpleDateFormat
### 注解
1. 定义 @interface Name{}
2. 可以使用元注解定义
   1. Target,定义可以注解的地方
   2. Inherited，子类可以继承
   3. Retention 使用该注解的生命周期，一般RUNTIME
3. 参数， String name() default "123";
   1. 没有默认值必须输入参数
   2. 当参数是value且只有一个时，不用指定
### 反射
1. 一个类型只有一个class类型
2. 获取class方式
   1. object.getClass()
   2. Class.forName("")
   3. Class.class
3. 有class对象的类型
   1. class
   2. interface
   3. 注解
   4. 枚举
   5. 数组
   6. 基本类型
### 泛型
1. 泛型不支持基本数据类型
2. 类型通配符 ？，可以传任意类型，接受用object
3. 通配符的基类型，<? extend BasicClass>，通配符的子类型 <? super SubClass>
### jdbc，数据库访问
1. 驱动，jdbc.mysql.jdbc.Driver，加载Class.forName("jdbc.mydql.jdbc.Driver")
2. 连接，Connection,数据库连接， DriverManager.getConnection(jdbc:mysql://localhost:3306/test,"username","password")
3. 状态 statement 数据库当前状态类，执行静态sql，connection.createStatement(); statement.excuteQuery/excuteupdate
4. 预处理状态，preparedstatement继承statement，可插入参数，防止sql注入，sql="select .. where name=?"，setInt(index,value);
5. ResultSet，结果集，excuteQuery返回结果，getInt(filedName)