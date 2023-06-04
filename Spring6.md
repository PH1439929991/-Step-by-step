# Spring6

## 一、基本的框架

三层架构 Dao（数据持久层） Service(业务层) Web(网页层)

![image-20230504161850012](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230504161850012.png)

层与层之间通过接口的方式传递。

我们在Dao层上写我们的方法接口，在Dao包下创建一个Impl包，在Impl包中写实现类

去实现这个接口 。

并在Service层中继续使用按照这个规则去实现接口，然后使用Dao层的方法。以此类推到Web层。





OCP

1. 什么是ocp？
   1. ocp是软件七大开发原则当中最基本的一个原则：开闭原则
   2. 对什么开？对扩展开放。
   3. 对什么闭？对修改关闭。

​	2.ocp原则是对核心的，最基本的，其他的六个原则都是围绕这个原则服务的。

​	3.ocp开闭原则的核心是什么？

​			只要你在扩展系统功能的时候，没有修改以前写好的代码，那么你就是符合OCP原则的。

​			反之，如果在扩展系统功能的时候，你修改了之前的代码。那么这个设计就是失败的，违背ocp原则。

​	4.当进行系统功能扩展的时候，如果动了之前稳定的程序，之前所有程序都需要进行重新测试。这是不想看到的。



2. 依赖倒置原则 DIP原则

​	什么是依赖倒置原则？

​			面向接口编程，面向抽象编程，不要面向具体编程。

​	依赖倒置原则的目的？

​			降低代码的耦合度，提高扩展性。

​	什么叫符合依赖倒置？

​			上 不依赖 下



​	3.当前程序的设计，显然违背了OCP，DIP原则，怎么办？

​			可以采用控制反转的编程思想？

​			inversion of control

​			Ioc

​			反转的两件事：

​					1.我不在程序中硬编码的方式new对象。把new对象的权力交出去了。

​					2.我不在程序中采用硬编码的方式来维护对象的关系了。





依赖注入DI

​	1.set注入

​	2.构造方法注入

依赖注入 中 "依赖" 的意思？ "注入"是什么意思？

- ​	依赖：A对象和B对象的关系

- ​    注入：一种手段，通过这种手段，可以让A对象和B对象产生关系。
-    依赖注入：A对象和B对象之间的关系，靠注入的手段来维护，而注入包括“set注入和构造注入 





## 二、Spring框架特点

每一个被spring管理的对象被称为Bean











1. 第一个Spring程序

    

   配置Xml文件

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <beans xmlns="http://www.springframework.org/schema/beans"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
   
       <!--这是spring的配置文件-->
       <!--IDEA工具为我们提供了这个文件的模板，一定要使用这个模块来创建-->
       <!--文件最好是在resource目录下 因为便于后期的移植-->
       <!--配置Bean 这样Spring才可以帮我们管理好这个对象-->
       <!--
           bean标签的两个重要属性：
               id:是这个bean的身份证，不能重复，是唯一的标识
               class:必须添写带带包名的类名
       -->
       <bean id = "UserBean" class="com.phDemo.spring.bean.User"></bean>
       <bean id = "nowTime" class="java.util.Date"></bean>
   <!--    //底层使用Map《id，对象》去储存-->
   <!--    //并且配置文件有很多种-->
   </beans>
   ```

   ```java
   
   public class FirstSpringTest1 {
       @Test
       public void testFirstSpringCode(){
           ApplicationContext applicationContext = new ClassPathXmlApplicationContext("xml/Bean.xml","spring.xml");
           Object studentBean = applicationContext.getBean("studentBean");
           System.out.println(studentBean);
   
   
           //Object studentBead2 = applicationContext.getBean("studentBean2");
           //如果studentBean2这个id不存在，他会报错而不是返回null
   
           Object nowTime = applicationContext.getBean("nowTime");
           //日期格式化
   
           //这个是强转的方式
           //如果我们想得到一个不需要强转的方式得到一个对象呢
           SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
           String format = sdf.format((Date) nowTime);
           System.out.println(format);
   
   
           //params1 是id名称 params2 是得到的类型
           Date nowTime1 = applicationContext.getBean("nowTime", Date.class);
           String format1 = sdf.format(nowTime1);
           System.out.println(format1);
   
       }
   }
   
   
   ```

   

配置文件

```xml
<!--Log4j2的依赖-->
<dependency>
    <groupId>org.apache.logging.log4j</groupId>
    <artifactId>log4j-core</artifactId>
    <version>2.19.0</version>
