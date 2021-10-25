## 1.API

### 1.1 概述

API(Application Programming Interface)，应用程序编程接口。

Java API：JDK中提供的各种功能的Java类。这些类将底层的代码实现封装了起来，我们不需要关心这些类是如何实现的，只需要学习这些类如何使用即可，我们可以通过帮助文档来学习这些API如何使用。

如何使用API帮助文档：

​	1、打开帮助文档

​	2、点击显示，找到索引，看到输入框

​	3、你要找谁？在输入框里输入，然后回车

​	4、看包。java.lang下的类不需要导包，其他需要

​	5、看类的解释和说明

​	6、学习构造方法

​	7、使用成员方法

### 1.2 键盘录入字符串

Scanner类：

​	1、next()：遇到了空格, 就不再录入数据了，结束标记：空格、tab键

​	2、nextLine()：可以将数据完整的接收过来，结束标记：回车换行符       

```java
package com.itheima.api;
import java.util.Scanner;

public class Demo1Scanner {
    public static void main(String[] args) {
        // 1. 创建Scanner对象
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入:");
        // 2. 调用nextLine方法接收字符串
        // ctrl + alt + v : 快速生成方法的返回值
        String s = sc.nextLine();

        System.out.println(s);
    }
}
```

```java
package com.itheima.api;
import java.util.Scanner;

public class Demo2Scanner {
    /*
        nextInt和nextLine方法配合使用的时候, nextLine方法就没有键盘录入的机会了
        
        原因：nextInt方法之后在缓冲区留下了“\r”，nextLine方法去缓冲区找数据的时候将“\r”接收，直接结束。

        建议: 今后键盘录入数据的时候, 如果是字符串和整数一起接受, 建议使用next方法接受字符串。
     */
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入整数:");
        int num = sc.nextInt(); // 10 + 回车换行
        System.out.println("请输入字符串:");
        String s = sc.nextLine();

        System.out.println(num);
        System.out.println(s);
    }
}
```

## 2. String类

### 2.1 概述

String 类代表字符串，Java 程序中的所有字符串文字（例如“abc”）都被实现为此类的实例。也就是说，Java 程序中所有的双引号字符串，都是 String 类的对象。

String 类在 java.lang 包下，使用时不需要导包。

注意：

1、字符串不变：字符串的值在创建后不能被更改。

```java
String s1 = "abc";
s1 += "d";
System.out.println(s1); // "abcd"
// 内存中有"abc"，"abcd"两个对象，s1从指向"abc"，改变指向，指向了"abcd"。
```

2、因为String对象是不可变的，所以它们可以被共享。

```java
String s1 = "abc";
String s2 = "abc";
// 内存中只有一个"abc"对象被创建，同时被s1和s2共享。
```

3、`"abc"` 等效于 `char[] data={ 'a' , 'b' , 'c' }` 。

```java
例如：
String str = "abc";
相当于：
char data[] = {'a', 'b', 'c'};
String str = new String(data);
// 字符串效果上相当于字符数组(char[])，但底层原理是字节数组(byte[])
```

### 2.2 构造方法

1、`public String()`：创建一个空白字符串对象，不含有任何内容

2、`public String(char[] chs)`：根据字符数组的内容，来创建字符串对象

3、`public String(byte[] bys)`: 根据字节数组的内容，来创建字符串对象

4、`String s = “abc”;` 直接赋值的方式创建字符串对象，内容就是abc

```java
public static void main(String[] args) {
    // String这个类比较特殊，打印其对象名的时候，不会出现内存地址，而是该对象所记录的真实内容。
    // 创建空白字符串对象
    String s1 = new String();
    System.out.println(s1);

    // 通过字符数组构造
    char[] chs = {'a','b','c'};
    String s2 = new String(chs);
    System.out.println(s2);

    // 通过字节数组构造
    byte[] bys = { 97, 98, 99 };
    String s3 = new String(bys);
    System.out.println(s3);
    
    // 直接赋值
    String s4 = "abc";
    System.out.println(s4);
}
```
### 2.3 字符串对象的创建对比

1、由构造方法创建：

​	通过 new 创建的字符串对象，每一次 new 都会申请一个内存空间，虽然内容相同，但是地址值不同。

2、直接赋值方式创建：

​	以“”方式给出的字符串，只要字符序列相同(顺序和大小写)，无论在程序代码中出现几次，JVM 都只会建立一个 String 对象（地址值相同），并在字符串池中维护。

### 2.4 String常见面试题

