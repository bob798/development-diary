

# Spring Context

## context是什么

提供进程运行时需要的一些数据及保存运行时的一些数据。

既：context可以理解为程序运行时需要的数据结构的抽象

## spring context 是什么

spring 应用上下文

## spring context 包含什么

- ioc容器、监听器
- BeanDefinitionRegistry
- AnnotatedBeanDefinitionReader

## spring context 的生命周期

### 初始化和启动

#### spring  context 初始化-准备材料

创建BeanFactory、注册BeanFactoryPostProcessor

#### spring context 启动

创建对象

### 运行

spring context提供它的服务

### 关闭/销毁

不需要使用srping context，既 关闭

## 总结



## 参考

https://juejin.im/post/5d61556b5188256dad113353