</dependency>
<dependency>
    <groupId>org.apache.logging.log4j</groupId>
    <artifactId>log4j-slf4j-impl</artifactId>
    <version>2.19.0</version>
</dependency>
```

```xml
<configuration>

<loggers>
    <!--日志级别 level
        ALL 《 TRACE 《 DEBUG 《 INFO 《 WARN 《 ERROR 《 FATAL 《 OFF
    -->
    <root level="DEBUG">
        <appender-ref ref="spring6log"/>
    </root>
</loggers>

<appenders>
    <!--输出日志信息到控制台-->
    <console name="spring6log" target="SYSTEM_OUT">
        <!--控制日志输出的格式-->
        <PatternLayout pattern="%d{yyyy-MM-dd HH:mm:ss SSS} [%t] %-3level %logger{1024} - %msg%n"/>
    </console>
</appenders>
</configuration>
```




Set注入

```java
private static final Logger logger = LoggerFactory.getLogger(UserDao.class);

public void insert(){
    //System.out.println("数据库正在保存用户信息。");
    // 使用一下log4j2日志框架
    logger.info("数据库正在保存用户信息。");
 }
```
```xml
<bean id="userBean" class="com.phDemo.spring6.Dao.User"/>
<bean id="vipBean" class="com.phDemo.spring6.Dao.VipDao"/>

<bean id="userServiceBean" class="com.phDemo.spring6.Service.UserService">
    <!-- 想让Spring调用对应的set方法，需要配置property标签 -->
    <!-- name属性怎么指定值：set方法的方法名，去掉set，然后把剩下的单词首字母变小写，写到这里。-->
    <!-- ref翻译为引用。英语单词：references。ref后面指定的是要注入的bean的id。-->
    <!--<property name="mySQLUserDao" ref="userDaoBean"/>-->

    <!--set方法起名的时候，不要为难自己，按照规范来。所以一般情况下name位置写属性名就行了。-->
    <property name="user1" ref="userBean"/>
    <property name="vip" ref="vipBean"/>

</bean>
```

实现原理：

- 通过property标签获取到属性名：userDao

- 通过属性名推断出set方法名：setUserDao
- 通过反射机制调用setUserDao()方法给属性赋值
- property标签的name是属性名。
- property标签的ref是要注入的bean对象的id。(通过ref属性来完成bean的装配，这是bean最简单的一种装配方式。装配指的是：创建系统组件之间关联的动作)

property标签的name是：setUserDao()方法名演变得到的。演变的规律是：

- setUsername() 演变为 username
- setPassword() 演变为 password
- setUserDao() 演变为 userDao
- setUserService() 演变为 userService
- 另外，对于property标签来说，ref属性也可以采用标签的方式，但使用ref属性是多余的：





构造注入

public class CustomerService {

```java
private UserDao userDao;
private VipDao vipDao;

public CustomerService(UserDao userDao, VipDao vipDao) {
    this.userDao = userDao;
    this.vipDao = vipDao;
}

public void save(){
    userDao.insert();
    vipDao.insert();
}
```

}



<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

```xml
<bean id="xxxx" class="com.powernode.spring6.dao.UserDao"/>

<bean id="yyyy" class="com.powernode.spring6.dao.VipDao"/>

<bean id="csBean3" class="com.powernode.spring6.service.CustomerService">
    <!--不指定下标，也不指定参数名，让spring自己做类型匹配吧。-->
    <!--这种方式实际上是根据类型进行注入的。spring会自动根据类型来判断把ref注入给哪个参数。-->
    <constructor-arg ref="yyyy"/>
    <constructor-arg ref="xxxx"/>