```java
// 下列代码的运行结果？
public static void main(String[] args) {
    String s1 = "abc";
    String s2 = "ab";
    String s3 = s2 + "c";
    System.out.println(s1 == s3); // false
	// 原因：当字符串之间使用＋号拼接的时候，系统底层会自动创建一个StringBuilder对象，然后再调用其append方法完成拼接，再调用toString方法转换成String类型，在堆内存中开辟新的内存空间。
    
    String s4 = "abc";
    String s5 = "a" + "b" + "c";
    System.out.println(s4 == s5); // true
    // 原因："a" + "b" + "c"为三个常量拼接，Java存在常量优化机制，在编译的时候，就会将"a" + "b" + "c"拼接成"abc"，s4跟s5都会指向常量池中的地址，结果为true。
}
```

### 2.5 字符串的比较

使用 == 作比较：

​	1、基本数据类型：比较的是具体的数据值

​	2、引用数据类型：比较的是对象地址值

字符串是对象，比较其内容是否相同，需使用“equals()”方法：

​	1、`public boolean equals (Object anObject)`：将此字符串与指定对象进行比较。

​	2、`public boolean equalsIgnoreCase (String anotherString)`：将此字符串与指定对象进行比较，忽略大小写。

```java
public class Demo1Equals {
    public static void main(String[] args) {
        String s1 = "abc";
        String s2 = "ABC";
        String s3 = "abc";

        // equals : 比较字符串内容, 区分大小写
        System.out.println(s1.equals(s2));// false
        System.out.println(s1.equals(s3));// true

        // equalsIgnoreCase : 比较字符串内容, 忽略大小写
        System.out.println(s1.equalsIgnoreCase(s2));// true
    }
}
```

### 2.6 String方法

| 方法名                                                       | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| public boolean equals(Object anObject)                       | 比较字符串的内容，严格区分大小写                             |
| public boolean equalsIgnoreCase(String anotherString)        | 比较字符串的内容，忽略大小写                                 |
| public int length()                                          | 返回此字符串的长度                                           |
| public char charAt(int index)                                | 返回指定索引处的char值                                       |
| public char[] toCharArray()                                  | 将字符串拆分为字符数组后返回                                 |
| public String substring(int beginIndex)                      | 返回从传入的索引处截取到末尾的新字符串                       |
| public String substring(int beginIndex, int endIndex)        | 返回从 [开始,结束) 索引截取的新字符串                        |
| public String replace(CharSequence target, CharSequence replacement) | 将与target匹配的字符串使用replacement字符串替换，返回新字符串 |
| public String[] split(String regex)                          | 根据传入的规则切割字符串，得到字符串数组                     |
| public String concat(String str)                             | 将指定的字符串连接到该字符串的末尾                           |
| public int indexOf(String str)                               | 返回指定子字符串第一次出现在该字符串内的索引                 |

### 2.7 应用

#### 2.7.1 用户登录

需求：已知用户名和密码，请用程序实现模拟用户登录。总共给三次机会，登录之后，给出相应的提示

思路：

​	1、已知用户名和密码，定义两个字符串表示即可

​	2、键盘录入要登录的用户名和密码，用 Scanner 实现

​	3、拿键盘录入的用户名、密码和已知的用户名、密码进行比较，给出相应的提示。

​	4、字符串的内容比较，用equals() 方法实现

​	5、用循环实现多次机会，这里的次数明确，采用for循环实现，并在登录成功的时候，使用break结束循环

```java
import java.util.Scanner;

public class Test1 {
    public static void main(String[] args) {
        // 1. 已知用户名和密码，定义两个字符串表示即可
        String username = "admin";
        String password = "123456";
        // 2. 键盘录入要登录的用户名和密码，用 Scanner 实现
        Scanner sc = new Scanner(System.in);
        // 4. 用循环实现多次机会，这里的次数明确，采用for循环实现
        for(int i = 1; i <= 3; i++){
            System.out.println("请输入用户名:");
            String scUsername = sc.nextLine();
            System.out.println("请输入密码:");
            String scPassword = sc.nextLine();
            // 3. 拿键盘录入的用户名、密码和已知的用户名、密码进行比较，给出相应的提示。
            if(username.equals(scUsername) && password.equals(scPassword)){
                System.out.println("登录成功");
                break;
            }else{
                if(i == 3){
                    System.out.println("您的登录次数已达到今日上限, 请明天再来");
                }else{
                    System.out.println("登录失败,您还剩余" + (3-i) +"次机会");
                }
            }
        }
    }
}
```

#### 2.7.2 遍历字符串

