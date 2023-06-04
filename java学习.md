## java学习第八章（韩顺平）

#### 1.包的命名

1.1命名规则

不能用数字开头,不能是关键字或保留字

1.2命名规范

一般是小写字母+小圆点

例如

com.公司名.项目名.业务模块名

例如.

com.phedu.input.model;

com.sina.crm.user；//用户模块

com.sina.crm.order; //订单模块

com.sina.crm.utils;//工具类

1.3常用包

java.lang.*//lang基础包，默认包，不需要引入

java.util.*//util包，系统提供的工具包。工具类，使用scanner

java.net.*//网络包，网络开发

java.awt.*//是做java的界面开发，GUI



![image-20230228102507400](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230228102507400.png)

关于包的知识还在继续



#### 2.访问修饰符

![image-20230228102637937](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230228102637937.png)

私密等级 private 》 protected 》默认级别 》 public

![image-20230228102753065](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230228102753065.png)



#### 3.面向对象编程-封装

1.封装介绍

封装的三大特点：

1.继承 2.封装 3.多态

封装的理解和好处
1）隐藏实现细节 方法（连接数据库）<--调用（传入参数..）

2)可以对数据进行验证，保证安全合理



##### 3.1封装的实现步骤

1)将属性进行私有化private [不能修改属性]

2)提供一个公共的(public)set方法，用于对属性判断并赋值

 public void setXxx(类型 参数名){//Xxx 表示某个属性

​	//加入数据验证的业务逻辑

   属性 = 参数名;

}

3)提供一个公共的get方法，用于获取属性的值

​	public XX getXxx(){//权值判断

​	return xx;

}

![image-20230228125411340](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230228125411340.png)

##### 3.2继承与构造器

`public Person(String name,int age, double salary){`

 			this.name = name;
 	
 			this.age = age;
 	
 		 this.salary = salary;

> 这里我们能发现如果用构造函数就破坏了其封装性，那我们要怎么解决呢？
>
> 其实我们可以使用在构造函数里使用Set方法

`}`

```java
public class Person {
    public String name;
    private int age;
    private double salary;
    private String job;

    public Person(){ };

    public Person(String name,int age,double salary,String job){
        this.SetName(name);
        this.SetJob(job);
        this.SetSalary(salary);
        this.SetAge(age);
    }

    public void SetName(String name){
        if(name.length() <= 6 && name.length() >= 2){
            this.name = name;
        }
        else{
            System.out.println("你设置的名字过长，范围在2-6以内");
        }
    }

    public void SetAge(int age){
        if(age <= 120 && age >0){
            this.age = age;
        }
        else{
            System.out.println("设置年龄超过范围（1-120）");
        }
    }

    public void SetSalary(double Salary){
        this.salary = Salary;
    }

    public void SetJob(String job){
        this.job = job;
    }
}
```

##### 3.3面向对象编程继承

继承关键字extends

我们去理解继承，其实就是由于代码比如说类之间总是很相似，并且代码存在复用性，其实效率是比较低的。

我们比如猫和狗两个类，但是呢，如果还要增加很多种动物，那如果要保存他们的信息的时候，如果单独从新去些类的属性和方法，就会浪费很多的时间。那这时候我们子需要通过继承一个父类Animal类即可，方法我们可以多加，也可以多增加属性。

并且子类还能够是父类，一层套一层

![image-20230302095544891](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230302095544891.png)

![image-20230302095646452](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230302095646452.png)



当我们在父类创造一个新的方法，子类及其子类的子类都会获得该方法。

10个细节:

1.子类继承了所有父类的属性和方法，但是私有属性和方法不能在子类直接访问，要通过父类公共的方法去访问。

![image-20230302102238975](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230302102238975.png)

![image-20230302102308521](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230302102308521.png)

2.子类必须调用父类的构造器来完成对父类的初始化

就是你继承父类然后创建子类对象，会自动调用父类的构造器

![image-20230302102908827](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230302102908827.png)

3.当创建子类对象时，不管使用子类的哪个构造器默认情况下都会去调用父类的无参构造器，如果父类没有提供无参构造器，则必须在子类的构造器中用super去指定使用父类的哪个构造器去完成对父类的初始化工作，否则，编译不会通过（怎么解释.）

4.如果想在子类中调用父类的构造器，super()，其中的参数可以根据不同的构造器的参数去对应执行相对应的构造器。

5.super()在使用时，必须在构造器中使用，并且放在第一行。

6.在子类构造器中。this和super只能有一个。

![image-20230304174402653](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230304174402653.png)





7.子类最多只能继承一个父类（直接继承），即java中是单继承机制

A-》B-》C  A就能使用B和C的方法和属性





继承的本质（原理）

实际上就是一个查找的过程

![image-20230304175148249](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230304175148249.png)

![image-20230304180224585](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230304180224585.png)

当我们把父类的age变量设为私有变量，我们的爷爷类也有一个age变量的话，当我们要查找age变量时，它是一层一层往上找。所以当你要输出age时，他会不会因为父类变量是私有类，而去找爷爷类的age呢？不会，因为他其实已经找到age了，只是由于它是私有类，所以不能直接访问



![image-20230304181112401](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230304181112401.png)

![image-20230304203953394](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230304203953394.png)











##### 3.4super关键字

- 访问父类的属性，但是不能访问父类的private属性，super.方法()可以去访问私有类。
- super()。只能在子类构造器中使用，并且是第一条指令.
- super(参数。。。) 参数的不同可以调用不同的父类构造器。
- 记住细节
- 1.分工明确
- 2.父类属性由父类初始化
- 3.子类的属性由子类初始化
- 4.最好是用这样的规则，最好不要搞混
- 2023/3/4

> 当希望调用父类的某个方法假设为cal
>
> 这时，因为子类B类没有cal的方法，因此哦我可以使用下面三种方法
>
> cal();
>
> 一、找cal的方法，顺序时，先找子类，如果有，并且可以调用
>
> 则调用，如果没有，则找父类.....以此类推
>
> 如果父类没有则继续找父类的父类。。。。。。。。直到object。。。。
>
> 如果找到了该方法但是是private类或则没找到该方法，则报错。。。haha4
>
> 二、super().cal 这个的逻辑是直接找父类以上的cal方法，其他规则一样

![image-20230304214414633](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230304214414633.png)





super和this的区别：

![image-20230304223529548](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230304223529548.png)

super和this再见了



##### 3.5方法覆盖override

子类的同名方法覆盖了父类的方法----

方法重写的细节override

- 如果要重写方法，那么形参列表和函数名，以及返回类型要一样
- 上面的好理解，但是这句话呢？父类返回类型的子类，这句话怎么理解呢？
- 来看图
- ![image-20230304224738523](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230304224738523.png)

- String 是 Object的子类，所以返回的没有问题
- ![image-20230304225323559](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230304225323559.png)



方法重写和方法重载的比较

发生范围

重载：同一个类 √

重写：继承的子类重写父类方法2 √

方法名：

重载：相同 √

重写：相同 √

形参列表：

重载：形参列表不同

重写：相同

返回类型：

重载：无要求

重写：返回类型和父类一样，或者其为父类返回类型的子类

修饰符：

重载：无要求

重写：子类方法不能缩小父类方法的访问范围 比如：父类默认修饰符 则子类public 因为优先级public>默认>protected>private

  			

![image-20230304230634538](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230304230634538.png)

今晚就到这了  

明天多态继续继续冲！

305集





##### 3.6面向对象编程多态

在封装中，多态难度比较大

![image-20230305102918945](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305102918945.png)

![image-20230305102840044](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305102840044.png)

其实理解起来也没有那么抽象，就是feed的方法针对更多的动物时，如果不使用多态的方法，将会造成feed的重载变多，是代码复用性增大。使用多态的方法就可以避免这种问题。。。。。。。。。。



- 多态的具体体现
- 1.方法的多态
- ![image-20230305103300639](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305103300639.png)

- 我们传入不同的参数，即调用不同的方法，体现出多态。
- 可以看出重载体现出多态
- 重写也可以体现出多态（a是b的子类，并且都有say方法()）
- ![image-20230305103429486](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305103429486.png)

- 







- 重载和重写我们还能理解。。。。接下来是对象的多态
- 并且对象多态是多态的核心
- ![image-20230305103640008](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305103640008.png)



编译类型是 Animal 运行类型是 Dog？ 怎么理解



![image-20230305144808609](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305144808609.png)

![image-20230305144819323](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305144819323.png)

<img src="C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305144847295.png" alt="image-20230305144847295" style="zoom: 67%;" />![image-20230305144912149](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305144912149.png)

编译类型看定义时 = 号 的左边    运行类型看 = 号的 右边

从表面上看是编译类型，从本质上看是运行类型  披着羊皮的狼



那回到我们最初主人给各种动物喂食的问题

![image-20230305150102338](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305150102338.png)

![image-20230305150118735](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305150118735.png)







多态的注意事项和细节讨论

- 多态的前提：两个对象存在继承关系
- 多态的向上转型
- 本质：父类的引用指向子类
- ![image-20230305151910993](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305151910993.png)



catchmouse() 这个方法是dog类中特有的方法，但是为什么在animal中又不能使用呢？

因为在编译阶段，能调用哪些成员，是由编译类型来决定，我们这里的编译类型就是Animals,而不是Dog（Dog是它的子类，有些抽象吧，慢慢理解）



- 向下兼容
- 把指向子类的父类引用，转成指向子类对象的子类引用
- ![image-20230305153156730](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305153156730.png)
- 呜呜 听不懂得看例子才能知道了┭┮﹏┭┮
- ![image-20230305153841055](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305153841055.png)

![image-20230305154053713](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305154053713.png)

![image-20230305154316861](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305154316861.png)

这句Dog dog = (Dog) animal 是错误的，因为原先animal引用类型指针指向了Cat对象，但是现在你创建的一个dog引用类型怎么可以又能去指向cat对象呢，不可以让一个猫对象变成一个狗对象，又会出现类异常。







多态细节--------

![image-20230305155542852](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305155542852.png)



![image-20230305155529941](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305155529941.png)

![image-20230305184206917](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305184206917.png)

做一题多态的课堂练习..........

<img src="C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305184926829.png" alt="image-20230305184926829" style="zoom:33%;" />

访问属性-->访问编译类型

那么第一个s.count 输出的就是20啦。

如果是访问方法，那就得按照查找关系去访问方法了

s.display也是20

![image-20230305185847770](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305185847770.png)

![image-20230305191458680](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305191458680.png)









##### 3.7java的动态访问机制(非常非常重要)

<img src="C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305193739340.png" alt="image-20230305193739340" style="zoom:50%;" />

让我们看看输出结果？其实也好懂   

A是编译类型  B是运行类型

那么我们的 a.sum() 是方法按照运行类型的方式去查找它的方法。。我们在B类中发现了这个方法，并调用i + 20

所以我们的输出结果就是40没问题

以下毫无疑问  a.sum1()同样是 i + 20 = 30了 



那什么时候引出我们的动态访问机制呢？来

当我们把B类的sum方法注销     我们再看看结果

这时候由于子类B的sum方法没有结果，那么我们按照查找的规则就来到了A类中并找到sum方法，但是其中的getI()方法父类A也有，子类B也有getI()的方法。那么此时调用的是哪一个呢？这时候动态访问机制的问题就来了。由于是方法的问题，那么我们要看会到编译类型和运行类型了 ，由于方法看的是咱们的运行类型，所以我们运行的是咱们的B类的getI()。。。唉 ，那么多细节 难死人了。如果不是方法的话，那么它看的是哪里声明，那里使用。

![image-20230305200417895](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305200417895.png)





多态数组

![image-20230305202754037](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230305202754037.png)

2023/3/6

但是你要输出多态数组里面不同类型的类的时候，你要怎么办呢？

其实联想到之前的 instanceof的方法就可以做到，因为instanceof的方法比较的是运行类型

![image-20230306092716042](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306092716042.png)



多态参数

很简单的看出

![image-20230306092858559](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306092858559.png)

feed的方法就可以表现出参数多态





##### 3.8Object类



- equals方法
- 》== 和 equals的对比【面试题】
- 1.==：比较运算符，既可以判断基本类型也可以判断引用类型
- 2.==：判断基本数据类型，判断值是否相等
- 3.==：判断引用类型，判断的是引用类型是否是同一个对象，实质是比较地址是否相等。



和c语言的指针其实差不多 java的引用 到现在我是那么理解的

![image-20230306101257496](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306101257496.png)

- equals方法只能判断引用类型
- ![image-20230306105656929](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306105656929.png)







课堂练习

![image-20230306122351686](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306122351686.png)









hashcode

