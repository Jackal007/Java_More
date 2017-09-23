HashSet 是一个**没有重复元素的集合**。  
它是由HashMap实现的，**不保证元素的顺序**，而且**HashSet允许使用 null 元素**。  
HashSet是**非同步的**。如果多个线程同时访问一个哈希 set，而其中至少一个线程修改了该 set，那么它必须 保持外部同步。这通常是通过对自然封装该 set 的对象执行同步操作来完成的。如果不存在这样的对象，则应该使用 Collections.synchronizedSet 方法来“包装” set。最好在创建时完成这一操作，以防止对该 set 进行意外的不同步访问：

```
Set s = Collections.synchronizedSet(new HashSet(...));
```

HashSet通过iterator\(\)返回的**迭代器是fail-fast的。**

![](/assets/hashset.png)

### **HashSet的构造函数**

```java
public HashSet()    // 默认构造函数

public HashSet(Collection<? extends E> c)     // 带集合的构造函数

public HashSet(int initialCapacity, float loadFactor)     // 指定HashSet初始容量和加载因子的构造函数

public HashSet(int initialCapacity)     // 指定HashSet初始容量的构造函数

HashSet(int initialCapacity, float loadFactor, boolean dummy)  // 指定HashSet初始容量和加载因子的构造函数,dummy没有任何作用
```

### **HashSet的主要API**

```java
boolean         add(E object)
void            clear()
Object          clone()
boolean         contains(Object object)
boolean         isEmpty()
Iterator<E>     iterator()
boolean         remove(Object object)
int             size()
```

### **HashSet遍历方式**

* ##### **通过Iterator遍历HashSet**
```java
for(Iterator iterator = set.iterator();
       iterator.hasNext(); ) { 
    iterator.next();
}   
```

* **通过for-each遍历HashSet**
```java
  String[] arr = (String[])set.toArray(new String[0]);
  for (String str:arr)
      System.out.printf("for each : %s\n", str);
  ```