</bean>

<bean id="csBean2" class="com.powernode.spring6.service.CustomerService">
    <!--根据构造方法参数的名字进行注入。-->
    <constructor-arg name="vipDao" ref="yyyy"/>
    <constructor-arg name="userDao" ref="xxxx"/>
</bean>

<bean id="csBean" class="com.powernode.spring6.service.CustomerService">
    <!--构造注入-->
    <!--
        index属性指定参数下标，第一个参数是0，第二个参数是1，第三个参数是2，以此类推。
        ref属性用来指定注入的bean的id
    -->
    <!--指定构造方法的第一个参数，下标是0-->
    <constructor-arg index="0" ref="xxxx"/>
    <!--指定构造方法的第二个参数，下标是1-->
    <constructor-arg index="1" ref="yyyy"/>
</bean>
```

</beans>





内部Bean和外部Bean

```xml
<!--声明/定义Bean-->
<bean id="orderDaoBean" class="com.powernode.spring6.dao.OrderDao"></bean>

<bean id="orderServiceBean" class="com.powernode.spring6.service.OrderService">
    <!--使用ref属性来引入。这就是注入外部Bean-->
    <property name="orderDao" ref="orderDaoBean"/>
</bean>
```

```xml
<bean id="orderServiceBean2" class="com.powernode.spring6.service.OrderService">
    <property name="orderDao">
        <!--在property标签中使用嵌套的bean标签，这就是内部Bean-->
        <bean class="com.powernode.spring6.dao.OrderDao"></bean>
    </property>
</bean>
```





基本类型注入

```java
public class User1 {
    private String username;
    private String password;

    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public String getPassword() {
        return password;
    }

    public void setPassword(String password) {
        this.password = password;
    }

    @Override
    public String toString() {
        return "User1{" +
                "username='" + username + '\'' +
                ", password='" + password + '\'' +
                '}';
    }
}
```

```xml
<bean id="user1Bean" class="com.phDemo.spring6.Dao.User1">
    <property name="username" value="张三"></property>
    <property name="password" value="12456789"></property>
