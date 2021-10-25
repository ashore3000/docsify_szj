# Java概述

Java跨平台原理：

Java程序执行时，Java编译器先将Java源程序(java文件)编译成与平台无关的字节码文件(class文件)，然后由Java虚拟机（JVM）对字节码文件解释执行。实现Java跨平台，只需在不同的操作系统下安装不同版本的 JVM 。

JRE 和 JDK：

JVM（Java Virtual Machine），Java虚拟机，我们编写的Java代码，都运行在 JVM 之上。

JRE（Java Runtime Environment），Java运行环境，包含了 JVM 和 Java 的核心类库（Java API）。

JDK（Java Development Kit），Java软件开发工具包，包含了 JRE 和开发工具（编译、运行工具）。

JDK安装目录：

| 目录名称 | 说明                                             |
| -------- | ------------------------------------------------ |
| bin      | 存放JDK的各种工具命令。javac和java就放在这个目录 |
| conf     | 存放JDK的相关配置文件                            |
| include  | 存放一些平台特定的头文件                         |
| jmods    | 存放JDK的各种模块                                |
| legal    | 存放JDK的各模块的授权文档                        |
| lib      | 存放JDK工具的一些补充JAR包                       |

常用DOS命令：

| 操作               | 说明                            |
| ------------------ | ------------------------------- |
| 盘符名称:          | 盘符切换。E:回车，表示切换到E盘 |
| dir                | 查看当前路径下的内容            |
| cd 目录            | 进入单级目录 cd itheima         |
| cd ..              | 回退到上一级目录                |
| cd 目录1\目录2\... | 进入多级目录 cd itheima\JavaSE  |
| cd \               | 回退到盘符目录                  |
| cls                | 清屏                            |
| exit               | 退出命令提示符窗口              |

HelloWorld程序执行过程：

~~~java
//1. 编写
public class HelloWorld {
	public static void main(String[] args) {
		System.out.println("HelloWorld");
	}
}

//打开命令行窗口，将目录切换至java文件所在目录，编译java文件生成class文件，运行class文件。
//2. 编译
//javac 文件名.java
javac HelloWorld.java
    
//3. 运行
//java 类名
java HelloWorld
~~~

# 数据类型

> 计算机是可以用来存储数据的，但是无论是内存还是硬盘，计算机存储设备的最小信息单元叫“位（bit）”，又称“比特位”，通常用”b”表示。而计算机中最基本的存储单元叫“字节（byte）”，通常用大写字母”B”表示，字节是由连续的8个位组成。
>
> 1B（字节） = 8bit、1KB = 1024B、1MB = 1024KB、1GB = 1024MB、1TB = 1024GB

Java是一个强类型语言，Java中的数据必须明确数据类型。数据类型分类：

​	1、基本数据类型：整数、浮点数、字符、布尔。

​	2、引用数据类型：类、数组、接口。

基本数据类型：共四类八种。

| 数据类型     | 关键字         | 内存占用 | 取值范围                 |
| ------------ | -------------- | -------- | ------------------------ |
| 字节型       | byte           | 1 byte   | -128 ~ 127               |
| 短整型       | short          | 2 byte   | -32768 ~ 32767           |
| 整型         | int（默认）    | 4 byte   | -2的31次方 ~ 2的31次方-1 |
| 长整型       | long           | 8 byte   | -2的63次方 ~ 2的63次方-1 |
| 单精度浮点数 | float          | 4 byte   | 1.4013E-45 ~ 3.4028E+38  |
| 双精度浮点数 | double（默认） | 8 byte   | 4.9E-324 ~ 1.7977E+308   |
| 字符型       | char           | 2 byte   | 0 ~ 65535                |
| 布尔型       | boolean        | 1 byte   | true，false              |

# 常量

| 类型       | 含义                                         | 数据举例                 |
| ---------- | -------------------------------------------- | ------------------------ |
| 整数常量   | 所有的整数                                   | 0，1，567，-9            |
| 小数常量   | 所有的小数                                   | 0.0， -0.1， 2.55        |
| 字符常量   | 单引号括起来的一个字符                       | 'a' ， ' '， '好'        |
| 字符串常量 | 双引号括起来的多个字符（0个、一个或多个）    | "A" ，"Hi" ，"你好" ，"" |
| 布尔常量   | 布尔值，表示真假，只有两个值                 | true ， false            |
| 空常量     | 一个特殊的值，空值（不能用输出语句直接输出） | null                     |

# 变量

变量的定义格式：

```java
//1. 声明变量并赋值
int age = 18;

//2. 先声明，后赋值（使用前赋值即可）
double money;
money = 55.5;

//3. 在同一行定义多个同一种数据类型的变量，中间使用逗号隔开。
//定义int类型的变量a和b
int a = 10, b = 20; 

//声明int类型的变量c和d
int c,d; 
c = 30;
d = 40;
```

注意事项：

1、在同一对花括号中，变量名不能重复。

2、变量在使用之前，必须初始化（赋值）。

3、定义long类型的变量时，需要在整数的后面加L（大小写均可，建议大写）。因为整数默认是int类型，整数太大可能超出int范围。

4、定义float类型的变量时，需要在小数的后面加F（大小写均可，建议大写）。因为浮点数的默认类型是double， double的取值范围是大于float的，类型不兼容。

```java
float a = 10.2; // 报错：从double转换到float可能会有损失
long b = 100; // 不报错
```

# 键盘录入

```java
//1. 导包
// Scanner 类在java.util包下，需要将该类导入。导包的语句需要定义在类的上面
import java.util.Scanner; 

//2. 创建Scanner对象
// System.in 系统输入指的是通过键盘录入数据
Scanner sc = new Scanner(System.in); 

//3. 接收数据
// 表示将键盘录入的值作为int数返回
int i = sc.nextInt(); 
```