需求：键盘录入一个字符串，使用程序实现在控制台遍历该字符串

思路一：

​	1、键盘录入一个字符串，用 Scanner 实现

​	2、遍历字符串，首先要能够获取到字符串中的每一个字符

​	`public char charAt(int index)`：返回指定索引处的char值。字符串的索引也是从0开始的

​	3、遍历字符串，其次要能够获取到字符串的长度

​	`public int length()`：返回此字符串的长度

​	4、遍历打印

```java
import java.util.Scanner;

public class Test2 {
    public static void main(String[] args) {
        //  1. 键盘录入一个字符串，用 Scanner 实现
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入:");
        String s = sc.nextLine();
        // 2. 遍历字符串，首先要能够获取到字符串中的每一个字符
        for(int i = 0; i < s.length(); i++){
            // i : 字符串的每一个索引
            char c = s.charAt(i);
            System.out.println(c);
        }
    }
}
```

思路二：

​	1、键盘录入一个字符串，用 Scanner 实现

​	2、将字符串拆分为字符数组

​	`public char[] toCharArray( )`：将当前字符串拆分为字符数组并返回

​	3、遍历字符数

```Java
import java.util.Scanner;

public class Test3 {
    public static void main(String[] args) {
        //  1. 键盘录入一个字符串，用 Scanner 实现
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入:");
        String s = sc.nextLine();
        // 2. 将字符串拆分为字符数组
        char[] chars = s.toCharArray();
        // 3. 遍历字符数组
        for (int i = 0; i < chars.length; i++) {
            System.out.println(chars[i]);
        }
    }
}
```

#### 2.7.3 统计字符次数

需求：键盘录入一个字符串，统计字符串中大小写字母及数字字符个数

思路：

​	1、键盘录入一个字符串，用Scanner实现

​	2、定义三个统计变量，初始化值都是0

​	3、遍历字符串，得到每一个字符

​	4、判断该字符属于哪种类型，然后对应类型的统计变量+1

```java
public class StringTest2 {
    public static void main(String[] args) {
        //键盘录入一个字符串数据
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入一个字符串数据：");
        String s = sc.nextLine();
        
        //定义三个统计变量，初始化值都是0
        int bigCount = 0;
        int smallCount = 0;
        int numberCount = 0;
        
        //遍历字符串，得到每一个字符
        for (int x = 0; x < s.length(); x++) {
            char ch = s.charAt(x);
            //拿字符进行判断
            if (ch >= 'A' && ch <= 'Z') {
            	bigCount++;
            } else if (ch >= 'a' && ch <= 'z') {
            	smallCount++;
            } else if (ch >= '0' && ch <= '9') {
            	numberCount++;
            } else {
            	System.out.println("该字符"+ch+"非法");
            }
        }
        
        //输出结果
        System.out.println("大写字符："+bigCount+"个");
        System.out.println("小写字符："+smallCount+"个");
        System.out.println("数字字符："+numberCount+"个");
    }
}
```

#### 2.7.4 字符串截取

需求：以字符串的形式从键盘接受一个手机号，将中间四位号码屏蔽。最终效果为：156****1234

思路：

​	1、键盘录入一个字符串，用 Scanner 实现

​	2、截取字符串前三位

​	`public String substring (int beginIndex, int endIndex)`：返回一个子字符串，从beginIndex到endIndex截取字符串。[beginIndex，endIndex)

​	3、截取字符串后四位

​	`public String substring (int beginIndex)`：返回一个子字符串，从beginIndex开始截取字符串到字符串结尾

​	4、将截取后的两个字符串，中间加上****进行拼接，输出结果

```java
import java.util.Scanner;

public class Test5 {
    public static void main(String[] args) {
        // 1. 键盘录入一个字符串，用 Scanner 实现
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入手机号:");
        String telString = sc.nextLine();
        // 2. 截取字符串前三位
        String start = telString.substring(0,3);
        // 3. 截取字符串后四位
        String end = telString.substring(7);
        // 4. 将截取后的两个字符串，中间加上****进行拼接，输出结果
        System.out.println(start + "****" + end);
    }
}
```

#### 2.7.5 字符串替换

需求：键盘录入一个 字符串，如果字符串中包含（TMD），则使用***替换

思路：

​	1、键盘录入一个字符串，用 Scanner 实现

​	2、替换敏感词 

​	`public String replace (CharSequence target, CharSequence replacement)`：将与target匹配的字符串使用replacement字符串替换，返回新的字符串

​	3、输出结果

