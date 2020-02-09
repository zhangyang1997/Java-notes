#### 1.汽水瓶

**题目描述**

“某商店规定：三个空汽水瓶可以换一瓶汽水。小张手上有十个空汽水瓶，她最多可以换多少瓶汽水喝？”答案是5瓶，方法如下：先用9个空瓶子换3瓶汽水，喝掉3瓶满的，喝完以后4个空瓶子，用3个再换一瓶，喝掉这瓶满的，这时候剩2个空瓶子。然后你让老板先借给你一瓶汽水，喝掉这瓶满的，喝完以后用3个空瓶子换一瓶满的还给老板。如果小张手上有n个空汽水瓶，最多可以换多少瓶汽水喝？

**输入描述**

```
输入文件最多包含10组测试数据，每个数据占一行，仅包含一个正整数n（1<=n<=100），表示小张手上的空汽水瓶数。n=0表示输入结束，你的程序不应当处理这一行。
```

**输出描述**

```
对于每组测试数据，输出一行，表示最多可以喝的汽水瓶数。如果一瓶也喝不到，输出0。
```

**测试用例**

```
input
3
10
81
0

output
1
5
40
```

**方法**

DFS或者找规律

**代码**

```java
import java.util.*;
public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in); 
        int n;
        while(sc.hasNext()){
            n = sc.nextInt();
            //System.out.println(dfs(n));//dfs
            System.out.println(n/2);//找规律
        }
    }
    public static int dfs(int n){
        if(n <= 1){
            return 0;
        }else if(n == 2 || n == 3){
            return 1;
        }else{
            return n / 3 + dfs(n / 3 + n % 3);
        }
    }
}
```

#### 2.明明的随机数

**题目描述**

明明想在学校中请一些同学一起做一项问卷调查，为了实验的客观性，他先用计算机生成了N个1到1000之间的随机整数（N≤1000），对于其中重复的数字，只保留一个，把其余相同的数去掉，不同的数对应着不同的学生的学号。然后再把这些数从小到大排序，按照排好的顺序去找同学做调查。请你协助明明完成“去重”与“排序”的工作(同一个测试用例里可能会有多组数据，希望大家能正确处理)。

##### **输入描述:**

```
输入多行，先输入随机整数的个数，再输入相应个数的整数
```

##### **输出描述:**

```
返回多行，处理后的结果
```

**方法**

哈希排序去重

**代码**

```java
import java.util.*;
public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        while(sc.hasNext()){
            int n = sc.nextInt();
            int[] a = new int[1001];
            for(int i = 0; i < n; i++){
                a[sc.nextInt()] = 1;
            }
            for(int i = 0; i < 1001; i++){
                if(a[i] == 1){
                    System.out.println(i);
                }
            }
        }
    }
}
```

#### 3.进制转换

**题目描述**

输入一个十六进制的数值字符串。

输出该数值的十进制字符串。

**代码**

```java
import java.util.*;
public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        while(sc.hasNext()){
            String s = sc.next();
            char[] ch = s.toCharArray();
            int sum = 0;
            for(int i = 2; i < ch.length; i++){
                if(ch[i] >= 'A' && ch[i] <= 'F'){
                    sum += (ch[i] - 'A' + 10) * Math.pow(16, (ch.length - i - 1));
                }else{
                    sum += (ch[i] - '0') * Math.pow(16, (ch.length - i - 1));
                }
            }
            System.out.println(sum);
        }
    }
}
```

#### 4.最高分是多少

老师想知道从某某同学当中，分数最高的是多少，现在请你编程模拟老师的询问。当然，老师有时候需要更新某位同学的成绩.

##### **输入描述:**

