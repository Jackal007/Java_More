> from ： [http://blog.csdn.net/hguisu/article/details/6155636](http://blog.csdn.net/hguisu/article/details/6155636)
>
> 参考：http://www.cnblogs.com/langtianya/p/5139465.html

异常指不期而至的各种状况，如：文件找不到、网络连接失败、非法参数等。异常是一个事件，它发生在程序运行期间，干扰了正常的指令流程。Java通 过API中Throwable类的众多子类描述各种不同的异常。因而，Java异常都是对象，是Throwable子类的实例，描述了出现在一段编码中的 错误条件。当条件生成时，错误将引发异常。

Java异常类层次结构图：

![](/assets/ Java异常类层次结构图.png)

Java 中，所有的异常都有一个共同的祖先 Throwable（可抛出）。Throwable 指定代码中可用异常传播机制通过 Java 应用程序传输的任何问题的共性。

**Throwable：**

有两个重要的子类：Exception（异常）和 Error（错误），二者都是 Java 异常处理的重要子类，各自都包含大量子类。

| 函数 |  |
| :--- | :--- |
| public Throwable\(\) |  |
| public Throwable\(String message\) |  |
| public Throwable\(String message,   Throwable cause\) |  |
| public Throwable\(Throwable cause\) |  |
| public final void addSuppressed\(Throwable exception\) | 当一个异常被抛出的时候，可能有其他异常因为该异常而被抑制住，从而无法正常抛出。这时可以通过addSuppressed方法把这些被抑制的方法记录下来。被抑制的异常会出现在抛出的异常的堆栈信息中，也可以通过getSuppressed方法来获取这些异常。这样做的好处是不会丢失任何异常，方便开发人员进行调试 |
|public Throwable fillInStackTrace()  |可以追溯到栈的底部|
|public void printStackTrace()  |将Throwable对象的栈轨迹信息打印到标准错误输出流上  |
|public void printStackTrace(PrintStream s)  |  |
|public void printStackTrace(PrintWriter s)  |  |
|public StackTraceElement [] getStackTrace()  |  |
|public void setStackTrace(StackTraceElement [] stackTrace)  |  |
|  |  |



