```java
public void subMoney(int money){  
    synchronized (this) {  //这样就是把当前这个对象给锁起来了，如果只是要保证代码块同步可以用其他变量
        //xxxxxx
    }   
}  
```



