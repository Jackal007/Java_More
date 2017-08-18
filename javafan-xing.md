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



> ```
> 作者：孔垂云
> 链接：http://www.jianshu.com/p/d4c00768d776
> 來源：简书
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
> ```