> - #### hashCode
>
>   ```
>   public int hashCode()
>   ```
>
>   返回对象的哈希码值。 支持此方法的优点是散列表，例如[`HashMap`](https://www.apiref.com/java11-zh/java.base/java/util/HashMap.html)提供的[散列表](https://www.apiref.com/java11-zh/java.base/java/util/HashMap.html) 。
>
>   `hashCode`的总合同是：
>
>   - 只要在执行Java应用程序期间多次在同一对象上调用它， `hashCode`方法必须始终返回相同的整数，前提是不修改对象上的`equals`比较中使用的信息。 从应用程序的一次执行到同一应用程序的另一次执行，该整数不需要保持一致。
>   - 如果两个对象根据`equals(Object)`方法相等，则对两个对象中的每个对象调用`hashCode`方法必须生成相同的整数结果。
>   - 这*不是*必需的：如果两个对象根据不相等[`equals(java.lang.Object)`](https://www.apiref.com/java11-zh/java.base/java/lang/Object.html#equals(java.lang.Object))方法，然后调用`hashCode`在各两个对象的方法必须产生不同的整数结果。 但是，程序员应该知道为不等对象生成不同的整数结果可能会提高哈希表的性能。
>
>   尽管合理可行，但是类`Object`定义的hashCode方法确实为不同的对象返回不同的整数。 （hashCode可能会或可能不会在某个时间点实现为对象的内存地址的某些功能。）
>
>   - **结果**
>
>     此对象的哈希码值。
>
>   - **另请参见：**
>
>     [`equals(java.lang.Object)`](https://www.apiref.com/java11-zh/java.base/java/lang/Object.html#equals(java.lang.Object)) ， [`System.identityHashCode(java.lang.Object)`](https://www.apiref.com/java11-zh/java.base/java/lang/System.html#identityHashCode(java.lang.Object))



HashCode的小结

1. 提高具有哈希结构的容器的效率
2. 两个引用，如果都指向同一个对象，则哈希值肯定一样
3. 同第二条小结反之，不同，则哈希值不一样
4. 哈希值主要是根据地址号来的！不能完全的将哈希值等同于地址
5. 在集合中，hashCode如果需要的话，也会重写



这里额外扩展一下，解决哈希冲突的方法：

拉链法和线形探测法

拉链法：数据＋链表的方式

线性探测法：就是当两个对象通过哈希函数得到的哈希值相同时，通过向后延伸的方式去储存，当然这要求tablesize》datasize,不然哪有那么多空间去存储数据。



toString方法

源码

> ```java
> public String toString() {
>  //getClass().getName() 类的全类名（包＋类）
>  //Integer.toHexString(hashCode()) 将对象的hashcode值转成16进制字符串
>  return getClass().getName() + "@" + Integer.toHexString(hashCode());
> }
> ```

![image-20230306124401364](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306124401364.png)





finalize方法

源码

> 当垃圾收集确定没有对该对象的更多引用时，由对象上的垃圾收集器调用。 子类重写`finalize`方法以处置系统资源或执行其他清理。
>
> 
>
> 

![image-20230306130544958](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306130544958.png)

![image-20230306130605364](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306130605364.png)



##### 3.9断点调试

F7跳入 F8跳出

shift+F8(跳出)

F9 执行到下一个断点





##### 4.0零钱通小项目

![image-20230306132911339](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306132911339.png)



步骤

- 先完成菜单。。
- 我自己打算用oop思想去写











练习 巩固

![image-20230306154532976](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306154532976.png)

![image-20230306163204891](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306163204891.png)

![image-20230306163550162](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306163550162.png)

![image-20230306163855348](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306163855348.png)

![image-20230306165710164](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230306165710164.png)

成功的完成了捏

冒泡排序多态数组其实自己在听课的时候并没有那么认真~！不过还好这里实现回来啦，印象深刻！！！！



2023/3/7 学习java中.....

![image-20230307095719012](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307095719012.png)

在复习一遍动态绑定机制？

![image-20230307100632630](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307100632630.png)

![image-20230307122350074](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307122350074.png)

房屋出租系统的框架实现





















## Java学习第十章

第二阶段了冲冲冲！

### 1.类变量和类方法

- static的使用
- 类似于全局变量哈哈
- 不过有不等同与全局变量
- 我们可以理解为让两个或者多个相同的类共同使用同一个变量或者方法

举个简单小例子，当我们如果有一个小游戏，陆续由各个小朋友加入到这个游戏，然后时不时统计人数的时候。如果不适使用类变量的方法的时候，你需要在main当中创建一个count变量然后不断地修改很麻烦！

这这时候我们只需要在class类中加入一个静态变量即可完成统计。例如

![image-20230307124144172](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307124144172.png)

![image-20230307124242127](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307124242127.png)



> 类变量的一个内存布局
>
> ![image-20230307130417487](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307130417487.png)
>
> 听了韩老师的讲解。。转化为在自己的理解
>
> 当我们的类在运行编译过程中，在方法区加载了类方法。这时候static修饰符修饰的变量，在JDK8以前呢？是在方法区的静态变量区加载static的变量，static变量都指向静态方法区的对应的存储区域。如果是在JDK8以后，是当JVM在加载类方法到方法区的时候，同时也在堆的区域创造一个类空间，static变量存放在类的尾部区域，然后类的static的变量都指向那块区域

![image-20230307131534262](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307131534262.png)

类变量其实是在类加载的过程中的就创建好了，所以即使没有创建对象也可以访问。



**类方法**

![image-20230307132824362](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307132824362.png)

也是可以通过类名直接访问的。。

感觉还行，不难不难



静态方法可以通过类名直接调用，非静态方法不能通过类名调用。

1.类方法中不允许使用和对象有关的关键字，比如this和super。普通方法（成员方法）可以

2.类方法（静态变量）中 只能访问 静态变量或静态方法

3.普通方法，及可以访问普通方法，也可以访问静态方法

![image-20230307155759240](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307155759240.png)



我们这里想要给total赋值怎么办？

在static方法中我们不能使用this和super。我们只能使用Person.total这样而不是this.total

[最重要的一句话](十分重要)

> 静态方法只能访问静态变量或者静态方法。
>
> 非静态成员可以访问所以的成员
>
> 编写代码时，仍然要遵守权限的规则（private public protected等）





### 2.main语法说明

深入理解main方法

> public static void main(String[] args){}
>
> - 是谁在调用main方法？
> - 1.是java虚拟机在调用
> - 2.java虚拟机需要调用类的main方法，所以该方法的访问权限必须是public
> - 3.java虚拟机在执行main（）方法时不必创建对象，所以该方法是static
> - 4.该方法接收String类型的数组参数，该数组中保存执行java命令时传递给所运行的类的参数。案例，接收参数
> - 5.java的执行程序 参数1 参数2 参数3

![image-20230307160916288](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307160916288.png)

静态方法main 不可以访问本类的非静态属性成员

![image-20230307162603014](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307162603014.png)

给args动态传递些参数，除了控制台还有IDEA的

![image-20230307162632206](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307162632206.png)

![image-20230307162648219](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307162648219.png)

程序参数那块地方



### 3.代码块

- 代码化块又称为初始化块，属于类中的成员【即 是类的一部分】,类似于方法，将逻辑语句封装在方法体中，通过{}包围起来。
- 但和方法不一样，没有方法名，没有返回，没有参数，只有方法体，而且不用通过对象或者类显式调用，而是加载类时，或创建对象时隐式调用。



- 基本语句
- [修饰符]{
- ​     代码
- }；
- 注意：
- ![image-20230307173800296](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307173800296.png)





> ![image-20230307180640914](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307180640914.png)
>
> ![image-20230307180714100](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307180714100.png)

我们可以发现4个构造函数创建对象时都调用了代码块的内容。。。。。。感觉代码块好像还是挺好玩的哈哈

代码块调用的顺序优先于构造器



**代码块细节**

1.static代码块也叫静态代码块，作用就是对类进行初始化，而且它随着类的加载而执行，并且只会执行一次。如果是普通代码块，没创建一个对象，即执行一次。

2.类什么时候被加载【**重要**】

1.创建对象实例new

2.创建子类对象实例，父类被加载

3.使用类的静态成员时（静态属性，静态成员）



普通代码块：在创建类对象的时候，会调用一次。（如果是使用类的静态成员，普通代码块不会执行）

静态代码块：在类加载的时候会执行一次。比如你创建两个类对象，第一个类对象加载会使用静态代码块，但是第二次类对象创建的时候由于第一次已经加载过了所有不会再调用静态代码块。



![image-20230307202459311](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307202459311.png)

![image-20230307204410371](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307204410371.png)

![image-20230307210109837](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307210109837.png)

静态代码块和静态方法的优先级高

普通代码块和普通属性的初始化

才到对象的构造初始化

![image-20230307210804372](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307210804372.png)



[非常重要](very very very)

![image-20230307215802362](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230307215802362.png)

今天有些极限了

wuwu

2023/3/7

391集

冲





### 4.单例设计模式



#### 一、饿汉式单例设计模式

其实就是整个程序只能创建唯一的类对象



![image-20230308085952357](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308085952357.png)

饿汉式-单利模式

![image-20230308090511489](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308090511489.png)



![image-20230308091203345](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308091203345.png)

![image-20230308091229258](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308091229258.png)

饿汉式类加载的时候就创建了（比较着急）

一般是重量级对象，饿汉式可能造成创建了对象而没有创建

ctrl + alt + L 代码规格化



懒汉式

![image-20230308092718675](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308092718675.png)

两者区别

![image-20230308092742491](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308092742491.png)

线程安全问题

![image-20230308092907299](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308092907299.png)





### 5.final关键字

![image-20230308093159138](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308093159138.png)

![image-20230308094223279](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308094223279.png)

1.不能继承

![image-20230308094419951](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308094419951.png)

2.不允许重写

![image-20230308094607599](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308094607599.png)

3.final修饰的变量也不能使用

4.不希望某个局部变量被修改



![image-20230308094737196](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308094737196.png)

![image-20230308104033628](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308104033628.png)

按道理来说，你在外部使用i变量的时候，应该会加载类导致调用静态代码块。但是你加了final之后，它不会调用静态代码块，有点神奇。

```
public int addOne(final int x){
    ++x;
    return x + 1;
}
```

错误的  final 修饰的变量不能变，把++x去掉就可以了





### 6.抽象类

我的理解：

就是一个类（基本都是父类给其他类继承的）

方法的不确定性，然后让子类去继承重写

小结：

当父类的某些方法，需要声明，但是又不确定如何实现时，可以将其声明为抽象方法，那么这个类就是抽象类

- 父类方法不确定性的问题
- 考虑将该方法设计为抽象（abstract）方法
- 所谓抽象方法就是没有实现的方法
- 所谓没有实现就是指，没有方法体

- 当一个类中存在抽象方法时，需要将该类声明为abstract类



- 抽象类的对象

- > 1. 用abstract关键字来修饰一个类时，这个类就叫抽象类
  >
  > 2. 用abstract关键字来修饰一个方法时，这个方法就是抽象方法
  >
  >    访问修饰符abstract 返回类型 方法名（参数列表）
  >
  > 3. 抽象类的价值更多作用是在于设计，让子类继承并实现抽象类（）
  >
  > 4. 抽象类，是考官比较爱问的知识点，在框架和设计模式比较多
  >
  > 



- 抽象类细节

  > 1.抽象类不能被实例化
  >
  > 2.抽象类不一定要包含abstract方法。也就是说，抽象类可以没有abstract方法
  >
  > 3.一旦类包含了abstract方法，则这个类必须声明为abstract
  >
  > 4.abstract只能修饰类和方法，不能修饰属性和其他的



![image-20230308113017911](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308113017911.png)

第一个错误的，final是不能继承

第二个错误的，static关键字和方法重写无关

第三个错误的，private的方法不能重写

![image-20230308113042443](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308113042443.png)



System.currentTimeMillis()s返回毫秒数

和c++里 #include<time>里面哪很像不过是java的



抽象设计模式

例子

![image-20230308181354513](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308181354513.png)

我们在抽象类中给出类代码块的模板，我们只需要在子类中继承抽象类重写其中的抽象方法即可

![image-20230308182246376](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308182246376.png)







### 7.接口

自己是怎么理解接口呢？

其实我也不太懂。。。。



先从一个例子开始

先创建一个Usbinterface接口

```java
public interface Usbinterface {
    public void start();
    public void end();
}
```

创建两个接口对象Phone和Camera

```java
public class Phone implements Usbinterface{
    @Override
    public void start() {
        System.out.println("手机开机了");
    }

    @Override
    public void end() {
        System.out.println("手机关机了");
    }
}
```

```java
public class Camera implements Usbinterface{//实现接口


    @Override
    public void start() {
        System.out.println("相机开始工作");
    }

    @Override
    public void end() {
        System.out.println("相机关闭了");
    }
}
```

然后我们再写一个Computer的对象

```java
public class Computer {
    //编写一个方法
    public void work(Usbinterface usbinterface){
        usbinterface.start();
        usbinterface.end();
    }
}
```

这里我们就把接口设置好,然后来测试一下

```java
public class test0 {
    public static void main(String[] args) {
        //创建手机
        Camera camera = new Camera();
        Phone phone = new Phone();
        //创建电脑
        Computer computer = new Computer();
        computer.work(phone);
        computer.work(camera);

    }
}
```

![image-20230308184723695](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308184723695.png)

我们可以看到phone 和 camera就像两个接口插入到电脑之中。。。。。确实很像哈哈





基本介绍

> ![image-20230308184959780](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308184959780.png)

基本用法

```java
package com.Interface_;

public interface Ainterface0 {
    //写属性(得初始化)
    public int n = 10;
    //写方法
    //在接口中，抽象方法，可以忽略abstract关键字
    public void say();
    /*
    * 如果你想要有默认方法
    * jdk8之后，可以有默认实现方法，需要使用default关键字修饰
    * jdk8之后，还有静态方法
    *
    */
    default public void cry(){
        System.out.println("说说话-王靖雯")
    }

    public static see(){
        System.out.println("爱，存在吗-王靖雯")
    }
```





深入讨论

我们要清楚什么时候使用接口？

![image-20230308190703027](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308190703027.png)

我们来句一个例子：：

比如你是一个项目经理，你手下有三个程序员。。让他们分别编写三个类，分别取对Mysql，Oracle，DB2数据库进行连接。但是由于人的习惯不一样，所以所编写的方法不一样。

比如A编写了两个方法，f（）是连接Mysql，f2（）是关闭数据库

B编写了两个方法，con（）是连接Oracle，close（）是关闭Oracle

C编写了两个方法，connect（）是连接DB2，close（）是关闭DB2

然后你发现他们三个人交上来的代码，虽然功能一样，但是各种命名方式不一样，导致你作为项目经理很挠头。。。

这时候你该怎么办，你就利用接口的方式，先写一个接口类，然后丢给程序员，去实现接口功能即可，就避免了这种麻烦事。。。。



接口的注意事项

1. 不能实例化，本是是一个抽象的概念。
2. 接口中所有的方法都是public方法，并且都是abstract
3. 一个类同时可以实现多个接口
4. 接口中的属性，接口中的属性只能是final，而且是public static final 修饰符。比如：int a = 1；实际上是public static final int a = 1;(必须初始化)
5. 接口中的访问形式：接口名.属性名
6. 一个接口不能继承其他的类，但是可以继承多个别的接口interface A extends B,C{}
7. 接口的修饰符只能是public和默认，这点和类的修饰符一样的

```java
public class InterfaceDetail2 {
    public static void main(String[] args) {
        System.out.println(AB.n);//接口中的属性是static final
        AB ab = new AB();
        ABC abc = new ABC();
        abc.see(ab,ab);
    }

}

class ABC{
    public void see(IA a,IB b){
        a.say();
        b.Cry();
    }
}

interface IA{
    int n = 19;
    void say();
}

interface IB{
    void Cry();
}

interface IC extends IA,IB{
    
}//这里不能用implements只是是extends

class AB implements IA,IB{
    @Override
    public void say() {
        System.out.println("说说话-王靖雯");
    }

    @Override
    public void Cry() {
        System.out.println("忘了吧-王靖雯");
    }
}
```



#### 实现接口VS继承类

小结：当之类继承了父类，就自动拥有父类的功能，如果子类需要扩展功能，可以通过实现接口的方式扩展

可以理解为实现接口是对java单继承机制的一种补充

![image-20230308201601350](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308201601350.png)

```java
package com.Interface_;

public class ExtendsVSInterface {
    public static void main(String[] args) {
        LittleMoney littleMoney = new LittleMoney("wukong");
        littleMoney.fly();
        littleMoney.Swimming();
        littleMoney.climbing();
    }
}

//猴子
class Monkey{
    private String name;


    public Monkey(String name) {
        this.name = name;
    }

    public void climbing(){
        System.out.println("猴子会爬树...");
    }
}

class LittleMoney extends Monkey implements Fishable,Bird{
    public LittleMoney(String name) {
        super(name);
    }

    @Override
    public void fly() {
        System.out.println("飞翔~~");
    }

    @Override
    public void Swimming() {
        System.out.println("游泳~~");
    }
}


//接口
interface Fishable{
    void Swimming();
}

interface  Bird{
    void fly();
}
```



接口多态和数组多态

**![image-20230308202558654](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308202558654.png)**

![image-20230308202517788](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308202517788.png)

```java
package com.Interface_;

public class InterFacePolyArr {
    public static void main(String[] args) {
        USB[] usb = new USB[4];
        usb[0] = new phone0();
        usb[1] = new camera0();
        usb[2] = new phone0();
        usb[3] = new phone0();
        for (int i = 0; i < 4; i++) {
            usb[i].start();
            usb[i].close();
            if(usb[i] instanceof camera0){
                camera0 t = (camera0) usb[i];
                t.call();
                //((camera0) usb[i]).call();
                //向下兼容
            }
        }
    }
}

interface USB{
    void start();
    void close();
}

class phone0 implements USB{
    @Override
    public void start() {
        System.out.println("手机正在连接~~~~");
    }
    @Override
    public void close() {
        System.out.println("手机关闭连接~~~~");
    }
}

class camera0 implements USB{
    public void call(){
        System.out.println("qeqeqe");
    }
    @Override
    public void start() {
        System.out.println("相机正在连接~~~~");
    }

    @Override
    public void close() {
        System.out.println("相机关闭连接~~~~");
    }
}

class computer0{
    public void use(USB usb){
        usb.start();
        usb.close();
    }
}
```

![image-20230308203608801](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230308203608801.png)

410集~~~~~~~



### 8.内部类

![image-20230309142514950](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309142514950.png)

```java
/*
* 定义在外部类局部位置上
* 局部内部类（有类名）
* 匿名内部类（没有类名，重点！！！）
*
* 定义在外部类的成员位置上
* 成员内部类（没有static修饰）
* 静态内部类（使用static修饰）
* */
```

```java
public class Test1 {
    public static void main(String[] args) {
        Outer1 outer1 = new Outer1();
        outer1.m1();
    }
}
//局部内部类
class Outer1{//外部类
    private int n = 100;

    private void say(){
        System.out.println("外部类的私有方法");
    }
    public void m1(){//方法
        //局部内部类是定义在外部类的局部位置，通常在方法
        class Inner1{//局部内部类
            //可以直接访问外部类的所有成员，包含私有的
            //不添加访问修饰符，但可以使用final修饰
            //作用域只在该方法体内或代码块内
            public void f1(){
                System.out.println("n= " + n);//可以直接访问私有的
                say();
            }
        }

        class Inner2 extends Inner1{
            public void m1(){
                System.out.println("吗" + n);
            }
        }
        //在外部类方法体中可以创建对象

        Inner1 inner1 = new Inner1();
        inner1.f1();
        Inner2 inner2 = new Inner2();
        inner2.m1();


    }

    {//代码块
        class Inner03{

        }
    }

    //外部类在方法中，可以创建Inner1对象，然后调用方法即可
    //new Inner1().var 不能直接创建局部内部类（无static）





}
```

![image-20230309142638679](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309142638679.png)

外部其他类不能直接访问局部内部类，地位是局部变量

外部类和局部内部类的成员重名时，默认遵循就近原则，如果想访问外部类的成员，则可以使用（外部类名.this.成员）去访问

System.out.prinltn("外部类的n =" + 外部类名.this.n);

最重要！！！！！！！！！！！！！！！！！！！！！！！！！！！

> 匿名内部类的使用
>
> 说明：匿名内部类是定义在外部类的局部位置，比如方法中，并且没有类名？？？？
>
> 1.匿名内部类的基本语法
>
> new 类或接口（参数列表）{
>
> ​		类体
>
> }；
>
> ```java
> package com.InnerOuter_;
> 
> public class AnnoymousInnerClass {
>  public static void main(String[] args) {
>      Outer3 outer3 = new Outer3();
>      outer3.method();
>  }
> }
> /*
> * 1.本质是类
> * 2.内部类
> * 3.该类没有名字，系统给你取的
> * 4.是一个对象
> */
> 
> class Outer3{
>     //外部类
>     private int n = 10;
>     public void method(){
>         //基于接口的匿名内部类
>         //1.为什么使用匿名内部类
>         //想使用A接口
>         //传统方法，写一个类实现这个接口，并创建对象
>         //现在只想需要使用一次Tiger类，后面不在使用了
>         //那我们为了简化开发空间，我们使用匿名内部类来实现Tiger的cry功能
>         //面向对象搞懂编译类型和运行类型
>         //tiger的编译类型？ 接口类型A
>         //tiger的运行类型？ 是匿名内部类
>         //jdk底层在创建匿名内部类Outer04￥1，离开马上就创建了，并把地址返回
>         //使用一次，就不能再用了
>         /*
>         * 我们看底层
>         * class XXX implements A{
>         *       @Override
>         *       public void cry(){
>         *           System.out.println("ppppp");
>         *       }
>         * }
>         *
>         * */
>         A tiger = new A(){
>             @Override
>             public void cry() {
>                 System.out.println("ppppp");
>             }
>         };
>         tiger.cry();
>         System.out.println("匿名内部类的名称== " + tiger.getClass());
>     }
> }
> interface A {
>     public void cry();
> }
> //class Tiger implements A{
> //    @Override
> //    public void cry() {
> //        System.out.println("老虎--");
> //    }
> //}
> class Father{
>     public Father(String name) {
>         super();
>     }
>     public void test(){
> 
>     }
> }
> ```
>
> ![image-20230309145237828](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309145237828.png)

```java
package com.InnerOuter_;

public class AnnoymousInnerClass {
    public static void main(String[] args) {
        Outer3 outer3 = new Outer3();
        outer3.method();
    }
}
/*
* 1.本质是类
* 2.内部类
* 3.该类没有名字，系统给你取的
* 4.是一个对象
*/

class Outer3{
    //外部类
    private int n = 10;
    public void method(){
        //基于接口的匿名内部类
        //1.为什么使用匿名内部类
        //想使用A接口
        //传统方法，写一个类实现这个接口，并创建对象
        //现在只想需要使用一次Tiger类，后面不在使用了
        //那我们为了简化开发空间，我们使用匿名内部类来实现Tiger的cry功能
        //面向对象搞懂编译类型和运行类型
        //tiger的编译类型？ 接口类型A
        //tiger的运行类型？ 是匿名内部类
        //jdk底层在创建匿名内部类Outer04￥1，离开马上就创建了，并把地址返回
        //使用一次，就不能再用了
        /*
        * 我们看底层
        * class XXX implements A{
        *       @Override
        *       public void cry(){
        *           System.out.println("ppppp");
        *       }
        * }
        *
        * */
        A tiger = new A(){
            @Override
            public void cry() {
                System.out.println("ppppp");
            }
        };
        tiger.cry();
        System.out.println("匿名内部类的名称== " + tiger.getClass());



        Father father = new Father("jack"){
            @Override
            public void test() {
                System.out.println("重回了方法");
            }
        };

        System.out.println("匿名内部类 = " + father.getClass());
        father.test();
    }
}
interface A {
    public void cry();
}
//class Tiger implements A{
//    @Override
//    public void cry() {
//        System.out.println("老虎--");
//    }
//}
class Father{
    public Father(String name) {
        System.out.println(name);
    }
    public void test(){

    }
}
```

```java
package com.InnerOuter_;

public class AnnoymousInnerExercise {
    public static void main(String[] args) {

        //当作实参直接传递
        f1(new AA(){
            @Override
            public void show() {
                System.out.println("这是一幅名画？");
            }
        });

        //传统方法
        f1(new Picture());


    }

    //静态方法
    public static void f1(AA a){
        a.show();
    }
}
//接口
interface AA{
    void show();
}

class Picture implements AA{
    @Override
    public void show() {
        System.out.println("这是另一副画");
    }
}
```

写一个练习题

![image-20230309161344153](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309161344153.png)

```java
package com.InnerOuter_;

public class AnnoymousInnerExercise1 {
    public static void main(String[] args) {

        Cellphone cellphone = new Cellphone();
        cellphone.alarmclock(new Bell() {
            @Override
            public void ring() {
                System.out.println("猪起床了哈哈");
            }
        });

        cellphone.alarmclock(new Bell() {
            @Override
            public void ring() {
                System.out.println("小伙伴们上课了");
            }
        });


    }
}

interface Bell{
    void ring();
}

class Cellphone{
    public void alarmclock(Bell a){
        a.ring();
    }
}
```

匿名内部类涉及到继承 多态 动态绑定 内部类 4个知识点



成员内部类（比较简单）

//可以直接访问所有的外部类成员，私有的也可以

第一种方法.外部其他类想访问内部类

![image-20230309163134394](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309163134394.png)

第二种方法。创建一个方法返回一个class对象

![image-20230309163307807](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309163307807.png)



静态内部类

![image-20230309163745680](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309163745680.png)

![image-20230309163949424](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309163949424.png)

![image-20230309164021279](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309164021279.png)

424！！！！！！！！！！！！！！！！！！！

![image-20230310154049910](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230310154049910.png)



```java
public class Homework06 {
    public static void main(String[] args) {
        Person tang = new Person("唐僧",new Horse());
        tang.passRoad();
        tang.passRiver();
        tang.passRoad();
    }
}
interface Vehicles{
    String work();
}
class Horse implements Vehicles{
    @Override
    public String work() {
        return "Horse";
    }
}
class Boat implements  Vehicles{
    @Override
    public String work() {
        return "Boat";
    }
}

class VehiclesFactory{

    private static Horse horse = new Horse();

    private VehiclesFactory() {}
    //    public static Horse getHorse(){
//        return new Horse();
//    }

    public static Horse getHorse() {
        return horse;
    }

    public static Boat getBoat(){
        return new Boat();
    }
}
```

## Java学习第十一章

### 枚举 注释

枚举：

我们以季节为例，他的对象具体值，是固定的四个，不会有更多

那我们要怎么样实现呢？

enumeration

[ , , , , ]

枚举是一组有限的集合

自定义实现枚举

```java
package com.phLearn.enum_;

public class Enumeration02 {
    public static void main(String[] args) {
        System.out.println(season1.AUTUMN);
    }
}


class season1 {
    private String season;
    private String desc;

    //定义四个对象
    public static season1 SPRING = new season1("春天", "温暖");
    public static season1 AUTUMN = new season1("秋天", "凉爽");
    public static season1 WINTER = new season1("冬天", "寒冷");
    public static season1 SUMMER = new season1("夏天", "炎热");


    /*
     * 首先是私有化构造器
     * 让其不能被直接new
     * 然后定义四个对象 春夏秋冬
     * 去掉setXxx方法，防止属性被修改
     * */

    private season1(String season, String desc) {
        this.season = season;
        this.desc = desc;
    }

    @Override
    public String toString() {
        return "Season " + season + " 描述 " + desc;
    }
}
```





第二种方式枚举类

```java
enum season{
SPRING("春天","温暖"),AUTUMN("秋天","凉爽"),WINTER("冬天", "寒冷"),SUMMER("夏天", "炎热");
private String season;
private String desc;
private season1(String season, String desc) {
    this.season = season;
    this.desc = desc;
}

public String getSeason() {
    return season;
}

public String getDesc() {
    return desc;
}

@Override
public String toString() {
    return "Season " + season + " 描述 " + desc;
}
}
```

![image-20230309183619506](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309183619506.png)





enum的常用方法

![image-20230309185513556](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309185513556.png)



还有一个用法就是switch与枚举类混用

例如

> 一个枚举类 Animals
>
> Animal tiger = new Animals.TIGER;
>
> 
>
> 
>
> switch(tiger){
>
> ​			case TIGER:break;
>
> ​			..........
>
> }

### 基本的Annotation介绍

使用Annotation时要在前面增加@符号，并把该Annotation当成一个修饰符使用，用于修饰它支持的程序元素。

三个基本的Annotation:

1)@Override:限定某个方法，是重写父类方法，该注释只能用于方法

2)@Deprecated:用于表示某个程序元素(类，方法等)已过时

3)@SuppressWarnings：一直编译器警告

