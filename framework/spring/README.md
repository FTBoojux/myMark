# Spring

### 1、Spring Bean的生命周期

- 加载配置文件并实例化Bean：Spring容器加载配置文件时，会创建相应的Bean实例。

- 设置Bean的属性：Spring容器会自动调用相应的Setter方法，为Bean设置属性值。

- BeanPostProcessor的前置处理：在Bean的初始化之前，Spring容器会调用所有实现BeanPostProcessor接口的类的postProcessBeforeInitialization方法，对Bean进行前置处理。

- 初始化Bean：在Bean实例化并设置完属性之后，Spring容器会调用InitializingBean接口的afterPropertiesSet方法或在配置文件中通过init-method指定的初始化方法对Bean进行初始化。

- BeanPostProcessor的后置处理：在Bean的初始化之后，Spring容器会调用所有实现BeanPostProcessor接口的类的postProcessAfterInitialization方法，对Bean进行后置处理。

- 使用Bean：Bean已经初始化完毕，可以使用了。

- 销毁Bean：当Bean不再被使用时，Spring容器会自动调用DisposableBean接口的destroy方法或在配置文件中通过destroy-method指定的销毁方法对Bean进行销毁。

### 2、Spring代理的实现方式

Spring的代理是通过JDK动态代理和CGLIB代理两种方式实现的。

JDK动态代理
JDK动态代理是Java原生支持的一种动态代理技术，它是通过反射机制来生成一个实现指定接口的代理类对象。Spring中的JDK动态代理主要应用于对接口的代理。

JDK动态代理的实现流程大致如下：

定义一个InvocationHandler接口的实现类，在实现类中实现对目标对象方法的增强逻辑。
使用Proxy.newProxyInstance()方法生成目标对象的代理对象，同时将InvocationHandler接口的实现类作为参数传入。
CGLIB代理
CGLIB代理是通过生成目标类的子类来实现代理的，它可以代理没有实现接口的类。CGLIB代理的实现依赖于asm框架来生成字节码，并使用FastClass机制来调用代理方法，因此比JDK动态代理更快，但也更消耗内存。

CGLIB代理的实现流程大致如下：

定义一个MethodInterceptor接口的实现类，在实现类中实现对目标对象方法的增强逻辑。
使用Enhancer类创建目标类的子类，同时将MethodInterceptor接口的实现类作为参数传入。
需要注意的是，CGLIB代理只能代理非final类的非final方法，因为final方法无法被子类覆盖。

### 3、SpringBoot启动过程

![img](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6ba8bf5c8177430b8f462f35948d1c74~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

Spring Boot的启动流程包括以下主要步骤：

1. **创建SpringApplication对象**：SpringApplication是Spring Boot的核心类，负责启动Spring Boot应用。它会根据当前应用的类型（Web应用或非Web应用）做出一些默认设置。

2. **运行SpringApplication**：执行SpringApplication的run方法开始启动Spring Boot应用。这个方法接收两个参数：应用的主配置类和命令行参数。

3. **加载Spring Boot的自动配置类**：Spring Boot自动配置是其主要特性之一。Spring Boot有许多自动配置类，它们在应用启动时会自动被加载并应用。

4. **创建并刷新Spring容器**：Spring Boot会创建一个ApplicationContext（应用上下文）实例，这个实例就是Spring的IoC容器。然后，Spring Boot会刷新这个容器，触发Bean的加载。

5. **启动内嵌的Servlet容器**（如果是Web应用）：如果当前是一个Web应用，Spring Boot会启动一个内嵌的Servlet容器（默认是Tomcat）。

6. **Spring Boot应用启动完成**：此时，Spring Boot应用已经启动完成，你的应用已经准备好接收请求了。

以上是Spring Boot的启动流程的一种简化描述，实际的过程要复杂得多。例如，在创建和刷新Spring容器的过程中，Spring Boot会做许多额外的工作，如加载Bean定义，解析配置，创建Bean实例等等。