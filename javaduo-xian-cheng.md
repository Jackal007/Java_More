### 获取信息

* ##### currentThread\(\)

  返回代码段正在被哪个线程执行

  ```java
  public static void main(String[] args){
  System.out.println(Thread.currentThread().getName());
  }
  //输出：main
  ```

* ##### getId\(\)

  获取id

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

---

### 操作线程

* #### 停止线程

  * ##### stop\(\)

    是过气的方法，会出现问题

  * ##### interrupt\(\)

    在当前线程中打一个停止的标记，并不真正停止线程  
    要让它停下来就要在run函数中来判断停止的标记是否为真，真的话就return

  * ##### 在睡眠状态停止

    会抛出InterruptedException
* ##### 暂停线程

* ##### sleep\(long millis\) 线程睡眠 :

  在指定的毫秒数内让当前正在执行的线程休眠，使线程转到阻塞状态。当睡眠结束后，就转为就绪（Runnable）状态。sleep\(\)平台移植性好。



