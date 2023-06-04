# 1.JAVAWeb

![image-20230311143751148](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311143751148.png)

肯定存在一个真实的文件在某个电脑上，我们在电脑上能访问到任何一个网页或者资源，都存在于这个世界的某个电脑上

URL：

这个统一的web资源会被放在同一个文件夹下，web应用程序

web应用程序--》tomcat：服务器

一个web应用由多部分组成（静态web） 动态（web）

- html css js
- jsp servlet
- java程序
- jar包
- 配资文件（properties）web应用程序编写完毕后，若想给外界访问：需要一个服务器统一管理；



## 静态web

- *html，*htm,这些都是网络的后缀，如果服务器上一直存在这些东西，我们就能直接访问

![image-20230311150228348](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311150228348.png)

静态web的缺点

- web页面是无法更新的，所有用户看到的都是同一个页面

- 轮播图 点击特效 ：伪动态
- javascript【实际开发】
- VBscript
- 数据无法持久化（它无法和数据库交互）



## 动态web

页面会动态展示："Web的页面展示的效果因人而异"

![image-20230311151245797](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311151245797.png)

缺点：

- 假如服务器的动态web资源出现了错误，我们需要重新编写我们的*后台程序*
- 停机维护



优点：

- web页面是动态更新的，所有用户看到的都是不同的页面

- 他可以做数据交互（数据持久化：注册，商品信息，用户信息）





新手村gogogo！

# 2.Web服务器

ASP（微软，国内最早流行）

在HTML文件中嵌入了VB的脚本，ASP + COM；

在ASP开发中，基本一个页面(html里嵌入c语言)c#

维护成本高！

````html
<h1>
    <h1>
        <%
           嵌入c语言代码
           printf("hello world");
           %>
        <body>
            
````

PHP

- php开发速度快，功能强大，跨平台，代码很简单（70%，WP）
- 无法承载大访问量的情况（局限性)



JSP：

- servlet：
- sun公司主推的B/S（浏览器和服务器）架构
- 主要的实现语言是基于java，（所有的大公司，或者一些开源的组件，都是用java写的）高并发，高性能，高可用
- 语法像ASP，ASP->JSP,加强市场强度；



web服务器

服务器是一种被动的操作，用来处理用户的一些请求和给用户一些响应信息

微软 ASP....Windows中自带

Tomcat

