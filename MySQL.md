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

数据定义语言

（数据库，表，字段）

DML 操作

数据操作语言

（增删改）

DQL 查询

（数据查询语言）

DCL 控制

（数据控制语言）

创建数据库用户、控制数据库的访问权限

# 三、数据库操作

DDL

- 查询

- > SHOW DATABASES;



- 查询当前数据库

- > SELECT DATABASE();

select 选择

- 创建

- > CREATE DATABASE [IF NOT EXISIS] 数据库名 [DEFAULT CHARSET 字符集] [COLLATE 排序规则];

Collate 整理 括号都是可选的

- 删除

- > DROP DATABASE[IF EXISTS]数据库名;

drop 减少，放弃

- 使用

- > USE 数据库名;







表查询-查询

- 查询当前数据

- > SHOW TABLES；



- 查询表结构

- > DESC 表名；



- 查询表的建表语句

- > SHOW CREATE TABLE 表名



Mysql中的sys是系统库的表结构

![image-20230306211235679](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306211235679.png)



- 表操作-创建

- > CREATE TABLE 表名（
  >
  > ​            字段1 字段1类型[COMMENT 字段1注释]，
  >
  > ​            字段2 字段2类型[COMMENT 字段2注释]，
  >
  > ​            字段3 字段3类型[COMMENT 字段3注释],
  >
  > ​            .......
  >
  > ​            字段n 字段n类型[COMMENT 字段n注释] (这后面没有，要注意一下细节)
  >
  > ）[COMMENT 表注释];

![image-20230306212441803](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306212441803.png)

![image-20230306212458728](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306212458728.png)

![image-20230306212643233](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306212643233.png)

这就是一个创数据库，然后又创表，然后表中加入列表项的一个过程大概。。。。。。。其实好像没那么难哈哈！

来

让我们看看建表语句

![image-20230306213704648](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306213704648.png)

2023/3/6

看到SQL-DDL-表操作-创建-----

明天继续













DML

1.给指定字段添加数据

INSERT INTO表名（字段名1，字段名2....）VALUES(值1，值2);

2.给全部字段添加数据

INSERT INTO表名 VALUES(值1，值2,...);

![image-20230315135615232](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315135615232.png)

![image-20230315143240225](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315143240225.png)





DML 修改 

update

![image-20230315143908789](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315143908789.png)

![image-20230315143849947](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315143849947.png)

> 如果你的where后面没有跟数值的话，默认全部更改

![image-20230315144035105](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315144035105.png)





DML-删除数据

> delete from 表名 [where 条件]

![image-20230315144143065](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315144143065.png)

![image-20230315144957635](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315144957635.png)



DML语句

增删改查

![image-20230315145228387](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315145228387.png)





## 

## DQL-介绍

查询  频次高于增删改

SELECT 

![image-20230315145427894](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315145427894.png)

1.差选多个字段

![image-20230315145603898](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315145603898.png)



2.设置别名

![image-20230315145637074](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315145637074.png)



3.去除重复记录

![image-20230315145653535](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315145653535.png)



查询需求

## DQL--基本查询

--1.查询指定字段 name workno age 返回

select name，workno，age from emp；

![image-20230315152212267](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315152212267.png)

![image-20230315152620750](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315152620750.png)

![image-20230315152325283](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315152325283.png)

![image-20230315152552263](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315152552263.png)

![image-20230315152540840](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315152540840.png)



## DQL-条件查询

![image-20230315152905836](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315152905836.png)



![image-20230315153647360](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315153647360.png)

![image-20230315153933985](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315153933985.png)

![image-20230315154023768](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315154023768.png)

![image-20230315154349806](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315154349806.png)

![image-20230315154247973](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315154247973.png)

![image-20230315154512621](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315154512621.png)

![image-20230315154616996](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315154616996.png)

![image-20230315154710055](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315154710055.png)

哈哈 还是很容易的

挺好玩

![image-20230316221525186](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230316221525186.png)

## DCL-管理用户

> USE mysql;
>
> SELECT * FROM user;



2.创建用户

> CREATE USER '用户名'@'主机名' IDENTIFIED BY '密码';



3.修改用户密码

> ALTER USER '用户名'@'主机名' identified with mysql_native_password BY '新密码';



4.删除用户

> DROP USER'用户名'@'主机名';











DCL-权限控制

![image-20230316221722628](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230316221722628.png)















# 四、函数

!!!!!!!!

## 1.字符串函数

![image-20230316221954302](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230316221954302.png)





![image-20230316223005370](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230316223005370.png)



![image-20230316223232323](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230316223232323.png)

## 2.数值函数

![image-20230316223702734](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230316223702734.png)

​                                                       随机生成六位随机验证码

![image-20230316224305211](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230316224305211.png)



![image-20230316224421993](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230316224421993.png)

![image-20230316225159906](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230316225159906.png)

![image-20230316225622970](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230316225622970.png)

## 3.流程函数

![image-20230316225740488](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230316225740488.png)





![image-20230317142956881](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317142956881.png)



![image-20230317151543824](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317151543824.png)





小结就是这个

![image-20230317151909265](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317151909265.png)

会用就好





# 五、约束

## 一、约束演示

保证数据库中的正确性和完整性

![image-20230317152759021](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317152759021.png)

![image-20230317152753054](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317152753054.png)

![image-20230317153334281](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317153334281.png)





![image-20230317153832813](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317153832813.png)

![image-20230317153816872](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317153816872.png)

年龄约束限制了

![image-20230317153900077](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317153900077.png)





外键约束

