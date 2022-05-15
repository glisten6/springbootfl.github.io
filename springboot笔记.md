  # SpringBoot工程笔记

##  1. 注解

### 1.1启动类

### 1.1.1

~~~
@SpringBootApplication以及SpringApplication.run(BlogApp.class,args)
依赖是starter 会把所有用到的依赖包含进来
~~~





### 1.2配置类

#### 1.2.1 跨域配置类

####  1.2.2  数据库插件

~~~
@Mapper：不用加入扫描包地址，通过mapper.xml的namespace,将对应的mapper加入spring容器中，缺点每个mapper类都要加
@MapperScanner：mapper代替品，需要加入扫描包的地址，通过mapper.xml的namespace，将对应的mapper加入spring容器中
但是 在扫描注解时，不会扫描类，所以当使用@autowired会爆红，@repository会将找到bean加入serviceimpl。所以可以联合使用
~~~

~~~
~~~

~~~
~~~

~~~
~~~





​		



### 1.3其它

#### 1.3.1 Component

~~~
Component:告诉Spring帮我们管理这个对象，放置在类上
@Controller @Service @Repository 分别管理控制层对象，service层的对象，repository对象，都是bean对象
~~~



#### 1.3.2

~~~
@Autowired 自动装配 放置在属性上，构造方法上，set方法上
@Qualifier：配合AutoWired，用来置顶具体注入的对象唯一标识，因为autowired默认按照类注入，而一个 接口可能有多个实现类，所以指定哪个实现类

@Resource 默认通过name属性进行指定，如果没有指定name属性，当注解在字段上，默认字段名进行安装名称 


~~~

~~~
@nullable:表明值为空
~~~

~~~
~~~



~~~
@Bean:在方法上声明，告诉方法产生一个Bean对象，然后把该方法交给Spring管理，产生这个Bean对象方法只调用一次，然后将该bean放入soc容器。
~~~

~~~
@Data:为类自动加入set和get
~~~

~~~
@AllArgsConstructor:加入全部的构造方法
~~~





#### 1.3.2 controller常用到的注解

##### 1.3.2.1 处理器注解

~~~
@ResponseBody:无法返回jsp,但可以返回json
~~~

~~~
@Control:可以和InternalResourceViewResolver配合返回html
~~~

~~~
@RequestController: 
~~~





##### 1.3.2.2 放在方法参数中的注解

~~~
@RequestBody：用来接受前端传给后端json字符串的数据的（应用在前端为post情况下）注意事项：前端传过来的json串的key必须和实体类的属性名一样,get无法接受，
~~~

~~~
@RequestParam:一个请求可以有多个RequestParam 如果参数放在请求体中后台要用RequestBody才能接受 将json字符串key匹配对应实体类的属性（value满足实体类属性类型要求,体类setter方法赋值），只接受非json/xml类型，
~~~



















# 2. Maven

## 2.1父子工程

父工程：

~~~
父工程需要<packaging>pom<packaging>声明自己是父文件
父工程利用modules整合子模块的artifactId
父工程的property会继承给子模块
父工程将dependencyManagement中的依赖传入子文件

~~~

子工程：

~~~
子工程必须显示定义<parent><parent> ，这样父工程将property和依赖继承下来
子工程只需定义artifactId而不需要groupId和版本
子模块继承工程依赖不需要写版本，但是自己独有的要加版本
~~~

# 3 Vue

# 



# 4 MyBatis

## 4.1 mapper.xml

~~~
MyBatis的关注点在POJO与SQL之间的映射关系，即写在mapper.xml中
~~~



~~~

~~~





# 5. Redis

## 5.1如何启动Redis

### 5.1.1 Windows怎么启动redis

cmd进入自己的redis文件夹：

~~~
1.redis-cli.exe
2 auth '你的密码'
3 shutdown
4 exit
5 redis-server.exe redis.windows.conf
~~~

### 5.1.2 Linux怎么启动redis

## 5.2Redis Introduction





# 6. **SpringBoot**

## 6.1.1SpringBoot配置













## 6.4 工具类

~~~
BeanUtils.copyProperties() 将相同类属性进行复制
~~~









# 7. 原理分析

Spring容器初始化流程原理：

~~~
1. 当spring容器启动的时候会去调用ConfigurationClassPostProcessor这个bean工厂的后置处理器完成扫描

2.会实例化一个BeanDefinition的对象，继而调用这个对象的各种set方法存储信息；每扫描到一个符合规则的类，spring都会实例化一个BeanDefinition对象，然后把根据类的类名生成一个bean的名字（比如一个类IndexService，spring会根据类名IndexService生成一个bean的名字`indexService`,spring内部有一套默认的名字生成规则，但是程序员可以提供自己的名字生成器覆盖spring内置的

3.而spring会把这个beanDefinition对象和生成的beanName放到一个map当中，key=beanName，value=beanDefinition对象
4.当spring把类所对应的beanDefintion对象存到map之后，spring会调用程序员提供的bean工厂后置处理器 BeanFactoryPostProcessor(合格Bean工厂后置处理器主要是干预Bean工厂初始化流程)

~~~







# 8. 源码分析