</bean>
```





什么是简单数据类型？

```java
public static boolean isSimpleValueType(Class<?> type) {
   return (Void.class != type && void.class != type &&
         (ClassUtils.isPrimitiveOrWrapper(type) ||
         Enum.class.isAssignableFrom(type) ||
         CharSequence.class.isAssignableFrom(type) ||
         Number.class.isAssignableFrom(type) ||
         Date.class.isAssignableFrom(type) ||
         Temporal.class.isAssignableFrom(type) ||
         URI.class == type ||
         URL.class == type ||
         Locale.class == type ||
         Class.class == type));
}
```

需要特别注意：如果给简单类型赋值，使用value属性或value标签。而不是ref。

通过源码分析得知，BeanUtils类，简单类型包括：

1. 基本数据类型
2. 基本数据类型对应的包装类
3. String或其他的CharSequence子类
4. Number子类
5. Date子类，java.util.Date是简单类型
6. Enum子类
7. URI
8. URL
9. Temporal子类，Temporal是Java8提供的时间和时区类型
10. Locale，Locale是语言类，也是简单类型。
11. Class
12. 另外还包括以上简单值类型对应的数组类型。







注入数组

其中数组的元素是简单元素

````java
public class QianDaYe {
    private String[] aiHaos;

    public void setAiHaos(String[] aiHaos) {
        this.aiHaos = aiHaos;
    }

    @Override
    public String toString() {
        return "QianDaYe{" +
                "aiHaos=" + Arrays.toString(aiHaos) +
                '}';
    }
}

````

````xml
    <bean id="yuQian" class="com.powernode.spring6.bean.QianDaYe">

        <!-- 这个数组属性当中的元素类型是String简单类型 -->
        <property name="aiHaos">
            <array>
                <value>抽烟</value>
                <value>喝酒</value>
                <value>烫头</value>
            </array>
        </property>

    </bean>
````

当数组中的元素是非简单类型：

````java
public class Woman {
    private String name;

    public void setName(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return "Woman{" +
                "name='" + name + '\'' +
                '}';
    }
}
````

````java
public class QianDaYe {
    private String[] aiHaos;

    // 多个女性朋友
    private Woman[] womens;

    public void setWomens(Woman[] womens) {
        this.womens = womens;
    }

    public void setAiHaos(String[] aiHaos) {
        this.aiHaos = aiHaos;
    }

    @Override
    public String toString() {
        return "QianDaYe{" +
                "aiHaos=" + Arrays.toString(aiHaos) +
                ", womens=" + Arrays.toString(womens) +
                '}';
    }
}
````

````java
    <bean id="w1" class="com.powernode.spring6.bean.Woman">
        <property name="name" value="小花"/>
    </bean>

    <bean id="w2" class="com.powernode.spring6.bean.Woman">
        <property name="name" value="小亮"/>
    </bean>

    <bean id="w3" class="com.powernode.spring6.bean.Woman">
        <property name="name" value="小明"/>
    </bean>

    <bean id="yuQian" class="com.powernode.spring6.bean.QianDaYe">

        <!-- 这个数组属性当中的元素类型是String简单类型 -->
        <property name="aiHaos">
            <array>
                <value>抽烟</value>
                <value>喝酒</value>
                <value>烫头</value>
            </array>
        </property>

        <!-- 这个数组当中的类型就不是简单类型了-->
        <property name="womens">
            <array>
                <ref bean="w1"/>
                <ref bean="w2"/>
                <ref bean="w3"/>
            </array>
        </property>

    </bean>
````

- 要点：
  - 如果数组中是简单类型，使用value标签。
  - 如果数组中是非简单类型，使用ref标签。







### 注入List集合与Set集合

- List集合：有序可重复
  - 注意：注入List集合的时候使用list标签，如果List集合中是简单类型使用value标签，反之使用ref标签。
- Set集合：无序不可重复
  - 要点：
    - 使用<set>标签
    - set集合中元素是简单类型的使用value标签，反之使用ref标签。

````java
public class Person {

    // 注入List集合
    private List<String> names;

    // 注入Set集合
    private Set<String> addrs;

    public void setNames(List<String> names) {
        this.names = names;
    }

    public void setAddrs(Set<String> addrs) {
        this.addrs = addrs;
    }

    @Override
    public String toString() {
        return "Person{" +
                "names=" + names +
                ", addrs=" + addrs +
                '}';
    }
}

````



````xml
    <bean id="personBean" class="com.powernode.spring6.bean.Person">

        <property name="names">
            <!--list集合有序可重复-->
            <list>
                <value>张三</value>
                <value>李四</value>
                <value>王五</value>
                <value>张三</value>
                <value>张三</value>
                <value>张三</value>
                <value>张三</value>
            </list>
        </property>

        <property name="addrs">
            <!--set集合无序不可重复-->
            <set>
                <value>北京大兴区</value>
                <value>北京大兴区</value>
                <value>北京海淀区</value>
                <value>北京海淀区</value>
                <value>北京大兴区</value>
            </set>
        </property>
    </bean>

````



### 注入Map集合与注入Properties

-  Map集合：
  - 使用<map>标签
    - 如果key是简单类型，使用 key 属性，反之使用 key-ref 属性。
    - 如果value是简单类型，使用 value 属性，反之使用 value-ref 属性。
- java.util.Properties继承java.util.Hashtable，所以Properties也是一个Map集合。
- Properties使用<props>标签嵌套<prop>标签完成。

````java
public class Person {

    // 注入Map集合
    // 多个电话
    private Map<Integer, String> phones;

    // 注入属性类对象
    // Properties本质上也是一个Map集合。
    // Properties的父类Hashtable，Hashtable实现了Map接口。
    // 虽然这个也是一个Map集合，但是和Map的注入方式有点像，但是不同。
    // Properties的key和value只能是String类型。
    private Properties properties;

    public void setProperties(Properties properties) {
        this.properties = properties;
    }

    public void setPhones(Map<Integer, String> phones) {
        this.phones = phones;
    }

    @Override
    public String toString() {
        return "Person{" +
                "phones=" + phones +
                ", properties=" + properties +
                '}';
    }
}
````

```xml
    <bean id="personBean" class="com.powernode.spring6.bean.Person">
        
        <property name="properties">
            <!--注入Properties属性类对象-->
            <props>
                <prop key="driver">com.mysql.cj.jdbc.Driver</prop>
                <prop key="url">jdbc:mysql://localhost:3306/spring6</prop>
                <prop key="username">root</prop>
                <prop key="password">123456</prop>
            </props>
        </property>

        <property name="phones">
            <!--注入Map集合-->
            <map>
                <!--如果key和value不是简单类型就用这个配置。-->
                <!--<entry key-ref="" value-ref=""/>-->
                <!--如果是简单类型就是key和value-->
                <entry key="1" value="110"/>
                <entry key="2" value="120"/>
                <entry key="3" value="119"/>
            </map>
        </property>
    </bean>