![image-20230309194822385](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309194822385.png)

![image-20230309194950522](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309194950522.png)



@Deprecated

![image-20230309195020949](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309195020949.png)

![image-20230309195605949](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309195605949.png)

@SupperssWarning

当我们不希望看到警告的时候，可以使用@SupperssWarning注解来抑制警告信息。

![image-20230309200021197](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230309200021197.png)

434集！！！！停下了



修饰注解的注解，简单了解一下就行

元注解

@Retention 注解

![image-20230310143241286](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230310143241286.png)

![image-20230310143735106](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230310143735106.png)



## Java学习第十二章

引出异常，如果程序碰到一个异常，程序就停止。。。听起来很正常。但是一旦一个程序的健壮性很差的时候，对于大型的项目来说，不是一件好事。

```java
public class Exception0 {
    public static void main(String[] args) {
        int num1 = 1;
        int num2 = 0;
        //ArithmeticException 计算错误
        //当抛出异常后，下面程序就退出了，不在执行了
        //健壮性很差，当项目体系庞大的时候，代码就停止，那健壮性就不好
        //大家想想这样的程序好吗？，不好，不应该出现了一个不算致命的问题
        //java设计者，提供了一个叫做异常处理机制来解决该问题
        //如果程序员，认为一段程序可能出现异常/问题，可以使用try-catch异常处理机制来解决问题
        //从而保证程序的健壮性
        try{
            int res = num1 / num2;
        }catch(Exception e){
            e.printStackTrace();
        }
        System.out.println("程序继续执行--");
    }
}
```

![image-20230312103409270](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312103409270.png)

### 运行时异常[程序运行时，发生的异常]

### 编译时异常[编程时，编译器检查出的异常]

#### 异常体系图

![image-20230312104750843](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312104750843.png)



### 运行时异常

1.NullPointerException（空指针异常）

```java
public class NullPointerException {
    public static void main(String[] args) {
        String name = null;
        try {
            int []a = {1 , 4 ,5 };
            System.out.println(name);
            for (int i = 0; i <= a.length; i++) {
                System.out.println(a[i]);
            }
        }catch (Exception e){
            System.out.println("nullPointerException");
        }
    }
}
```



2.ClassCastExcpetion(类型转换异常)

```java
public class ClassCastException {
    public static void main(String[] args) {
        A b = new B();
        B b1 = (B)b;
        try{
            C c = (C)b;
        }catch (Exception e){
            System.out.println("出错了"); 
        }
    }
}

class A{}
class B extends A{}
class C extends A{}
```

3.ArithmeticExcepetion（运算异常）

```java
public class ClassCastException {
    public static void main(String[] args) {
        A b = new B();
        B b1 = (B)b;
        try{
            C c = (C)b;
        }catch (Exception e){
            System.out.println("出错了"); 
        }
    }
}

class A{}
class B extends A{}
class C extends A{}
```

4.NumBerFormatException（数字格式异常）

```java
public static void main(String[] args) {
    String name = "1234";
    //将String 转成int
    int num = Integer.parseInt(name);
    System.out.println(name);
    //抛出NumberFormatExcption
    name = "afha";
    num = Integer.parseInt(name);
    System.out.println(name);
}
```

5.数组下标越界

ArrayIndexOutOfBound(数组下标越界)



### 编译时异常

SQLException//操作数据库时，查询表可能发生异常

IOException//操作文件发生的异常

FileNotFoundEXception//当操作一个不存在的文件时，发生异常

ClassNotFoundException//加载类，而该类不存在，异常

EOFException//操作文件，到文件尾部，发生异常

illegalArguementException//参数异常 





### 异常处理

处理方式

try - catch - finally

![image-20230312132840497](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312132840497.png)



throws处理机制图

![image-20230312133242411](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312133242411.png)

二选一



JVM的处理机制：//1.输出异常信息。2.退出程序

如果没有设置t-c-f方法处理异常，则默认采用throws方法丢给JVM

例题

```java
public class TryCatch0 {
    public static void main(String[] args) {
        try {
            String name = " 12att3";
            int a = Integer.parseInt(name);
            System.out.println("afaf");
        } catch (Exception e) {
            System.out.println("异常信息=" + e.getMessage());
        } finally {
            System.out.println("。。。。。。。。。。。");
        }
        //ctrl + alt + t
        System.out.println("程序继续");
    }
}
```

