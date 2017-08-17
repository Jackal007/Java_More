try-catch语句还可以包括第三部分，就是finally子句。它表示无论是否出现异常，都应当执行的内容。try-catch-finally语句的一般语法形式为：

```java
try {  
    // 可能会发生异常的程序代码  
} catch (Type1 id1) {  
    // 捕获并处理try抛出的异常类型Type1  
} catch (Type2 id2) {  
    // 捕获并处理try抛出的异常类型Type2  
} finally {  
    // 无论是否发生异常，都将执行的语句块  
} 
```

**try 块：**

用于捕获异常。其后可接零个或多个catch块，如果没有catch块，则必须跟一个finally块。

**catch 块：**

用于处理try捕获到的异常。

**finally 块：**

无论是否捕获或处理异常，finally块里的语句都会被执行。

当在try块或catch块中遇到return语句时，finally语句块将在方法返回之前被执行。在以下4种特殊情况下，finally块不会被执行：

1）在finally语句块中发生了异常。

2）在前面的代码中用了System.exit\(\)退出程序。

3）程序所在的线程死亡。

4）关闭CPU。



* 必须在 try 之后添加 catch 或 finally 块。try 块后可同时接 catch 和 finally 块，但至少有一个块。  若代码同时使用 catch 和 finally 块，则必须将 catch 块放在 try 块之后。
*  一个 try 块可能有多个 catch 块。若如此，则执行第一个匹配块。即Java虚拟机会把实际抛出的异常对象依次和各个catch代码块声明的异常类型匹配，如果异常对象为某个异常类型或其子类的实例，就执行这个catch代码块，不会再执行其他的 catch代码块
* 在 try-catch-finally 结构中，可重新抛出异常
* 当try没有捕获到异常时：try语句块中的语句逐一被执行，程序将跳过catch语句块，执行finally语句块和其后的语句
* 当try捕获到异常，catch语句块里没有处理此异常的情况：此异常将会抛给JVM处理，finally语句块里的语句还是会被执行，但finally语句块后的语句不会被执行



