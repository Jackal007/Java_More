### 获取信息

* ##### currentThread\(\)

  返回代码段正在被哪个线程执行

  ```java
  public static void main(String[] args){
  System.out.println(Thread.currentThread().getName());
  }
  //输出：main
  ```

* ##### isAlive\(\)

  判断当前线程是否处于活动状态\(已经启动，尚未终止\)

  ```java
  public MyThread extends Tread{
      public void run(){
              System.out.println(this.isAlive());
      }
  }
  ```

  > 看不懂
  >
  > 在使用isAlive\(\)时，如果将线程对象以构造参数的方式传给Thread对象进行start启动，运行的结果是呵呵的。
  >
  > 因为current和this的差异

* ##### 判断线程是否停止

  * ##### interrupted\(\)

    测试运行xxx.interrupted\(\)的线程是否已经中断  
    具有清除状态的功能，调用后清除原先的状态，变为false

  * ##### isInterrupted\(\)

    测试xx线程是否已经中断，不会清除状态
* ##### getId\(\)

  获取id

* ##### activeCount\(\)

  程序中活跃的线程数

* ##### enumerate\(\):

  枚举程序中的线程

* ##### currentThread\(\):

  得到当前线程

* ##### isDaemon\(\)

  一个线程是否为守护线程

* ##### setDaemon\(\):

  设置一个线程为守护线程\(用户线程和守护线程的区别在于，是否等待主线程依赖于主线程结束而结束\)

* ##### setName\(\)

  为线程设置一个名称

---

### 操作线程

* #### 停止线程

  * ##### stop\(\)

    是过气的方法，会出现问题

  * ##### interrupt\(\)

    在当前线程中打一个停止的标记，并不真正停止线程  
    要让它停下来就要在run函数中来判断停止的标记是否为真，真的话就return  
    **它只是线线程发送一个中断信号，让线程在无限等待时（如死锁时）能抛出抛出，从而结束线程，但是如果你吃掉了这个异常，那么这个线程还是不会中断的！**

  * ##### 在睡眠状态停止

    会抛出InterruptedException
* ##### 暂停线程

  * ##### suspend\(\)

    挂起线程

  * ##### resume\(\)

    恢复线程
* ##### sleep\(long millis\) 线程睡眠 :

  在指定的毫秒数内让当前正在执行的线程休眠，使线程转到阻塞状态。当睡眠结束后，就转为就绪（Runnable）状态。sleep\(\)平台移植性好。

* ##### join\(\) 线程加入 :

  指等待t线程终止。 t.join\(\) 表示其他线程阻塞，要等待t执行完毕才能执行。

  > 为什么要用join\(\)方法？  
  > 在很多情况下，主线程生成并起动了子线程，如果子线程里要进行大量的耗时的运算，主线程往往将于子线程之前结束，但是如果主线程处理完其他的事务后，需要用到子线程的处理结果，也就是主线程需要等待子线程执行完成之后再结束，这个时候就要用到join\(\)方法了。

* ##### 优先级

  * ##### setPriority\(\)

    更改线程的优先级（具有继承性：子线程和父线程优先级一样）
    MIN\_PRIORITY = 1 　　 NORM\_PRIORITY = 5 MAX\_PRIORITY = 10

  用法：

  ```java
  Thread4 t1 = new Thread4("t1");
  Thread4 t2 = new Thread4("t2");
  t1.setPriority(Thread.MAX_PRIORITY);
  t2.setPriority(Thread.MIN_PRIORITY);
  ```

* ##### getPriority\(\)