```
输入包括多组测试数据。
每组输入第一行是两个正整数N和M（0 < N <= 30000,0 < M < 5000）,分别代表学生的数目和操作的数目。
学生ID编号从1编到N。
第二行包含N个整数，代表这N个学生的初始成绩，其中第i个数代表ID为i的学生的成绩
接下来又M行，每一行有一个字符C（只取‘Q’或‘U’），和两个正整数A,B,当C为'Q'的时候, 表示这是一条询问操作，他询问ID从A到B（包括A,B）的学生当中，成绩最高的是多少
当C为‘U’的时候，表示这是一条更新操作，要求把ID为A的学生的成绩更改为B。
```

##### **输出描述:**

```
对于每一次询问操作，在一行里面输出最高成绩.
```

##### 测试用例

```
Input:
5 7
1 2 3 4 5
Q 1 5
U 3 6
Q 3 4
Q 4 5
U 4 5
U 2 9
Q 1 5

Output:
5
6
5
9
```

**代码**

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        while (sc.hasNext()) {
            int n1 = sc.nextInt();
            int n2 = sc.nextInt();
            int[] a = new int[n1];  
            for (int i = 0; i < n1; i++) {
                a[i] = sc.nextInt();
            }
            for (int i = 0; i < n2; i++) {
                String op = sc.next();
                char chop = op.charAt(0);
                int first = sc.nextInt();
                int second = sc.nextInt();
                if (chop == 'Q') {
                    System.out.println(max(a, first - 1, second - 1));
                }
                if (chop == 'U') {
                    a[first - 1] = second;
                }
            }
        }
        sc.close();
    }

    public static int max(int[] a, int first, int second) {
        int left, right;
        if (first <= second) {
            left = first;
            right = second;
        } else {
            left = second;
            right = first;
        }  
        int max = a[left];
        for (int i = left; i <= right; i++) {
            if (max < a[i]) {
                max = a[i];
            }
        }
        return max;
    }
}
```

#### 5.简单错误记录

开发一个简单错误记录功能小模块，能够记录出错的代码所在的文件名称和行号。
处理:
1.记录最多8条错误记录，对相同的错误记录(即文件名称和行号完全匹配)只记录一条，错误计数增加；(文件所在的目录不同，文件名和行号相同也要合并)
2.超过16个字符的文件名称，只记录文件的最后有效16个字符；(如果文件名不同，而只是文件名的后16个字符和行号相同，也不要合并)
3.输入的文件可能带路径，记录文件名称不能带路径

##### **输入描述:**

```
一行或多行字符串。每行包括带路径文件名称，行号，以空格隔开。
    文件路径为windows格式
    如：E:\V1R2\product\fpgadrive.c 1325
```

##### **输出描述:**

```
将所有的记录统计并将结果输出，格式：文件名代码行数数目，一个空格隔开，如: fpgadrive.c 1325 1 
    结果根据数目从多到少排序，数目相同的情况下，按照输入第一次出现顺序排序。
    如果超过8条记录，则只输出前8条记录.
    如果文件名的长度超过16个字符，则只输出后16个字符
```

**测试用例**

```
Input:
E:\V1R2\product\fpgadrive.c 1325

Output:
fpgadrive.c 1325 1
```

**方法**

LinkedHashMap排序去重。

**代码**

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Map<String, Integer> map = new LinkedHashMap<>();
        while (sc.hasNext()) {
            String s = sc.nextLine();
            int begin = s.lastIndexOf('\\');
            String key = s.substring(begin + 1, s.length());
            if (map.containsKey(key)) {
                map.put(key, map.get(key) + 1);
            } else {
                map.put(key, 1);
            }
        }
        List<Map.Entry<String, Integer>> list = new ArrayList<>(map.entrySet());
        Collections.sort(list, new Comparator<Map.Entry<String, Integer>>() {
            @Override
            public int compare(Map.Entry<String, Integer> o1, Map.Entry<String, Integer> o2) {
                return -o1.getValue().compareTo(o2.getValue());
            }
        });
        if (list.size() < 8) {
            for (Map.Entry<String, Integer> m : list) {
                String[] s = m.getKey().split(" ");
                if (s[0].length() > 16) {
                    String temp1 = s[0].substring(s[0].length() - 16);
                    String temp2 = s[1];
                    System.out.println(temp1 + " "+ temp2 + " "+ m.getValue());
                } else {
                    System.out.println(m.getKey() + " " + m.getValue());
                } 
            }
        } else {
            for (int i = 0; i < 8; i++) {
                String[] s = list.get(i).getKey().split(" ");
                if (s[0].length() > 16) {
                    String temp1 = s[0].substring(s[0].length() - 16);
                    String temp2 = s[1];
                    System.out.println(temp1 + " "+ temp2 + " "+ list.get(i).getValue());
                } else {
                    System.out.println(list.get(i).getKey() + " " + list.get(i).getValue());
                }
            }
        } 
        sc.close();
    }
}
```