# 书写规范

标识符是用户编程时使用的名字，用于给类、方法、变量、常量等命名。

命名规则：

​	1、标识符可以包含英文字母26个（区分大小写）、0-9数字、$（美元符号）和 _（下划线）。

​	2、标识符不能以数字开头。

​	3、标识符不能是关键字。

命名规范：

​	1、类名规范：首字母大写，后面每个单词首字母大写（大驼峰式）。

​	2、方法名规范： 首字母小写，后面每个单词首字母大写（小驼峰式）。

​	3、变量名规范：全部小写。

另外，标识符的命名最好可以做到见名知意。例如：username、studentNumber等。

# 类型转换

## 隐式转换

把一个表示数据范围小的数值或者变量赋值给另一个表示数据范围大的变量。该转换自动进行。

```java
double num = 10;
System.out.println(num); //10.0
```

<img src="https://gitee.com/sunzhijie28/img/raw/master/img/20211017105747.png" alt="image-20211017104522999" style="zoom:67%;" />

## 强制转换

把一个表示数据范围大的数值或者变量赋值给另一个表示数据范围小的变量。非自动进行。

```java
//格式
目标数据类型 变量名 = (目标数据类型)值或者变量;

double num1 = 5.5;
int num2 = (int) num1;
System.out.println(num2); //5（小数位直接舍弃）
```

注意事项：

1、整数默认是int类型，byte、short和char类型数据参与运算均会自动转换为int类型。

```java
byte b1 = 10;
byte b2 = 20;
byte b3 = b1 + b2; //报错。b1和b2会自动转换为int类型，计算结果为int，int赋值给byte需要强制类型转换
// 修改方法：
int b3 = b1 + b2;
byte b3 = (byte) (b1 + b2);
```

2、boolean类型不能与其他基本数据类型相互转换。

3、常量优化机制：编译时，整数常量的计算会直接算出结果，并自动判断该结果是否在byte取值范围内，超出范围则编译失败。

```java
byte a = 3;
byte b = 4;
byte c = a + b; //错误
byte d = 3 + 4; //正确
```

# 运算符

## 算术运算符

| +、-、*、/（相除取商）、%（相除取余数）、++、-- |
| :---------------------------------------------- |

注意事项：

1、++a、a++的区别

```java
int a = 1;
int b = ++a; //先计算后赋值。b = 2
int b = a++; //先赋值后计算。b = 1
```

2、char类型参与算术运算，使用的是计算机底层对应的十进制数值。 'a' --> 97、'A' --> 65、'0' --> 48

3、整个表达式的类型自动提升到与表达式中最高等级的操作数相同的类型。

~~~java
int num1 = 10;
double num2 = 20.0;
double num3 = num1 + num2; //num1自动提升为double类型
~~~

4、“ + ”的运算过程中出现了字符串，“ + ”变为连接运算符。当连续进行“+”操作时，从左到右逐个执行。

~~~java
System.out.println(1 + 99 + "年黑马");            // 输出：100年黑马
System.out.println(1 + 2 + "itheima" + 3 + 4);   // 输出：3itheima34
System.out.println(1 + 2 + "itheima" + (3 + 4)); // 输出：3itheima7
~~~

应用：

```java
/*
	需求：键盘录入一个三位数，将其拆分为个位，十位，百位，打印在控制台。
*/
public static void main(String[] args) {
    // 1：使用Scanner键盘录入一个三位数
    Scanner sc = new Scanner(System.in);
    System.out.println("请输入一个三位数");
    int num = sc.nextInt();

    // 2：个位的计算：数值 % 10
    int ge = num % 10;		

    // 3：十位的计算：数值 / 10 % 10
    int shi = num / 10 % 10;	

    // 4：百位的计算：数值 / 100
    int bai = num / 100;

    // 5：将个位, 十位, 百位拼接上正确的字符串, 打印即可
    System.out.println("整数" + num + "个位为:" + ge);
    System.out.println("整数" + num + "十位为:" + shi);
    System.out.println("整数" + num + "百位为:" + bai);	
}
```

## 赋值运算符

| =、+=、-=、*=、/=、%= |
| --------------------- |

注意事项：

1、表达式左边必须是可修改的，不能是常量。

2、扩展的赋值运算符隐含了强制类型转换。

~~~java
short s = 10;
s = s + 10; //报错
s += 10; //20。相当于 s = (short) (s + 10);
~~~

## 关系运算符

| ==、!=、>、>=、<、<= |
| -------------------- |

注意事项：

1、关系运算符的结果都是boolean类型，即true / false。可以将关系运算结果赋值给boolean型变量。

```java
int a = 10;
int b = 20;

boolean flag = a > b;
System.out.println(flag); //false
```

2、"=="是判断是否相等的关系，"="是赋值。

## 逻辑运算符

| & 逻辑与、\|逻辑或、^ 逻辑异或、! 逻辑非、&& 短路与、\|\|短路或 |
| ------------------------------------------------------------ |

注意事项：

1、逻辑与&、逻辑或|，无论左边真假，右边都执行。

2、短路与&&，左边为真，右边执行；左边为假，右边不执行。

3、短路或||，左边为假，右边执行；左边为真，右边不执行。

~~~java
int x = 3;
int y = 4;
System.out.println((x++ > 4) & (y++ > 5)); //x = 4, y = 5
System.out.println((x++ > 4) && (y++ > 5)); //x = 4, y = 4
~~~

## 三元运算符

~~~java
关系表达式 ? 表达式1 : 表达式2;
//表达式为true，执行1，为false执行2
~~~

