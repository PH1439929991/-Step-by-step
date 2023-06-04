# JDBC





## 1.快速入门

[(350条消息) JDBC从入门到熟练使用——功能类详解、增删改查(CRUD)、sql注入、事务、连接池_Lichee20的博客-CSDN博客](https://blog.csdn.net/weixin_45195665/article/details/108627965?ops_request_misc=%7B%22request%5Fid%22%3A%22168050302116800180632338%22%2C%22scm%22%3A%2220140713.130102334..%22%7D&request_id=168050302116800180632338&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-108627965-null-null.142^v81^insert_down38,201^v4^add_ask,239^v2^insert_chatgpt&utm_term=jdbc&spm=1018.2226.3001.4187)

1.导入jar包

2.注册驱动

Class.forName("com.mysql.jdbc.Driver");

3.获取连接

Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/db2", "root", "root");

4.获取执行者对象

Statement stat = conn.createStatement();

5.执行sql语句，并接收返回结果

1. ```java
   String sql = "SELECT * FROM user";
   ResultSet rs = stat.executeQuery(sql);
   ```

6.处理结果

while(rs.next()) {  

​		  System.out.println(rs.getInt("id") + "\t" + rs.getString("name")); 

}

7.释放资源

rs.close();
stat.close();
conn.close();

创建一个java项目：JDBC基础

public class JDBCDemo01 {
    public static void main(String[] args) throws Exception{
        //1.导入jar包
        //2.注册驱动
        Class.forName("com.mysql.jdbc.Driver");

```java
    //3.获取连接 （连接的数据库名是db2，第二个第三个参数是连接数据库的用户名密码）
    Connection conn = DriverManager.getConnection("jdbc:mysql://127.0.0.1:3306/db2","root","lichee");

    //4.获取执行者对象 （statement：表现，声明，跟程序意思不匹配）
    Statement stat = conn.createStatement();

    //5.执行sql语句，并且接收结果
    String sql = "SELECT * FROM user";
    ResultSet rs = stat.executeQuery(sql); //execute执行，query：查询，resultset：结果集

    //6.处理结果
    while(rs.next()) {
        System.out.println(rs.getInt("id") + "\t" + rs.getString("name"));
    }

    //7.释放资源
    conn.close();
    stat.close();
    conn.close();
}
```
} 


## 2.JDBC各个功能类详解

### 1.DriverManager(驱动管理对象)

- 注册驱动(告诉程序该使用哪一个数据库驱动)
- 获取数据库连接(获取到数据库的连接并返回连接对象)
- static Connection getConnection(String url, String user, String password);
  返回值：Connection数据库连接对象
  参数
  url：指定连接的路径。语法：jdbc:mysql://ip地址(域名):端口号/数据库名称
  user：用户名
  password：密码

### 2.Connection（数据库连接对象）

- 获取执行者对象
- 获取普通执行者对象：Statement createStatement();
- 获取预编译执行者对象：PreparedStatement prepareStatement(String sql);

  

- 管理事务
- 开启事务：setAutoCommit(boolean autoCommit); 参数为false，则开启事务。
- 提交事务：commit();
- 回滚事务：rollback();



- 释放资源
  - 立即将数据库连接对象释放：void close();

### 3.Statement

Statement：执行sql语句的对象

- 执行DML语句：int executeUpdate(String sql);
  - 返回值int：**返回影响的行数**。
  - 参数sql：可以执行insert、update、delete语句。

- 
- 

- 执行DQL语句：ResultSet executeQuery(String sql);
  - 返回值ResultSet：**封装查询的结果**。
  - 参数sql：可以执行select语句。
- 释放资源
  - 立即将执行者对象释放：void close();



### 4.ResultSet

- ResultSet：结果集对象
  - 判断结果集中是否还有数据：boolean next();
    - 有数据返回true，并将索引向下移动一行
    - 没有数据返回false

- 获取结果集中的数据：XXX getXxx(“列名”);
  - XXX代表数据类型(要获取某列数据，这一列的数据类型)
  - 例如：String getString(“name”); int getInt(“age”);

- 释放资源
  - 立即将结果集对象释放：void close();