#### 6.扑克牌大小

扑克牌游戏大家应该都比较熟悉了，一副牌由54张组成，含3~A，2各4张，小王1张，大王1张。牌面从小到大用如下字符和字符串表示（其中，小写joker表示小王，大写JOKER表示大王）:)
3 4 5 6 7 8 9 10 J Q K A 2 joker JOKER
输入两手牌，两手牌之间用“-”连接，每手牌的每张牌以空格分隔，“-”两边没有空格，如：4 4 4 4-joker JOKER
请比较两手牌大小，输出较大的牌，如果不存在比较关系则输出ERROR

基本规则：
（1）输入每手牌可能是个子，对子，顺子（连续5张），三个，炸弹（四个）和对王中的一种，不存在其他情况，由输入保证两手牌都是合法的，顺子已经从小到大排列；
（2）除了炸弹和对王可以和所有牌比较之外，其他类型的牌只能跟相同类型的存在比较关系（如，对子跟对子比较，三个跟三个比较），不考虑拆牌情况（如：将对子拆分成个子）
（3）大小规则跟大家平时了解的常见规则相同，个子，对子，三个比较牌面大小；顺子比较最小牌大小；炸弹大于前面所有的牌，炸弹之间比较牌面大小；对王是最大的牌；
（4）输入的两手牌不会出现相等的情况。

答案提示：
（1）除了炸弹和对王之外，其他必须同类型比较。
（2）输入已经保证合法性，不用检查输入是否是合法的牌。
（3）输入的顺子已经经过从小到大排序，因此不用再排序了.

##### **输入描述:**

```
输入两手牌，两手牌之间用“-”连接，每手牌的每张牌以空格分隔，“-”两边没有空格，如4 4 4 4-joker JOKER。
```

##### **输出描述:**

```
输出两手牌中较大的那手，不含连接符，扑克牌顺序不变，仍以空格隔开；如果不存在比较关系则输出ERROR。
```

##### **测试用例**

```
Input:
4 4 4 4-joker JOKER

Output:
joker JOKER
```

**方法**

1.存在王炸，输出王炸。

2.其中一边是普通炸弹，另一边是非炸弹，输出炸弹。

3.两边是同类，输出大的手牌。

4.其他情况输出"ERROR"。

**代码**

```
import java.util.*;

public class Main {
    public static void main(String[] args) {
        String poker = "345678910JQKA2jokerJOKER";
        Scanner sc = new Scanner(System.in);
        while (sc.hasNext()) {
            String s = sc.nextLine();
            if (s.contains("joker JOKER")) {
                System.out.println("joker JOKER");
            } else {
                String[] str = s.split("-");
                String[] left = str[0].split(" ");
                String[] right = str[1].split(" ");
                if (left.length == 4 && right.length != 4) {
                    System.out.println(str[0]);
                } else if (left.length != 4 && right.length == 4) {
                    System.out.println(str[1]);
                } else if (left.length == right.length) {
                    String larger = poker.indexOf(left[0]) > poker.indexOf(right[0]) ? str[0] : str[1];
                    System.out.println(larger);
                }else{
                    System.out.println("ERROR");
                }
            }
        }
        sc.close();
    }
}
```