# 判断语句

## if语句

~~~java
if (关系表达式) {
    语句体;	
}
~~~

## if...else语句

~~~java
if (关系表达式) {
    语句体1;	
} else {
    语句体2;	
}
~~~

## if...else if...else语句

~~~java
if (关系表达式1) {
    语句体1;	
} else if (关系表达式2) {
    语句体2;	
} 
…
else {
    语句体n+1;
}
~~~

# switch语句

```java
switch (表达式) {
	case 1:
		语句体1;
		break;
	case 2:
		语句体2;
		break;
	...
	default:
		语句体n+1;
		break;
}
//表达式类型：整数表达式（int、Integer包装类型），byte、short、char（可以隐式转换为int类型），枚举常量，String类型。
```

case穿透：

如果switch语句中，case省略了break语句，就会开始case穿透。当开始case穿透，后续的case就不会具有匹配效果，内部的语句都会执行，直到看见break，或者将整体switch语句执行完毕，才会结束。

```java
/*
	需求：键盘录入星期数，输出工作日、休息日 (1-5)工作日，(6-7)休息日。
*/
public static void main(String[] args){
		Scanner sc = new Scanner(System.in);
		System.out.println("请输入星期数:");
		int week = sc.nextInt();
		switch(week){
			case 1:
			case 2:
			case 3:
			case 4:
			case 5:
				System.out.println("工作日");
				break;
			case 6:
			case 7:
				System.out.println("休息日");
				break;
			default:
				System.out.println("您的输入有误");
				break;
		}
	}	
}
```

# 循环语句

## for循环

```java
for (初始化语句; 条件判断语句; 条件控制语句) {
	循环体语句;
}
```

应用：

```java
public class ForTest01 {
    /*
		需求：在控制台输出1-5和5-1的数据。
	*/
    public static void main(String[] args) {
		//1-5
        for(int i=1; i<=5; i++) {
			System.out.println(i);
		}
		System.out.println("--------");
		//5-1
		for(int i=5; i>=1; i--) {
			System.out.println(i);
		}
    }
}
```

```java
public class ForTest03 {
    /*
		需求：求1-100之间的偶数和，并把求和结果在控制台输出。
	*/	
    public static void main(String[] args) {
		//求和的最终结果必须保存起来，需要定义一个变量，用于保存求和的结果，初始值为0
		int sum = 0;
		for(int i=1; i<=100; i++) {
			//判断是否是偶数
			if(i%2 == 0) {
				sum += i;
			}
		}
		System.out.println("1-100之间的偶数和是：" + sum);
    }
}
```

```java
public class ForTest04 {
    /*
        需求：在控制台输出所有的“水仙花数”。
        水仙花数，指的是一个三位数，个位、十位、百位的数字立方和等于原数，如153, 3*3*3 + 5*5*5 + 1*1*1 = 153。
    */
    public static void main(String[] args) {
		//输出所有的水仙花数必然要使用到循环，遍历所有的三位数，三位数从100开始，到999结束
		for(int i=100; i<1000; i++) {
			//在计算之前获取三位数中每个位上的值
			int ge = i % 10;
			int shi = i / 10 % 10;
			int bai = i / 100 % 10;
			
			//判定条件是将三位数中的每个数值取出来，计算立方和后与原始数字比较是否相等
			if(ge*ge*ge + shi*shi*shi + bai*bai*bai == i) {
				//输出满足条件的数字就是水仙花数
				System.out.println(i);
			}
		}
    }
}
```

```java
public class Demo6For {
    /*
        需求：在控制台输出所有的“水仙花数”，要求每行打印2个。
            System.out.print (打印内容)：打印后不换行
            System.out.println(打印内容)：打印后换行
    */
	public static void main(String[] args){
		// 1. 定义变量count，用于保存“打印过”的数量，初始值为0
		int count = 0;
		for(int i = 100; i <= 999; i++){
			int ge = i % 10;
			int shi = i / 10 % 10;
			int bai = i / 10 / 10 % 10;
			
			if(	(ge*ge*ge + shi*shi*shi + bai*bai*bai) == i){
				//  2. 在判定和打印水仙花数的过程中，拼接空格, 但不换行，并在打印后让count变量+1，记录打印过的数量
				System.out.print(i + " ");
				count++;
				// 3. 在每一次count变量+1后，判断是否到达了2的倍数，是的话，换行
				if(count % 2 == 0){
					System.out.println();
				}
			}
		}
	}
}
/*
	本题要点：
		1. 今后如果需求带有统计xxx，先想到计数器变量
		2. 计数器变量定义的位置，必须在循环外部
*/
```

```java
public class Test {
    /*
        需求：在控制台打印出1-100之间的满足逢七必过（7的倍数或者含7）规则的数据。
    */
    public static void main(String[] args) {
        for(int x=1; x<=100; x++) {
            //用if语句实现数据的判断：要么个位是7，要么十位是7，要么能够被7整除
            if( x % 10 == 7 || x / 10 % 10 == 7 || x % 7 == 0) {
                System.out.println(x);
            }
        }
    }
}
```

```java
public class Test {
    /*
		需求：有一对兔子，从出生后第3个月起每个月都生一对兔子，小兔子长到第三个月后每个月又生一对兔子，假如兔子都不死，问第二十个		 月的兔子对数为多少？
    */
    public static void main(String[] args) {
        //1.定义数组存储每个月的兔子对数
        int[] arr = new int[20];
        
        //2.第1、2个月兔子的对数都是1，所以数组的第1、2个元素值都是1
        arr[0] = 1;
        arr[1] = 1;
        
        //3.用循环实现计算每个月的兔子对数（斐波那契数列）
        for(int x=2; x<arr.length; x++) {
        	arr[x] = arr[x-2] + arr[x-1];
        }
        //4.输出数组中最后一个元素的值，就是第20个月的兔子对数
        System.out.println("第二十个月兔子的对数是：" + arr[19]);
    }
}
```