Tomcat是Apache 软件基金会（Apache Software Foundation）的[Jakarta](https://baike.baidu.com/item/Jakarta/15952232?fromModule=lemma_inlink) 项目中的一个核心项目，由[Apache](https://baike.baidu.com/item/Apache/6265?fromModule=lemma_inlink)、Sun 和其他一些公司及个人[共同开发](https://baike.baidu.com/item/共同开发/12674474?fromModule=lemma_inlink)而成。由于有了Sun 的参与和支持，最新的Servlet 和[JSP](https://baike.baidu.com/item/JSP/141543?fromModule=lemma_inlink) 规范总是能在Tomcat 中得到体现，Tomcat 5支持最新的Servlet 2.4 和JSP 2.0 规范。因为Tomcat 技术先进、性能稳定，而且免费，因而深受[Java](https://baike.baidu.com/item/Java/85979?fromModule=lemma_inlink) 爱好者的喜爱并得到了部分软件开发商的认可，成为比较流行的Web [应用服务器](https://baike.baidu.com/item/应用服务器/4971773?fromModule=lemma_inlink)。

Tomcat 服务器是一个免费的[开放源代码](https://baike.baidu.com/item/开放源代码/114160?fromModule=lemma_inlink)的[Web](https://baike.baidu.com/item/Web/150564?fromModule=lemma_inlink) 应用服务器，属于轻量级应用服务器，在中小型系统和并发访问用户不是很多的场合下被普遍使用，是开发和调试JSP 程序的首选。对于一个初学者来说，可以这样认为，当在一台机器上配置好Apache 服务器，可利用它响应[HTML](https://baike.baidu.com/item/HTML/97049?fromModule=lemma_inlink)（[标准通用标记语言](https://baike.baidu.com/item/标准通用标记语言/6805073?fromModule=lemma_inlink)下的一个应用）页面的访问请求。实际上Tomcat是Apache 服务器的扩展，但[运行时](https://baike.baidu.com/item/运行时/3335184?fromModule=lemma_inlink)它是独立运行的，所以当你运行tomcat 时，它实际上作为一个与Apache 独立的进程单独运行的。

诀窍是，当配置正确时，Apache 为HTML页面服务，而Tomcat 实际上运行JSP 页面和Servlet。另外，Tomcat和IIS等Web服务器一样，具有处理HTML页面的功能，另外它还是一个Servlet和JSP容器，独立的Servlet容器是Tomcat的默认模式。不过，Tomcat处理静态[HTML](https://baike.baidu.com/item/HTML/97049?fromModule=lemma_inlink)的能力不如Apache服务器。Tomcat最新版本为10.0.23**。**

工作3-5年之后，乐意尝试手写Tomcat服务器；

- 下载tomcat：
- 1.安装或则解压
- 2.了解配置文件及其目录结构
- 3.作用？

# 3.安装Tomcat

![image-20230311153906328](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311153906328.png)

![image-20230311154200583](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311154200583.png)

解压之后的文件

![image-20230311154306629](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311154306629.png)

文件夹作用

启动tomcat 

startup..

<img src="C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311154802998.png" alt="image-20230311154802998" style="zoom:33%;" />

启动成功

shutdown关闭tomcat

![image-20230311154848770](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311154848770.png)

访问https://localhost:8080/

可能遇到的问题

- 1.java环境变量没有配置
- 闪退问题：需要配置兼容性
- 服务器核心配置文件 server.xml

一个文件夹代表一个JSP程序

![image-20230311155102756](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311155102756.png)

这个server.xml核心文件

````xml
<Connector port="8080" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />

<Host name="localhost"  appBase="webapps"
       unpackWARs="true" autoDeploy="true">
````

可以配置启动的端口号

tomcat的默认端口号:8080

mysql的默认端口号:3306

http的默认端口80

https的默认端口443

可以配置主机的称号

![image-20230311160237325](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311160237325.png)

存放JSP程序的文件夹



![image-20230311160544795](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311160544795.png)

抓包

![image-20230311160631926](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311160631926.png)

百度的抓包



可以配置主机名为：localhost->127.0.0.1

默认网站应用存放的位置：webapps

高难度面试题：请你谈一谈网站如何进行访问

- 输入一个域名
- 检查本机的
- C:\windows\System32\drives\etc\hosts配置文件下有没有域名映射
- 有，直接返回对应的ip地址
- 没有：去DNS服务器上找，找到就返回ip，找不到就返回失败
- （计算机网络的内容）

4.配置一下环境变量(可选)

# 4.发布一个web网站

首先我通过学习可以知道

![image-20230311190619448](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311190619448.png)

然后之前写过一个个人简介的前端html，我们把html文件拉到这里来试试看看我们第一个web小程序能不能查看。。。

![image-20230311190836268](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311190836268.png)

![image-20230311190923300](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311190923300.png)

我们通过网站去访问试试。。

首先访问https://localhost:8080/主文件夹

![image-20230311191149537](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311191149537.png)

通过http://losthost:8080/panheng/可以查看到我的文档

它会自动加载index.html文件（默认的）

![image-20230311191205583](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311191205583.png)

![image-20230311191505289](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311191505289.png)

/docs/

![image-20230311191529307](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230311191529307.png)

所以总结一下🤭

- 将自己写的网站，放到服务器（Tomcat）中指定的web应用的文件夹（webapps）下，就可以访问了

- ````java
  - -webapps: Tomcat服务器的web文件夹
      -ROOT
      -panheng：网站的目录名
         --WEB-INF
      	--classes ： java程序
      	--lib：web应用所依赖的jar包
      	--web.xml:网站配置文件
         --index.jsp 默认的首页
         -- static
              -css
                -style.css
         --js
         --img
       --.........
             
  ````

- 

# 5.HTTP讲解

Http：超文本传输协议（Hyper Text [Transfer Protocol](https://baike.baidu.com/item/Transfer Protocol/612755?fromModule=lemma_inlink)，HTTP）是一个简单的请求-响应协议，它通常运行在[TCP](https://baike.baidu.com/item/TCP/33012?fromModule=lemma_inlink)之上。它指定了客户端可能发送给服务器什么样的消息以及得到什么样的响应。请求和响应消息的头以[ASCII](https://baike.baidu.com/item/ASCII/309296?fromModule=lemma_inlink)形式给出；而 [9] 消息内容则具有一个类似[MIME](https://baike.baidu.com/item/MIME/2900607?fromModule=lemma_inlink)的格式。这个简单模型是早期Web成功的有功之臣，因为它使开发和部署非常地直截了当。

- 文本：html，字符串。。。。。。
- 超文本：图片，音乐，视频，定位，地图。。。。。
- 80

Https：（安全）

- 443



## 两个时代

http1.0

-  HTTP/1.0:客户端可以与web服务器连接后，只能获得一个web资源，断开连接。想要链接只能再请求

http2.0

- HTTP/1.1：做了优化可以获得更多的web资源



## Http请求request

- 客户---请求-----服务器

百度：

````java
Request URL: https://www.baidu.com/?tn=15007414_8_dg  请求地址
Request Method: GET 请求方法 （Post）
Static Code: 200 OK   状态码 200 
Remote Address: 14.119.104.189:443 (百度地址和端口)
引用者策略: strict-origin-when-cross-origin
````

1.请求行

- 请求行中的请求方式：GET
- 请求方式：Get，Post，HEAD，DELETE，PUT，TRACT
- get：请能够获得的参数比较少，大小有限制，会在浏览器的URL地址栏显示数据内容，不安全，但高效
- post：请求能够携带的参数没有限制，大小没有限制，不会在浏览器的URL地址栏显示数据内容，安全。但不高效

2.请求头

````java
Accept:告诉浏览器，他所支持的数据类型
Accept-Encoding：支持哪种编码格式 GBK UTF-8 GB2312 Iso8859-1
Accept-languge:浏览器语言环境
Cache-conctrol:缓存控制
Connection:告诉浏览器，请求完成时断开还是保持连接
Host:主机.../.
````



## Http响应response

- 服务器----

```java
Bdpagetype: 2
Bdqid: 0xb8d0d489001ca2e8
Cache-Control: private 缓存控制
Connection: keep-alive 连接
Content-Encoding: gzip 编码类型 
Content-Type: text/html;charset=utf-8 类型
Date: Sat, 11 Mar 2023 11:37:28 GMT
Expires: Sat, 11 Mar 2023 11:37:28 GMT
Isprivate: 1
P3p: CP=" OTI DSP COR IVA OUR IND COM "
Server: BWS/1.1
Set-Cookie: BDRCVFR[-BxzrOzUsTb]=mk3SLVN4HKm; path=/; domain=.baidu.com
Set-Cookie: BDSVRTM=428; path=/
Set-Cookie: BD_HOME=1; path=/
Set-Cookie: H_PS_PSSID=26350; path=/; domain=.baidu.com
Strict-Transport-Security: max-age=172800
Traceid: 1678534648043918593013317377783012041448
Transfer-Encoding: chunked
X-Frame-Options: sameorigin
X-Ua-Compatible: IE=Edge,chrome=1
```

响应体：

````java
Accept:告诉浏览器，他所支持的数据类型
Accept-Encoding：支持哪种编码格式 GBK UTF-8 GB2312 Iso8859-1
Accept-languge:浏览器语言环境
Cache-conctrol:缓存控制
Connection:告诉浏览器，请求完成时断开还是保持连接
Host:主机.../.
Reflesh:刷新，告诉客户端多久刷新一次
Localtion:让网络重新定位
````

响应状态码：

200:请求响应成功

4** :找不到资源，资源不存在 404

3**:重定向，重新到一个指定的地方

5**：服务器代码错误 500 502网关错误

面试题：

当你的浏览器中地址栏并回车的一瞬间到页面能够展示回来，经历了什么？

















![在这里插入图片描述](https://img-blog.csdnimg.cn/8cef58a9d21847818137e1010b4a9bcb.png)

有哪些角色（在整个BS结构的系统当中，有哪些人参与进去了）
浏览器软件的开发团队（浏览器软件太多了：谷歌浏览器、火狐浏览器、IE浏览器…）
WEB Server的开发团队（WEB Server这个软件也是太多了：Tomcat、Jetty、WebLogic、JBOSS、WebSphere…）
DB Server的开发团队（DB Server这个软件也是太多了：Oracle、MySQL…）
webapp的开发团队（WEB应用是我们做为JavaWEB程序员开发的）
角色和角色之间需要遵守哪些规范，哪些协议
webapp的开发团队 和 WEB Server的开发团队 之间有一套规范: JavaEE规范之一Servlet规范。
Servlet规范的作用是什么？
WEB Server 和 webapp解耦合。
Browser 和 WebServer之间有一套传输协议：HTTP协议。（超文本传输协议。）
webapp开发团队 和 DB Server的开发团队之间有一套规范：JDBC规范。
![在这里插入图片描述](https://img-blog.csdnimg.cn/e04f048e2ef1425a8dcbf065fc190043.png)

### 模拟Servlet本质

package javax.servlet;

/*
	我们现在充当的角色时SUN公司
	SUN公司把Servlet接口/规范制定出来
*/
public interface Servlet{

```java
// 一个专门提供服务的方法
void service();
```
}



充当Tomcat服务器的开发者

package org.apache;

import java.util.Scanner;
import java.util.Properties;
import java.io.FileReader;
import javax.servlet.Servlet;

// 充当Tomcat服务器的开发者
public class Tomcat{
	public static void main(String[] args) throws Exception{
		System.out.println("Tomcat服务器启动成功，开始接收用户的访问。");

```java
	// 简单的使用Scanner来模拟一下用户的请求
	// 用户访问服务器是通过浏览器上的“请求路径”
	// 也就是说用户请求路径不同，后台执行的Servlet不同。
	/*
		/userList    UserListServlet
		/login		 UserLoginServlet
		/bank		 BankServlet
		......
	*/
	System.out.print("请输入您的访问路径：");
	Scanner s = new Scanner(System.in);

	// 用户的请求路径  /bbbb
	String key = s.nextLine(); // Tomcat服务器已经获取到了用户的请求路径了。

	// Tomcat服务器应该通过用户的请求路径找对应的XXXServlet
	// 请求路径和XXXServlet之间的关系应该由谁指定呢？
	// 对于Tomcat服务器来说需要解析配置文件
	FileReader reader = new FileReader("web.properties");
	Properties pro = new Properties();
	pro.load(reader);
	reader.close();

	// 通过key获取value
	String className = pro.getProperty(key);
	// 通过反射机制创建对象
	Class clazz = Class.forName(className);
	Object obj = clazz.newInstance(); // obj的类型对于Tomcat服务器开发人员来说不知道。
	
	// 但是Tomcat服务器的开发者知道，你写的XXXXServlet一定实现了Servlet接口
	Servlet servlet = (Servlet)obj;
	servlet.service();

 }
}
```






````java
充当Webapp的开发者

package com.bjpowernode.servlet;

import javax.servlet.Servlet;

// 充当的角色发生了改变:webapp开发者
// 只要是我们webapp开发者写的XXXServlet都要实现Servlet接口

//银行

public class BankServlet implements Servlet{
	public void service(){
		System.out.println("BankServlet's service...");
	}
}


````



````java
//使用者列表

package com.bjpowernode.servlet;

import javax.servlet.Servlet;

// 充当的角色发生了改变:webapp开发者

public class UserListServlet implements Servlet{
	public void service(){
		System.out.println("UserListServlet's service...");
	}
}
````



````java
package com.bjpowernode.servlet;

import javax.servlet.Servlet;

// 充当的角色发生了改变:webapp开发者
// 登入webapps

public class UserLoginServlet implements Servlet{
	public void service(){
		System.out.println("UserLoginServlet's service...");
	}
}
````



//web.properties

````properties
/aaaa=com.bjpowernode.servlet.UserListServlet
/bbbb=com.bjpowernode.servlet.UserLoginServlet
/cccc=com.bjpowernode.servlet.BankServlet
````



# Servlet规范

遵循Servlet规范的webapp，这个webapp就可以放在不同的WEB服务器中运行。（因为这个webapp是遵循Servlet规范的。）
Servlet规范包括什么呢？
规范了哪些接口
规范了哪些类
规范了一个web应用中应该有哪些配置文件
规范了一个web应用中配置文件的名字
规范了一个web应用中配置文件存放的路径
规范了一个web应用中配置文件的内容
规范了一个合法有效的web应用它的目录结构应该是怎样的。





# 开发一个带有Servlet

（Java小程序）的webapp（重点）

第一步：在webapps目录下新建一个目录，起名crm（这个crm就是webapp的名字）。当然，也可以是其它项目，比如银行项目，可以创建一个目录bank，办公系统可以创建一个oa。

注意：crm就是这个webapps的根

![在这里插入图片描述](https://img-blog.csdnimg.cn/fa6e4ce989f34f80b3b9f3a54da37ef9.png)

第二步：在webapp的根下新建一个目录：WEB-INF

注意：这个目录的名字是Servlet规范中规定的，必须全部大写，必须一模一样。必须的必须。

![在这里插入图片描述](https://img-blog.csdnimg.cn/3558962613704a1c8197b7be50e60c32.png)

第三步：在WEB-INF目录下新建一个目录：classes

注意：这个目录的名字必须是全部小写的classes。这也是Servlet规范中规定的。另外这个目录下一定存放的是Java程序编译之后的class文件（这里存放的是字节码文件）。

![在这里插入图片描述](https://img-blog.csdnimg.cn/cce9afaa3cb04a6fbec90b9870ecb4d8.png)

第四步：在WEB-INF目录下新建一个目录：lib

注意：这个目录不是必须的。但如果一个webapp需要第三方的jar包的话，这个jar包要放到这个lib目录下，这个目录的名字也不能随意编写，必须是全部小写的lib。例如java语言连接数据库需要数据库的驱动jar包。那么这个jar包就一定要放到lib目录下。这Servlet规范中规定的。
![image-20230420230134165](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230420230134165.png)

第五步：在WEB-INF目录下新建一个文件：web.xml

注意：这个文件是必须的，这个文件名必须叫做web.xml。这个文件必须放在这里。一个合法的webapp，web.xml文件是必须的，这个web.xml文件就是一个配置文件，在这个配置文件中描述了请求路径和Servlet类之间的对照关系。

![image-20230420230335432](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230420230335432.png)

- 这个文件最好从其他的webapp中拷贝，最好别手写。没必要。复制粘贴

````xml
<?xml version="1.0" encoding="UTF-8"?>

<web-app xmlns="https://jakarta.ee/xml/ns/jakartaee"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://jakarta.ee/xml/ns/jakartaee
                      https://jakarta.ee/xml/ns/jakartaee/web-app_5_0.xsd"
  version="5.0"
  metadata-complete="true">


</web-app>


````

第六步：编写一个Java程序，这个小Java程序也不能随意开发，这个小java程序必须实现Servlet接口。

这个Servlet接口不在JDK当中。（因为Servlet不是JavaSE了。Servlet属于JavaEE，是另外的一套类库。）
Servlet接口（Servlet.class文件）是Oracle提供的。（最原始的是sun公司提供的。）
Servlet接口是JavaEE的规范中的一员。
Tomcat服务器实现了Servlet规范，所以Tomcat服务器也需要使用Servlet接口。Tomcat服务器中应该有这个接口，Tomcat服务器的CATALINA_HOME\lib目录下有一个servlet-api.jar，解压这个servlet-api.jar之后，你会看到里面有一个Servlet.class文件。

![image-20230420230516123](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230420230516123.png)

重点：从JakartaEE9开始，Servlet接口的全名变了：jakarta.servlet.Servlet

注意：编写这个Java小程序的时候，java源代码你愿意在哪里就在哪里，位置无所谓，你只需要将java源代码编译之后的class文件放到classes目录下即可。

第七步：编译我们编写的HelloServlet

````java
package com.bjpowernode.servlet;

// 在Tomcat9以及Tomcat9之前的版本中使用javax.servlet这个包
import jakarta.servlet.Servlet;
import jakarta.servlet.ServletException;
import jakarta.servlet.ServletRequest;
import jakarta.servlet.ServletResponse;
import jakarta.servlet.ServletConfig;
import java.io.IOException;
import java.io.PrintWriter;


public class HelloServlet implements Servlet{

	// 5个方法
	public void init(ServletConfig config) throws ServletException{
	
	}

	public void service(ServletRequest request,ServletResponse response)
		throws ServletException , IOException{

		// 向控制台打印输出
		System.out.println("My First Servlet, Hello Servlet");
		
	}

	public void destroy(){
	
	}

	public String getServletInfo(){
		return "";
	}

	public ServletConfig getServletConfig(){
		return null;
	}
}

````

重点：你怎么能让你的HelloServlet编译通过呢？配置环境变量CLASSPATH `CLASSPATH=.;C:\dev\apache-tomcat-10.0.12\lib\servlet-api.jar`

得看你的存储位置

![image-20230420231451297](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230420231451297.png)

- 思考问题：以上配置的CLASSPATH和Tomcat服务器运行有没有关系？
  - 没有任何关系，以上配置这个环境变量只是为了让你的HelloServlet能够正常编译生成class文件。

第八步：将以上编译之后的HelloServlet.class文件拷贝到WEB-INF\classes目录下。

````java
javac -d . HelloServlet.java
````

![image-20230420231602745](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230420231602745.png)

第九步：在web.xml文件中编写配置信息，让“请求路径”和“Servlet类名”关联在一起。

- 这一步用专业术语描述：在web.xml文件中注册Servlet类。
- 可能会由于xml配置文件中的注释信息导致Tomcat启动报错，可以将xml配置文件中的注释信息删除

````xml
<?xml version="1.0" encoding="UTF-8"?>

<web-app xmlns="https://jakarta.ee/xml/ns/jakartaee"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://jakarta.ee/xml/ns/jakartaee
                      https://jakarta.ee/xml/ns/jakartaee/web-app_5_0.xsd"
  version="5.0"
  metadata-complete="true">

	<!--servlet描述信息-->
	<!--任何一个servlet都对应一个servlet-mapping -->
	<servlet>
		<servlet-name>fdsafdsagfdsafdsa</servlet-name>
		<!--这个位置必须是带有包名的全限定类名-->
		<servlet-class>com.bjpowernode.servlet.HelloServlet</servlet-class>
	</servlet>

	<!--servlet映射信息-->
	<servlet-mapping>
		<!--这个也是随便的，不过这里写的内容要和上面的一样。-->
		<servlet-name>fdsafdsagfdsafdsa</servlet-name>
		<!--这里需要一个路径-->
		<!--这个路径唯一的要求是必须以 / 开始-->
		<!--当前这个路径可以随便写-->
		<url-pattern>/fdsa/fd/saf/d/sa/fd/sa/fd</url-pattern>
	</servlet-mapping>
	
</web-app>


````

第十步：启动Tomcat服务器

![image-20230420231716336](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230420231716336.png)

第十一步：打开浏览器，在浏览器地址栏上输入一个url，

这个URL必须是：http://127.0.0.1:8080/crm/fdsa/fd/saf/d/sa/fd/sa/fd

   启动Tomcat服务器之后，Tomcat会监听ip地址表示的主机的8080端口，crm表示访问部署在Tomcat服务器上的crm项目，fdsa/fd/saf/d/sa/fd/sa/fd表示访问的项目资源路径
   非常重要的一件事：浏览器上的请求路径不能随便写，这个请求路径必须和web.xml文件中的url-pattern一致。
   注意：浏览器上的请求路径和web.xml文件中的url-pattern的唯一区别就是：浏览器上的请求路径  带项目名：/crm
浏览器上编写的路径太复杂，可以使用超链接。（**非常重要：html页面只能放到WEB-INF目录外面。**）

````html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <a href="/crm/fdsa/fd/saf/d/sa/fd/sa/fd">HelloServelet</a>
  </body>
</html>

````

![image-20230420231928717](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230420231928717.png)

以后不需要我们编写main方法了。tomcat服务器负责调用main方法，Tomcat服务器启动的时候执行的就是main方法。我们javaweb程序员只需要编写Servlet接口的实现类，然后将其注册到web.xml文件中，即可。

总结一下：一个合法的webapp目录结构应该是怎样的？

````txt
webapproot
     |------WEB-INF
     		  |------classes(存放字节码)
     		  |------lib(第三方jar包)
     		  |------web.xml(注册Servlet)
     |------html
     |------css
     |------javascript
     |------image
     ....

````

浏览器发送请求，到最终服务器调用Servlet中的方法，是怎样的一个过程？（以下这个过程描述的很粗糙。其中还有很多步骤我省略了。）

用户输入URL，或者直接点击超链接：http://127.0.0.1:8080/crm/fdsa/fd/saf/d/sa/fd/sa/fd
然后Tomcat服务器接收到请求，截取路径：/crm/fdsa/fd/saf/d/sa/fd/sa/fd
Tomcat服务器找到crm项目
Tomcat服务器在web.xml文件中查找/fdsa/fd/saf/d/sa/fd/sa/fd 对应的Servlet是：com.bjpowernode.servlet.HelloServlet
Tomcat服务器通过反射机制，创建com.bjpowernode.servlet.HelloServlet的对象。
Tomcat服务器调用com.bjpowernode.servlet.HelloServlet对象的service方法。





1.Sevlet由谁创建？Servlet由谁调用？

​     servlet由web服务器创建，Servlet方法由web服务器创建调用.

2.服务器怎么知道Servlet中一定有service方法?

​	 实现servlet接口中会有该方法.





Servlet生命周期

分为四个阶段：

第一个阶段：加载和实例化，默认情况下，当Servlet第一次被访问的时候，有容器创建Servlet对象

第二个阶段：在Servlet实例化之后，容器将调用Servlet的init（）方法来初始化这个对象，完成一些加载配置文件、创建链接等初始化的工作。该方法只调用一次。

第三个阶段：请求处理：每次请求Servlet时，Servlet容器都会调用Servlet方法对请求进行处理。

第四个阶段：服务终止：当需要释放内存或者容器关闭时，容器就会调用Servlet实例的Destroy（）方法完成资源的释放。在destroy（）方法调用之后，容器会释放这个servlet实例，该实例随后会被java的垃圾收集器回收



Servlet -->体系根接口

genericServlet --> Servlet抽象实现类

httpServlet --> 对HTTP协议封装的实现类



> @WebServlet()
>
> 请求路径
>
> 1. 精确匹配 例如 @WebServlet("/user/seclect")
>
> 2. 目录匹配 例如 @WebServlet("/user/*")  精确匹配和目录匹配 优先级前者高
>
> 3. 扩展名匹配 例如 @WebServlet("*.do") 后缀扩展名 .do
>
> 4. 任意匹配 例如 @WebServlet("/*") 
>
>    @WebServlet("/")  静态资源会被覆盖



# Request&&Response

> request:获取请求数据
>
> - ​     浏览器会发送HTTP请求到后台服务器[Tomcat]
> - ​     HTTP的请求中会包含很多请求数据[请求行+请求头+请求体]
> - ​     后台服务器[Tomcat]会对HTTP请求中的数据进行解析并把解析结果存入到一个对象中
> - ​     所存入的对象即为request对象，所以我们可以从request对象中获取请求的相关参数
> - ​     获取到数据后就可以继续后续的业务，比如获取用户名和密码就可以实现登录操作的相关业务
>
> response:设置响应数据
>
> - 业务处理完后，后台就需要给前端返回业务处理的结果即响应数据
> - 把响应数据封装到response对象中
> - 后台服务器[Tomcat]会解析response对象,按照[响应行+响应头+响应体]格式拼接结果
> - 浏览器最终解析结果，把内容展示在浏览器给用户浏览



### Request

1.Request继承体系

![image-20230428123123655](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230428123123655.png)

![image-20230428123523069](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230428123523069.png)

2.Request获取请求数据

HTTP请求数据总共分为三部分内容，分别是请求行、请求头、请求体，对于这三部分内容的数据，分别该如何获取，首先我们先来学习请求行数据如何获取?

####  获取请求行数据

![image-20230428205426261](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230428205426261.png)

对于这三部分内容，request对象都提供了对应的API方法来获取，具体如下:

1.String getMethod() 

​	获取请求方式：GET

2.String getContextPath()

​	获取虚拟目录（项目访问路径）:/request-demo

3.StringBuffer getRequestURL()

   获取URL(统一资源定位符): `http://localhost:8080/request-    demo/req1`

 4.String getRequestURI()

​	获取URI(统一资源标识符): `/request-demo/req1`

5.String getQueryString()

   获取请求参数(GET方式): `username=zhangsan&password=123`

> 1. 调用getReader()或者getInputStream()方法，因为目前前端传递的是纯文本数据，所以我们采用getReader()方法来获取
>
> - 请求头
>   - getHeader(String name)根据请求头名称获取其对应的值
> - 请求体
>   - 注意: 浏览器发送的POST请求才有请求体
>   - 如果是纯文本数据:getReader()
>   - 如果是字节数据如文件数据:getInputStream()

不用手动关闭

BufferedReader流是通过request对象来获取的，当请求完成后request对象就会被销毁，request对象被销毁后，BufferedReader流就会自动关闭，所以此处就不需要手动关闭流了。





GET请求和POST请求获取请求参数的方式不一样，在获取请求参数这块该如何实现呢?

要想实现，我们就需要思考:

GET请求方式和POST请求方式区别主要在于获取请求参数的方式不一样，是否可以提供一种统一获取请求参数的方式，从而统一doGet和doPost方法内的代码?

方案一：

使用request的getMethod()来获取请求方式，根据请求方式的不同分别获取请求参数值，这样就可以解决上述问题，但是以后每个Servlet都需要这样写代码，实现起来比较麻烦，这种方案我们不采用



方案二：

request对象已经将上述获取请求参数的方法进行了封装，并且request提供的方法实现的功能更强大，以后只需要调用request提供的方法即可，在request的方法中都实现了哪些操作?

![image-20230428225344390](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230428225344390.png)

![image-20230428225359049](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230428225359049.png)

- 获取所有参数Map集合

```java
Map<String,String[]> getParameterMap()
```

- 根据名称获取参数值（数组）

```java
String[] getParameterValues(String name)
```

- 根据名称获取参数值(单个值)

```java
String getParameter(String name)
```





#### 请求中文乱码问题

![image-20230429155158975](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230429155158975.png)

例子上说会有该问题 不过我没出现 ，也当学习吧

![image-20230429155432038](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230429155432038.png)

![image-20230429163600571](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230429163600571.png)

![image-20230429163730711](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230429163730711.png)

URL编码

1.将字符串按编码方式转为二进制

2 每个字节转为2个16进制数并在前边加上%

![image-20230429164536233](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230429164536233.png)

![image-20230429164807239](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230429164807239.png)

![image-20230429164832791](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230429164832791.png)

具体的实现步骤为:

> 1.按照ISO-8859-1编码获取乱码`å¼ ä¸‰`对应的字节数组
>
> 2.按照UTF-8编码获取字节数组对应的字符串

![image-20230429165509261](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230429165509261.png)

![image-20230429165527743](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230429165527743.png)





#### Request请求转发

![image-20230429234648453](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230429234648453.png)

req.getRequestDispatcher("资源路径").forward(req,resp); 

![image-20230429235613654](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230429235613654.png)





## Response

![image-20230430150257680](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230430150257680.png)

````java
void setStatus(int sc);
````

![image-20230430150338212](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230430150338212.png)

```java
void setHeader(String name,String value);
```

![image-20230430150406104](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230430150406104.png)

```java
PrintWriter getWriter();
ServletOutputStream getOutputStream();
```



Response完成重定向

重定向 :一种资源跳转方式

![image-20230430150631656](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230430150631656.png)

![image-20230430151518971](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230430151518971.png)

![image-20230430151952496](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230430151952496.png)

路径问题

- 明确路径谁使用？
  - 浏览器使用：需要加虚拟目录（项目访问路径）
  - 服务端使用：不需要加载虚拟目录



![image-20230430152144110](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230430152144110.png)

1. 加虚拟目录 因为是在浏览器端请求
2. 加虚拟目录 同上
3. 不需要加虚拟目录，是在服务器内部跳转
4. 需要加虚拟目录 发送到浏览器端处理



出现中文乱码问题

 

```java
public class ResDemo3 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //获取输出流
        //resp.setCharacterEncoding("UTF-8");
        resp.setContentType("text/html;charset=utf-8");
        PrintWriter writer = resp.getWriter();
        //resp.setHeader("content-type","text/html");
        writer.write("潘恒");
        writer.write("<h1>aaa<h1>");
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        this.doGet(req, resp);
    }
```





## 用户登入案例

接下来我们通过两个比较常见的案例，一个是注册，一个是登录来对今天学习的内容进行一个实战演练，首先来实现用户登录。

![image-20230430164408581](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230430164408581.png)































# MVC模式和三层架构

## MVC模式

![image-20230503160756187](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230503160756187.png)



**MVC 好处：**

- 职责单一，互不影响。每个角色做它自己的事，各司其职。
- 有利于分工协作。
- 有利于组件重用。



## 三层架构

![image-20230503160839078](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230503160839078.png)

1. 数据访问层：对数据库的CRUD基本操作
2. 业务逻辑层：对业务逻辑进行封装，组合数据访问层层中基本功能，形成复杂的业务逻辑功能。例如 注册业务功能 ，我们会先调用 数据访问层 的 selectByName() 方法判断该用户名是否存在，如果不存在再调用 数据访问层 的 insert() 方法进行数据的添加操作
3. 表现层：接收请求，封装数据，调用业务逻辑层，响应数据

而整个流程是，浏览器发送请求，表现层的Servlet接收请求并调用业务逻辑层的方法进行业务逻辑处理，而业务逻辑层方法调用数据访问层方法进行数据的操作，依次返回到serlvet，然后servlet将数据交由 JSP 进行展示。



![image-20230503161028610](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230503161028610.png)





MVC模式和三成架构的联系

![image-20230503161258723](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230503161258723.png)





## 项目准备

![image-20230503161432960](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230503161432960.png)



````xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>org.example</groupId>
    <artifactId>brand-demo</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>war</packaging>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- mybatis -->
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
            <version>3.5.5</version>
        </dependency>

        <!--mysql-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.34</version>
        </dependency>

        <!--servlet-->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
            <version>3.1.0</version>
            <scope>provided</scope>
        </dependency>

        <!--jsp-->
        <dependency>
            <groupId>javax.servlet.jsp</groupId>
            <artifactId>jsp-api</artifactId>
            <version>2.2</version>
            <scope>provided</scope>
        </dependency>

        <!--jstl-->
        <dependency>
            <groupId>jstl</groupId>
            <artifactId>jstl</artifactId>
            <version>1.2</version>
        </dependency>
        <dependency>
            <groupId>taglibs</groupId>
            <artifactId>standard</artifactId>
            <version>1.1.2</version>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.tomcat.maven</groupId>
                <artifactId>tomcat7-maven-plugin</artifactId>
                <version>2.2</version>
            </plugin>
        </plugins>
    </build>
</project>

````