可以有多个catch语句，finally不管是否有异常，都会执行

![image-20230312135713365](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312135713365.png)

相当于没有检测异常

课堂练习

![image-20230312141931242](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312141931242.png)

这里有一个陷阱。。别以为抛出异常了 就return 3（这里是空指针异常），由于呢finally是肯定会执行的，所以return 4.。。                这题的答案也是返回4   真离谱啊啊啊啊

再来一题

![image-20230312142143100](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312142143100.png)

输出多少？

输出 4.。。。。。

再来一题

![image-20230312142339161](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312142339161.png)

这里的return 不会马上执行 会有一个temp保存临时变量 3 等finally执行完输出 4 了才会return 3；

![image-20230312142547848](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312142547848.png)

练习一个小题

```java
public static void main(String[] args) {

    //如果用户输入的不是一个整数，就会提示他反复输入，直到输入一个整数为止
    //思路
    Scanner scanner = new Scanner(System.in);
    boolean flag = true;
    while(flag){
        try {
            System.out.println("请输入一个整数");
            int a = Integer.parseInt(scanner.next());
            flag = false;
        } catch (NumberFormatException e) {
            System.out.println("输入错误噢，请重新再来!");
        }
    }
    System.out.println("成功的输出");
}
```





#### 异常处理的第二种机制

throws异常处理

![image-20230312143654912](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312143654912.png)

我丢弃这个异常不处理，丢给上一层处理。

![image-20230312144636452](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312144636452.png)

```java
public class Throws0 {
    public static void main(String[] args) {
        //f1();
    }
    
    
    public void f2(){
        /*
         * 1.FileNotFound是一个编译异常，程序中必须处理
         * 比如try - catch 或者 throws
         * 2.对于运行时异常，程序中如果没有处理，默认就是throws的方式处理
         *
         *
         * */
         int n1 = 10;
         int n2 = 0;
         double res = n1 / n2;
    }
    
    
    public void f1() throws FileNotFoundException{
        //创建一个文件流异常
        //这里的一场是一个FileNotFoundException 编译异常
        FileInputStream fis = new FileInputStream("d://a.txt");
        //1.使用throws，抛出异常，让调用f1方法的调用者（）处理
        //FileNotFoundException 可以用 Exception 代替，由于Exception是FileNotFoundException的父类
//        try {
//            FileInputStream fis = new FileInputStream("d://a.txt");
//        } catch (FileNotFoundException e) {
//            System.out.println();
//        }
    }

}
```

子类重写父类的方法时，对抛出异常的规定：子类重写的方法所抛出的异常要么一致，要么为父类抛出的异常类型的子方法。



![image-20230312145335617](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312145335617.png)

这里的Son方法 不能抛出throws，只能是RuntimeException或者是它的子类



![image-20230312145728314](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312145728314.png)

这里f3()抛出的是编译异常，必须处理。

f1()中要么try - catch - finally，或者继续throws 这个编译异常

![image-20230312150053329](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312150053329.png)





### 自定义异常

<img src="C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312104750843.png" alt="image-20230312104750843" style="zoom:200%;" />

```java
public class Excercise0 {
    public static void main(String[] args) {
        int age = 141;
        if(age<120||age>30){
            throw new AgeException("年龄范围错误~");
        }
    }
}

//自定义一个异常
class AgeException extends RuntimeException{
    public AgeException(String message) {
        super(message);
    }
}
```

简单🤭

一般我们自定义异常是继承运行时异常RuntimeException，好处是可以使用默认的处理机制。否则还得throws 编译异常



![image-20230312152456232](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230312152456232.png)



## Java学习第十三章

Wrapped 包装类

八大基本数据类型的包装类

boolean 和 char 的继承类有些不一样

其他6个基本数据类型的包装类是 Number

![image-20230313133016127](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313133016127.png)

![image-20230313133319223](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313133319223.png)

![image-20230313133352965](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313133352965.png)

![image-20230313133408772](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313133408772.png)



### 装箱和拆箱

int 和 Interger之间怎么转化

装箱：基本数据类型-》包装类型

Jdk5之前是手动装箱和拆箱

Jdk5之后是自动拆箱和装箱

底层调用的是ValueOf

```java
public class Interger0 {
    public static void main(String[] args) {
        //手动装箱
        int n1 = 100;
        Integer i = new Integer(n1);
        Integer integer1 = Integer.valueOf(n1);
        
        //手动拆箱
        //Integer -> int
        int i0 = integer1.intValue();
        
        //自动装箱
        Integer integer2 = n1;//让然调用的是底层的ValueOf（）方法
        //自动拆箱
        int n1 = integer2;//底层仍然使用的是Value（）的方法
        
        //其他包装类的用法类似
    }
}
```

![image-20230313134625377](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313134625377.png)







### 包装类型和String类型的转换

```java
public static void main(String[] args) {
    //手动装箱
    int n1 = 100;
    Integer i = new Integer(n1);
    Integer integer1 = Integer.valueOf(n1);

    //手动拆箱
    //Integer -> int
    int i0 = integer1.intValue();

    //自动装箱
    Integer integer2 = n1;//让然调用的是底层的ValueOf（）方法
    //自动拆箱
    int n2 = integer2;//底层仍然使用的是Value（）的方法
    //其他包装类的用法类似
}
```







![image-20230313140654526](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313140654526.png)





其实就是当我们直接给Integer对象赋值时，如果他是-128 ~ 127之间的时候，它原本对象内部cache（缓存数组）本身就有了值，这时候我们如果通过==去比较两个 Integer对象时，发现他们是相等的。 这就不奇怪了。

但是如果你new 两个新对象。那就肯定不一样。

具体来看看Integer.valueOf的源码

public static Integer valueOf(int i) {
        if (i >= IntegerCache.low && i <= IntegerCache.high)
            return IntegerCache.cache[i + (-IntegerCache.low)];
        return new Integer(i);
}


在IntegerCache中cache数组初始化如下，存入了-128 - 127的值

cache = new Integer[(high - low) + 1];
int j = low;
for( int k = 0; k < cache.length ; k ++)
    cche[k] = new Integer(j ++);
从上面我们可以知道给Interger 赋予的int数值在-128 - 127的时候，直接从cache中获取，这些cache引用对Integer对象地址是不变的，但是不在这个范围内的数字，则new Integer(i) 这个地址是新的地址，不可能一样的

![image-20230313150307080](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313150307080.png)

![image-20230313151834117](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313151834117.png)

实例七中，比较的是基本数据类型 

![image-20230313152031637](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313152031637.png)





### String

![image-20230313152134824](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313152134824.png)

```java
public class string01 {
    public static void main(String[] args) {
        String name = "hello";
        //String对象用于保存字符串，也就是一组字符序列
        //String 类实现了接口 SerializableString 可以串行化 可以在网络传输
        //Comparable   comparaTo【string对象可以比较大小】
        //String 是一个final类 ，不能那个被其它类继承
        //String 有属性 private final char value【】;用于存放字符串内容
        //一定要注意 value是一个final类型，不可以修改（地址不能修改）
        //真正存放 private final char value【】
    }
}
```

```java
public class string02 {
    public static void main(String[] args) {
        //直接赋值的方式：
        //先从常量池查看是否“hsp”数据空间，如果有直接指向。否则创建一个新的常量然后再指向它。
        String s = "hsp";
        //构造器赋值方式：
        //先在堆中创建空间，里面维护了value的属性，指向常量池的特点空间，如果常量池有该
        //常量，直接指向该空间。否则，重新创建，通过value指向。最终指向的是堆中的空间地址。
        String s1 = new String("stribng" );


        String a = "abc";
        String b = "abc";
        System.out.println(a.equals(b));//T
        System.out.println(a==b);//T
    }
}
```

这两个"abc"都是指向常量池那块空间.



```java
public class string02 {
    public static void main(String[] args) {
        //直接赋值的方式：
        //先从常量池查看是否“hsp”数据空间，如果有直接指向。否则创建一个新的常量然后再指向它。
        String s = "hsp";
        //构造器赋值方式：
        //先在堆中创建空间，里面维护了value的属性，指向常量池的特点空间，如果常量池有该
        //常量，直接指向该空间。否则，重新创建，通过value指向。最终指向的是堆中的空间地址。
        String s1 = new String("stribng" );


        String a = "abc";
        String b = "abc";
        System.out.println(a.equals(b));//T
        System.out.println(a==b);//T

        String a1 = "hsp";//a直接指向常量池
        String b1 = new String("hsp");//b指向堆中对象
        //b 指向堆中对象
        System.out.println(a1 == b1);
        System.out.println(a1.equals(b1));

        //string.intern() //intern方法调用底层C++的 string.intern的方法查看常量池是否有 该常量
        System.out.println(a1==b1.intern());
        
    }
}
```

谈谈String.intern方法

1. 首先明确什么是intern()方法？

String.intern()是一个Native方法，底层调用C++的 StringTable::intern方法实现。当通过语句str.intern()调用intern()方法后，JVM 就会在当前类的常量池中查找是否存在与str等值的String，若存在，则直接返回常量池中相应Strnig的引用；若不存在，则会在常量池中创建一个等值的String，然后返回这个String在常量池中的引用。

2. intern()方法在jdk6和jdk(7/8)的区别

（1）在jdk6中，字符串常量池在永久代，调用intern()方法时，若常量池中不存在等值的字符串，JVM就会在字符串常量池中创建一个等值的字符串，然后返回该字符串的引用；

（2）在jdk7/8中，字符串常量池被移到了堆空间中，调用intern()方法时，如果常量池已经存在该字符串，则直接返回字符串引用，否则复制该堆空间中字符串对象到常量池中并返回。


![image-20230313202811618](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313202811618.png)



练习题

![image-20230313203507513](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313203507513.png)

![image-20230313204434350](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313204434350.png)

![image-20230313205351610](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313205351610.png)

c并不是直接指向常量区，而是指向堆的value  总共创建3个对象。

![image-20230313205541724](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313205541724.png)

![image-20230313205805673](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313205805673.png)

![image-20230313210108070](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313210108070.png)

都是精品 也很简单

![image-20230313211628531](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313211628531.png)

![image-20230313223836058](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313223836058.png)

![image-20230313230128361](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230313230128361.png)





```java
System.out.println("hello".indexOf('e'));
System.out.println("helleo".lastIndexOf('e'));
System.out.println("heelo".toUpperCase());
System.out.println("HELLO".toLowerCase());
String s1 = "sad";
//字符串补充连接
s1 = s1.concat("中华").concat("人民");
System.out.println(s1);
s1 = s1.replace("中华","adc");
System.out.println(s1);

//split 字符串切割
String s2 = "谁知盘中餐,粒粒皆辛苦,啊方法";
String[] sp = s2.split(",");
//切割的是每一个字符串，然后保存在String[]的数组中
for(int i = 0 ;i < sp.length ; i++){
    System.out.println(sp[i]);
}


String fileroad = "E:\\afaf\\sgsg";
sp = fileroad.split("\\\\");//这里是需要四个左斜杠，需要注意这个细节哦，不是两个
for(int i = 0 ;i < sp.length ; i++){
    System.out.println(sp[i]);
}


//c.compareTo比较两个字符串的大小，如果前者大，
//则返回正数,后者大，则返回负数，如果相等，返回0;
//如果长度相同，并且每个字符也相同，就返回0
//如果长度不相同或则相同但字符不同，则比较区分大小
String a = "jchn";
String b = "jack";
System.out.println(a.compareTo(b));//返回的是'c' -'a'的值


//格式化字符串
// String info = "我的姓名" + name + " 年龄 " + age + " 爱好是 " + hobby + "希望大家喜欢我";
String formatStr = "我的姓名是%s 年龄是%d 成绩是%.2f 性别是%c 希望大家喜欢我";
int age = 13;
double score = 423.2;
char c = '男';
String info2 = String.format(formatStr,"潘恒",age,score,c);
System.out.println("info2= " + info2);
```





### StringBuffer

神他妈重要

1.StringBuffer 的直接父类 AbstractStringBuilder

2.StringBuffer 实现了 Seriallizable，即Stringbuffer 可以序列化

3.在分类中 AbstractStringbulider 有属性 char[] value,不是final

Stringbuffer类是final类型 ，不能被继承。

4.它和String的区别还体现在一点，就是字符串的内容存放不在常量区,而是在堆中

5.String保存的内容是final类 里面的值不能修改 每次更改改的是地址 不是内容

6.stringbuffer的更新实际上是更新内容，不用每次更新地址，效率高于String

![image-20230314113758369](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230314113758369.png)





StringButter初始化的时候是如果没有字符串，那么默认长度是16；

![image-20230314122328449](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230314122328449.png)

```java
public static void main(String[] args) {
    //构造方法1
    StringBuffer s = new StringBuffer();//默认长度16

    //构造方法2
    StringBuffer stringbuffer = new StringBuffer(100);
    
    //构造方法三
    StringBuffer stringBuffer1 = new StringBuffer("hello");//这个缓冲区的长度为字符串长度加上16
}
```

![image-20230314122623081](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230314122623081.png)

StringBuffer 转化 String方法



```java
//转化String
//方式一
String stringBuffer2 = stringBuffer1.toString();
//方式二
String string0 = new String(stringBuffer1);
```

String几种常用方法

```java
//Stringbuffer的几种常用方法
StringBuffer string1 = new StringBuffer("hello");
string1.append('f');
string1.append("fghaf");
System.out.println(string1);
string1.append("11111").append("22222").append("333333");
System.out.println(string1);

//删除字符
//删除的是11~14的字符[11,14)
string1.delete(11,14);
System.out.println(string1);

//替换字符
string1.replace(9,11,"fha");
//[9,11)
System.out.println(string1);

string1.replace(0,1,"里大牛啊的发达");
System.out.println(string1);//超过范围往后移

//插入字符串 insert
string1.insert(string1.length(),"xiaobai");
System.out.println(string1);
```

![image-20230314125515077](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230314125515077.png)





### Stringbuilder

![image-20230314174723637](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230314174723637.png)

```java
//1.Stringbuilder一般是用在单线程，没锁hh
//2.实现了Serializable，说明可以进行序列化，进行网络传输
//3.StringBuilder 是final类，不能被继承
//4.Stringbuilder 对象字符序列仍然是存放在其父类 AbstractStringbuilder value [] 在堆中
//6.由于Stringbuilder没有synchronized 关键字，所以一般在单线程中使用。
```





Stringbuilder和StringBuffer的区别

1. Stringbuffer和Stringbuilder的比较
2. StringBuilder和StringBuffer非常相似
3. String 不可变字符序列，效率低，但是复用率高
4. StringBuilder 可变字符串序列 ，效率高，适合单线程,线程不安全
5. StringBuffer 可变字符串序列 ，效率高，适合多线程,线程安全
6. String 我们需要大量对字符串修改，不要使用String
7. 效率测试 
8. StringBuilder > StringBuffer > String









### Math

![image-20230314184223010](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230314184223010.png)

