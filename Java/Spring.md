**1.IoC概念**

+ Inversion of Control，控制反转，依赖注入(Dependency Injection)。
+ 控制：控制对象的创建及销毁（生命周期）。
+ 反转：将对象的控制权交给IoC容器。
+ bean：对象
+ 约定：
  + 所有Bean的生命周期交由IoC容器管理。
  + 所有被依赖的Bean通过构造方法执行注入。
  + 被依赖的Bean需要优先创建。
+ Ioc容器功能和实现
  + 实例化bean。
  + 每一个bean要产生一个唯一的id，与之对应。
  + getBean方法，输入一个beanid，返回bean。
  + setBean方法，输入class，beanId，paraBeanIds(要创建bean的class的构造方法依赖的beanId)，创建一个bean。
    + 组装构造方法所需要的参数值。
    + 调用构造方法实例化bean。
    + 将实例化的bean放入beans。
+ IoC优点
  + 所有依赖关系被集中统一管理。
  + 每个类只需要关注自己的业务逻辑。
  + 容易修改依赖关系。

