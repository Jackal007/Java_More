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

> 在使用isAlive\(\)时，如果将线程对象以构造参数的方式传给Thread对象进行start启动，运行的结果是呵呵的。
>
> 因为current和this的差异



