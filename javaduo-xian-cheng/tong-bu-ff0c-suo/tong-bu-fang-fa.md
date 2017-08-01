### 对象方法：

```java
public synchronized void methodA()
{
    //…
}
```

这样子做会把这一整个**对象**锁定起来，同一个类生成的其他对象不会被锁定。

### 类方法：

```java
public synchronized static void methodAAA()   // 同步的static 函数  
{  
//….  
}  
```



