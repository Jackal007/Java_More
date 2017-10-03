```java
public void subMoney(int money){  
    xxx
    synchronized (this) {  //这样就是把当前这个对象给锁起来了，如果只是要保证代码块同步可以用其他变量
        //xxxxxx
    }   
    xxx
}
```

只会将代码块锁起来，其他非同步部分不被锁住，比如当前函数中的非同步部分。

