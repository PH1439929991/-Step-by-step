# 学习Springboot

## 一、Web入门

![image-20230528222624465](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230528222624465.png)

Springboot将传统的Web开发的mvc.json.tomcat等应用框架整合，提供了一个spring-boot-starter-web组件，简化了Web应用配置

1. 创建SpringBoot项目勾选Spring Web选项后，会自动将Spring-boot-starter-web组件加入到项目中
2. spring-boot-starter-web启动器主要包括web.webmvc.json.tomcat等基础依赖组件，作用是提供Web开发应用场景所需的所有底层依赖。

## 二、控制器

![image-20230528223028848](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230528223028848.png)

![image-20230528223038018](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230528223038018.png)

MVC数据模式

- Model 储存数据
- Controller 处理数据
- View 显示数据



Springboot提供了两种注解让我们去创建Controller

@RestController 返回的是数据

默认情况下，@RestController注解会将返回的对象数据转换为JSON格式

![image-20230528223437544](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230528223437544.png)

@Controller 返回的是一个视图，可以理解为一个html页面 （前后端分离）



#### 路径映射

@ResquestMapping

![image-20230528223746650](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230528223746650.png)

![image-20230528223936300](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230528223936300.png)

![image-20230528224319758](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230528224319758.png)

两种方式都可以



![image-20230528224453948](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230528224453948.png)



## 三、静态资源访问

![image-20230529120833428](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230529120833428.png)



## 四、文件上传

![image-20230529122105235](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230529122105235.png)

![image-20230529162734071](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230529162734071.png)



![image-20230529164043040](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230529164043040.png)

![image-20230601152645686](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230601152645686.png)

![image-20230601152837859](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230601152837859.png)

## 五、RESTful介绍

接口风格

![image-20230601153920084](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230601153920084.png)

![image-20230601153940920](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230601153940920.png)

![image-20230601154113200](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230601154113200.png)

![image-20230601154241026](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230601154241026.png)

![image-20230601154307715](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230601154307715.png)

![image-20230601154324936](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230601154324936.png)

![image-20230601154502479](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230601154502479.png)

![image-20230601154529288](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230601154529288.png)

@PathVariable 动态路径







### Swagger(接口设计模块)

![image-20230601155520082](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230601155520082.png)

![image-20230601155957047](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230601155957047.png)

![image-20230601155944050](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230601155944050.png)

```java
@Configuration//告诉Springboot 这是一个配置类
@EnableSwagger2//启用Swagger2功能
public class SwaggerConfig extends WebMvcConfigurationSupport {

    @Bean
    public Docket createResApi(){
        return new Docket(DocumentationType.SWAGGER_2)
                .apiInfo(apiInfo())
                .select()
                //com包下所有Api都交给Swagger2管理
                .apis(RequestHandlerSelectors.basePackage("com"))
                .paths(PathSelectors.any()).build();
    }

    //API文档页面显示信息
    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
                .title("演示项目API")
                .description("学习Swagger2的演示项目")
                .build();
    }

    /**
     * 解决swagger-ui.html 404无法访问的问题
     */
    @Override
    protected void addResourceHandlers(ResourceHandlerRegistry registry) {
        // 解决静态资源无法访问
        registry.addResourceHandler("/**")
                .addResourceLocations("classpath:/static/");
        // 解决swagger无法访问
        registry.addResourceHandler("/swagger-ui.html")
                .addResourceLocations("classpath:/META-INF/resources/");
        // 解决swagger的js文件无法访问
        registry.addResourceHandler("/webjars/**")
                .addResourceLocations("classpath:/META-INF/resources/webjars/");
    }
}

```

```xml
spring.mvc.pathmatch.matching-strategy=ant_path_matcher
```

```xml
<!--        添加swagger2相关语言-->
        <dependency>
            <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger2</artifactId>
            <version>2.9.2</version>
        </dependency>
<!--        添加swagger-ui相关功能-->
        <dependency>
            <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger-ui</artifactId>
            <version>2.9.2</version>
        </dependency>
    </dependencies>
```