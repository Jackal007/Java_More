### [线程同步synchronized](/javaduo-xian-cheng/tong-bu-ff0c-suo.md)为什么要线程同步

因为当我们有多个线程要同时访问一个变量或对象时，如果这些线程中既有读又有写操作时，就会导致变量值或对象的状态出现混乱，从而导致程序异常。举个例子，如果一个银行账户同时被两个线程操作，一个取100块，一个存钱100块。假设账户原本有0块，如果取钱线程和存钱线程同时发生，会出现什么结果呢？取钱不成功，账户余额是100.取钱成功了，账户余额是0.那到底是哪个呢？很难说清楚。因此多线程同步就是要解决这个问题。

### Synchronized

* 修饰方法前
* ```java
  Public synchronized void methodA(){}
  ```
* 加在代码块前

* ```java
  synchronized (this){}  
  synchronized (一个变量){}
  ```



