Java反射机制可以让我们在编译期（Compile Time）之外的运行期（Runtime）获得任何一个类的字节码。包括接口、变量、方法等信息。还可以让我们在运行期实例化对象，通过调用get/set方法获取变量的值。下面是一个小例子，让大家感受下Java反射的魔力

```java
Method[] methods = MyObject.class.getMethods();

for(Method method : methods){
    System.out.println("method = " + method.getName());
}
```

这个例子通过调用类的class属性获取对应的class对象，通过这个 Class 类的对象获取 MyObject 类中的方法集合

```java
Class myObjectClass = MyObject.class;
```

使用 Java 反射机制可以在运行时期检查 Java 类的信息，检查 Java 类的信息往往是你在使用 Java 反射机制的时候所做的第一件事情

  


> 作者：总是擦破皮
>
> 链接：http://www.jianshu.com/p/2315dda64ad2
>
> 來源：简书
>
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