```java
public class Test {
    /*
        需求：鸡翁一值钱五，鸡母一值钱三，鸡雏三值钱一。 百钱买百鸡，问鸡翁、鸡母、鸡雏各几何？
    */
    public static void main(String[] args) {
        //1.表示百钱能买鸡翁的数量范围
        for(int x=0; x<=20; x++) { 
            //2.表示百钱能买鸡母的数量范围
            for(int y=0; y<=33; y++) { 
                //3.表示鸡雏的数量 z = 100 – x – y
                int z = 100 - x - y;
                //4.鸡雏需满足：被三整除；与鸡翁、鸡母共百钱
                if(z%3==0 && 5*x+3*y+z/3==100) {
                	System.out.println(x+","+y+","+z);
                }
            }
        }
    }
}
```

## while循环

```java
初始化语句;
while (条件判断语句) {
	循环体语句;
    条件控制语句;
}
```

## do...while循环

```java
初始化语句;
do {
	循环体语句;
	条件控制语句;
}while(条件判断语句);
```

三种循环的区别：

1、for、while先判断后执行，do...while先执行后判断。

2、条件控制语句所控制的自增变量，当归属for循环的语法结构中时，在for循环结束后，则无法再被访问，而对于while循环来说不归属其语法结构中，在while循环结束后，该变量还可以继续使用。

## 死循环

```java
for(;;){}

while(true){}

do {} while(true);
```

## 跳转控制语句

1、continue：用于跳过本次循环，继续下次循环。只能在循环中使用。

2、break：用于终止switch语句或者结束循环。

```java
//利用switch中的break结束外层死循环
lo:while(true){
    Scanner sc = new Scanner(System.in);
    int week = sc.nextInt();
    
    switch(week){
        case 0:
            System.out.println("感谢您的使用");
            break lo;
        default:
            System.out.println("您的输入有误");
            break;
    }
}	
```

## 循环嵌套

在循环中，继续定义循环。外循环执行一次，内循环执行一圈。总共的循环次数 = 外循环次数 * 内循环次数。

```java
for(初始化表达式; 循环条件; 步进表达式) {
    for(初始化表达式; 循环条件; 步进表达式) {
        执行语句;
    }
}
```

```java
// 需求：打印24小时及每个小时60分钟。
public static void main(String[] args) {
    //1.外循环控制小时的范围
    for (int hour = 0; hour < 24; hour++) {
        //2.内循环控制分钟的范围
        for (int minute = 0; minute < 60; minute++) {
            System.out.println(hour + "时" + minute + "分");
        }
        System.out.println("--------");
    }
}
```

```java
// 需求：使用嵌套循环，打印5*8的矩形。
public static void main(String[] args) {
    //5*8的矩形，打印5行*号，每行8个
    //外循环5次，内循环8次
    for(int i = 0; i < 5; i++){
        for(int j = 0; j < 8; j++){
            //不换行打印星号
            System.out.print("*");
        }
        //内循环打印8个星号后，需要一次换行
        System.out.println();
    }
}
```

# 13. Random类

```java
//1. 导入包
import java.util.Random;

//2. 创建对象
Random r = new Random();

//3. 产生随机数
//每次调用nextInt()方法，都会生成一个新的随机数。
int num = r.nextInt(10); //10代表的是一个范围，实际产生的随机数为0-9
```

```java
import java.util.Scanner;
import java.util.Random;

public class Test {
    /*
        需求：生成一个1-100之间的数字，猜出这个数字是多少？猜错时系统提示大了或者小了，直到玩家猜中，游戏结束。
    */
	public static void main(String[] args){
		Random r = new Random();
		Scanner sc = new Scanner(System.in);
        
		//使用Random产生一个1-100之间的数
		int randomNum = r.nextInt(100) + 1;
		
		while(true){
			System.out.println("请输入您猜的数据:");
			int num = sc.nextInt();

			if(num > randomNum){
				System.out.println("猜大了");
			}else if(num < randomNum){
				System.out.println("猜小了");
			}else{
				System.out.println("恭喜,猜中了");
				break;
			}
		}
	}
}
```

# 14. 数组

数组就是存储数据长度固定的容器，存储多个数据的数据类型要一致。 定义格式：

```java
数据类型[] 数组名
int[] arr;        
double[] arr;      
char[] arr;

数据类型 数组名[]
int arr[];
```

## 动态初始化

只给定数组的长度，由系统给出默认初始化值0。

```java
数据类型[] 数组名 = new 数据类型[数组长度];

int[] arr = new int[3];
```

```java
package com.itheima.array;

public class Demo2Array {
    /*
        打印数组变量的时候, 会打印出数组的内存地址
            
        [I@10f87f48 :
            @ : 分隔符
            [ : 当前的空间是一个数组类型
            I : 当前数组容器中所存储的数据类型
            10f87f48 : 十六进制内存地址
     */
    public static void main(String[] args) {
        // 通过new关键字创建了一个int类型的数组容器, 该容器可以存储5个int类型的整数, 该容器被arr数组变量所记录
        int[] arr = new int[5];
        System.out.println(arr); //[I@10f87f48

        byte[] bArr = new byte[3];
        System.out.println(bArr); //[B@b4c966a
    }
}
```

## 访问格式

索引：每一个存储到数组的元素，都会自动的拥有一个编号，即数组索引（index）。索引从0开始，用于访问数组容器中的空间位置。

```java
数组名[索引];
```

