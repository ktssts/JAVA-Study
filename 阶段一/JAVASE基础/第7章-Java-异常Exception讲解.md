# 第7章 Java 异常Exception讲解

# **Java异常Exception讲解**

**介绍什么是异常，java出现异常的场景**

- 什么是错误
    - 程序运行时发生的不被期望的事件，阻止程序按照预期正常执⾏
    - 常⻅程序错误分三类
        - 编译错误:新手最常见，没遵循语法规范
        - 运⾏时错误:程序在执行时
        - 逻辑错误:程序没有按照预期的逻辑顺序执⾏
- Java.lang软件包中有⼀个java.lang.Throwable类，这个类是java中所有错误和异常的超类,Throwable类有两个子类，Error与 Exception
    - Error
        - 是Throwable 的子类，包含⼤量子类
        - 出错后程序⽆法处理，如OutOfMemoryError
    - Exception
        - 是Throwable 的⼦类，包含⼤量⼦类
        - 程序本身可以处理的异常，如ArrayIndexOutOfBoundException
    - 两大类
        - 可查异常(编译器要求必须处置的异常):RuntimeException及其⼦类以外，其他的Exception类及其⼦类, 如 IOException和ClassNotFoundException
        - 不可查异常(编译器不要求强制处置的异常): 包括运⾏时异常(RuntimeException与其
          ⼦类)和错误(Error)，如ArrayIndexOutOfBoundsException

      ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7579abb1-2661-4b55-a86d-da394a100f66/Untitled.png)


# **Java内置异常体系分类和核⼼方法讲解**

**java内置的异常和Throwable核⼼心⽅方法介绍**

- java内置异常
    - 可查异常(必须要在⽅法里⾯捕获或者抛出)
        - ClassNoFoundException 应用程序试图加载类，找不到对应的类
        - IllegalAccessException 拒绝访问⼀个类的时候
        - NoSuchFieldExcetion 请求的变量不存在
        - NoSuchMethodException 方法不存在
    - 不可查异常
        - ArrayIndexOutOfBoundsException 数组索引越界
        - ClassCastException 强制失败抛出异常
        - NullPointerException 需要对象的地⽅使用 null 时，抛出该异常
        - NumberFormatException 将字符串转换成一种数值类型，但该字符串不能转换为适当格时，抛出该异常
- Throwable类核⼼⽅法
    - public String getMessage()
        - 异常的详细信息
    - public Throwable getCause()
        - 异常原因
    - public void printStackTrace()
        - 打印错误的堆栈信息，即错误输出流，可以看到错误原因和所在位置
    - public StackTraceElement [] getStackTrace()
        - 堆栈层次的数组，下标为0的元素代表栈顶，最后一个元素代表⽅法调用堆栈的栈底
        -

# **java进阶基础之Try Catch异常捕获**

**讲解使用Try Catch进⾏异常捕获**

- 异常处理理之捕获
    - 语法
    -

    ```java
    try{
    // 可能发⽣生异常的代码
    }catch(AExceptionName e){
    //出异常的时候处理理
    }catch(BExceptionName e){
    }fianall{
    }
    ```

    - try后⾯跟⼀个或多个catch块，或⼀个finally块，或两者的组合
    - catch 不不能独⽴立于 try ⽽而单独存在
    - 如果代码没有对应的异常类进行捕获，则默认打印异常堆栈

# **Java异常进阶之Finally讲解和多重捕获**

**finally和多重异常捕获**

- 一个 try 代码块后⾯跟多个 catch 代码块的情况就叫多重捕获
    - 语法

    ```java
    	try
    // 可能发⽣生异常的代码
    }catch(ExceptionName1 e1){
    //出异常的时候处理理
    }catch(ExceptionName2 e2){
    //出异常的时候处理理
    }
    ```

    - 代码中发⽣异常，异常被抛给第一个 catch 块, 如果不匹配则继续往下⼀个catch进⾏传递
- finally关键字


    - 用来创建在 try 代码块后面执行的代码块
    - finally 代码块中的代码总会被执行
    - 一般⽤于资源回收释放等操作
    - 语法:
    
    ```java
    try{
    // 可能发⽣生异常的代码
    
    }catch(ExceptionName1 e1){
    //出异常的时候处理理
    
    }finally{
    //肯定执⾏行行的代码
    
    }
    ```


或者

```java
try{
// 可能发⽣生异常的代码

}finally{
//肯定执⾏行行的代码

}
```

- 课程代码演示 ⾯试题，返回结果最终是finally为准(尽量不要在finally里⾯使⽤return，会忽略try catch⾥面的return，容易造成未知的bug)

```
public static int divide(int num1, int num2){
    try {
        int result = num1/num2;
				 return result;
    }catch (Exception e){
			System.out.println("出异常")

		}finally {
			System.out.println("finally执行了了");
			return -2; }
			//return -1;}
```

- 三者的组合
    - try，catch和finally块有两种可能的组合:try-catch-finally或try-finally。

# **java异常处理理之throws/throw关键词**

**讲解异常的抛出throw和声明throws**

- 代码出异常⻅的处理⽅法
    - try catch捕获
    - throws 声明异常 往外抛出
        - 语法:throws子句放在方法参数列表的右括号之后，⼀个⽅法可以声明抛出多个异常，多个异常之间用逗号隔开。
        - 例⼦

```
public class Main {
  public static void readChar() throws
IOException,RemoteException {
    int input = System.in.read();
 }
}
```

- try catch中捕获了异常，处理方法
    - 当前捕获自己处理
    - 捕获自己处理然后继续往外⾯抛异常
        - 语法

        ```java
        throw new ExceptionName("异常信息");
        
        ```

        - 例子

        ```java
        throw  new IOException("File not  found")
        ```


总结:当抛出一个被检查的异常，我们必须使⽤try-catch块来处理它，或者在方法声明中使用
throws⼦句继续往外抛

# **java进阶基础之⾃定义异常**

**讲解使用java进行自定义异常**

- 为什么要使⽤⾃定义异常
    - 当前JDK内置的异常不满足需求,项⽬会出现特有异常
    - 自定义异常可以让业务更清晰
- 如何进行⾃定义异常
    - 异常都是继承自Exception类，所以我们要自定义的异常也需要继承这个基类。
- 例子

```java
public class BaseException extends Exception {

    private  String errorMessage;
    private  String errorCode;

    public BaseException(String errorCode,String errorMessage){
        super(errorMessage);
        this.errorCode = errorCode;
        this.errorMessage = errorMessage;
    }

    public  String getErrorMessage() {
        return errorMessage;
    }

    public  String getErrorCode() {
        return errorCode;
    }

    public  void setErrorCode(String errorCode) {
        this.errorCode = errorCode;
    }

    public  void setErrorMessage(String errorMessage) {
        this.errorMessage = errorMessage;
    } 
}
```