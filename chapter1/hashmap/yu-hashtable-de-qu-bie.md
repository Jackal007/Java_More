### 主要的区别有：线程安全性，同步\(synchronization\)，以及速度

HashMap几乎可以等价于Hashtable，除了HashMap是非synchronized的，并可以接受null\(HashMap可以接受为null的键值\(key\)和值\(value\)，而Hashtable则不行\)。

1. HashMap是非synchronized，而Hashtable是synchronized，这意味着Hashtable是线程安全的，多个线程可以共享一个Hashtable；而如果没有正确的同步的话，多个线程是不能共享HashMap的。Java 5提供了ConcurrentHashMap，它是HashTable的替代，比HashTable的扩展性更好。
2. 另一个区别是HashMap的迭代器\(Iterator\)是fail-fast迭代器，而Hashtable的enumerator迭代器不是fail-fast的。所以当有其它线程改变了HashMap的结构（增加或者移除元素），将会抛出ConcurrentModificationException，但迭代器本身的remove\(\)方法移除元素则不会抛出ConcurrentModificationException异常。但这并不是一个一定发生的行为，要看JVM。这条同样也是Enumeration和Iterator的区别。
3. 由于Hashtable是线程安全的也是synchronized，所以在单线程环境下它比HashMap要慢。如果你不需要同步，只需要单一线程，那么使用HashMap性能要好过Hashtable。
4. HashMap不能保证随着时间的推移Map中的元素次序是不变的。

> \* 结构上的更改指的是删除或者插入一个元素，这样会影响到map的结构。

#### 我们能否让HashMap同步？

HashMap可以通过下面的语句进行同步：  
Map m = Collections.synchronizeMap\(hashMap\);

### 结论

Hashtable和HashMap有几个主要的不同：

线程安全以及速度。仅在你需要完全的线程安全的时候使用Hashtable，而如果你使用Java 5或以上的话，请使用ConcurrentHashMap吧。

