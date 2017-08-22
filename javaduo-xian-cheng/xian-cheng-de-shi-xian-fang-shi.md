Java 中实现多线程有两种方法：继承 Thread 类、实现 Runnable 接口，在程序开发中只要是多线程，肯定永远以实现 Runnable 接口为主，因为实现 **Runnable 接口相比继承 Thread 类有如下优势**：

* 可以避免由于 Java 的单继承特性而带来的局限；
* 增强程序的健壮性，代码能够被多个线程共享，代码与数据是独立的；
* 适合多个相同程序代码的线程区处理**同一资源**的情况。

---

```java
class MyThread extends Thread{  
    private int ticket = 5;  
    public void run(){  
        for (int i=0;i<10;i++)  
        {  
            if(ticket > 0){  
                System.out.println("ticket = " + ticket--);  
            }  
        }  
    }  
}  

public class ThreadDemo{  
    public static void main(String[] args){  
        new MyThread().start();  
        new MyThread().start();  
        new MyThread().start();  
    }  
}
```

执行结果：

![](/assets/im2port.png)

```java
class MyThread implements Runnable{  
    private int ticket = 5;  
    public void run(){  
        for (int i=0;i<10;i++)  
        {  
            if(ticket > 0){  
                System.out.println("ticket = " + ticket--);  
            }  
        }  
    }  
}  

public class RunnableDemo{  
    public static void main(String[] args){  
        MyThread my = new MyThread();  
        new Thread(my).start();  
        new Thread(my).start();  
        new Thread(my).start();  
    }  
}
```

![](/assets/im34port.png)

from [http://www.cnblogs.com/wxd0108/p/5479442.html](http://www.cnblogs.com/wxd0108/p/5479442.html)

---

## 一个奇葩

```java
public class ThreadTest {

    public static void main(String[] args) {
        for (int i = 0; i < 100; i++) {
            System.out.println(Thread.currentThread().getName() + " " + i);
            if (i == 30) {
                Runnable myRunnable = new MyRunnable();
                Thread thread = new MyThread(myRunnable);
                thread.start();
            }
        }
    }
}

class MyRunnable implements Runnable {
    private int i = 0;

    @Override
    public void run() {
        System.out.println("in MyRunnable run");
        for (i = 0; i < 100; i++) {
            System.out.println(Thread.currentThread().getName() + " " + i);
        }
    }
}

class MyThread extends Thread {

    private int i = 0;

    public MyThread(Runnable runnable){
        super(runnable);
    }

    @Override
    public void run() {
        System.out.println("in MyThread run");
        for (i = 0; i < 100; i++) {
            System.out.println(Thread.currentThread().getName() + " " + i);
        }
    }
}
```

注意到里面的Thread thread = new MyThread\(myRunnable\);没有

那么这种方式可以顺利创建出一个新的线程么？答案是肯定的。至于此时的线程执行体到底是MyRunnable接口中的run\(\)方法还是MyThread类中的run\(\)方法呢？通过输出我们知道线程执行体是MyThread类中的run\(\)方法。其实原因很简单，因为Thread类本身也是实现了Runnable接口，而run\(\)方法最先是在Runnable接口中定义的方法。

我们看一下Thread类中对Runnable接口中run\(\)方法的实现：

```java
　　@Override public void run() {        
        if (target != null) {
            target.run();
        }
    }
```

也就是说，当执行到Thread类中的run\(\)方法时，会首先判断target是否存在，存在则执行target中的run\(\)方法，也就是实现了Runnable接口并重写了run\(\)方法的类中的run\(\)方法。但是上述给到的列子中，由于多态的存在，根本就没有执行到Thread类中的run\(\)方法，而是直接先执行了运行时类型即MyThread类中的run\(\)方法。

