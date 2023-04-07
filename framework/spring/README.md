# Spring

### 1、Spring Bean的生命周期

- 加载配置文件并实例化Bean：Spring容器加载配置文件时，会创建相应的Bean实例。

- 设置Bean的属性：Spring容器会自动调用相应的Setter方法，为Bean设置属性值。

- BeanPostProcessor的前置处理：在Bean的初始化之前，Spring容器会调用所有实现BeanPostProcessor接口的类的postProcessBeforeInitialization方法，对Bean进行前置处理。

- 初始化Bean：在Bean实例化并设置完属性之后，Spring容器会调用InitializingBean接口的afterPropertiesSet方法或在配置文件中通过init-method指定的初始化方法对Bean进行初始化。

- BeanPostProcessor的后置处理：在Bean的初始化之后，Spring容器会调用所有实现BeanPostProcessor接口的类的postProcessAfterInitialization方法，对Bean进行后置处理。

- 使用Bean：Bean已经初始化完毕，可以使用了。

- 销毁Bean：当Bean不再被使用时，Spring容器会自动调用DisposableBean接口的destroy方法或在配置文件中通过destroy-method指定的销毁方法对Bean进行销毁。