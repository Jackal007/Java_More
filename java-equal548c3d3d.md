==比较的是地址是否相等

equal比较的是里面的值是否相等（自己写的类要自己实现，否则还是直接比较地址了）



```java
String a="abc";
```

这个代码会在内存中只创建一个被引号括起来的常量“abc”，然后有新的String b="abc"时候，会直接把b的值设置为和a一样的地址。

所以这时a==b的值是true

但是

```java
String a=new String("abc");
String b=new String("abc");
```

这样的话，会创建两个独立的变量。