```java
import java.util.Scanner;

public class Test6 {
    public static void main(String[] args) {
        // 1. 键盘录入一个字符串，用 Scanner 实现
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入:");
        String s = sc.nextLine();
        // 2. 替换敏感词
        String result = s.replace("TMD","***");
        // 3. 输出结果
        System.out.println(result);
    }
}
```

#### 2.7.6 切割字符串

需求：以字符串的形式从键盘录入学生信息，例如：“张三 , 23” 从该字符串中切割出有效数据，封装为Student学生对象

思路：

​	1、编写Student类，用于封装数据

​	2、键盘录入一个字符串，用 Scanner 实现

​	3、根据逗号切割字符串，得到（张三）（23）

​	`public String[] split(String regex)`：将此字符串按照给定的regex（规则）拆分为字符串数组并返回

​	4、从得到的字符串数组中取出元素内容，通过Student类的有参构造方法封装为对象

​	5、调用对象getXxx方法，取出数据并打印

```java
import com.bjut.domain.Student;
import java.util.Scanner;

public class Test7 {
    public static void main(String[] args) {
        // 2. 键盘录入一个字符串，用 Scanner 实现
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入学生信息:");
        String stuInfo = sc.nextLine();

        // 3. 根据逗号切割字符串，得到（张三）（23）
        String[] sArr = stuInfo.split(",");
        
        // 4. 从得到的字符串数组中取出元素内容，通过Student类的有参构造方法封装为对象
        Student stu = new Student(sArr[0],sArr[1]);

        // 5. 调用对象getXxx方法，取出数据并打印。
        System.out.println(stu.getName() + "..." + stu.getAge());
    }
}
```

#### 2.7.7 拼接字符串

需求：定义一个方法，把int数组中的数据按照指定的格式拼接成一个字符串返回。例如，数组为int[] arr = {1, 2, 3}，执行方法后的输出结果为：[1, 2, 3]

思路：

​	1、定义一个int类型的数组，并静态初始化

​	2、写方法，用于把数组中的元素按照指定的格式拼接成一个字符串。返回值类型：String，参数列表：int[] arr

​	3、遍历数组，并拼接字符串

​	`public String concat (String str)`：将指定的字符串连接到该字符串的末尾

​	4、调用方法，用一个变量接受结果并输出

```java
public class StringTest1 {
    public static void main(String[] args) {
        //定义一个int类型的数组
        int[] arr = {1, 2, 3};
        
        //调用方法
        String s = arrayToString(arr);
        
        //输出结果
        System.out.println("s:" + s);
    }

    public static String arrayToString(int[] arr) {
        // 创建字符串s
        String s = "[";
        
        // 遍历数组，并拼接字符串
        for (int x = 0; x < arr.length; x++) {
            if (x == arr.length ‐ 1) {
            	s = s.concat(arr[x] + "]");
            } else {
            	s = s.concat(arr[x] + ", ");
            }
        }
        return s;
    }
}
```

## 3. StringBuilder类

### 3.1 概述

StringBuilder 是一个可变的字符串类，我们可以把它看成是一个容器，这里的可变指的是 StringBuilder 对象中的内容是可变的。该对象在拼接时不会创建新的对象。

StringBuilder类和String类的区别：

​	1、String类：内容是不可变的

​	2、StringBuilder类：内容是可变的

### 3.2 构造方法

| 方法名                           | 说明                                       |
| -------------------------------- | ------------------------------------------ |
| public StringBuilder()           | 创建一个空白可变字符串对象，不含有任何内容 |
| public StringBuilder(String str) | 根据字符串的内容，来创建可变字符串对象     |

```java
public class StringBuilderDemo01 {
    public static void main(String[] args) {
        //public StringBuilder()：创建一个空白可变字符串对象，不含有任何内容
        StringBuilder sb = new StringBuilder();
        System.out.println("sb:" + sb);
        System.out.println("sb.length():" + sb.length());// 0

        //public StringBuilder(String str)：根据字符串的内容，来创建可变字符串对象
        StringBuilder sb2 = new StringBuilder("hello");
        System.out.println("sb2:" + sb2);
        System.out.println("sb2.length():" + sb2.length());// 5
    }
}
```

### 3.3 StringBuilder方法

| 方法名                                | 说明                                |
| ------------------------------------- | ----------------------------------- |
| public StringBuilder append(任意类型) | 添加数据，并返回对象本身            |
| public StringBuilder reverse()        | 返回相反的字符序列                  |
| public String toString()              | 把 StringBuilder 类转换为 String 类 |

