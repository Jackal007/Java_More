在Java中，异常通过try-catch语句捕获。其一般语法形式为：

```java
try {//监控区域
    // 可能会发生异常的程序代码  
} catch (Type1 id1){  
    // 捕获并处置try抛出的异常类型Type1  
}  
catch (Type2 id2){  
     //捕获并处置try抛出的异常类型Type2  
}  
```

 关键词try后的一对大括号将一块可能发生异常的代码包起来，称为**监控区域**。Java方法在运行过程中出现异常，则创建异常对象。将异常抛出监控区域之 外，由Java运行时系统试图寻找匹配的catch子句以捕获异常。若有匹配的catch子句，则运行其异常处理代码，try-catch语句结束。

       匹配的原则是：如果抛出的异常对象属于catch子句的异常类，或者属于该异常类的子类，则认为生成的异常对象与catch块捕获的异常类型相匹配。

需要注意的是，一旦某个catch捕获到匹配的异常类型，将进入异常处理代码。一经处理结束，就意味着整个try-catch语句结束。其他的catch子句不再有匹配和捕获异常类型的机会。



Java通过异常类描述异常类型。对于有多个catch子句的异常程序而言，应该尽量将捕获底层异常类的catch子 句放在前面，同时尽量将捕获相对高层的异常类的catch子句放在后面。否则，捕获底层异常类的catch子句将可能会被屏蔽。

      RuntimeException异常类包括运行时各种常见的异常，ArithmeticException类和ArrayIndexOutOfBoundsException类都是它的子类。因此，RuntimeException异常类的catch子句应该放在最后面，否则可能会屏蔽其后的特定异常处理或引起编译错误。

