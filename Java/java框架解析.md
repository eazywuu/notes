## 1. Spring

bean注入关键：自定义BeanDefinition类

回调：BeanNameAware

bean初始化：InitializingBean

Bean后处理程序：BeanPostProcessor，属于一套技术，AOP，依赖注入等都依赖于它

IOC：控制反转（依赖注入）

Bean生命周期：

class（UserService.class）-> 实例化对象 -> 属性填充（依赖注入） -> bean初始化（affterPropertiesSet()）-->

AOP -> bean对象（经过AOP则可能为代理对象）

DefaultListableBeanFactory