```java
public static void main(String[] args) {  
    int[] arr = {11, 22, 33, 44, 55};    
    //使用通用的遍历格式   
    for (int i = 0; i < arr.length; i++) { 
        System.out.println(arr[i]);   
    }
}
```

## 静态初始化

初始化时指定每个数组元素的初始值，由系统决定数组长度。

```java
//完整版格式
数据类型[] 数组名 = new 数据类型[]{元素1,元素2,...};

int[] arr = new int[]{11,22,33};

//简化版格式
数据类型[] 数组名 = {元素1,元素2,...};
 
int[] arr2 = {44,55,66};
```

# 15. Java的内存划分和作用

内存是临时存储区域，作用是运行程序。我们编写的程序存放于硬盘中，需要加载到内存中才能运行，运行完毕后会清空内存。 Java虚拟机要运行程序，必须要对内存进行空间的分配和管理。 

| 区域名称   | 作用                                                    |
| ---------- | ------------------------------------------------------- |
| 寄存器     | 给CPU使用，和我们开发无关                               |
| 本地方法栈 | JVM在使用操作系统功能的时候使用，和我们开发无关         |
| 方法区     | 存储可以运行的class文件                                 |
| 堆内存     | 存储由new创建的对象和数组。垃圾回收器空闲时进行内存回收 |
| 方法栈     | 方法运行时使用的内存。运行完毕，立即消失                |
| 栈内存     | 存储局部变量（定义在方法中的变量和对象的引用变量）      |

# 16. 数组在内存中的存储

## 一个数组内存图

<img src="https://gitee.com/sunzhijie28/img/raw/master/img/20211017160215.png" alt="image-20211017160214379" style="zoom:67%;" />

## 两个数组内存图

<img src="https://gitee.com/sunzhijie28/img/raw/master/img/20211017160243.png" alt="image-20211017160242780" style="zoom:67%;" />

## 多个数组指向相同内存图

<img src="https://gitee.com/sunzhijie28/img/raw/master/img/20211017160304.png" alt="image-20211017160303585" style="zoom:67%;" />

# 17. 数组的常见操作

## 索引越界异常

```java
public static void main(String[] args) {
    int[] arr = new int[3];   
    System.out.println(arr[3]); //报错。ArrayIndexOutOfBoundsException，数组越界异常。
}
/*
	1. 原因：数组长度为3，索引范围是0~2，但是我们却访问了一个3的索引。
	2. 解决：修改编写的代码，将错误的索引修改为正确的索引范围。
*/
```

## 空指针异常

```java
public static void main(String[] args) { 
    int[] arr = new int[3];  
    arr = null;  
    System.out.println(arr[0]); //报错。NullPointerException，空指针异常。
}
/*
	1. 原因：arr = null 表示变量arr不再保存数组的内存地址，也就不允许再操作数组。
	2. 解决：给数组一个真正的堆内存空间引用。
*/
```

## 数组获取最大值

```java
public static void main(String[] args) {    
    int[] arr = {12, 45, 98, 73, 60};    
    //定义变量，保存数组中0索引的元素    
    int max = arr[0];    
    //遍历数组，取出每个元素 
    for (int i = 1; i < arr.length; i++) {  
        //遍历到的元素和变量max比较       
        if (arr[i] > max) {         
            //max记录住大值         
            max = arr[i];         
        }       
    }     
    System.out.println("数组最大值是:" + max);
}
```

## 数组元素求和

```java
package com.itheima.test;
import java.util.Scanner;

public class Test3Array {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int sum = 0;

        int[] arr = new int[5];
        //键盘录入的数值存储到数组中
        for(int i = 0; i < arr.length; i++){
            System.out.println("请输入第" + (i+1) + "个整数:");
            arr[i] = sc.nextInt();
        }
		//求和
        for (int i = 0; i < arr.length; i++) {
            sum += arr[i];
        }
        System.out.println("sum:" + sum);
    }
}
```

## 数组反转

```java
public static void main(String[] args) {  
    int[] arr = { 1, 2, 3, 4, 5 };   
    
    for (int min = 0, max = arr.length‐1; min <= max; min++, max‐‐) {  
        //利用第三方变量完成数组中的元素交换     
        int temp = arr[min];      
        arr[min] = arr[max];     
        arr[max] = temp;   
    }  
    // 反转后，遍历数组    
    for (int i = 0; i < arr.length; i++) { 
        System.out.println(arr[i]);  
    }
}
```

## 数组基本查找

```java
/*
	需求：已知一个数组 arr = {19, 28, 37, 46, 50}; 键盘录入一个数据，查找该数据在数组中的索引，并在控制台输出找到的索引值。
*/
public static void main(String[] args) {
        int[] arr = {19, 28, 37, 46, 50};

        Scanner sc = new Scanner(System.in);
        System.out.println("请输入您要查找的元素:");
        int num = sc.nextInt();
    
        //定义一个索引变量，初始值为-1。假设要查找的数据在数组中不存在。
        int index = -1;

        for (int i = 0; i < arr.length; i++) {
            if(num == arr[i]){
                //值相同，就把该值对应的索引赋值给索引变量，并结束循环
                index = i;
                break;
            }
        }
        System.out.println(index);
    }
}
```

## 评委打分

