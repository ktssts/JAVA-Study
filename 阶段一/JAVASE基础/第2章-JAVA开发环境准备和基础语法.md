# 第二章 JAVA 开发环境准备和基础语法

# 1.CMD Sublime工具安装，环境变量介绍使用。

- Sublime简单的文本工具，轻量级写代码-不过用intellij用习惯了。
- CMD，mac终端：dos命令语句，需要学习
- JDK安装，环境变量设定

# 2.环境变量设定

# 3.完成第一个java程序

```java
public class Main{
	public static void main(String [] args){
		System.out.println("hello");
  }
}
```

刚开始学习的时候，全部要手打出来。不要用快捷键，让大脑记忆

# 4.第一个程序的基础语法分析

关于命名和书写格式

- java文件名必须和类名相同，后缀为.java。 那一个文件里可以有多个类吗？
    - 可以有多个类，但最多只能有一个被public修饰的class。 且若这个. java文件中有一个public类型的class，则这个class名需与.java文件名一致。
- 类class
    - 表示声明一个类，类名的首字母要大写。驼峰书写格式。
- 方法method：方法名要小写字母开头
- 主方法
    - 固定搭配：public static void main(String[] args){}
- 所有的变量、名称都是大小写敏感的！只有大括号{}后面不加; 其他都加;收尾