* ##### **yield\(\) 线程让步 :**

  暂停当前正在执行的线程对象，把执行的机会让给其他线程，相同或者更高优先级的线程。sleep\(\) 可以让优先级比较低的线程执行，而yield不行，只是退让高的。

* ##### **join\(\) 线程加入 :**

  指等待t线程终止。 t.join\(\) 表示其他线程阻塞，要等待t执行完毕才能执行。

  > 为什么要用join\(\)方法？
  >
  > 在很多情况下，主线程生成并起动了子线程，如果子线程里要进行大量的耗时的运算，主线程往往将于子线程之前结束，但是如果主线程处理完其他的事务后，需要用到子线程的处理结果，也就是主线程需要等待子线程执行完成之后再结束，这个时候就要用到join\(\)方法了。

** setPriority\(\) 更改线程的优先级 :**

MIN\_PRIORITY = 1  
  　　  NORM\_PRIORITY = 5  
           MAX\_PRIORITY = 10

用法：

```java
Thread4 t1 = new Thread4("t1");
Thread4 t2 = new Thread4("t2");
t1.setPriority(Thread.MAX_PRIORITY);
t2.setPriority(Thread.MIN_PRIORITY);
```

**interrupt\(\):不要以为它是中断某个线程！它只是线线程发送一个中断信号，让线程在无限等待时（如死锁时）能抛出抛出，从而结束线程，但是如果你吃掉了这个异常，那么这个线程还是不会中断的！**

---

**isAlive\(\): 判断一个线程是否存活**

**activeCount\(\): 程序中活跃的线程数**

**enumerate\(\): 枚举程序中的线程**

**currentThread\(\): 得到当前线程**

**isDaemon\(\): 一个线程是否为守护线程**

**setDaemon\(\): 设置一个线程为守护线程\(用户线程和守护线程的区别在于，是否等待主线程依赖于主线程结束而结束\) **

**setName\(\): 为线程设置一个名称**

---

**wait\(\)** **线程等待**：Object类中的wait\(\)方法，导致当前的线程等待，直到其他线程调用此对象的 notify\(\) 方法或 notifyAll\(\) 唤醒方法。这个两个唤醒方法也是Object类中的方法，行为等价于调用 wait\(0\) 一样。wait\(\)方法是Object类里的方法；**当一个线程执行到wait\(\)方法时，它就进入到一个和该对象相关的等待池中**，同时失去（释放）了对象的机锁（暂时失去机锁，wait\(long timeout\)超时时间到后还需要返还对象锁）；其他线程可以访问；wait\(\)使用notify或者notifyAlll或者指定睡眠时间来唤醒当前等待池中的线程。wiat\(\)必须放在synchronized block中，否则会在program runtime时扔出”java.lang.IllegalMonitorStateException“异常。

> #### wait和sleep区别
>
> **共同点：**
>
> 1. 他们都是在多线程的环境下，都可以在程序的调用处阻塞指定的毫秒数，并返回。
>
> 2. wait\(\)和sleep\(\)都可以通过interrupt\(\)方法 打断线程的暂停状态 ，从而使线程立刻抛出InterruptedException。
>
>    如果线程A希望立即结束线程B，则可以对线程B对应的Thread实例调用interrupt方法。如果此刻线程B正在wait/sleep /join，则线程B会立刻抛出InterruptedException，在catch\(\) {} 中直接return即可安全地结束线程。
>
>    需要注意的是，InterruptedException是线程自己从内部抛出的，并不是interrupt\(\)方法抛出的。对某一线程调用 interrupt\(\)时，如果该线程正在执行普通的代码，那么该线程根本就不会抛出InterruptedException。但是，一旦该线程进入到 wait\(\)/sleep\(\)/join\(\)后，就会立刻抛出InterruptedException 。
>
> **不同点：             
> **
>
> 1. Thread类的方法：sleep\(\),yield\(\)等
>
>    Object的方法：wait\(\)和notify\(\)等
>
> 2. 每个对象都有一个锁来控制同步访问。Synchronized关键字可以和对象的锁交互，来实现线程的同步。
>
>    **sleep方法没有释放锁，而wait方法释放了锁**，使得其他线程可以使用同步控制块或者方法。
>
> 3. wait，notify和notifyAll只能在同步控制方法或者同步控制块里面使用，而sleep可以在任何地方使用
>
> 所以sleep\(\)和wait\(\)方法的最大区别是：
>
> **sleep\(\)睡眠时，保持对象锁，仍然占有该锁；            
> **
>
> **　　　　而wait\(\)睡眠时，释放对象锁。            
> **
>
> 但是wait\(\)和sleep\(\)都可以通过interrupt\(\)方法打断线程的暂停状态，从而使线程立刻抛出InterruptedException（但不建议使   用该方法）。

