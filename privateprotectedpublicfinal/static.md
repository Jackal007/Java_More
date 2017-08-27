JAVA静态方法在子类中写一样的叫做重载，不是重写。因为静态方法只与类相关，不与具体实现相关，声明的是什么类，则引用相应类的静态方法，看下例子：

```java
class Base{  
        static void a( ){System.out.println("A");  }  
                 void b( ){System.out.println("B"); }  
}  
public class  Inherit extends Base{  
          static void a( ){System.out.println("C");  }  
                  void b( ){System.out.println("D"); }  
           public static void main(String args[]){  
                    Base b=new Base();  
                    Base  c=new Inherit();  
                    b.a();  
                    b.b();  
                    c.a();  
                    c.b();  
         }  
}  
```

以上输出的结果是：A  
                                 B  
                                 A  
                                 D  
       非静态方法按重写规则调用相应的类实现方法，而静态方法只与类相关。

       所谓静态，就是在运行时，虚拟机已经认定此方法属于哪个类。

"重写"只能适用于实例方法.不能用于静态方法.对于静态方法,只能隐藏\(刚才的例子可以重写那只是形式上的 ，并不满足多态的特征，所以严格说不是重写\)。

      静态方法的调用不需要实例化.  不实例化也就不能用多态了，也就没有所谓的父类引用指向子类实例.因为不能实例化也就没有机会去指向子类的实例。所以也就不存在多态了。

