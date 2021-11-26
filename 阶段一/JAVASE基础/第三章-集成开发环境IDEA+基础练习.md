# 第三章 集成开发环境IDEA

# Intellij IDEA安装和使用。

# 创建类和主方法

```java
public class User {

  public void sleep() {
    System.out.println("睡觉");
  }

  public static void main(String[] args) {
    User user = new User();
    user.sleep();
  }
}
```

每个项目里只能有一个 public static void main(String [] args)主方法。

主方法可以调用类和方法。使用new创建新的个体。

# idea debug基础调试技能 ！

- 程序启动有两个模式
  - 运行模式run
  - 调试模式debug
- 断点
  - 在需要停留代码位置打个标示，程序运行到这个地方会暂停
  - 断点真的很方便啊，用debug模式，然后对想要停下来的地方打断点后，运行后就可以手动stepover
- step over
  - 程序向下执⾏行行⼀一⾏行行
- step into
  - 进⼊入⾃自定义⽅方法
  - 遇到方法的时候，可以用这按钮跳进去
- step out
  - 跳出对应的⽅方法

# 注释

- 单行注释 用 //
- 多行注注释用：
  - 单行注释 `// 这是单注释`
  - 多行注释 `/*这是多行注释*/`
  - Javadoc注释 `/**这是javadoc注释*/`

    ```java
    /*
    * 多行注释
    * @author xxx
    * @@version 1.0.0
    */
    ```

  `注意:注释内容不不能过多，也不不能过少，核⼼心逻辑⼀一定要加注释，⾃自⼰己衡量量`


# JAVA 模块划分和包的使用

- 不同的package里可以有相同名字的class
- 常⻅见的java⾃自带的包
  - java.lang 基础类包，默认⾃自动导⼊入的包，⾥里里⾯面有Obect, String, StringBuffer, System等包，应⽤用最⼴广
  - java.util 常⻅见的⼯工具类包
  - java.io 提供系统的输⼊入输出
  - [java.net](http://java.net/) 提供⽹网络操作相关的类
- 导入其他的包
  - import关键词导入
  -

    ```java
    //导⼊入util包下的Date类 import java.util.Date;
    // *号表示这个util包下⾯面的全部类都导⼊入进来 import java.util.*;
    ```


```java
import java.util.Random;

//这个是类
public class HomeWork3 {

    //这个是主方法
    public static void main(String [] args){
        System.out.println("今天这个是我的第一个程序");
        System.out.println("java课程");

        Random random1 = new Random();

        boolean b1 = random1.nextBoolean();

        System.out.println(b1);
    }
}
```