# JAVA程序的标识符和常用关键词

- 标识符：java程序的组成，类名，方法名，变量名等

  注意点: * 标识符可以由字⺟母、数字、下划线_ 、美元符($)组成，但不能包含%，空格等其他
  特殊字符，不能以数字开头 * 区分⼤⼩写 * 不能是java关键字

- JAVA 保留字

    ```java
    boolean、byte、char、double、enum、float、int、long、short、void
    private、protected、public、default
    
    abstract、extends、class、interface、return、static、super
    assert、break、case、try、catch、const、continue、do、else、final、finally、
    for、goto、if、implements、import
    instanceof、native、new、package
    
    switch、synchronized 、this、throw、throws
    transient、volatile、while
    ```


# **java核心基础知识之修饰符下集**

- 修饰符的作用是?用来定义类、⽅法或者变量的访问权限
- 两⼤类
    - 访问修饰符
        - 限定类、属性或⽅法是否可以被程序⾥的其他部分访问和调⽤修饰符
    - private < default < protected < public
    - ⾮访问修饰符:⽤来修饰或者辅助功能，
        - 例如static、final、abstract、synchronized等
- 主要记住!!!!:
    - 外部类修饰符: public或者为默认
    - ⽅法、属性修饰符:private、default、protected、public
        - public - 公开对外部可见
        - protected - 对包和所有⼦类可⻅
        - private - 仅对类内部可⻅

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c57152a8-cdf8-4ec1-a20e-82b8bbc57e0f/Untitled.png)

- 属性或者成员变量，都⽤private修饰，不⽤其他的，这个是java开发的约束
- Java中public class与class的区别
    - 在⼀个*.java的⽂文件中，只能有⼀个public class的声明，有多个public则编译报错，其类名 称必须与⽂文件名称完全⼀致,但是允许有多个class的声明，

```java
public class A{
    public static void main(String [] args){
        System.out.println("A");
    }
};
class B{};
class C{};
```

只有public修饰的类，才能在包外部包见;否则只是包内私有的类，类不能被其他包访问。

# Java核心基础-数据类型

**Java内置数据类型**

- 计算机基础知识
    - bit 位 ,即0或者1, 0101010110
    - byte字节，8位作为⼀个字节，字节是处理数据的基本单位
    - 1 byte = 8bits
    - 1KB = 1024 bytes
    - 1MB = 1024 KB
    - 1GB = 1024 MB
- ⼋种基本数据类型(每个数据都需要从计算机内存中申请空间，来存储它)
    - byte
        - 8位
          最⼤大127，最⼩小-128
          节省空间，占⽤用int类型的四分之⼀
          默认 0
    - short
        - 16位
          最⼩-32768，最大32767
          int类型的⼆分之⼀
          默认是0
    - int
        - 32位
          最小 -2147483648，最⼤大2147483647
          整数默认是int类型
          默认是0
    - long
        - 64位
          最小 -9223372036854774808，最大 9223372036854774807
          默认是 0L,
    - float 浮点
        - 单精度32位
        - 默认0.0f
    - double
        - 双精度 64位
          浮点数默认位double类型
          默认是0.0
    - boolean
        - 1位
          true或者false
          默认是false
    - char
        - 16位的 unicode字符，即两个字节表示⼀一个字符
          最小是 \u0000 即0，做大 \ufff 即65535
          例⼦ char demo = 'A'
    - 类型转换 double > float > long > int > short > byte
      ⼩转换到大，可以直接转换，⽽大到⼩，需要强制转，会有精度丢失
- 引⽤用数据类型:Class创建的对象 或者 数组都是引用数据类型
    - String :字符串对象，也是引⽤数据类型


# JAVA核心基础之数组讲解

- 使⽤数组
  声明数组变量时，需要指出数据类型和数组变量的名字
    - new int[n]将会创建⼀个长度为n的数组

```java
//可以使⽤用这两种形式声明数组,推荐第⼀种 
int [] numbers;
int numbers2 [];
```

- 数组初始化和匿名数组

```java
//初始化，数组的大小就是初始值的个数
int[] numbers = { 1,2,3,4,5,6 };
//匿匿名数组
new int[] { 1,2,3,4,5,6 };
```

- 注意:
    - 所有元素都初始化为0，boolean数组的元素会初始化为false
    - 一旦创建了数组，就不能改变它的⼤
    - 数组需要初始化才可以操作，不能索引越界

多维数组

```java
int [] numbers = {1,2,3};
String[] str=new String[2];
String[] str= {"apple", "xdclass", "cat", "dog"};
```

- 获取数组⻓度的属性名称 length，使用就是数组名.length

# **Java内存空间堆栈讲解**

**Java内存空间堆栈**