```

### 注入null和空字符串

- 注入空字符串使用：`<value/>` 或者 value=“”
- 注入null使用：`<null/>` 或者 不为该属性赋值



````java
public class Cat {
    private String name;
    private int age;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Cat{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
````

````xml
    <bean id="catBean" class="com.powernode.spring6.bean.Cat">
        <!--不给属性注入，属性的默认值就是null-->
        <!--<property name="name" value="tom"></property>-->
        <!-- 这不是注入null，这只是注入了一个"null"字符串-->
        <!--<property name="name" value="null"/>-->
        <!--这种方式是手动注入null-->
        <!--<property name="name">
            <null/>
        </property>-->

        <!--注入空字符串第一种方式-->
        <!--<property name="name" value=""/>-->
        <!--注入空字符串第二种方式-->
        <property name="name">
            <value/>
        </property>

        <property name="age" value="3"></property>
    </bean>
````





## P命名空间注入

p命名空间注入实际上也是set注入

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:p="http://www.springframework.org/schema/p"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="dateBean" class="java.util.Date"/>
    <bean id="dogBean" class="com.phDemo.spring6.bean.Dog" p:birth-ref="dateBean" p:id="21" p:name="liuqiming"/>

</beans>
```

```java
@Test
public void test4(){
    ApplicationContext applicationContext = new ClassPathXmlApplicationContext("spring-p.xml");
    Dog dogBean = applicationContext.getBean("dogBean", Dog.class);
    System.out.println(dogBean);
}
```





## C命名空间注入

使用c命名空间的两个前提条件:

第一:需要在xml配置文件头部添加信息:xmlns:p="http://www.springframework.org/schema/c"

第二:

```java
public void test5(){
    ApplicationContext applicationContext = new ClassPathXmlApplicationContext("spring-c.xml");
    Cat cat = applicationContext.getBean("catBean", Cat.class);
    System.out.println(cat);
}
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:c="http://www.springframework.org/schema/c"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

        <bean id="catBean" class="com.phDemo.spring6.bean.Cat" c:_0="liuqiming" c:_1="女" c:_2="31214"/>
</beans>
```





## util命名空间让配置复用

- 使用util命名空间可以让配置复用。
- 使用util命名空间的前提是：在spring配置文件头部添加配置信息。如下：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:util="http://www.springframework.org/schema/util"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util.xsd">

    <util:properties id="proMap">
        <prop key="driver">com.mysql.cj.jdbc.Driver</prop>
        <prop key="url">jdbc:mysql://localhost:3306?/spring</prop>
        <prop key="username">root</prop>
        <prop key="password">123456</prop>
    </util:properties>
    
    <bean id="dataSource" class="com.phDemo.spring6.bean.DataSource">
        <property name="properties" ref="proMap"/>
    </bean>

    <bean id="dataSource1" class="com.phDemo.spring6.bean.DataSource">
        <property name="properties" ref="proMap"/>
    </bean>