**notify\(\) 线程唤醒**：Object类中的notify\(\)方法，唤醒在此对象监视器上等待的单个线程。如果所有线程都在此对象上等待，则会选择唤醒其中一个线程。选择是任意性的，并在对实现做出决定时发生。线程通过调用其中一个 wait 方法，在对象的监视器上等待。 直到当前的线程放弃此对象上的锁定，才能继续执行被唤醒的线程。被唤醒的线程将以常规方式与在该对象上主动同步的其他所有线程进行竞争；例如，唤醒的线程在作为锁定此对象的下一个线程方面没有可靠的特权或劣势。类似的方法还有一个notifyAll\(\)，唤醒在此对象监视器上等待的所有线程。

> _**注意**：Thread中suspend\(\)和resume\(\)两个方法在JDK1.5中已经废除，因为有死锁倾向。_

---

**synchronized\(xx\) 给一个资源加锁：**

> ### 看一个例子
>
> 建立三个线程，A线程打印10次A，B线程打印10次B,C线程打印10次C，要求线程同时运行，交替打印10次ABC。这个问题用Object的wait\(\)，notify\(\)就可以很方便的解决。代码如下：
>
> ```java
> package com.multithread.wait;
> public class MyThreadPrinter2 implements Runnable {   
>       
>     private String name;   
>     private Object prev;   
>     private Object self;   
>   
>     private MyThreadPrinter2(String name, Object prev, Object self) {   
>         this.name = name;   
>         this.prev = prev;   
>         this.self = self;   
>     }   
>   
>     @Override  
>     public void run() {   
>         int count = 10;   
>         while (count > 0) {   
>             synchronized (prev) {   
>                 synchronized (self) {   
>                     System.out.print(name);   
>                     count--;  
>                     
>                     self.notify();   
>                 }   
>                 try {   
>                     prev.wait();   
>                 } catch (InterruptedException e) {   
>                     e.printStackTrace();   
>                 }   
>             }   
>   
>         }   
>     }   
>   
>     public static void main(String[] args) throws Exception {   
>         Object a = new Object();   
>         Object b = new Object();   
>         Object c = new Object();   
>         MyThreadPrinter2 pa = new MyThreadPrinter2("A", c, a);   
>         MyThreadPrinter2 pb = new MyThreadPrinter2("B", a, b);   
>         MyThreadPrinter2 pc = new MyThreadPrinter2("C", b, c);   
>            
>            
>         new Thread(pa).start();
>         Thread.sleep(100);  //确保按顺序A、B、C执行
>         new Thread(pb).start();
>         Thread.sleep(100);  
>         new Thread(pc).start();   
>         Thread.sleep(100);  
>         }   
> }
> ```
>
> 每次要打印前要先获得前一个，再获得自己才能打印。
>
> 先获得前一个是因为要保证在前一个打印完才能自己打印；
>
> 获得自己是因为要保证自己打印的时候下一个不能打印。

from [http://blog.csdn.net/evankaka/article/details/44153709](http://blog.csdn.net/evankaka/article/details/44153709)