```java
/*
	需求：编程竞赛中，6个评委为选手打分（0-100的整数）。最后得分：去掉一个最高分和一个最低分后的4个评委的平均值 (不考虑小数)。
*/
public static void main(String[] args) {
    int[] arr = new int[6];
    Scanner sc = new Scanner(System.in);
    
    //循环接收评委分数
    for (int i = 0; i < arr.length; i++) {
        System.out.println("请输入第" + (i+1) + "个评委的打分:");
        int score = sc.nextInt();
        if(score >= 0 && score <= 100){
            // 合法的分值
            arr[i] = score;
        }else{
            // 非法的分值
            System.out.println("您的打分输入有误, 请检查是否是0-100之间的");
            i--;
        }
    }
    
    //找出最大值
    int max = arr[0];
    for (int i = 1; i < arr.length; i++) {
        if(max < arr[i]){
            max = arr[i];
        }
    }

    //找出最小值
    int min = arr[0];
    for (int i = 1; i < arr.length; i++) {
        if(min > arr[i]){
            min = arr[i];
        }
    }

    //求出数组总和
    int sum = 0;
    for (int i = 0; i < arr.length; i++) {
        sum += arr[i];
    }

    int avg = (sum - max - min ) / 4;
    System.out.println(avg);
}
```

# 18. 二维数组

二维数组也是一种容器，不同于一维数组，该容器存储的都是一维数组容器。

## 动态初始化

```java
数据类型[][] 变量名 = new 数据类型[m][n];

// m：这个二维数组可以存放一维数组的个数
// n：每一个一维数组可以存放的元素个数
```

```java
public static void main(String[] args) {
    int[][] arr = new int[3][3];
    /*
		[[I@10f87f48
		
		@ : 分隔符
		10f87f48 : 十六进制内存地址
		I : 数组中存储的数据类型
		[[ : 几个中括号就代表的是几维数组
    */
    System.out.println(arr);

    /*
		二维数组存储一维数组的时候, 存储的是一维数组的内存地址
    */
    System.out.println(arr[0]); // [I@880ec60
    System.out.println(arr[0][0]); // 0

    //存储元素并打印
    arr[0][0] = 11;
    System.out.println(arr[0][0]); // 11
}
```

```java
/*
	二维数组中可以存入提前创建好的一维数组。
*/
public static void main(String[] args) {
    int[][] arr = new int[3][3]; // 在堆内存为三个含有三个元素的一维数组分配内存
    arr[0][3] = 11; 
    System.out.println(arr[0][3]); // 报错。索引越界

    int[] smallArray = {11, 22, 33, 44};
    arr[0] = smallArray; // // 将堆内存中初始化时为一维数组分配的内存地址替换掉
    System.out.println(arr[0][3]); // 44
}
```

## 静态初始化

```java
//完整格式
数据类型[][] 变量名 = new 数据类型[][]{ {元素1, 元素2...} , {元素1, 元素2...};
                            
//简化格式
数据类型[][] 变量名 = { {元素1, 元素2...} , {元素1, 元素2...} ...};
```

```java
public static void main(String[] args) {
    int[] arr1 = {11,22,33};
    int[] arr2 = {44,55,66};

    int[][] arr = {{11,22,33}, {44,55,66}};
    System.out.println(arr[0][2]);// 33

    int[][] array = {arr1,arr2};
    System.out.println(array[0][2]);// 33
}
```

应用：

```java
public class Test {
    /*
    	需求：已知一个二维数组 arr = {{11, 22, 33}, {33, 44, 55}}; 遍历该数组，取出所有元素进行求和。
    */
    public static void main(String[] args) {
        int sum = 0;
        
        int[][] arr = {{11, 22, 33}, {33, 44, 55}};

        // 1. 遍历二维数组，取出里面每一个一维数组
        for (int i = 0; i < arr.length; i++) {
            // 2. 在遍历的过程中，对每一个一维数组继续遍历，获取内部存储的每一个元素
            for (int j = 0; j < arr[i].length; j++) {
                sum += arr[i][j];
            }
        }
    }
}
```

# 19. 方法的定义和调用

方法（method）是将具有独立功能的代码块组成一个整体，使其具有特殊功能的代码集。

注意事项：

1、方法必须先创建才可以使用，该过程称为方法定义。

2、方法创建后并不是直接可以运行的，需要手动使用后，才执行，该过程称为方法调用。

## 无参数方法

```java
//定义
public static void 方法名 (   ) {
	// 方法体;
}

//调用
方法名();

//1. 方法必须先定义，后调用，否则程序将报错。
//2. 方法在被调用执行时，会进入栈内存，拥有自己独立的内存空间，方法内部代码调用完毕之后，会从栈内存中弹栈消失。
```

## 带参数方法

```java
//定义
public static void 方法名 (参数1, 参数2, 参数3...) {
	方法体;
}

//调用
方法名(参数1,参数2);

//方法调用时，参数的数量与类型必须与方法定义中的设置相匹配，否则程序将报错。
```

应用：

```java
/*
	需求：设计一个方法（print）用于打印 n 到 m 之间所有的奇数。
*/
public static void main(String[] args) {
    print(10,20);
}

public static void print(int n, int m){
    System.out.println(n + "到" + m + "之间的奇数为:");
    for(int i = n; i <= m; i++){
        if(i % 2 == 1){
            System.out.println(i);
        }
    }
}
```

## 带返回值方法

```java
//定义
public static 数据类型 方法名 ( 参数 ) { 
	return 数据 ;
}

//调用
方法名(参数);
数据类型 变量名 = 方法名(参数);

//1. 方法定义时，return后面的返回值与方法定义上的数据类型要匹配，否则程序将报错。
//2. 方法的返回值通常会使用变量接收，否则该返回值将无意义。
```

应用：

```java
/*
	需求：设计一个方法可以获取两个数的较大值，数据来自于参数。
*/
public static void main(String[] args) {
    //输出调用
    System.out.println(getMax(10,20));  

    int result = getMax(10,20);
    System.out.println(result);
}

public static int getMax(int a, int b){
    return a > b ? a : b;
}
```

