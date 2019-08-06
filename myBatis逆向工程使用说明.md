# myBatis逆向工程使用说明

## 一、环境说明

1. jdk 1.8+
2. maven工程
3. mysql 8.0+（8.0以下版本请查看 二 ）

## 二、部署说明

1. 新建maven项目

2. 向pom文件中添加mybatis逆向工程官方依赖

   ```
   <dependency>
   	<groupId>org.mybatis.generator</groupId>
       <artifactId>mybatis-generator</artifactId>
       <version>1.3.7</version>
   </dependency>
   
   <dependency>
   	 <groupId>org.mybatis.generator</groupId>
        <artifactId>mybatis-generator-maven-plugin</artifactId>
        <version>1.3.7</version>
   </dependency>
   ```

3. 向pom文件中添加数据库连接依赖（数据库为5.0版本时请使用注释部分）

   ```powershell
   <!-- mysql-connector for 5.0 -->
   	<!--<dependency>-->
      	 	<!--<groupId>mysql</groupId>-->
       	<!--<artifactId>mysql-connector-java</artifactId>-->
       	<!--<version>5.1.26</version>-->
   <!--</dependency>-->
   
   <!-- mysql-connector for 8.0 -->
   	<dependency>
       	<groupId>mysql</groupId>
           <artifactId>mysql-connector-java</artifactId>
           <version>8.0.13</version>
       </dependency>
   ```

4. 修改generatorConfig.xml中的jdbcConnection内容（使用旧版本数据库时请更改driverClass包）

   ```xml
   <!-- Mysql数据库连接的信息：驱动类、连接地址、用户名、密码 -->
   <!--driverClass="com.mysql.jdbc.Driver"当使用旧版本数据库时for mysql8.0以下-->
   <jdbcConnection driverClass="com.mysql.cj.jdbc.Driver"
   connectionURL="jdbc:mysql://localhost:3306/exam?characterEncoding=utf8&amp;useSSL=false&amp;serverTimezone=UTC&amp;rewriteBatchedStatements=true" userId="root" password="root">
   </jdbcConnection>
   ```

5. 修改数据库表名

   ```xml
   <table schema="" tableName="paper"></table>
   <table schema="" tableName="roleright"></table>
   <table schema="" tableName="studentpaper"></table>
   <table schema="" tableName="subject"></table>
   <table schema="" tableName="sysfunction"></table>
   <table schema="" tableName="sysrole"></table>
   <table schema="" tableName="sysuser"></table>
   ```

6. 运行GeneratorSqlmap类生成pojo、mapper、Dao文件

## 三、附加说明

1. 该项目是根据CSDN博主「Oxygenzzz」的原创文章而编写，如有侵权请联系删除，原文链接：https://blog.csdn.net/qq_39056805/article/details/80585941。
2. 在博文的基础上增加了对mysql 8.0+版本的兼容，重新定义了输出的路径，使用了maven进行了工具包的管理，支持该作为maven项目的工具类插入web项目中。