</beans>
```

````java
package com.powernode.spring6.beans;

import java.util.Properties;

public class MyDataSource1 {
	// Properties属性类对象，这是一个Map集合，key和value都是String类型。
    private Properties properties;

    public void setProperties(Properties properties) {
        this.properties = properties;
    }

    @Override
    public String toString() {
        return "MyDataSource1{" +
                "properties=" + properties +
                '}';
    }
}
````

## 基于XML的自动装配

spring还可以完成自动化的注入，自动化注入又被称为自动装配。它可以根据名字进行自动装配，也可以根据类型进行自动装配

## 基于XML的自动类型装配







## Bean的作用域（Scope）

Spring默认情况下都是以单例模式创建对象

```java
public class test1 {
    @Test
    public void test1(){
        /*1.spring默认情况下是如何管理这个Bean的？
        *         默认情况下Bean是单例的（singleton）
        *         在spring上下文初始化的时候初始化
        *         每一次调用getBean（）方法的时候，都返回那个单例的对象
        * */
        ApplicationContext applicationContext = new ClassPathXmlApplicationContext("example1.xml");
        UserName sb = applicationContext.getBean("sb", UserName.class);
        System.out.println(sb);

        UserName sb1 = applicationContext.getBean("sb", UserName.class);
        System.out.println(sb1);
    }
}
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="sb" class="com.phDemo.spring004.bean.UserName"  scope="prototype" />
</beans>
```

scope = "prototype" 多例模式

scope = "singletom" 单例模式

![image-20230509220742171](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230509220742171.png)

其实scope属性有多个值

​		例如：request session

​		但是request session要求项目必须是一个web应用。当你引入springmvc框架的时候，这两个值就可以使用了。

​		request：一次请求当中一个bean

​		session：一次会话当中只有一个bean

​		还有很多。。。





## GoF之工厂模式

### 1.spring底层

​		工厂模式+反射机制

### 2.工厂模式的三种模式

- 第一种：简单工厂模式：它不属于23中设计模式之一 （Simple Factory）（静态工厂方法模式）
- 第二种：工厂方法模式：是23种设计模式之一 （Factory Method）‘’
- 第三种：抽象工厂模式：是23种设计模式之一	(Abstract Factory)



#### 简单工厂模式：

- 优点：需要哪个对象的时候，只需要想工厂索要即可。初步实现了责任的分离。客户端只负责”消费“，工厂负责”生产“。

- 缺点：工厂类不能出问题，一旦出问题，整个系统瘫痪。

  ​			不符合OCP开闭原则，在进行系统扩展时，需要修改工厂类





#### 工厂方法模式：

- 优点：

  一个调用者像创建一个对象，只要知道其名称就可以

  扩展性高，如果想增加一个产品，只要扩展一个工厂类就可以

  屏蔽产品的具体实现，调用者只关心产品的接口

- 缺点

  每次增加一个产品时，都需要增加一个具体类和对象实现工厂，使得系统中类的个数成倍增加，在一定程度上增加了系统的复杂性，同时业增加了系统具体类的依赖。这并不是一件什么好事.





#### 抽象工厂模式：（了解）

![image.png](https://cdn.nlark.com/yuque/0/2022/png/21376908/1665370116084-46b714b8-95d2-45c5-89b6-564057c45694.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_33%2Ctext_5Yqo5Yqb6IqC54K5%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)

- 优点：当一个产品族中的多个对象被设计成一起工作时，它能保证客户端始终只使用同一个产品族中的对象。
- 缺点：产品族扩展非常困难，要增加一个系列的某一产品，既要在AbstractFactory里加代码，又要在具体的里面加代码。



## Bean的实例化方式

#### 第一种 构造方式实例化：

​			我们之前一直使用的就是这种方式。默认情况下，会调用Bean的无参数构造方法。

#### 第二种 通过简单工厂模式实例化

​			第一步：定义一个Bean

​			第二步：编写简单工厂模式当中的工厂类

​			第三步：在Spring配置文件中指定创建该Bean的方法（使用factory-method属性指定）

#### 第三种 通过factory-bean实例化

​			这种方式本质上是：通过工厂方法模式进行实例化。

​		

#### 注入自定义Date

我们前面说过，java.util.Date在Spring中被当做简单类型，简单类型在注入的时候可以直接使用value属性或value标签来完成。但我们之前已经测试过了，对于Date类型来说，采用value属性或value标签赋值的时候，对日期字符串的格式要求非常严格，必须是这种格式的：Mon Oct 10 14:30:26 CST 2022。其他格式是不会被识别的。

```java
public class Student {
    private Date birth;
    public void setBirth(Date birth){
        this.birth = birth;
    }

