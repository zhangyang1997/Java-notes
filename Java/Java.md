**1.Java开发环境配置**

+ 安装JDK
+ 配置系统环境变量
  + JAVA_HOME 配置JDK安装路径 C:\Program Files\Java\jdk1.8.0_231
  + Path 配置JDK命令文件路径 C:\Program Files\Java\jdk1.8.0_231\bin
  + CLASSPATH 配置类库文件路径  .;C:\Program Files\Java\jdk1.8.0_231\lib
    + 点(.)表示搜索类文件时，先搜索当前目录。

**2.Java程序编译运行流程**

+ .java源代码文件经过javac.exe编译器进行编译生成.class字节码文件。
+ .class字节码文件经过java.exe解释器进行解释运行。

**3.Array类**

+ ``import java.util.Arrays;``
+ Arrays 类是 Java 中提供的一个工具类，在 java.util 包中。该类中包含了一些方法用来直接操作数组，比如可直接实现数组的排序、搜索等。
+ 数组排序：``Arrays.sort(数组名);``
+ 数组转换为字符串：``Array.toString(a);``得到[a[0], a[1], a[2], ..., a[n-1]]

**4.集合类**

+ Collection根接口
  + List子接口，ArrayList实现类，LinkedList实现类
  + Queue子接口，LinkedList实现类
  + Set子接口，HashSet实现类
+ Map根接口
  + HashMap实现类

**5.Java反射机制的功能**

+ 在运行时判断任意一个对象所属的类。
+ 在运行时构造任意一个类的对象。
+ 在运行时判断任意一个类所具有的成员变量和方法。
+ 在运行时调用任意一个对象的方法。

**6.Java注解(Annotation)**

提供一种源程序中的元素关联任何信息和任何元数据的途径和方法。