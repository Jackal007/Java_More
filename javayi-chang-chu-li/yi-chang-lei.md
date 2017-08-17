在Java中提供了一些异常用来描述经常发生的错误，对于这些异常，有的需要程序员进行捕获处理或声明抛出，有的是由Java虚拟机自动进行捕获处理。Java中常见的异常类:

### **1. runtimeException子类:**

> 1、 java.lang.ArrayIndexOutOfBoundsException
>  
>     数组索引越界异常。当对数组的索引值为负数或大于等于数组大小时抛出。
>  
>     2、java.lang.ArithmeticException
>  
>     算术条件异常。譬如：整数除零等。
>  
>     3、java.lang.NullPointerException
>  
>     空指针异常。当应用试图在要求使用对象的地方使用了null时，抛出该异常。譬如：调用null对象的实例方法、访问null对象的属性、计算null对象的长度、使用throw语句抛出null等等
>  
>     4、java.lang.ClassNotFoundException
>  
>     找不到类异常。当应用试图根据字符串形式的类名构造类，而在遍历CLASSPAH之后找不到对应名称的class文件时，抛出该异常。
> 5、java.lang.NegativeArraySizeException 数组长度为负异常
>
>    6、java.lang.ArrayStoreException数组中包含不兼容的值抛出的异常
>
>    7、java.lang.SecurityException安全性异常  
>
>
>   8、java.lang.IllegalArgumentException非法参数异常

### 2.**IOException**

> IOException：操作输入流和输出流时可能出现的异常。
>
> EOFException   文件已结束异常
>
> FileNotFoundException   文件未找到异常

### 3. 其他

> ClassCastException    类型转换异常类
>
> ArrayStoreException  数组中包含不兼容的值抛出的异常
>
> SQLException   操作[数据库](http://lib.csdn.net/base/mysql)异常类
>
> NoSuchFieldException   字段未找到异常
>
> NoSuchMethodException   方法未找到抛出的异常
>
> NumberFormatException    字符串转换为数字抛出的异常
>
> StringIndexOutOfBoundsException 字符串索引超出范围抛出的异常
>
> IllegalAccessException  不允许访问某类异常
>
> InstantiationException  当应用程序试图使用Class类中的newInstance\(\)方法创建一个类的实例，而指定的类对象无法被实例化时，抛出该异常