    @Override
    public String toString() {
        return "Student{" +
                "birth=" + birth +
                '}';
    }
}
```

```xml
<bean id="studentBean" class="com.phDemo.spring004.bean.Student">
        <property name="birth" value="Mon Oct 10 14:30:26 CST 2002"/>
</bean>
```

![image-20230524155146974](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230524155146974.png)



#### Bean的生命周期

##### 什么是Bean的生命周期？

Spring其实就是一个管理Bean对象的工厂。它负责对象的创建，对象的销毁等。

所谓的生命周期就是：对象从创建开始到最终销毁的整个过程。

- 什么时候创建Bean对象？
- 创建Bean对象的前后会调用什么方法？
- Bean对象什么时候销毁？
- Bean对象的销毁前后调用什么方法？

##### 为什么要知道Bean的生命周期？

- 其实生命周期的本质是：在哪个时间节点上调用了哪个类的哪个方法。
- 我们需要充分的了解在这个生命线上，都有哪些特殊的时间节点。
- 只有我们知道了特殊的时间节点都在哪，到时我们才可以确定代码写到哪。
- 我们可能需要在某个特殊的时间点上执行一段特定的代码，这段代码就可以放到这个节点上。当生命线走到这里的时候，自然会被调用。

#### Bean的生命周期之5步

Bean生命周期的管理，可以参考Spring的源码：AbstractAutowireCapableBeanFactory类的doCreateBean()方法

- 第一步：实例化Bean
- 第二步：Bean属性赋值
- 第三步：初始化Bean
- 第四步：使用Bean
- 第五步：销毁Bean

需要注意的：

- 第一：只有正常关闭spring容器，bean的销毁方法才会被调用。
- 第二：ClassPathXmlApplicationContext类才有close()方法。
- 第三：配置文件中的init-method指定初始化方法。destroy-method指定销毁方法。

```xml
<bean id="personBean" class="com.phDemo.spring004.TestBean.Person1" init-method="initBean" destroy-method="destroyBean">
    <property name="name" value="I Love it"/>
</bean>
```

#### Bean生命周期之7步

在以上的5步中，第3步是初始化Bean，如果你还想在初始化前和初始化后添加代码，可以加入“Bean后处理器”。

编写一个类实现BeanPostProcessor类，并且重写before和after方法：

```java
public class LogBeanPostProcessor implements BeanPostProcessor {
    //初始化之后
    @Override
    public Object postProcessAfterInitialization(Object bean, String beanName) throws BeansException {
        System.out.println("bean后处理器的before方法执行，即将开始初始化");
        return bean;
    }


