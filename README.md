**1.使用JAVA刷OJ的说明**

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

**2.Map基本用法**

+ TreeMap是有序map，HashMap是无序map。

+ Map基本用法

  + 创建map对象``Map<keytype,valuetype> map=new XXXMap<>()``

  + 插入元素`map.put(key,value)`

  + 删除元素`map.remove(key)`或者`map.remove(key,value)`

  + 根据key查询元素`map.get(key)`

  + 修改元素`map.replace(key,value)`

  + 判断元素是否存在`map.containKey(key)`或者`map.containValue(value)`

  + 增强for循环遍历

  + ```java
    for (String key : map.keySet()) {
        System.out.println(key + " ：" + map.get(key));
    }
    ```

  + ```java
    for (Map.Entry<String, String> entry : map.entrySet()) {
        System.out.println(entry.getKey() + " ：" + entry.getValue());
    }
    ```

  + 迭代器遍历

  + ```java
    Iterator<String> iterator = map.keySet().iterator();
    while (iterator.hasNext()) {
        String key = iterator.next();
        System.out.println(key + "　：" + map.get(key));
    }
    ```

  + ```java
    Iterator<Map.Entry<String, String>> iterator = map.entrySet().iterator();
    while (iterator.hasNext()) {
        Map.Entry<String, String> entry = iterator.next();
        System.out.println(entry.getKey() + "　：" + entry.getValue());
    }
    ```