# 20. 方法的通用格式

```java
修饰符 返回值类型 方法名(参数) {
   方法体; 
   return 返回值;
}

/*
	方法的两个明确:
		1. 明确返回值类型：主要是明确方法操作完毕之后是否有数据返回，如果没有，写void；如果有，写对应的数据类型。
        2. 明确参数：主要是明确参数的类型和数量。
*/
```

注意事项：

1、方法不能嵌套定义，必须定义在一个类中、方法外。

```java
public class MethodDemo {
    public static void main(String[] args) {
    }

    public static void methodOne() {
		public static void methodTwo() {
       		// 这里会引发编译错误!!!
    	}
    }
}
```

2、无返回值时，返回值类型固定为void，可以省略return，也可以单独的书写return，后面不加数据。

```java
public class MethodDemo {
    public static void main(String[] args) {
    }
    public static void methodTwo() {
        //return 100; 编译错误，因为没有具体返回值类型
        return;	
        //System.out.println(100); return语句后面不能跟数据或代码，方法执行到return停止。
    }
}
```

# 21. 方法的重载

方法重载指同一个类中定义的多个方法之间的关系，满足下列条件的多个方法相互构成重载：

​	1、多个方法在同一个类中

​	2、多个方法具有相同的方法名

​	3、多个方法的参数不相同，类型不同或者数量不同

```java
public class MethodDemo {
	public static void fn(int a) { //方法体 }
    public static int fn(double a) { //方法体 }
}

public class MethodDemo {
	public static float fn(int a) { //方法体 }
    public static int fn(int a , int b) { //方法体 }
}
```

注意事项：

1、重载仅对应方法的定义，与方法的调用无关，调用方式参照标准格式。

2、重载仅针对同一个类中方法的名称与参数进行识别，与返回值无关，不能通过返回值来判定两个方法是否相互构成重载。

```java
//错误原因：重载与返回值无关
public class MethodDemo {
	public static void fn(int a) { //方法体 }
    public static int fn(int a) { //方法体 }
}

//错误原因：这是两个类的两个fn方法
public class MethodDemo01 {
    public static void fn(int a) { //方法体 }
} 
public class MethodDemo02 {
    public static int fn(double a) { //方法体 }
}
```

应用：

```java
public class MethodTest {
    /*
    	需求：使用方法重载的思想，设计比较两个整数是否相同的方法，兼容全整数类型（byte,short,int,long）。
    */
    public static void main(String[] args) {
        //调用方法
        System.out.println(compare(10, 20));
        System.out.println(compare((byte) 10, (byte) 20));
        System.out.println(compare((short) 10, (short) 20));
        System.out.println(compare(10L, 20L));
    }

    //int
    public static boolean compare(int a, int b) {
        System.out.println("int");
        return a == b;
    }

    //byte
    public static boolean compare(byte a, byte b) {
        System.out.println("byte");
        return a == b;
    }

    //short
    public static boolean compare(short a, short b) {
        System.out.println("short");
        return a == b;
    }

    //long
    public static boolean compare(long a, long b) {
        System.out.println("long");
        return a == b;
    }
}
```

# 22. 方法的参数传递

## 传递基本类型

```java
public class Test1 {
    /*
         传递基本类型：传入方法中的, 是具体的数值。
     */
    public static void main(String[] args) {
        int number = 100;
        System.out.println("调用change方法前:" + number); //100
        change(number);
        System.out.println("调用change方法后:" + number); //100
    }

    public static void change(int number) {
        number = 200;
    }
}

//1. 基本数据类型的参数，形式参数的改变，不影响实际参数。
//2. 每个方法在栈内存中，都会有独立的栈空间，方法运行结束后就会弹栈消失。
```


## 传递引用类型

```java
public class Test2 {
    /*
         传递引用类型：传入方法中的, 是内存地址.
     */
    public static void main(String[] args) {
        int[] arr = {10, 20, 30};
        System.out.println("调用change方法前:" + arr[1]); //20
        change(arr);
        System.out.println("调用change方法后:" + arr[1]); //200
    }

    public static void change(int[] arr) {
        arr[1] = 200;
    }
}

//1. 对于引用类型的参数，形式参数的改变，影响实际参数的值。
//2. 引用类型的传参，传入的是地址值，内存中会造成两个引用指向同一个内存，即使方法弹栈，堆内存中的数据也已经是改变后的结果。
```

应用：

```java
public class Test1 {
    /*
    	需求：设计一个方法用于数组遍历，要求遍历的结果是在一行上的。例如：[11, 22, 33, 44, 55]
    */
    public static void main(String[] args) {
        int[] arr = {11, 22, 33, 44, 55};

        printArray(arr);
    }

    public static void printArray(int[] arr){
        System.out.print("[");
        
        for (int i = 0; i < arr.length; i++) {
            if(i == arr.length -1){
                //最后一个元素, 特殊处理
                System.out.println(arr[i] + "]");
            }else{
                //遍历打印，数据不换行
                System.out.print(arr[i] + ", ");
            }
        }
    }
}
```

```java
public class Test3 {
    /*
    	需求：设计一个方法，该方法能够同时获取数组的最大值，和最小值。
    	
    	注意：return语句，只能带回一个结果。
    */
    public static void main(String[] args) {
        int[] arr = {11,55,33,22,44};

        int[] maxAndMin = getMaxAndMin(arr);

        System.out.println(maxAndMin[0]);
        System.out.println(maxAndMin[1]);
    }

    public static int[] getMaxAndMin(int[] arr){
        int max = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (max < arr[i]) {
                max = arr[i];
            }
        }

        int min = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (min > arr[i]) {
                min = arr[i];
            }
        }

        int[] maxAndMin = {min, max};
        return maxAndMin;
    }
}
```

