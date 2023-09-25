# spring spring-boot springMVC的区别
**spring**
- Spring是一个IOC容器，用来存放管理Bean，使用依赖注入实现控制反转。
- 也是一个桥梁，可以很方便地整合各种框架。
- 还提供了AOP机制，弥补了OOP的代码重复问题，更方便将不同类不同方法中的共同处理抽取成切面，比如日志、异常等。

**SpringMVC**
- SpringMVC是spring对web框架的一个解决方案，主要赋予 Spring 快速构建 MVC 架构的 Web 程序的能力， 
- 提供了一个总的前端控制器dispatcherServlet，用来接收请求，然后定义了一套路由策略(url到handle的映射)及适配执行handle， 将handle执行结果使用视图解析技术生成视图展现给前端。
- MVC 是模型(Model)、视图(View)、控制器(Controller)的简写，其核心思想是通过将业务逻辑、数据、显示分离来组织代码。 

**SpringBoot**
- springboot是spring提供的一个快速开发工具包，我们使用它能够更加快速方便地开发spring+SprngMvc应用。
- 它约定了很多默认配置，整合了一系列解决方案(Starter机制)、redis、mybatisPlus、activiti等等可以开箱即用。
- 它是一种快速构建独立、生产级的、基于 Spring 框架的应用程序的框架。它提供了自动配置、快速开发等功能，并可以将您的应用程序打包成可执行

# spring spring-boot springMVC的常用注解
## spring
@Configuration
@Import 导入注解
@Bean @Service @Repository
@Autowired @Qualifier配合使用
@Resource
@Value
@PostContrust @PreDestory
@Lazy(true)
@Scope—singleton·
@Primary--自动装配时当出现多个Bean候选者时，被注解为@Primary的Bean将作为首选者
@Value
@Value的值有两类：
① ${ property : default_value }
② #{ obj.property? : default_value }
就是说，第一个注入的是外部参数对应的property，第二个则是SpEL表达式对应的内容
那个 default_value，就是前面的值为空时的默认值。注意二者的不同。
第一种主要是配置文件上的值获。
第二种是对象属性的获取，需要注意的是，如果是获取一个方法的值时，需要在前面增加@，比如#{@obj.getProperty()}

## spring-boot
- @SpringBootApplication = @SpringBootConfiguration，@EnableAutoConfiguration和@ComponentScan 
  - @SpringBootConfiguration 继承至@Configuration，对于熟悉spring的开发者而言，此标注当前类是配置类，并会将当前类内声明的一个或多个以@Bean注解标记的方法的实例纳入到srping容器中，且实例名就是方法名
  - @EnableAutoConfiguration 这个注解就是springboot能自动进行配置的魔法所在了。主要是通过此注解，能所有符合自动配置条件的bean的定义加载到spring容器中，比如根据spring-boot-starter-web ，来判断你的项目是否需要添加了webmvc和tomcat，就会自动的帮你配置web项目中所需要的默认配置。 
  - @ComponentScan 这个熟悉spring的开发者也应该熟悉，会扫描当前包及其子包下被@Component，@Controller，@Service，@Repository等注解标记的类并纳入到spring容器中进行管理。
- @Profile 供了一种隔离应用程序配置的方式，并让这些配置只能在特定的环境下生效
- @ControllerAdvice 统一处理异常
- @ExceptionHandler（Exception.class）用在方法上面表示遇到这个异常就执行以下方法
- @JsonIgnore作用是json序列化时将Java bean中的一些属性忽略掉,序列化和反序列化都受影响。 
- @Transient：表示该属性并非一个到数据库表的字段的映射,ORM框架将忽略该属性


## springMVC

- @RestController = @Conroller + @ResponseBody
- @RequestBody @RequestParam 参数 的绑定 @RequestParam常用来处理简单类型的绑定
- @RequestMapping 类或者方法上
- @PathVariable 获取url上的参数
- @RequestHeader  @CookieValue @ModelAttribute和 @SessionAttributes