- 数据类型
    - 基本数据类型 byte,short, int,long, float,doble,boolean,char
    - 引⽤数据类型，即除了了基本的变量类型之外的所有类型
      java在内存中堆、栈两块存储空间
- 数据类型在内存中使⽤用介绍
    - 基本的变量类型只有一块存储空间(分配在stack中),
        - 传递的时候直接是值传递，
        - 对数据进⾏行操作，不影响原先的值
    - 引⽤类型有两块存储空间(⼀块在stack中,⼀块在heap中)
        - 一个对象在内存中会请求⼀块空间来保存数据，访问对象的时候不会直接是访问对象在内存中的数据，⽽是通过引⽤用去访问
        - 什么是引用??? 也是一种数据类型，保存的是内存的地址，引⽤用是存储在 stack栈空间⾥里里⾯面，不不同的引⽤用可以指向同⼀一个对象，⼀一个对象可以有多个引⽤用
- 下⾯面代码在堆栈⾥里里⾯面怎么分配的

```java
int a=1;
boolean flag=false;

Student s = new Student();
Person p = new Person();
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/457fb8d2-02f7-425d-a13c-49d6a657d1fd/Untitled.png)

- 引⽤后修改结果如何呢?
    - 因为字符串、数组或者对象是引⽤类型，所以修改后正在的数据都会发⽣变化

这一节的内容学完后，对于引用数据类型有了一些了解，引用大致理解为索引地址，所以c=b b=a 这样都是在栈中复制同一个队形的索引地址，所以最终a b c任何一个更改了对象的内容，那a b c输出的值也都会相同的改变。因为对象只有一个，存在于Heap堆中。

# **Java核心基础之变量类型**

**java类⾥⾯的变量类型**

- 类变量(静态变量): -通常使用静态变量
    - 使⽤static声明的变量，可以直接使⽤类名.变量名访问
    - 一个类不管创建了了多少个对象，类只拥有类变量的⼀份拷贝，数值默认值是0，布尔型默认值是false，引⽤类型默认值是null
    - ⽣命周期在第⼀次被访问时创建，在程序结束时销毁
    - 声明为public类型，⼀般这样声明 public static final存储在⽅法区，和堆栈不⼀样的⼀个空间
- 实例例变量(属性)-通常使用属性
    - 需要使用对象.变量名才可以访问
    - 对象被实例化之后，实例变量的值就跟着确定，可以是赋值，也可以是默认值
    - 生命周期
        - 在对象创建的时候创建，在对象被销毁的时候销毁
    - 访问修饰符可以修饰实例例变量，⼀般是私有的，private修饰，然后通过方法来进行查看或者修改
- 局部变量
  方法中的变量
    - 声明在⽅法、构造⽅法、语句块、形式参数
    - 生命周期
        - 当它们执行完成后，变量量将会被销毁
    - 访问修饰符不不能⽤用于局部变量量
    - 局部变量量没有初始值，必须初始化后才可以被使⽤用

# **方法入参和返回值讲解**

**java方法入参和返回类型讲解**

- ⽅法入参和返回类型
    - 方法入参
        - 基础数据类型
        - 引⽤数据类型

        ```java
        修饰符 返回类型 方法名(参数类型 参数名,参数类型 参数名...){ 
        
        //⽅法体
        
        return 
        }
        ```

    - ⽅法返回类型
        - return xxx 具体类型
        - 如果不用返回，则方法返回类型上写 void

        ```java
        修饰符 void ⽅法名(参数类型 参数名,参数类型 参数名...){ 
        
        //⽅法体
        
        }
        ```


    # **Java核⼼之基础运算符上**
    
    ```java
    加法 + 减法 - 乘法 * 除法 / 取余 %
    ⾃自增1 ++
    a++ 就是 a=a+1
    ⾃自减1 --
    a-- 就是 a=a-1
    int a = 5;
    int b = a++;
    int c = ++a;
    int d = a--;
    int e = --a;
    等号 ==
    不不等 !=
    ⼤大于 > ⼤大于或等于 >= ⼩小于 < ⼩小于或等于 <=
    
    字符串不能用==去比较，相同的字符串会显示ture，是因为引用的内存地址相同。字符串比较要用equals()方法，这是个面试的考点，是个坑
    
    ```


# **Java核⼼之基础运算符和优先级下集**

- 运算符优先级和数学运算⼀一样，可以加括号控制优先级

```java
乘除取余 * / %
加减 + -
关系运算>, >=, <,<=
相等 ==、!=
逻辑与 &&
逻辑或 ||
三⽬目运算 ? :
赋值 =
```

与，或可以进行短路运算。关于java的其他运算可以搜索一下，比如>>>等等