```java
public class StringBuilderDemo01 {
    public static void main(String[] args) {
        //创建对象
        StringBuilder sb = new StringBuilder();

        //public StringBuilder append(任意类型)：添加数据，并返回对象本身
//        StringBuilder sb2 = sb.append("hello");
//
//        System.out.println("sb:" + sb);// hello
//        System.out.println("sb2:" + sb2);// hello
//        System.out.println(sb == sb2);// true

//        sb.append("hello");
//        sb.append("world");
//        sb.append("java");
//        sb.append(100);

        //链式编程。是对象就可以调用方法
        sb.append("hello").append("world").append("java").append(100);

        System.out.println("sb:" + sb);

        //public StringBuilder reverse()：返回相反的字符序列
        sb.reverse();
        System.out.println("sb:" + sb);
    }
}
```

### 3.4 StringBuilder和String相互转换

StringBuilder转换为String：

​	`public String toString()`：通过 toString() 就可以实现把 StringBuilder 转换为 String

String转换为StringBuilder：

​	`	public StringBuilder(String s)`：通过构造方法就可以实现把 String 转换为 StringBuilder

```java
public class StringBuilderDemo02 {
    public static void main(String[] args) {
        //StringBuilder 转换为 String
        StringBuilder sb = new StringBuilder();
        sb.append("hello");

        //String s = sb; //这个是错误的做法
        //public String toString()：通过 toString() 就可以实现把 StringBuilder 转换为 String
        String s = sb.toString();
        System.out.println(s);
        

        //String 转换为 StringBuilder
        String s = "hello";

        //StringBuilder sb = s; //这个是错误的做法
        //public StringBuilder(String s)：通过构造方法就可以实现把 String 转换为 StringBuilder
        StringBuilder sb = new StringBuilder(s);
        System.out.println(sb);
    }
}
```

### 3.5 拼接字符串

需求：定义一个方法，把 int 数组中的数据按照指定的格式拼接成一个字符串返回，调用该方法，并在控制台输出结果。例如，数组为int[] arr = {1,2,3}; ，执行方法后的输出结果为：[1, 2, 3]

思路：

​	1、定义一个 int 类型的数组，用静态初始化完成数组元素的初始化

​	2、定义一个方法，用于把 int 数组中的数据按照指定格式拼接成一个字符串返回。

​		返回值类型 String，参数列表 int[] arr

​	3、在方法中用 StringBuilder 按照要求进行拼接，并把结果转成 String 返回

​	4、调用方法，用一个变量接收结果

​	5、输出结果

```java
public class StringBuilderTest01 {
    public static void main(String[] args) {
        //定义一个 int 类型的数组，用静态初始化完成数组元素的初始化
        int[] arr = {1, 2, 3};

        //调用方法，用一个变量接收结果
        String s = arrayToString(arr);

        //输出结果
        System.out.println("s:" + s);
    }

    //定义一个方法，用于把 int 数组中的数据按照指定格式拼接成一个字符串返回
    /*
        两个明确：
        
            返回值类型：String
            参数：int[] arr
     */
    public static String arrayToString(int[] arr) {
        //在方法中用 StringBuilder 按照要求进行拼接，并把结果转成 String 返回
        StringBuilder sb = new StringBuilder();

        sb.append("[");

        for(int i=0; i<arr.length; i++) {
            if(i == arr.length-1) {
                sb.append(arr[i]).append("]");
            } else {
                sb.append(arr[i]).append(", ");
            }
        }
        String s = sb.toString();
        return  s;
    }
}
```

### 3.6 字符串反转

需求：定义一个方法，实现字符串反转。键盘录入一个字符串，调用该方法后，在控制台输出结果。例如：键盘录入abc，输出：cba

思路：

​	1、键盘录入一个字符串，用 Scanner 实现

​	2、定义一个方法，实现字符串反转

​		返回值类型 String，参数 String s

​	3、在方法中用 StringBuilder 实现字符串的反转，并把结果转成 String 返回

​	4、调用方法，用一个变量接收结果

​	5、输出结果

```java
public class Test01 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入字符串：");
        String s = sc.nextLine();

        String s2 = myReverse(s);
        System.out.println(s2);
    }

    public static String myReverse(String s){

//        StringBuilder sb = new StringBuilder(s);
//        sb.reverse();
//        String s1 = sb.toString();
//        return s1;

        // 匿名对象：没有变量名的对象。创建对象时，只有创建对象的语句，却没有把对象地址值赋值给某个变量。
        return new StringBuilder(s).reverse().toString();
    }
}
```

