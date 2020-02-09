**OJ记录**

+ 剑指offer
+ 华为

**使用JAVA刷OJ的说明**

+ 形式

  ```java
  import java.util.*;
  public class Main{
  	public static void main(String[] args){
  		//代码
  	}
  }
  ```

+ 使用Scanner创建标准输入对象，`Scanner sc = new Scanner(System.in);`
+ **输入格式**
  + 判断是否有下一个输入，`while(sc.hasNext());`
  + 输入整数 ，`int a = cin.nextInt();`
  + 输入浮点数，`double t = sc.nextDouble();`
  + 输入字符串，空格或者行为分隔符(不读取分隔符)，`String s = sc.next();`
  + 输入字符串，行为分隔符(会读取换行符)，`String s = sc.nextLine()`
+ **输出格式**
  + `System.out.println()`
  + `System.out.print()`
  + `System.out.printf()`