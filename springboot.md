#### 开始
1. 使用maven创建项目
2. 添加启动框架
     <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.4.5</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
3. 添加web依赖
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
4. 创建应用类
   1. 添加main函数，@SpringBootApplication注解
   2. SpringApplication.run(helloWorldApplication.class, args); Spring应用启动该类
5. 然后建立Controller即可，main方法启动就可以了
6. 添加插件，部署时会有启动类
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
#### 配置
1. 在resources下，默认为application.properties,application.yml
#### 原理
1. 没有配置CommponentScan,默认SpringApplication的包为扫描包
2. 