```java
public static void main(String[] args) {
    //Math(静态方法)
    //1.abs绝对值
    int abs = Math.abs(-9);
    System.out.println(abs);
    //2.pow
    double pow = Math.pow(2,4);//2的4次方
    System.out.println(pow);
    //3.ceil 返回》=该参数的最小整数
    double ceil = Math.ceil(-3.000001);
    System.out.println(ceil);
    //4.floor 返回《=该参数的最大整数
    double floor = Math.floor(-4.4444449);
    System.out.println(floor);
    //5.round 四舍五入
    double round = Math.round(4.4444449);
    System.out.println(round);

    //6.sqrt 求开方
    double sqrt = Math.sqrt(-9.0);
    System.out.println(sqrt);
    //NaN


    //&.romdom 求随机数
    //random 返回0~1之间的随即小数
    //思考，获取一个a~b之间的随机整数，a,b均为整数，比如2~7
    for (int i = 0; i < 10; i++) {
        System.out.println((int)(Math.random()*10% 5+2));
    }
```

![image-20230314184256383](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230314184256383.png)





### ArraysMethod

```java
Integer[] a = {1,3,-2,5,43};
        //Arrays，最重要的功能就是sort了，平常写算法题也能用到
       //默认也是升序 从小到大
//       Arrays.sort(a);
//       System.out.println(Arrays.toString(a));
//      自定义排序和 c++里面的compare也很想 c++的是重写一个sort返回 true 或则 false;
        //使用匿名内部类 接口的方式
        Arrays.sort(a, new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                Integer o3 = (Integer)o1;
                Integer o4 = (Integer)o2;
                return o4 - o3;
                //如果是object1 - object2 那么是升序
                //如果是object2 - object1 那么是降序
            }
        });
        System.out.println(Arrays.toString(a));
```

![image-20230315104042539](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315104042539.png)

通过匿名内部类重写Comparator >0则升序  <0则降序

体现了接口编程+动态绑定+匿名内部类

手写Sort方法 + 接口实现Comparator方法

```java
public class Exercise1 {
    public static void main(String[] args) {
        Integer s[] = {2,-1,2,52,23,5,9,-1,2,-5,2};
        sort0.Sort1(s, new comparator1() {
            @Override
            public int Comparator(Object o1, Object o2) {
                Integer o3 = (Integer)o1;
                Integer o4 = (Integer)o2;
                return o4 - o3;
            }
        });
        System.out.println(Arrays.toString(s));
    }
}

interface comparator1{
    int Comparator(Object o1,Object o2);
}

class sort0{
    public static void Sort1(Integer[] a,comparator1 c){
        for (int i = 0; i < a.length; i++) {
            for (int j = 0; j < a.length - 1 - i; j++) {
                if(c.Comparator(a[j],a[j+1])<0){
                    int temp = a[j];
                    a[j] = a[j+1];
                    a[j+1] = temp;
                }
            }
        }
    }
}
```

```java
Integer[] arr = {1,3,87,423,12};
    //copyOf数组元素的复制
    //1.从arr数组中，拷贝arr.length个元素到newArr数组中
    //2.如果拷贝的长度 > arr.lengh就在新数组的后面增加null
    //3.如果拷贝长度 < 0 就异常
    Integer[] newArr = Arrays.copyOf(arr,3);
    System.out.println(Arrays.toString(newArr));


    //fill
    //1.数组填充
    Integer[] arr1 = {2,-2,98,21};
    Integer[] arr2 = new Integer[]{4,5,6,7};
    Arrays.fill(arr2,88);
    System.out.println(Arrays.toString(arr2));


    //equals 比较两个数组内容是否完全一致
    System.out.println(Arrays.equals(arr1,arr2));

    //aList方法
    List<Integer> list = Arrays.asList(arr1);
    //1.返回的asList 编译类型List（接口）
    //2.asList 运行类型 java.util.Arrays#ArrayList,是Arrays类的一个静态内部类
}
```

### System

.exit(0)

>  0表示一个状态 知道推出就完事



arraycopy：复制数组元素，比较适合底层

一般都用Arrays.valueOf完成复制数组



1. src:源数组

2. srcPos:从源数组的哪个索引位置开始拷贝

3. dest：目标素组，即把源素组的数据拷贝到哪个数组

4. destPos:把源素组的数据拷贝到 目标数组的哪个索引。

5. length:从源数组拷贝多少个数组到目标数组

   

![image-20230315133345334](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230315133345334.png)



System.currentTimeMillens:返回当地时间距离1970-1-1的毫秒数



### BigInteger

大long的意思哈哈     



![image-20230321103049273](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230321103049273.png)

```java
public class test {
    public static void main(String[] args) {
        //当我们编程中，需要处理很大的整数 long 不够用
        //可以使用BigInter的类来确定
        //long l = 23149174179471947174197491749174;

        BigInteger bigInteger = new BigInteger("14657164169561985691659615961659165961561659165916561651956916");
        System.out.println(bigInteger);

        //1.在对BigInteger进行加减乘除时，需要使用相应的方法 不能直接使用+ - * /
        //2.使用包装类BigInteger里封装的方法
    }
}
```

### BigDecimal



```java
//浮点型的大数呢？
    BigDecimal bigDecimal = new BigDecimal("414114.52262627534525263473734535363467367367373834756845845");
    BigDecimal bigDecimal1 = new BigDecimal("361.19659165619");
    System.out.println(bigDecimal.subtract(bigDecimal1));
}
```

![image-20230321105217678](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230321105217678.png)





### Date

![image-20230321105310143](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230321105310143.png)

> 1.获取当前系统时间
>
> 2.这里的Date 类是在java.util包
>
> 

![image-20230321120906329](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230321120906329.png)



第二代

![image-20230321124700790](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230321124700790.png)

第三类日期类

![image-20230321124859940](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230321124859940.png)

![image-20230321124627734](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230321124627734.png)

![image-20230321125522395](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230321125522395.png)

格式化

![image-20230321130904369](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230321130904369.png)

![image-20230321131552729](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230321131552729.png)













## Java学习第十四章

### 集合（重要的呀匹）

1.可以动态地保存任意多个对象，使用比较方便

2.提供了一系列方便的操作对象的方法：add remove set get等

3.使用集合添加，删除新元素的代码更加简洁了

> Collection
>
> 1.集合主要分为两类(单列集合，双列集合)
>
> 2.Collection 接口有两个重要的子接口（List Set），他们的实现子类都是单列集合
>
> 3.Map 接口的实现子类 双列集合存放的是键值对的方式

![image-20230321210234737](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230321210234737.png)

![image-20230321210336127](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230321210336127.png)





继承Collection接口的基本方法

```java
public class test0 {
    //collecction接口的常用方法
    @SuppressWarnings("all")
    public static void main(String[] args) {
        //List有序 且元素不重复
        List list = new ArrayList();
        //add:添加元素
        list.add("jack");
        list.add(10);
        System.out.println("list=" + list);

        //remove:删除元素
        list.remove("jack");//指定删除某个元素
        System.out.println("list:= " + list );

        //contains:查找元素是否存在
        System.out.println(list.contains("jack"));

        //size()：查看list的元素个数
        System.out.println(list.size());

        //clear():清空集合


        ArrayList list2 = new ArrayList();
        list2.add("红楼梦");
        list2.add("西游记");
        list.addAll(list2);
        System.out.println("list :=" + list);
        //containsAll,查找多个元素是否存在
        System.out.println(list.containsAll(list2));

        //removeAll:删除多个元素
        list.add("聊斋");
        list.removeAll(list2);
        System.out.println("list:=" + list);
    }
}
```

![image-20230322103922016](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230322103922016.png)

![image-20230322103934334](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230322103934334.png)

```java
public class test1 {
    @SuppressWarnings("all")
    public static void main(String[] args) {
        Collection col = new ArrayList();
        col.add(new Book("小白",2,"打篮球"));
        col.add(new Book("苏白",7,"打羽毛球"));
        col.add(new Book("梦瑶",5,"打排球"));
        col.add("hfa");

        //现在希望遍历ArrayList怎么做？
        //我们有迭代器iterator
        Iterator it = col.iterator();
        //使用while进行遍历
        while(it.hasNext()){
            //判断是否还有数据
            //返回下一个元素，类型是Object(全是Object的子类)
            Object obj = it.next();
            System.out.println("obj=" + obj);
        }
        //ctrl + j快捷键提示
        //itit-》while
//        while (it.hasNext()) {
//            Object next =  it.next();
//
//        }
    }
}
```





增强for

```java
package com.learnCollection_demo1;

import java.util.ArrayList;
import java.util.Collection;

public class test2 {
    @SuppressWarnings("all")
    public static void main(String[] args) {
        Collection col = new ArrayList();
        col.add(new Book("小白",2,"打篮球"));
        col.add(new Book("苏白",7,"打羽毛球"));
        col.add(new Book("梦瑶",5,"打排球"));

        //使用增强for
        for(Object book : col){
            System.out.println("book:=" + book);
        }
        int[] a = {2,4,6,1,3,4};
        for(int i : a){
            System.out.println("i:=" + i);
        }
    }
}
```

两种遍历

> 1.
>
> while(iterator.hasNext()){
>
> ​		Obejct obj = iteratoer.next();
>
> }
>
> 2.for(Object obj : col){
>
> }









### List接口

- List集合类中的元素是有序的，且可以重复



![image-20230322194926011](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230322194926011.png)



ListMethod方法

> ```java
> @SuppressWarnings("all")
> public class ListMethod {
>  public static void main(String[] args) {
>      List list = new ArrayList();
>      list.add("jack");
>      list.add("simple");
>      list.add("merry");
>      System.out.println(list);
>      //insert
>      list.add(1,"panheng");
>      System.out.println(list);
> 
>      //addAll插入多个元素
>      List list2 = new ArrayList();
>      list2.add("林泓旭");
>      list2.add("农棋松");
>      list.addAll(list2);
>      System.out.println(list);
> 
>      //int indexOf(Object obj)返回对象obj在list中的位置
>      System.out.println(list.indexOf("林泓旭"));
> 
>      //Object remove(int index);移除指定的Index位置的元素，并返回此元素
>      list.remove(0);
>      System.out.println("list:="+list);
> 
>      //替换 Object set(int index ,Object else);设置指定index位置的元素为else ，相当于是替换
>      list.set(1,"玛丽");
>      System.out.println("list=" + list);
> 
>      //.subList(0,2)  前闭后开
>      List list3 = list.subList(0,2);
>      System.out.println("returnlist:=" + list3);
> 
>  }
> }
> ```



List的三种遍历方式[ArrayList,LinkedList,vector]



> 1. 使用迭代器iterator
>
>    Iterator it = col.iterator;
>
>    while(it.hasNext()){
>
>    ​	object obj = it.next();
>
>    }
>
> 2. 方式二 使用增强For
>
>    for(Object obj : col){
>
>    }
>
> 3. 方式三:使用普通for
>
>    for(int i = 0 ; i < list.szie() ;i++){
>
>    ​	Object obj = list.get(i);
>
>    ​	Sysytem.out.println(obj);
>
>    }

​    

```java
//集合的冒泡排序
public void sort(ArrayList list){
    for (int i = 0; i < list.size(); i++) {
        for (int j = 0; j < list.size() - 1; j++) {
            Book boo1 = (Book)list.get(j);
            Book boo2 = (Book)list.get(j + 1);
            if(boo1.price > boo2.price){
                Book bootemp = boo1;
                list.set(j,list.get(j+1));
                list.set(j+1,bootemp);
            }

        }
    }
}
```



> ArrayList的注意事项
>
> 1.ArrayList可以防住null
>
> 2.ArrayList是由数组来实现数据存储的
>
> 3.ArrayList基本等同于Vector，除了ArrayList是线程不安全（执行效率高）看源码，在多线程的情况下，不建议使用ArrayList

![image-20230322193733697](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230322193733697.png)

源码中没有synchronized加锁互斥



ArrayList的底层源码操作机制分析

![image-20230322194909350](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230322194909350.png)

ArrayListSource

> 1. ArrayList中维护的是一个Object类型的数组中elementDate。
> 2. ArrayList的扩容机制是当达到阈值大小时，以原先1.5倍大小进行扩容
> 3. ![image-20230322202927036](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230322202927036.png)

源码

![image-20230322200920613](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230322200920613.png)

![image-20230322201025460](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230322201025460.png)

![image-20230322201047497](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230322201047497.png)

为什么使用copyOff方法呢？

因为copyOf能保留原先的数据，效率会高一些

??调试按键步入//alt + shit + F7







### Vector

- 底层也是Object[] 数组
- 线程安全，效率不太高 加了synchronized锁

![image-20230323151232052](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230323151232052.png)





### LinkedList

- LinkedList底层实现了双向链表和双端队列特点
- 可以添加任意元素（元素可以重复），包括null
- 线程不安全，没有实现同步
- ![image-20230323151523347](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230323151523347.png)



底层维护了双向链表

![image-20230323151640537](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230323151640537.png)



Node的构造函数

![image-20230323153146750](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230323153146750.png)



```java
LinkedList linkedList = new LinkedList();
    linkedList.add(1);
    /*
    * public boolean add(E e) {
               linkLast(e);
      return true;
      }
    *
    *
    void linkLast(E e) {
    final Node<E> l = last;
    final Node<E> newNode = new Node<>(l, e, null);
    last = newNode;
    if (l == null)
        first = newNode;
    else
        l.next = newNode;
        size++;
        modCount++;
    }
    *
    * */
    
    
    //删除结点
    linkedList.remove();
    //默认删除第一个元素
    //按0 1 来编号
    
    
    //也能用迭代器循环
    //it.hasNext
    //普通for循环   .get()
}
```

其他方法和ArrayList差不多 

![image-20230323154104400](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230323154104400.png)





### Set接口

```haxe
/*
* 无序（添加和取出的方式顺序不一致），没有索引
* 不允许重复元素，所以最多包含一个null
* 还有很多继承Set接口的Api
* */
```

首先它也是继承了Conllection的子接口，因此，常用方法和Conllection接口一样

set接口的遍历方式

1.可以用迭代器

2.增强for

*3.不能使用索引的方式来获取*

![image-20230323162926376](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230323162926376.png)

不能插入重复的否则返回false

![image-20230323163639323](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230323163639323.png)



HashSet的底层是HashMap（数组+链表+红黑树）





#### 源码追查Let go

![image-20230329101559067](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329101559067.png)

![image-20230329101447946](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329101447946.png)

PRESENT是hashSet里面的东西，是个static,final，起到一个占位的作用

来下一步

![image-20230329101543140](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329101543140.png)

然后开始进入hash(key)

![image-20230329101934091](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329101934091.png)

hash值

我们可以看到这里的hashCode取出之后还需要与自身算数右移16位进行异或运算？

为什么呢？异或 有1得1 无一得9
因为这样会得到一个新的值，使得低16位和高16位都参与到最终的hahs值计算中，提高hash值分布均匀性

来让我们看看hashCode怎么运算？

![image-20230329102334866](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329102334866.png)





开始深入到里边

![image-20230329102803510](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329102803510.png)

这个位置hash值已经得到 key也传入

<img src="C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329102859707.png" alt="image-20230329102859707" style="zoom:150%;" />

辅助变量

由于呢这是第一次add所以会执行

```java
if ((tab = table) == null || (n = tab.length) == 0)
    n = (tab = resize()).length;
```



执行resize()

<img src="C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329103434406.png" alt="image-20230329103434406" style="zoom:150%;" />

