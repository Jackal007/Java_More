在JavaSE5.0中新增了一个java.util.concurrent包来支持同步。ReentrantLock类是可重入、互斥、实现了Lock接口的锁， 它与使用synchronized方法和快具有相同的基本行为和语义，并且扩展了其能力。

ReenreantLock类的常用方法有：

ReentrantLock\(\) : 创建一个ReentrantLock实例

lock\(\) : 获得锁

unlock\(\) : 释放锁

**它能做到一些比synchronized高级的操作。**

注：ReentrantLock\(\)还有一个可以创建公平锁的构造方法，但由于能大幅度降低程序运行效率，不推荐使用

```java
package threadTest;  

import java.util.concurrent.locks.Lock;  
import java.util.concurrent.locks.ReentrantLock;  
 
public class XX{  

    //需要声明这个锁  
    private Lock lock = new ReentrantLock();  
 
    public void addMoney(int money) {  
        lock.lock();//上锁  
        //做一些事情
        lock.unlock();//解锁  
    }
}
```