# 23. 计算机基础知识

## 进制转换

```java
public class Demo1 {
    /*
        十进制：Java中，数值默认都是10进制，不需要加任何修饰。
        二进制：数值前面以0b开头，b大小写都可以。
        八进制：数值前面以0开头。
        十六进制：数值前面以0x开头，x大小写都可以。

        注意: 书写的时候, 虽然加入了进制的标识, 但打印在控制台展示的都是十进制数据.
     */
    public static void main(String[] args) {
        System.out.println(10);
        System.out.println("二进制数据0b10的十进制表示为:" + 0b10);
        System.out.println("八进制数据010的十进制表示为:" + 010);
        System.out.println("十六进制数据0x10的十进制表示为:" + 0x10);
    }
}
```

其他进制转为十进制：

公式：系数 * 基数的权次幂，相加。系数：每一【位】上的数，基数：几进制，就是几，权：从数值的右侧，以0开始，逐个 +1。

<img src="https://gitee.com/sunzhijie28/img/raw/master/img/20211017204222.png" alt="image-20211017204221166" style="zoom:67%;" />

<img src="https://gitee.com/sunzhijie28/img/raw/master/img/20211017204202.png" alt="image-20211017204201287" style="zoom:67%;" />

十进制转为其他进制：

公式：除基取余使用源数据，不断的除以基数（几进制，基数就是几）得到余数，直到商为0，再将余数倒着拼起来即可。

<img src="https://gitee.com/sunzhijie28/img/raw/master/img/20211017194653.png" alt="image-20211017194652432" style="zoom:67%;" />

<img src="https://gitee.com/sunzhijie28/img/raw/master/img/20211017194719.png" alt="image-20211017194718185" style="zoom:67%;" />

快速进制转换法：

8421码：又称BCD码，是BCD代码中最常用的一种BCD： (Binary-Coded Decimal‎) 二进制码十进制数在这种编码方式中，每一位二进制值的1都是代表一个固定数值，把每一位的1代表的十进制数加起来得到的结果就是它所代表的十进制数。

<img src="https://gitee.com/sunzhijie28/img/raw/master/img/20211017194850.png" alt="image-20211017194849312" style="zoom: 50%;" />

<img src="https://gitee.com/sunzhijie28/img/raw/master/img/20211017194956.png" alt="image-20211017194955846" style="zoom: 50%;" />

<img src="https://gitee.com/sunzhijie28/img/raw/master/img/20211017195047.png" alt="image-20211017195045927" style="zoom: 50%;" />

## 原码反码补码

计算机中的数据，都是以二进制补码的形式在运算，而补码则是通过反码和原码推算出来的

原码：二进制定点表示法，即最高位为符号位，【0】表示正，【1】表示负，其余位表示数值的大小。

```java
byte b1 = 7;
byte b2 = -7;

//二进制
//一个字节等于8个比特位，即8个二进制位
0(符号位)  0000111
1(符号位)	0000111
```

反码：正数的反码与其原码相同；负数的反码是对其原码逐位取反，但符号位除外。

补码：正数的补码与其原码相同；负数的补码是在其**反码的末位加1**。

**根据负数的补码求原码：**

1、该负数补码的补码就是要求的原码。

如：-1的补码是（11111111b）→ 除符号位其余各位取反，得到（10000000b）→ 加1后得到 -1的原码(10000001b)

2、将补码减1，再将符号位保持不变其余各位取反。

-1的补码是（11111111b）→减1（11111110b）→ 除符号位其余各位取反(10000001b) 

## 位运算

位运算符指的是二进制位的运算，先将十进制数转成二进制后再进行运算。在二进制位运算中，1表示true，0表示false。

位运算符：

| 符号 | 计算方式                                 |
| :--- | :--------------------------------------- |
| &    | 遇false则false, 遇0则0                   |
| \|   | 遇true则true, 遇1则1                     |
| ^    | 相同为false，不同为true                  |
| ~    | 全部取反, 0变1, 1变0，包括符号位         |
| <<   | 带符号左移。左边符号位丢弃，右边补齐0    |
| >>   | 带符号右移。正数右移高位补0，负数高位补1 |
| >>>  | 无符号右移。无论是正负，高位通通补0      |

```java
public class Demo2 {
    /*
	    	00000000 00000000 00000000 00000110     // 6的二进制
		  & 00000000 00000000 00000000 00000010     // 2的二进制
			------------------------------------
			00000000 00000000 00000000 00000010     // 结果: 2
			

			00000000 00000000 00000000 00000110         // 6的二进制补码
		  ~ 11111111 11111111 11111111 11111001

		  -                                   1         // -1求反码
			------------------------------------
			11111111 11111111 11111111 11111000         // 反码推原码

			10000000 00000000 00000000 00000111         // -7
			
		  ^ ：一个数, 被另外一个数, 异或两次, 该数本身不变
     */
    public static void main(String[] args) {
        System.out.println(6 & 2); // 2
        System.out.println(~6); // -7
        
        System.out.println(10 ^ 5 ^ 10); // 5
    }
}
```

```java
public class Demo3 {
    /*
		<< : 向左移动几位, 就是乘以2的几次幂
		>> : 向右移动几位, 就是除以2的几次幂

		000000000 00000000 00000000 0000001(1)  // 3的二进制
		(0)0000000 00000000 00000000 000011000  // 12的二进制
     */
    public static void main(String[] args) {
        System.out.println(12 << 1);  // 24
        System.out.println(12 << 2);  // 48
		
        System.out.println(4 >> 1);  // 2
        System.out.println(3 >> 1);  // 1
    }
}
```