![image-20230329103510044](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329103510044.png)

加载因子默认Default_load_factor = 0.75

![image-20230329103639710](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329103639710.png)

默认初始大小default_Initial_capacity = 16

> 当我们的table数组的使用长度达到newCap x loadfactory = 16 * 0.75 = 12（这里我们拿初始化来做例子）的时候需要扩展，因为害怕多个线程突然大量涌入阻塞，可以理解为一个缓冲的作用

![image-20230329104159924](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329104159924.png)

把newCap-》newTab-》table

出去

接下来下一步

这一步计算hash该队应在table表中的哪一个位置

//并把这个位置的对象赋值给p

//判断p是否为空

//1.如果为空，这创建一个新的Node

//2.不为空,这另行判断

```java
if ((p = tab[i = (n - 1) & hash]) == null)
    tab[i] = newNode(hash, key, value, null);
```

![image-20230329104739617](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329104739617.png)



就结点加加，再看看是否大于threshold(12)

afterNodeInsertion是hashMap留给子类实现的一个函数

然后返回null证明添加成功，不为空则是已经存在

![image-20230329105004240](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329105004240.png)

2.

到下一个add("panheng")

![image-20230329105101788](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329105101788.png)

然后到putval函数

![image-20230329105216036](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329105216036.png)

和第一次没太大区别

就是不用resize（）

然后就返回

![image-20230329105257900](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329105257900.png)



3.第三次再加入一个相同的java

![image-20230329105413501](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329105413501.png)

这一步算出来同样的是3，且p已经存在不为null

去掉else里，跟着看

```java
else {
    Node<K,V> e; K k;
    if (p.hash == hash && 
        ((k = p.key) == key || (key != null && key.equals(k))))
        e = p;
    //如果当前索引的第一个元素和准备插入的key的hash值一样
    //或者调用equals方法比较值是否相等
    //则不往下走了
    else if (p instanceof TreeNode)
        e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
    //判断p是不是一棵红黑树
    else {
        for (int binCount = 0; ; ++binCount) {
            if ((e = p.next) == null) {
                p.next = newNode(hash, key, value, null);
                if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                    treeifyBin(tab, hash);
                //再把元素添加链表后的时候，立即判断是否达到8个结点
                //如果到达8个节点就编程红黑树
                break;
            }
            if (e.hash == hash &&
                ((k = e.key) == key || (key != null && key.equals(k))))
                break;
            p = e;
        }
       //判断链表里是否存在相同元素
       //死循环
       //如果找到相同元素就退出
       //比较到最后然后接上结点才能退出
    }
    if (e != null) { // existing mapping for key
        V oldValue = e.value;
        if (!onlyIfAbsent || oldValue == null)
            e.value = value;
        afterNodeAccess(e);
        return oldValue;
    }
}
```



拓展看看treeifyBin的源码

![image-20230329111403770](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329111403770.png)



我们发现tab.length的长度如果小于64，就先对table进行resize()扩容;而不是直接把长度为8的链表树化.

如果长度大于tab.length，则树化.

![image-20230329111820955](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329111820955.png)

![image-20230329112045602](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329112045602.png)



##### 练习1

/*

创建一个hashSet值，我们加入三个对象

add(new Student("panheng",18));

add(new Student("Smith",28));

add(new Student("panheng",18));

*/

你说我们hashSet会有几个值？
有3个 为什么？

因为new一个新对象，他们的属性会相同但是hashCode会不一样，所以它会加入到hashset中，但是这就不符合我们的元素单一的原则。那我们该怎么办？？？？？？？？？

> 我们要重写对象的HashCode的方法和 equals方法，当对象的属性相等时，返回相同的hashcode的值



![image-20230329170214672](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329170214672.png)



![image-20230329170345620](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329170345620.png)



```java
@Override
public boolean equals(Object o) {
    if (this == o) return true;
    if (o == null || getClass() != o.getClass()) return false;
    Student student = (Student) o;
    return id == student.id && Objects.equals(name, student.name);
}

@Override
public int hashCode() {
    return Objects.hash(name, id);
    //取决于name和id的值
}
```



### LinkedHashSet

- LinkedHashSet是HashSet的子类
- LinkedHashSet底层是一个LinkedHashMap,底层维护了一个 数组（hash表） +**双向链表**(注意区别)
- LinkedHashSet根据元素的hashCode值来决定元素的存储位置,同时使用链表维护元素的**次序**，这使得元素看起来是以插入顺序保存的.
- LinkedHashSet不循序添加重复元素



![image-20230329194142413](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329194142413.png)

新的结点在创建的时候（第一个创建除外）结点的前驱指针pre指向前一个结点，next为空。下一个结点则是新结点。

![image-20230329194609115](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329194609115.png)





![image-20230329200146537](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230329200146537.png)

1. LinkedHashSet 加入顺序和取出元素/数据的顺便一致
2. LinkedHashSet 底层维护的是一个LinkedHashMap（是HashMap的子类）
3. .........

```java
Node<K,V> newNode(int hash, K key, V value, Node<K,V> e) {
    LinkedHashMap.Entry<K,V> p =
        new LinkedHashMap.Entry<K,V>(hash, key, value, e);
    linkNodeLast(p);
    return p;
}
```

```java
static class Entry<K,V> extends HashMap.Node<K,V> {
    Entry<K,V> before, after;
    Entry(int hash, K key, V value, Node<K,V> next) {
        super(hash, key, value, next);
    }
}
```



```java
public class HouseWork1 {
    public static void main(String[] args) {
        Set<Car> linkedHashSet = new LinkedHashSet<>();
        linkedHashSet.add(new Car("奥拓",1000));
        linkedHashSet.add(new Car("奥迪",300000));
        linkedHashSet.add(new Car("法拉利",100000000));
        linkedHashSet.add(new Car("奥拓",1000));
        linkedHashSet.add(new Car("保时捷",123131000));
        linkedHashSet.add(new Car("比亚迪",117451000));

        Iterator<Car> it = linkedHashSet.iterator();
        while (it.hasNext()) {
            Car next =  it.next();
            System.out.println(next);
        }

    }
}

class Car{
    private String name;
    private double price;


    public Car() {
    }

    public Car(String name, double price) {
        this.name = name;
        this.price = price;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Car car = (Car) o;
        return Double.compare(car.price, price) == 0 && Objects.equals(name, car.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, price);
    }

    @Override
    public String toString() {
        return "Car{" +
                "name='" + name + '\'' +
                ", price=" + price +
                '}';
    }
}
```



一个简单的例子





### Map接口

- 1.Hashtable

  Properties

- 2.HashMap

  LinkedHashMap

- 3.TreeMap

![image-20230331214347323](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230331214347323.png)

存放的是双列的架构<K,V>(Key,Present)

Map和Collection并列存在。用于保存映射的数据关系

![image-20230331214700896](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230331214700896.png)



> 1. 底层源码解析
> 2. K-v 最后是hashMap$Node node = newNode(hash,key,value.null)
> 3. K-v 为了方便程序员的遍历，还会创建EntrySet 集合 ,该集合存放的元素的类型 Entry
> 4. 对象就有K，v  EntrySet<Entry<K,V>> 即：transient Set<Map,Entry<K,v>> entrySet
> 5. entrySet中 ，定义的类型 是 Map，Entry, 但是实际上存放的还是HashMap$Node

 ![image-20230401180539169](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230401180539169.png)

 

HashMap$Node为什么能够放在EntrySet集合中呢？ 因为这个hashMap$Node继承了 Entry

```java
//在EntrySet中定义的类型是Map.Entry
//当我们把hashMap$node对象 存放到entrySet方便我们遍历 因为Map。Entry重写了重要方法
//K.getKey V.getValue
```



