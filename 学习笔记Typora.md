# 一、MySQL

javaEE:企业级java开发 Web

前端：页面：展示：数据

后端：连接点：连接数据库JDBC，链接前端（控制，控制视图跳转，和前端传递数据）

数据库(存数据，Txt，Excel，word)

> 只会写代码,学号数据库,基本混饭吃

> 操作系统,数据结构与算法!当一个不错的程序员

> 离散数学,数字电路,体系结构,编译原理 + 实战经验



## 1.1、为什么学习数据库

1.岗位需求

2.现在的时代

3.被迫需求

4.数据是软件体系中最核心的存在 DBA(数据库管理员)

## 1.2、什么是数据库

数据库(DB DateBases)

概念:数据仓库,软件,安装在操作系统(window,linux)之上 SQL,可以存储大量的数据

作业:存储数据 , 管理数据

## 1.3、数据库分类

关系型数据库:

MySQL,Oracle,Sql Server,DB2,SQLlite

通过表和表之间,行和列之间的关系进行数据的存储.......

非关系型数据库:(NoSQL)  Not Only

Readis,MongDB

以对象存储,对象存储,通过对象的自身的属性来决定.



DBMS(数据库管理系统)

1.数据库的管理系统

2.MySql

![image-20230227163908984](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227163908984.png)

## 1.4、MySql

1.语言使用,SQL语言

2.前世:MySql AB公司

3.今生:属于Oracle旗下公式

MySQL是最好的RDBMS,开源--

中小型网站,或者大型网站,集群!

官网:[MySQL](https://www.mysql.com/)

5.7稳定 8.0

安装建议:

1、尽量不要使用exe,注册表

2、尽可能使用压缩包安装~

3.安装教程

1.解压

2.把这个包给解压

3.配置环境变量

4.新建mysql配置文件,后缀名ini

> [mysqld]
>
> //路径一定是自己的
>
> basedir=D:\MySQL\mysql-8.0.32\mysql-8.0.32-winx64
> datedir=D:\MySQL\mysql-8.0.32\mysql-8.0.32-winx64\data\
> port=3306
> skip-grant-tables

5.管理员模式cmd,运行所以的命令

![image-20230227170642190](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227170642190.png)

6.再次启动mysql

![image-20230227170735490](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227170735490.png)

![image-20230227170944999](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227170944999.png)

![image-20230227171130323](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227171130323.png)

mysql8 用：ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';

我调试了五花八门,发现狂神的mysql版本5.7和我在官网下的8.0版本 命令不匹配 晕死了

![image-20230227172043927](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227172043927.png)

验证一下就行

加注释//skip-......

![image-20230227172138034](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227172138034.png)

最后重新启动mysql即可正常使用

net stop mysql

net start mysql

![image-20230227172409110](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227172409110.png)





#### 总结

进入mysql通过命令行(-p)后面千万不能假空格,修改密码(sql语句后面一定要加分号!) 注释掉跳过密码 重启mysql.连接测试.

然后登入mysql 就是 net start mysql

mysql -u root -p这地方不能有空格

然后输入密码即可 我们设置为123456





## 1.5、安装sqlyog

但是其实我安装了Navict哈哈



# 二、MySQL入门学习



## 2.1创建基本的数据库

## (其他文件千万别动，动了就重新安装了┭┮﹏┭┮)

![image-20230227192457299](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227192457299.png)

![image-20230227192527663](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227192527663.png)

除了这个你自己创建的school，千万别动其他的文件

![image-20230227194129367](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227194129367.png)

下面就是对表的一系列操作

## 2.2连接数据库

命令行连接！

> 1mysql -uroot -p123456       --连接数据库

<img src="C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227194428129.png" alt="image-20230227194428129" style="zoom:50%;" />

> 修改密码 ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';

也可以在mysql的user中去查看密码

![image-20230227194703345](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227194703345.png)

不过是加密过的。

ok，接下来就是到windows终端的过程了。

> #显示数据库
>
> mysql>show databases;



> #创建数据库
>
> mysql>create database mysqltest;



> 进入数据库
>
> use mysqltest;



> #显示表
>
> show tables

> #切换数据库
>
> use 数据库名



> #查看数据库中所以的表 
>
> --show tables;  



> exit; -- 退出连接

> -- 单行注释



> 多行注释
>
> /*
>
> (sql的多行注释)
>
> */

就类似这样

<img src="C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230227200747276.png" alt="image-20230227200747276" style="zoom:67%;" />

数据库xxx语言 CRUD增删改查！  CV程序员   API程序员   CRUD程序员！（业务）

DDL 定义

DML 操作

DQL 查询

DCL 控制