两张表之间的数据建立连接，从而保证数据的一致性和完整性

![image-20230317154920795](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317154920795.png)

![image-20230317154911396](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317154911396.png)

创建员工表

![image-20230317162425230](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317162425230.png)

![image-20230317163240824](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317163240824.png)



> Alter table worker add constraint fk_worker_dept_id foreign key (dept_id) references dept(id); 

![image-20230317163843008](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317163843008.png)

![image-20230317163930976](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317163930976.png)

删除外键名fk_worker_dept_id 

![image-20230317164040174](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317164040174.png)

![image-20230317165710130](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317165710130.png)

cascade



要记住那个子表的允许设置要为null才行

![image-20230317182154155](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317182154155.png)



![image-20230317182555641](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317182555641.png)

![image-20230317182538906](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317182538906.png)

![image-20230317182523914](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230317182523914.png)



# 六、多表查询

一对多 多对多 一对一

![image-20230318121123019](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318121123019.png)

一个部门对应多个N成员



多对多

学生和课程的关系

![image-20230318121405072](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318121405072.png)

````mysql
CREATE TABLE student ( id auto_incrementint PRIMARY KEY auto_increment COMMENT '·1', NAME VARCHAR ( 10 ) COMMENT '内容', number VARCHAR ( 10 ) COMMENT '学号' ) COMMENT '学生表';
INSERT INTO student ( NAME, number )
VALUES
	( 'panheng', '2020218028' ),(
		'liwenge',
		'2020218020' 
		),(
		'gaoxingyu',
		'2020217988' 
	);
CREATE TABLE course ( id INT auto_increment PRIMARY KEY COMMENT '主键', NAME VARCHAR ( 10 ) COMMENT '课程名称' ) COMMENT '课程表';
CREATE TABLE student_course (
	id INT auto_increment PRIMARY KEY COMMENT '主键',
	student_id INT COMMENT '学生id',
	course_id INT COMMENT '课程id',
	CONSTRAINT fk_coureid FOREIGN KEY ( course_id ) REFERENCES course ( id ),
CONSTRAINT fk_studentid FOREIGN KEY ( student_id ) REFERENCES student ( id ) 
) COMMENT '学生课程中间表';
````



多表查询

笛卡尔积

select * from emp,dept;

![image-20230318143902048](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318143902048.png)

````mysql
select * from worker,dept where worker.deptid = dept.id;
````

> 连接查询
>
> 内连接 ：相当于查询A B交集部分
>
> 外连接：
>
> ​		左外连接：查询左表所有数据，以及两张表交集部分数据
>
> ​		右外连接：查询右表所有数据，以及两张表交集部分数据
>
> 自连接：当前表与自身的连接查询，自连接必须使用表别名
>
> 子查询：
>
> ​		![image-20230318144424281](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318144424281.png)







内连接

查询两章表交集的部分



![image-20230318145648956](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318145648956.png)

![image-20230318145829790](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318145829790.png)

![image-20230318150151736](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318150151736.png)





外连接

![image-20230318153139194](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318153139194.png)

![image-20230318153125638](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318153125638.png)

![image-20230318153518950](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318153518950.png)

如果把左外连接改写右外连接那么改写 left outer join 两边的位置即可 



自连接

记得细节就是同一个表最好重命名

![f4669e4800d429424ee836549877af4](C:\Users\14399\AppData\Local\Temp\WeChat Files\f4669e4800d429424ee836549877af4.jpg)

![image-20230318154434872](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318154434872.png)

![image-20230318154441715](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318154441715.png)





联合查询

![image-20230318154931171](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318154931171.png)

![image-20230318154836237](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318154836237.png)





子查询

![image-20230318155256799](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318155256799.png)

标量子查询

![image-20230318155402705](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318155402705.png)

![image-20230318155520716](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318155520716.png)

列表子查询

![image-20230318160250689](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318160250689.png)

![image-20230318160630041](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318160630041.png)

all 和 in 和 any的用法

列子查询

![image-20230318160934250](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318160934250.png)

![image-20230318161015392](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318161015392.png)



表子查询

![image-20230318161328339](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230318161328339.png)

与行子列表查询不同的是这里不是 = 号 而是 in





外连接1.左连接 2.右连接

![img](https://img-blog.csdnimg.cn/20200916152844965.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvdmVseV9fUlI=,size_16,color_FFFFFF,t_70#pic_center)





1.左连接

```mysql
select * from tablea LEFT JOIN tableb on tablea.aid=tableb.bid;
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200916153343905.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvdmVseV9fUlI=,size_16,color_FFFFFF,t_70#pic_center)

是以tablea为基准

````mysql
select * from tableb LEFT JOIN tablea on tablea.aid=tableb.bid;
````

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200916153503708.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvdmVseV9fUlI=,size_16,color_FFFFFF,t_70#pic_center)

是以tableb为基准

看完这两个例子,想必大家也能够自己分析出来了,显然永远是左表的数据是完整的,右表中只会查询出与左表匹配的数据,如果不匹配就不显示,显示为空.整个过程都是`以左表为基准`的



2.右连接

````mysql
select * from tablea RIGHT JOIN tableb on tablea.aid=tableb.bid;
````

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200916154043562.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvdmVseV9fUlI=,size_16,color_FFFFFF,t_70#pic_center)

显然是以tableb的数据为基准的

````mysql
select * from tableb RIGHT JOIN tablea on tablea.aid=tableb.bid;
````

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020091615410268.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvdmVseV9fUlI=,size_16,color_FFFFFF,t_70#pic_center)

![image-20230327190321959](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230327190321959.png)