Map遍历方式 （五种）

 ①、[Iterator](https://so.csdn.net/so/search?q=Iterator&spm=1001.2101.3001.7020)+entrySet写法【推荐JDK8以下】，Map.Entry是Map接口的内部接口，获取迭代器，然后依次取出每个迭代器里面的Map.Entry

```java
    Iterator<Map.Entry<Integer,String>> iterator=map.entrySet().iterator();
    while(iterator.hasNext()){
        Map.Entry<Integer,String> entry=iterator1.next();
        System.out.println(entry.getKey());
        System.out.println(entry.getValue());
    }
```

②、Iterator+keyset写法【不推荐，只能获取key，然后通过key获取对应的value,重复计算】

```java
    Iterator<Integer> iterator=map.keySet().iterator();
    while (iterator.hasNext()){
        Integer key=iterator.next();
        System.out.println(key);
        System.out.println(map.get(key));
    }
```

 ③、foreach遍历方式【JDK8以下推荐写法】

```java
    for(Map.Entry<Integer,String> entry:map.entrySet()){
        System.out.println(entry.getKey());
        System.out.println(entry.getValue());
    };
```

④：lambda表达式遍历【JDK8推荐写法，简捷】

```java
    map.forEach((key,value)->{
        System.out.println(key);
        System.out.println(value);
    });
```







Map常用方法

1. map.remove() 删除
2. map.get()根据键值获取
3. map.size()获取元素个数
4. map.isEmpty:判断个数是否为0
5. map.clear();清空
6. map.containsKey:查找键值是否存在



![image-20230402200028688](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230402200028688.png)

为啥要使用set和collection呢  ？ 方便遍历

Map接口实现类 ->HashMap

1. Map接口的常用实现类：HashMap,Hashtable和Properties
2. HashMap是Map接口使用频率最高的实现类
3. Hashmap是以key-value对的方式来存储数据
4. key不能重复 但是Value的值可以重复，且允许使用null键
5. 如果存放相同的key，则覆盖原来的value
6. 与HashSet一样，无序
7. HashMap没有实现同步，线程不安全





HashTable

Hashtable的基本介绍

基本用法和HashMap类似

（线程安全）

1.底层有数组HashTable￥Entry[] 初始化大小是 11 (hashMap是16)

2.临界值也是加载因子 x table Size

![image-20230403142109276](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230403142109276.png)



![image-20230403143035023](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230403143035023.png)

扩容:两倍加一

![image-20230403143140258](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230403143140258.png)



Properties （Hashtable的子类）

![image-20230403143215938](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230403143215938.png)

![image-20230403143347044](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230403143347044.png)

![image-20230403143850926](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230403143850926.png)

TreeSet（有排序需要传入匿名内部类）

```java
public static void main(String[] args) {
        //当我们使用无参构造器，创造TreeSet时，仍然是无序的
        //希望使用字符串大小进行排序
        //使用匿名内部类实现
        TreeSet treeSet = new TreeSet(new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                //调用String的Compareto
                return ((String)o1).compareTo((String)o2);
            }
        });

        treeSet.add("fafa");
        treeSet.add("abc");
        treeSet.add("fhau");
        treeSet.add("vbsded");

        Iterator<String> it = treeSet.iterator();
        while (it.hasNext()) {
            String next =  it.next();
            System.out.println(next);
        }

/*
*     public TreeSet(Comparator<? super E> comparator) {
        this(new TreeMap<>(comparator));
    }
*
* */
    }
```





## Java学习第十五章

### 泛型

- 不能对到集合ArraysList中的数据类型进行约束，不安全
- 遍历的时候需要向下兼容，进行类型转换，如果数据量大的时候对效率有影响



```java
public class test1 {
    public static void main(String[] args) {
        ArrayList arrayList = new ArrayList();
        arrayList.add(new Dog("123"));
        arrayList.add(new Dog("456"));
        arrayList.add(new Dog("789"));

        //传统方法没问题
        for(Object o : arrayList){
            Dog dog = (Dog)o;
            System.out.println(dog.toString());
        }

        //但是当我们这时候加入了一只猫
        arrayList.add(new Cat("fha"));
        //这里是没有报错的，编译器并不能检测出来
        for(Object o : arrayList){
            Dog dog = (Dog)o;
            System.out.println(dog.toString());
        }
    }
}
```

![image-20230327162727580](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230327162727580.png)

这里类类型转化失败



这时候我们该如何解决呢？

泛型的作用就出来了

```java
public class test2 {
    public static void main(String[] args) {
        //引入泛型
        //1.当我们ArrayList<Dog> 表示存放到 ArrayList 集合中的元素是Dog类型
        //2.如果编译器发现你传入Arraylist的类型不是Dog类型，编译器会报错
        //3.在遍历的时候取出的直接是Dog而不是Object
        ArrayList<Dog> arrayList = new ArrayList<Dog>();
        //ArrayList集合中的元素只能是Dog类型，还有它的子类型
        arrayList.add(new Dog("123"));
        arrayList.add(new Dog("456"));
        arrayList.add(new Dog("789"));

        for(Dog dog : arrayList){
            System.out.println(dog.toString());
        }
    }
}
```

> 泛型的好处？
>
> 1. 编译时，检查添加元素的类型，提高了安全性
> 2. 减少了类型转换的次数，提高效率
>
> 不使用泛型
>
> Dog -> Obejct -> Dog
>
> 使用泛型
>
> Dog->Dog->Dog

泛型说明

> ![image-20230327164225652](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230327164225652.png)



```java
class Person<E>{
    E s;

    public Person(E s) {
        this.s = s;
    }
    
    public E f(){
        return s;
    }
}
```



例子kk

```java
public class test4 {
    public static void main(String[] args) {
        //1.HashSet
        HashSet<student<String,Integer>> hashSet = new HashSet<>();
        hashSet.add(new student<>("panheng",12));
        hashSet.add(new student<>("liuyaguo",15));
        hashSet.add(new student<>("libai",13));
        hashSet.add(new student<>("xierupu",18));

//        Iterator<student<String,Integer>> it = hashSet.iterator();
//        while (it.hasNext()) {
//            student<String, Integer> next =  it.next();
//            System.out.println(next.toString());

        HashMap<String,student<String,Integer>> map = new HashMap<>();
        map.put("panheng",new student<String,Integer>("panheng",12));
        map.put("liuyaguo",new student<String,Integer>("34234",12));
        map.put("libai",new student<String,Integer>("libai",12));
        map.put("abc",new student<String,Integer>("abc",12));

        //迭代器EntrySet
        Set<Map.Entry<String,student<String,Integer>>> entries = map.entrySet();
        /*
        * public final Iterator<Map.Entry<K,V>> iterator() {
            return new EntryIterator();
        }
        * */
        Iterator<Map.Entry<String,student<String,Integer>>> it = entries.iterator();
        while (it.hasNext()) {
            Map.Entry<String, student<String, Integer>> next =  it.next();
            System.out.println(next);
        }
        }

}

class student<K,T>{
    public K name;
    public T age;

    public student(K name, T age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return "student{" +
                "name=" + name +
                ", age=" + age +
                '}';
    }
}
```



### 泛型使用细节1



![image-20230327171559878](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230327171559878.png)

只能是引用类型，而不是基本数据类型记住！！！！！！！



```java
class Car{
    public void run(){

    }//普通方法

    //说明
    //1.<T,R>是泛型
    //2.是提供fly使用的
    public <T,R> void fly(T t,R r){}//泛型方法
}


class Fish<T,R>{
    //泛型类
    //也可以使用泛型方法
    public<U,Y> void fly(U u,Y y){}
}
```





```java
//1.Tiger后面泛型，所以我们把Tiger就称为自定义泛型
//2.T,R,M泛型的标识符，一般是大写字母
//3.泛型的标识符可以有多个
//4.普通成员，方法可以使用泛型
class Tiger<T,R,M>{
    String name;
    R r;
    M m;
    T t;


    public Tiger(String name, R r, M m, T t) {
        this.name = name;
        this.r = r;
        this.m = m;
        this.t = t;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public R getR() {
        return r;
    }

    public void setR(R r) {
        this.r = r;
    }

    public M getM() {
        return m;
    }

    public void setM(M m) {
        this.m = m;
    }

    public T getT() {
        return t;
    }

    public void setT(T t) {
        this.t = t;
    }
}
```



```java
class tiger{
    //说明: List<?> 表示任意的泛型类型都可以接受
    public static void printConllection1(List<?> c){
        for(Object object : c){
            System.out.println(object);
        }//通配符，取出时，就是Object
    }

    // ? extends AA 表示上限，可以接受AA 或者 AA子类
    public static void printCollection2(List<? extends AA> c){
        for(Object object : c){
            System.out.println(object);
        }
    }
    
    // ? super 子类类名AA:支持AA类以及AA类的父类，不限于直接父类
    //规定了泛型的下限
    public static void printCollection3(List<? super AA> c){
        for(Object object : c)
            System.out.println(object);
    }
    
}

class AA{}
```



```java
public class GenericExtends {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        List<Object> list1 = new ArrayList<>();
        List<AA> list2 = new ArrayList<>();
        List<BB> list3 = new ArrayList<>();
        List<CC> list4 = new ArrayList<>();
        
        //List<?>
        printConllection1(list);
        printConllection1(list1);
        printConllection1(list2);
        printConllection1(list3);
        printConllection1(list4);
        
        //List<? extends AA>
        printCollection2(list2);
        printCollection2(list3);
        
        //List<? super AA>
        printCollection3(list4);
        printCollection3(list2);
        
    }
    //说明: List<?> 表示任意的泛型类型都可以接受
    public static void printConllection1(List<?> c){
        for(Object object : c){
            System.out.println(object);
        }//通配符，取出时，就是Object
    }

    // ? extends AA 表示上限，可以接受AA 或者 AA子类
    public static void printCollection2(List<? extends AA> c){
        for(Object object : c){
            System.out.println(object);
        }
    }

    // ? super 子类类名AA:支持AA类以及AA类的父类，不限于直接父类
    //规定了泛型的下限
    public static void printCollection3(List<? super AA> c){
        for(Object object : c)
            System.out.println(object);
    }

}

class CC{}

class AA extends CC{}

class BB extends AA{}
```

















































## Java学习第十七章

### 程序

程序----》运行--》进程---》使用一定的运行空间（资源）系统分配的

进程是程序的一次执行过程，或是正在运行的一个程序，是动态过程：有它自身的产生、存在和消亡的过程。







### 线程相关概念

单线程：同一时刻，只允许执行一个线程

多线程：同一时刻，只允许执行多个线程





并发：同一时刻。多个任务交替执行，造成一种“貌似同时”的错觉，简单地说，单核cpu实现的多任务就是并发。

不是真正意义上同时。

并行：同一时刻，多个任务同时执行。多核cpu可以实现并行。



线程使用的两种方法

1.继承Thread类 ，重写run方法

2.实现Runnable接口，重写run方法

![image-20230405155928054](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230405155928054.png)





instance（例子）

```java
public class LearnThread {
    public static void main(String[] args) {
        //创建一个cat对象 可以当作线程使用
        Cat cat = new Cat();
        cat.start();//启动线程
    }
}

//1.当一个类继承了Thread类，这个类就可以当作线程使用
//2.我们会重写run方法，写上自己的业务逻辑
//3.run Thread类 实现了runnable接口 的 run（）方法
class Cat extends Thread{
    int time = 0;
    //重写run（）方法，写上自己的业务逻辑
    @Override
    public void run() {
        while (true) {
            System.out.println("喵喵 我是小猫咪"+(++time));
            //让线程休眠一秒钟
            //ctrl + alt + t
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
            if(time == 80) break;
        }
    }
}
```





```java
public class LearnThread {
    public static void main(String[] args) {
        //创建一个cat对象 可以当作线程使用
        Cat cat = new Cat();
        cat.start();//启动线程
        //当main主线程启动了一个子线程Thread-0，主线程不会诸塞，会继续执行
        for (int i = 0; i < 5; i++) {
            System.out.println("A");
        }
//        Cat cat1 = new Cat();
//        cat1.start();
    }
}
```



![image-20230405162017101](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230405162017101.png)





> 1. 为什么先执行start方法？而不是run方法
>
>    因为如果调用run方法，只是调用了这个方法（普通方法）并不是真正启动一个线程，只是执行一个run（）方法后继续往下执行,是串行化执行,相当于在主线程main执行 而不是Thread-0
>
> 2. 
>
> 3. ```java
>    cat.start();//启动线程
>    /*
>    * 追寻源码
>    * 1.public synchronized void start()
>    * 2.start0();
>    * 3.private native void start0();
>    * start0 是一个native本地方法 由JVM机来使用 由C/C++来使用
>    * */
>    ```

![image-20230405163252101](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230405163252101.png)

![image-20230405163514484](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230405163514484.png)

```java
public class LearnThread2 {
    public static void main(String[] args) {
        T1 t1 = new T1();
        T2 t2 = new T2();
        Thread thread = new Thread(t1);
        Thread thread1 = new Thread(t2);
        thread1.start();
        thread.start();
    }
}


class T2 implements Runnable{
    @Override
    public void run() {
        while(true){
            System.out.println("hi T2");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
class T1 implements Runnable{
    //每隔1s执行一次
    @Override
    public void run() {
        while(true){
            System.out.println("hi T1");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
```



![image-20230405171518117](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230405171518117.png)



```java
public class SellTicket {
    public static void main(String[] args) {
//        sellTicket01 sellTicket01 = new sellTicket01();
//        sellTicket01 sellTicket011 = new sellTicket01();
//        sellTicket01 sellTicket012 = new sellTicket01();
//
//        sellTicket01.start();
//        sellTicket011.start();
//        sellTicket012.start();

        SellTicket2 sellTicket21 = new SellTicket2();
        SellTicket2 sellTicket22 = new SellTicket2();
        SellTicket2 sellTicket23 = new SellTicket2();
        Thread thread1 = new Thread(sellTicket21);
        Thread thread2 = new Thread(sellTicket22);
        Thread thread3 = new Thread(sellTicket23);

        thread1.start();
        thread2.start();
        thread3.start();
    }
}

//使用Tread方式 售票
class sellTicket01 extends Thread{
    private static int ticketNum = 100;//静态变量 类变量  让多个线程共享

    @Override
    public void run() {
        while(true){
            if(ticketNum <= 0){
                System.out.println("售票结束...");
                break;
            }
            //休眠50毫秒
            try {
                Thread.sleep(5000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }

            System.out.println("窗口售出:  " + Thread.currentThread().getName() + "售出一张票" + " 还剩下:"
            + (--ticketNum));
        }
    }
}

class SellTicket2 implements Runnable{
    private static int ticketNum = 50;//静态变量 类变量  让多个线程共享
    @Override
    public void run() {
        while(true){
            if(ticketNum <= 0){
                System.out.println("售票结束...");
                break;
            }
            //休眠50毫秒
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }

            System.out.println("窗口售出:  " + Thread.currentThread().getName() + "售出一张票" + " 还剩下:"
                    + (--ticketNum));
        }
    }
}
```



我们发现输出的时候线程同步  造成数据不正确。那怎么样让线程直接单独访问共享资源呢？

其实和操作系统的方式一样 信号量机制



### 线程终止

> 1.通知方式
>
> ​	例如设置一个私有变量boolean 值在线程类中 While(loop){}  ,然后写setloop方法，要关闭的时候     setloop=false即可。线程就退出了







### 线程常用方法

![image-20230407102259747](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230407102259747.png)

![image-20230407102950718](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230407102950718.png)

![image-20230407103027649](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230407103027649.png)







### 线程插队

- yield（产量） 静态方法

![image-20230407103650184](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230407103650184.png)

- join 

```java
public class LearnThread3 {
    public static void main(String[] args) throws Exception {
        test test = new test();
        Thread thread = new Thread(test);
        thread.start();
        int count = 0;
        while(true){
            System.out.println("大哥吃包子");
            try {
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
            count++;
            if(count == 5){
                System.out.println("先让小弟先吃");
                thread.join();
            }
            if(count == 10) break;
        }
    }
}

class test implements Runnable{
    private int count = 0;
    @Override
    public void run() {
        while(true){
            System.out.println("小弟吃包子");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
            count++;
            if(count == 20) break;
        }
    }
}
```

yield 是调用自己的礼让

join是调用别人static方法 插进来



### 用户线程和守护线程

1. 用户线程：也就是工作线程，当线程的任务执行或通知方式结束
2. 守护线程：一般是为工作线程服务的，当所有的用户线程结束，守护线程自动结束
3. 常见的守护线程：垃圾回收机制







如何构守护线程？

```java
public class LearnThread5 {
    public static void main(String[] args) throws InterruptedException {
        DeamonThread deamonThread = new DeamonThread();
        deamonThread.setDaemon(true);//设置为守护进程
        deamonThread.start();
        //如果我们希望当主线程结束后，子线程可以自动结束
        //只需将子线程设为守护线程
        /*
        * 守护线程当其他线程退出了
        * 它就最后退出
        * */
        for (int i = 0; i < 10; i++) {
            System.out.println("ttttttttttttttttttt");
            Thread.sleep(1000);
        }
    }

}


/*
Daemon 守护线程
 */
class DeamonThread extends Thread{
    @Override
    public void run() {
        for(;;){//无线循环
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
            System.out.println("hhhhhhhhhhhhhhhhh");
        }
    }
}
```

### 线程的生命周期

![image-20230407111319482](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230407111319482.png)





### Synchrocized

![image-20230407155132639](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230407155132639.png)

![image-20230407162936260](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230407162936260.png)

代码块上加锁

同步方法·（非静态）的锁可以是this，也可以是其他对象（但是是同一个对象）

同步方法：（静态）的锁加在.class类上

![image-20230407163750276](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230407163750276.png)



### 线程死锁

![image-20230407184156259](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230407184156259.png)

![image-20230407184308908](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230407184308908.png)

<img src="C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230407184512143.png" alt="image-20230407184512143" style="zoom: 200%;" />

![image-20230407184709975](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230407184709975.png)











## Java学习第十八章



1. Java.io 包几乎包含了所有操作输入、输出需要的类。所有这些流类代表了输入源和输出目标。
2. Java.io 包中的流支持很多种格式，比如：基本类型、对象、本地化字符集等等。
3. 一个流可以理解为一个数据的序列。输入流表示从一个源读取数据，输出流表示向一个目标写数据。
4. Java 为 I/O 提供了强大的而灵活的支持，使其更广泛地应用到文件传输和网络编程中。
5. 但本节讲述最基本的和流与 I/O 相关的功能。我们将通过一个个例子来学习这些功能。





### 读取控制台输入

Java 的控制台输入由 System.in 完成。

为了获得一个绑定到控制台的字符流，你可以把 System.in 包装在一个 BufferedReader 对象中来创建一个字符流。

下面是创建 BufferedReader 的基本语法：

````java
BufferedReader br = new BufferedReader(new 
                      InputStreamReader(System.in));
````

BufferedReader 对象创建后，我们便可以使用 read() 方法从控制台读取一个字符，或者用 readLine() 方法读取一个字符串。



### 从控制台读取多字符输入

从 BufferedReader 对象读取一个字符要使用 read() 方法，它的语法如下：

``int read( ) throws IOException``

每次调用 read() 方法，它从输入流读取一个字符并把该字符作为整数值返回。 当流结束的时候返回 -1。该方法抛出 IOException。

下面的程序示范了用 read() 方法从控制台不断读取字符直到用户输入 **q**。

````java
//使用 BufferedReader 在控制台读取字符
 
import java.io.*;
 
public class BRRead {
    public static void main(String[] args) throws IOException {
        char c;
        // 使用 System.in 创建 BufferedReader
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        System.out.println("输入字符, 按下 'q' 键退出。");
        // 读取字符
        do {
            c = (char) br.read();
            System.out.println(c);
        } while (c != 'q');
    }
}
````





### 从控制台读取字符串

从标准输入读取一个字符串需要使用 BufferedReader 的 readLine() 方法。

它的一般格式是：

`String readLine( ) throws IOException`

下面的程序读取和显示字符行直到你输入了单词"end"。

````java
//使用 BufferedReader 在控制台读取字符
import java.io.*;
 
public class BRReadLines {
    public static void main(String[] args) throws IOException {
        // 使用 System.in 创建 BufferedReader
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String str;
        System.out.println("Enter lines of text.");
        System.out.println("Enter 'end' to quit.");
        do {
            str = br.readLine();
            System.out.println(str);
        } while (!str.equals("end"));
    }
}
````



*JDK 5 后的版本我们也可以使用* [Java Scanner](https://www.runoob.com/java/java-scanner-class.html) *类来获取控制台的输入。*



### 控制台输出

在此前已经介绍过，控制台的输出由 print( ) 和 println() 完成。这些方法都由类 PrintStream 定义，System.out 是该类对象的一个引用。

PrintStream 继承了 OutputStream类，并且实现了方法 write()。这样，write() 也可以用来往控制台写操作。

PrintStream 定义 write() 的最简单格式如下所示：

````java
void write(int byteval)
````

该方法将 byteval 的低八位字节写到流中。

**注意：**write() 方法不经常使用，因为 print() 和 println() 方法用起来更为方便。

![img](https://www.runoob.com/wp-content/uploads/2013/12/iostream2xx.png)



### 文件操作

![image-20230411203321008](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230411203321008.png)



```java
@Test
//方式1 ； new File(String pathname)
public void create01(){
    String filePath = "d:\\news1.txt";
    File file = new File(filePath);

    try {
        file.createNewFile();
        System.out.println("文件创建成功");
    } catch (IOException e) {
        throw new RuntimeException(e);
    }
}
```

```java
@Test
//方式2 new File(File parent,String child) 根据父目录文件+子路径构建
//d:\\new2.txt
public void create02(){
    File Parentfile = new File("d:\\");//父路径
    String filepath = "new2.txt";
    File file = new File(Parentfile,filepath);

    try {
        file.createNewFile();
        System.out.println("创建成功");
    } catch (IOException e) {
        throw new RuntimeException(e);
    }
}
```

```java
@Test
//方式3 new File(String parent ,String child) //根据父目录+子路径构建
public void create03() throws IOException {
    String parentPath = "d:\\";
    String child = "news3.txt";
    File file = new File(parentPath,child);

    try {
        file.createNewFile();
        System.out.println("创建文件成功");
    } catch (IOException e) {
        throw new RuntimeException(e);
    }
}
```



### 文件基本操作

![image-20230411205156528](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230411205156528.png)





![image-20230411205934707](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230411205934707.png)



1. mkdir() 创建一级目录
2. mkdirs() 创建多级目录

### IO流原理及流的分类

![image-20230411211336346](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230411211336346.png)

![image-20230411211525209](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230411211525209.png)

![image-20230411212506341](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230411212506341.png)





1. FileInputStream

   该流用于从文件读取数据，它的对象可以用关键字 new 来创建。

   有多种构造方法可用来创建对象。

   可以使用字符串类型的文件名来创建一个输入流对象来读取文件：

```java
public static void main(String[] args) throws IOException {
    String filepath = "d:\\hello.txt";
    //File file = new File(filepath);
    FileInputStream fileInputStream = null;
    int readDate = 0;

    //创建输入流对象FileInputStraeam  用于读取文件
    try {
        fileInputStream = new FileInputStream(filepath);
        //从该字节流读取一个字节的数据。如果没有输入可用，此方法将阻止
        //如果返回-1 ，表示读取完毕
        while((readDate = fileInputStream.read())!=-1){
            System.out.println((char)readDate);//转成char
        }

        //记住一定要关闭流对象
    } catch (IOException e) {
        throw new RuntimeException(e);
    }finally {
         fileInputStream.close();
    }
```

```java
String filepath = "d:\\hello.txt";
//File file = new File(filepath);
FileInputStream fileInputStream = null;
int readlen = 0;
//字节数组
byte[] buf = new byte[20];//一次读取20个字节
//创建输入流对象FileInputStraeam  用于读取文件
try {
    fileInputStream = new FileInputStream(filepath);
    //从该字节流读取一个字节数组的数据。如果没有输入可用，此方法将阻止
    //如果返回-1 ，表示读取完毕
    //如果读取正常，返回实际读取的字节数
    while((readlen = fileInputStream.read(buf))!=-1){
        System.out.println(new String(buf,0,readlen));//转成char
    }

    //记住一定要关闭流对象
} catch (IOException e) {
    throw new RuntimeException(e);
}finally {
    fileInputStream.close();
}
```





### 字符流输入



![image-20230412130828526](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230412130828526.png)





### 节点流和处理流

![image-20230412153750983](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230412153750983.png)

![image-20230412153834329](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230412153834329.png)



![image-20230412154253402](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230412154253402.png)



节点流和处理六的区别和联系

![image-20230412155101630](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230412155101630.png)



















·







## Java学习第十九章



网络通信

Java.net

![在这里插入图片描述](https://img-blog.csdnimg.cn/dfce48b4dd5344d3b9d5e2b6696a1f38.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_15,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/be7611596e7e47188531b4c80e89a522.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_20,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/6e16fddcd43543df9cdad20553029c6b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_15,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/bca6b4bf8bc344b18a97652c4b51a090.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_18,color_FFFFFF,t_70,g_se,x_16)







### Socket

![在这里插入图片描述](https://img-blog.csdnimg.cn/5c48d2ed647345f8a26f2e4052e479e1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_15,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/998a424cdfee4345a77a4d4f63d159e2.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_15,color_FFFFFF,t_70,g_se,x_16)

客户端Client

```java
public class SocketTCP01Client {
    public static void main(String[] args) throws Exception {
        //1.连接服务器(ip,端口)
        //解读 连接本机的9999端口，如果连接成功，则返回Socket对象
        Socket socket = new Socket(InetAddress.getLocalHost(),9999);
        System.out.println("客户端 socket返回= " + socket.getClass());
        //2.连接上后，生成socket ， 通过socket.getOutStream()
        //  得到 和 socket对象关联的输出流对象
        OutputStream outputStream = socket.getOutputStream();
        //3. 通过输出流
        outputStream.write("hello,server".getBytes());
        //4.关闭流对象和socket，必须关闭
        outputStream.close();
        socket.close();
        System.out.println("客户端退出.....");
    }
}
```

服务端

```java
public class SocketTCP01Server {
    public static void main(String[] args) throws Exception {
        //1.在本机的999端口监听 等待连接
        // 细节：要求在本机没有其他服务器在监听9999
        // 细节：这个ServerSocket 可以通过accept() 返回多个Socket[多个客户端连接服务器的并发]
        ServerSocket serverSocket = new ServerSocket(9999);
        System.out.println("服务器,在9999端口监听,等待连接...");
        //2.当没有客户端连接9999端口，程序会 阻塞，等待连接
        // 如果有客户端连接，则会返回Socket对象，程序继续

        Socket socket = serverSocket.accept();

        System.out.println("服务器 socket =" + socket.getClass());
        //
        //3.通过socket.getInputStream() 读取客户端吧写入到数据通道的数据，显示
        InputStream inputStream = socket.getInputStream();
        //4.Io读取
        byte[] buf = new byte[1024];
        int readLine = 0;
        while((readLine = inputStream.read(buf))!=-1){
            System.out.println(new String(buf,0,readLine));
            //根据读取到的实际长度，显示内容
        }
        //5.关闭流和socket
        inputStream.close();
        socket.close();
        serverSocket.close();




    }
}
```





### UDP编程

![在这里插入图片描述](https://img-blog.csdnimg.cn/1ebf5339ce25418885e385537225bf24.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_12,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/fe832ff198e04960946931520826abdd.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_19,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/486d619efd334acabe9d8247821e8353.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_16,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/6733142a7752413f96392f1700aadf5b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_20,color_FFFFFF,t_70,g_se,x_16)



StreamUtils 工具类

```java
public class StreamUtils {
    //功能 ：将输入流转化为Byte[] 即可以把文件的内容读入到byte[]
    public static byte[] streamToByteArray(InputStream is) throws Exception {
        // 创建输出流对象
        ByteArrayOutputStream bos = new ByteArrayOutputStream();
        // 字节数组
        byte[] b = new byte[1024];
        int len;
        while ((len = is.read(b)) != -1) {
            // 循环读取
            // 把读取到的数据，写入 bos
            bos.write(b, 0, len);
        }
        byte[] array = bos.toByteArray();
        bos.close();
        return array;
    }

    public static String streamToString(InputStream is) throws Exception {
        //功能 将InputStream转换成String
        BufferedReader reader = new BufferedReader(new InputStreamReader(is));
        StringBuilder builder = new StringBuilder();
        String line;
        while ((line = reader.readLine()) != null) {
            builder.append(line + "\r\n");
        }
        return builder.toString();
    }
}
```

```java
public class UDPReceiverA {
    public static void main(String[] args) throws IOException {
        //1.创建一个DataGramSocket
        DatagramSocket datagramSocket = new DatagramSocket(9997);
        //2.构建一个DatagramPacket对象 ，准备接收数据
        byte[] buf = new byte[1024];
        DatagramPacket packet = new DatagramPacket(buf, buf.length);
        //调用接受方法
        //填充到packet中
        System.out.println("接收端A正在等待接收数据");
        datagramSocket.receive(packet);
        //如果有数据包发送到9999端口 我会继续往下走
        //如果没有数据发送到9999端口，我会一直等待

        //拆包取出数据并显示
        int length = packet.getLength();
        byte data[] = packet.getData();
        String s = new String(data,0,length);
        System.out.println(s);

        //关闭流
        datagramSocket.close();
    }
}
```

```java
public class UDPSendB {
    public static void main(String[] args) throws IOException {
        //创建一个DatagramSocket
        DatagramSocket socket = new DatagramSocket(9998);

        //将需要发送的数据封装到packet中
        byte buf[] = "hello,明天吃火锅".getBytes();
        DatagramPacket packet = new DatagramPacket(buf, buf.length, InetAddress.getLocalHost(), 9997);
        //接收方在本机9999上等待
        socket.send(packet);

        //关闭资源
        socket.close();
        System.out.println("B端发送完成");
    }
}
```



Receiv

```java
public class UDPReceiveA1 {
    public static void main(String[] args) throws IOException {
        DatagramSocket  socket  = new DatagramSocket(8888);

        byte data[] = new byte[1024];
        DatagramPacket packet = new DatagramPacket(data, data.length);
        //创建个包去接收数据
        System.out.println("接收端正在等待数据");
        socket.receive(packet);

        //拆包取出数据并显示
        int length = packet.getLength();
        byte buf[] = packet.getData();
        String s = new String(buf,0,length);
        System.out.println(s);
        String answer = "";
        if(s.equals("四大名著是哪些?")){
               answer = "<西游记><红楼梦><水浒传><三国演义>";
        }else{
            answer = "what?";
        }


        //===回复信息给B1端
        data = answer.getBytes();
        packet = new DatagramPacket(data, data.length, InetAddress.getLocalHost(),8889);
        System.out.println(data.length);
        socket.send(packet);

        //关闭资源
        socket.close();
        System.out.println("A1端关闭");
    }
}
```

```java
public class UDPSendB1 {
    public static void main(String[] args) throws IOException {
        //创建一个DatagramSocket
        DatagramSocket socket = new DatagramSocket(8889);

        //将需要发送的数据封装到packet中
        Scanner scanner = new Scanner(System.in);
        String question = scanner.nextLine();
        byte buf[] = question.getBytes();
        DatagramPacket packet = new DatagramPacket(buf, buf.length, InetAddress.getLocalHost(), 8888);
        //发送
        System.out.println("B端发送完成");
        socket.send(packet);

        //接收
        System.out.println("B端等待回应");
        byte answer[] = new byte[1024];
        packet = new DatagramPacket(answer, answer.length);
        socket.receive(packet);
        byte data[] = packet.getData();
        int readLine = packet.getLength();
        System.out.println(readLine);
        String s = new String(data,0,readLine);
        System.out.println(s);

        //关闭资源
        socket.close();
        System.out.println("B端完成");
    }
}
```





## Java学习第二十章

### 反射机制

![在这里插入图片描述](https://img-blog.csdnimg.cn/f92be206467a42199a3975295512828e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_14,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/b74d24414fcb479a8e2292c2a251fcc8.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_17,color_FFFFFF,t_70,g_se,x_16)

### 快速入门

![在这里插入图片描述](https://img-blog.csdnimg.cn/6ecd727101224c1abdd013956bbbe32a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_16,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/86113c4759944268a49802d1c2c63c47.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_15,color_FFFFFF,t_70,g_se,x_16)

### 原理

![ ](https://img-blog.csdnimg.cn/d21299f09ffb4c3eb607daeb8246a8a4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_16,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/9ad88c40f7354c7498a7475838b07fab.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_17,color_FFFFFF,t_70,g_se,x_16)

### 反射相关类

![在这里插入图片描述](https://img-blog.csdnimg.cn/0b8df8e7f23449e79ea26cc7bf0b1e41.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_10,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/f6f210b9acf84a91a9d071d19e26dcad.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_14,color_FFFFFF,t_70,g_se,x_16)

### 反射调优

![在这里插入图片描述](https://img-blog.csdnimg.cn/9e49a57a7792403aa5a6fa7801162f49.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_14,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/45c47d07940d4223bf66e94c43989aef.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_14,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/69276dec8ecb42159e4a8e5f81c28705.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_14,color_FFFFFF,t_70,g_se,x_16)

关闭访问检测

.setAccessible(true)

### Class类分析

![在这里插入图片描述](https://img-blog.csdnimg.cn/81df62bf4d2045ac80862bc1a8d26b1d.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/dc9ec9eabda047448ae9c8ef3cea620f.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_16,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/b31427febb244871b839cd3a580821b4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_17,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/7e11cab4ea42433799192fd2d81264f5.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_15,color_FFFFFF,t_70,g_se,x_16)

#### 3）获取Class类对象的六大方式

![在这里插入图片描述](https://img-blog.csdnimg.cn/127ee64564d240e38e94a5ccda9a5bad.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_17,color_FFFFFF,t_70,g_se,x_16)

四种核心方法

![在这里插入图片描述](https://img-blog.csdnimg.cn/190be7cc508d4a5cacd069bfbe0fbbbd.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_14,color_FFFFFF,t_70,g_se,x_16)



![在这里插入图片描述](https://img-blog.csdnimg.cn/142d0e98179847c0978791445f249fa6.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_14,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/823d4564aa2749faaf7b257007bcf683.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_20,color_FFFFFF,t_70,g_se,x_16)

```java
public class GetClass_ {
    public static void main(String[] args) throws ClassNotFoundException {

        //1.Class.forName()
        String classPath = "LearnReflection.Car";//通过配置文件读取
        Class<?> cls = Class.forName(classPath);
        System.out.println("1:="+cls);
        //2. 类名.Class 应用场景：用于参数传递
        Class cls2 = Car.class;
        System.out.println("2:="+cls2);

        //3.已知某个类的实例，通过getClass()对象，运行类型
        //应用场景 有对象实例
        Car car = new Car();
        Class cls3 = car.getClass();//得到它的运行类型
        System.out.println("3:="+cls3);

        //4.通过类加载器来获取Class对象
        //1.先得到类加载器
        ClassLoader classLoader = car.getClass().getClassLoader();
        //2.通过类加载器得到Class对象
        Class cl4 = classLoader.loadClass(classPath);
        System.out.println("4:="+cl4);

        //cls1 ,cls2 ,cls3 ,cls4 是同一个对象
        //5.基本数据类型
        Class<Integer> integerClass = int.class;
        Class<Character> characterClass = char.class;
        System.out.println(integerClass);
        //这里会有一个自动装箱，拆箱的过程
        //.....

        
        //6.基本数据类型对应的包装类可以通过.Type来获取
        Class<Integer> type1 = Integer.TYPE;
        Class<Double> type2 = Double.TYPE;
        System.out.println(type1);
        System.out.println(type2);
    }
}
```



### 哪些类型有class对象呢？

![在这里插入图片描述](https://img-blog.csdnimg.cn/85128145963447aca843404e62bad07a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_12,color_FFFFFF,t_70,g_se,x_16)



![在这里插入图片描述](https://img-blog.csdnimg.cn/0c3f1d48906f4776b14eb324c592371b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_11,color_FFFFFF,t_70,g_se,x_16)





### 类加载器

![在这里插入图片描述](https://img-blog.csdnimg.cn/50e2df2ff26b4ff181669c9eddc7efd6.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_13,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/509efc4c814948a98dbf9bfa2594a6e9.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_17,color_FFFFFF,t_70,g_se,x_16)



#### 类加载图

![在这里插入图片描述](https://img-blog.csdnimg.cn/f3c8608637d84787aefe380456b45b07.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_16,color_FFFFFF,t_70,g_se,x_16)

#### 类加载的五个阶段

![在这里插入图片描述](https://img-blog.csdnimg.cn/af2f17b1e96646048aaad109c653022e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_15,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/68a59187ccd048d6a0781e014d52f839.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_15,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/ddb95ebb3aaa4444bffd30ba8b5f66fe.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_15,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/65c9addf285b425a934d60dc0cf93edc.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_14,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/be96c90450db4fe2bc08659c25559c1d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_16,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/3f400781faae459faf31e88fd00ffede.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_15,color_FFFFFF,t_70,g_se,x_16)

#### 获取类结构信息

![在这里插入图片描述](https://img-blog.csdnimg.cn/abefeaa6514449d58c85245cbc3f53f7.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_11,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/86dfbed59d4046ddb4c9c2e2a370cf76.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_13,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/61fbdd7e6dc545be89521f3ea44142b0.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_13,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/a6edfd759c3142c3829bece96b637c21.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_9,color_FFFFFF,t_70,g_se,x_16)



#### 通过反射创建对象

![在这里插入图片描述](https://img-blog.csdnimg.cn/a9fdd735bb5043c593b6c15371bf077c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6LWr5rW35LuK5aSp5pS-6Zeq5LqG5ZCX77yf,size_15,color_FFFFFF,t_70,g_se,x_16)