    //初始化之前
    @Override
    public Object postProcessBeforeInitialization(Object bean, String beanName) throws BeansException {
        System.out.println("bean后处理器的after方法执行，已完成初始化");
        return bean;
    }
}
```

```xml
<bean class="com.phDemo.spring004.TestBean.LogBeanPostProcessor">
</bean>
```

![image-20230524202836290](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230524202836290.png)

![image.png](https://cdn.nlark.com/yuque/0/2022/png/21376908/1665393936765-0ea5dcdd-859a-4ac5-9407-f06022c498b9.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_29%2Ctext_5Yqo5Yqb6IqC54K5%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)

#### Bean生命周期之10步

比七步添加的那3步在哪里？

点位1：在（Bean后）处理器before方法之前



点位2：在（Bean后）处理器before方法之后

点位3：在使用Bean之后，或则说是销毁Bean之前

![image.png](https://cdn.nlark.com/yuque/0/2022/png/21376908/1665394697870-15de433a-8d50-4b31-9b75-b2ca7090c1c6.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_12%2Ctext_5Yqo5Yqb6IqC54K5%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)

Aware相关的接口包括：BeanNameAware、BeanClassLoaderAware、BeanFactoryAware

- 当Bean实现了BeanNameAware，Spring会将Bean的名字传递给Bean。
- 当Bean实现了BeanClassLoaderAware，Spring会将加载该Bean的类加载器传递给Bean。
- 当Bean实现了BeanFactoryAware，Spring会将Bean工厂对象传递给Bean。

测试以上10步，可以让User类实现5个接口，并实现所有方法：

- BeanNameAware
- BeanClassLoaderAware
- BeanFactoryAware
- InitializingBean
- DisposableBean

#### Bean的作用域不同，管理方式不同

Spring 根据Bean的作用域来选择管理方式。

- 对于singleton作用域的Bean，Spring 能够精确地知道该Bean何时被创建，何时初始化完成，以及何时被销毁；
- 而对于 prototype 作用域的 Bean，Spring 只负责创建，当容器创建了 Bean 的实例后，Bean 的实例就交给客户端代码管理，Spring 容器将不再跟踪其生命周期。

我们把之前User类的spring.xml文件中的配置scope设置为prototype：

![img](https://cdn.nlark.com/yuque/0/2022/png/21376908/1665395807399-a3b71b4d-d871-4230-8fe4-b939ed03b301.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_29%2Ctext_5Yqo5Yqb6IqC54K5%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)

通过测试一目了然。只执行了前8步，第9和10都没有执行。

#### 自己new的对象怎么样让spring管理

```java
public void testBeanTest(){
    //自己new的对象
    Person1 person1 = new Person1();
    System.out.println(person1);

    //创建 默认列表BeanFactory对象
    DefaultListableBeanFactory factory =new DefaultListableBeanFactory();
    //注册Bean
    factory.registerSingleton("personBean",person1);
    //从spring容器获取Bean
    Person1 personBean1 = factory.getBean("personBean", Person1.class);
    System.out.println(personBean1);
}
```

先new一个对象，然后获得默认factory ，把对象注册其中。



#### Bean的循环依赖问题

A对象中有B属性。B对象中有A属性。这就是循环依赖。

来测试一下

我们来编写程序，测试一下在singleton+setter的模式下产生的循环依赖，Spring是否能够解决？

```java
public class Husband {
    private String name;
    private Wife wife;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Wife getWife() {
        return wife;
    }

    public void setWife(Wife wife) {
        this.wife = wife;
    }
}
```

```java
public class Wife {
    private String name;
    private Husband husband;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Husband getHusband() {
        return husband;
    }

    public void setHusband(Husband husband) {
        this.husband = husband;
    }
}
```

```xml
<bean id="husbandBean" class="Bean.Husband">
    <property name="name" value="liming"/>
    <property name="wife" ref="wifeBean"/>
</bean>
<bean id="wifeBean" class="Bean.Wife">
    <property name="name" value="小花"/>
    <property name="husband" ref="husbandBean"/>
</bean>
```

![image-20230524213440590](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230524213440590.png)

**通过测试得知：在singleton + set注入的情况下，循环依赖是没有问题的。Spring可以解决这个问题。**

在这种模式下，spring对Bean的管理主要分为两个清晰的阶段

​			第一个阶段：在spring容器加载的时候，实例化Bean，只要其中任意一个Bean实例化之后，马上进行“曝光”（因为单例的，只要一个Bean实例化的时候，其他也跟着”曝光“） 。

​			第二个阶段：曝光之后，在进行属性赋值调用set方法。

​           只有scope是Singleton的条件下才会曝光

如果改成prototype呢？

![image-20230524215434897](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230524215434897.png)



![image-20230524215527792](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230524215527792.png)

报错！！！！
