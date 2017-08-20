作用：调用包装在当前Method对象中的方法。

原型：Object invoke（Object obj,Object...args）

参数解释：

```java
obj：实例化后的对象
args：用于方法调用的参数
```

返回：根据obj和args调用的方法的返回值

抛出错误：

```java
IllegalAccessException    //Method对象强制[Java](http://lib.csdn.net/base/java)语言执行控制 或 无权访问obj对象

IllegalArgumentException    //方法是实例化方法，而指定需要调用的对象并不是实例化后的类或接口
```

例：

```java
Class l = Class.forName("test1.A"); 
Object obj1 = l.newInstance(); 
Object[] obj2 = new Object[1];
obj2[0] = new String("hello world"); 
Method m = l.getMethod("a1",new Class[] { String.class });
Object obj3 = m.invoke(obj1, obj2);
```



