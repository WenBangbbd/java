####  普通项目
1. 一个project是一个进程
2. 创建普通java工程，new=>project
3. 设置utf-8编码，editor->file encoding
4. jdk设置，选择jdk即可
5. web=>可以创建java项目，然后选择模块=>add framworks=>web
6. 需要部署，下载tomcat，右上角addconfiguration=>添加=>tomcat server=>local=>configruation=>deployment=>选择项目目录
   1. 必须要有web项目才能部署
#### maven项目
1. maven => archettype quickstart =>属性中添加archetypeCatalog=internal
2. maven=>右侧小工具可以看依赖及递归依赖
3. maven 使用 
   1. 设置设置环境变量，MAVEN_HOME Path
   2. 设置settings.xml的<localRepository></localRepository>
   3. 设置mirror
         <mirror>
            <id>alimaven</id>
            <mirrorOf>central</mirrorOf>
            <name>aliyun maven</name>
            <url>http://maven.aliyun.com/nexus/content/repositories/central/</url>
         </mirror>
4. maven->chartype-webapp->可以添加java和resources等
5. 