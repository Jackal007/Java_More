## 泛型的好处

> 没有泛型的话很多时候要进行强制类型转换：
>
> ```java
> ArrayList al = new ArrayList();
> al.add("ysjian001");
> al.add(1);
> al.add(new Object());
> String first = (String) al.get(0);
> ```

**1，类型安全。**泛型的主要目标是提高 Java 程序的类型安全。通过知道使用泛型定义的变量的类型限制，编译器可以在一个高得多的程度上验证类型假设。没有泛型，这些假设就只存在于程序员的头脑中（或者如果幸运的话，还存在于代码注释中）。

**2，消除强制类型转换。**泛型的一个附带好处是，消除源代码中的许多强制类型转换。这使得代码更加可读，并且减少了出错机会。

**3，潜在的性能收益。**泛型为较大的优化带来可能。在泛型的初始实现中，编译器将强制类型转换（没有泛型的话，程序员会指定这些强制类型转换）插入生成的字节码中。但是更多类型信息可用于编译器这一事实，为未来版本的 JVM 的优化带来可能。由于泛型的实现方式，支持泛型（几乎）不需要 JVM 或类文件更改。所有工作都在编译器中完成，编译器生成类似于没有泛型（和强制类型转换）时所写的代码，只是更能确保类型安全而已。

**4.提高代码可复用性**

### **泛型类**

```java
// 泛型类：把泛型定义在类上 
public class ObjectTool<T> { 
      private T obj; 
      public T getObj() { 
         return obj; 
      } 
      public void setObj(T obj) { 
           this.obj = obj;
     }
}
//  泛型类的测试 
public class ObjectToolDemo { 
    public static void main(String[] args) { 
        ObjectTool<String> ot = new ObjectTool<String>();    
        ot.setObj(new String("中国")); 
        String s = ot.getObj(); 
        System.out.println("姓名是：" + s); 
        ObjectTool<Integer> ot2 = new ObjectTool<Integer>();    
        ot2.setObj(new Integer(69)); 
        Integer i = ot2.getObj(); 
        System.out.println("年龄是：" + i); 
   }
}
```

### 泛型方法

```java
* * 泛型方法：把泛型定义在方法上 **
public class ObjectTool {  
      public <T> void show(T t) {
           System.out.println(t); 
      }
}
  public class ObjectToolDemo { 
        public static void main(String[] args) { 
             // 定义泛型方法后
            ObjectTool ot = new ObjectTool(); 
            ot.show("hello"); 
            ot.show(100);
            ot.show(true);
       }
  }
```

### 泛型接口

```java
/* * 泛型接口：把泛型定义在接口上 */
public interface Inter<T> { 
  public abstract void show(T t);
}
//实现类在实现接口的时候，我们会遇到两种情况
//第一种情况：已经知道是什么类型的了
public class InterImpl implements Inter<String> { 
@Override 
public void show(String t) { 
  System.out.println(t);
}
}
//第二种情况：还不知道是什么类型的
public class InterImpl<T> implements Inter<T> { 
@Override 
public void show(T t) { 
       System.out.println(t);
}
}
public class InterDemo { 
  public static void main(String[] args) {
      // 第一种情况的测试
     Inter<String> i = new InterImpl(); 
     i.show("hello"); 
     // 第二种情况的测试
     Inter<String> i = new InterImpl<String>(); 
     i.show("hello"); 
     Inter<Integer> ii = new InterImpl<Integer>(); 
     ii.show(100);
}
}
```

```java
// ?表示任意的类型都是可以的
Collection<?> c5 = new ArrayList<Object>();

/ ? extends E:向下限定，E及其子类
Collection<? extends Animal> c10 = new ArrayList<Animal>();
Collection<? extends Animal> c11 = new ArrayList<Dog>();

// ? super E:向上限定，E极其父类
Collection<? super Animal> c13 = new ArrayList<Object>();
Collection<? super Animal> c14 = new ArrayList<Animal>();
```

**使用大写字母A,B,C,D......X,Y,Z定义的，就都是泛型，把T换成A也一样，这里T只是名字上的意义而已**

* **？**
   表示不确定的java类型
* **T \(type\)**
   表示具体的一个java类型
* **K V \(key value\)**
   分别代表java键值中的Key Value
* **E \(element\)**
   代表Element

String和Integer不是Object的子类

> ```
> 作者：孔垂云
> 链接：http://www.jianshu.com/p/d4c00768d776
> 來源：简书
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
> ```



