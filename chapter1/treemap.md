> TreeMap 是一个**有序的key-value集合**，它是通过**红黑树**实现的。  
> TreeMap**继承于AbstractMap**，所以它是一个Map，即一个key-value集合。  
> TreeMap 实现了NavigableMap接口，意味着它**支持一系列的导航方法。**比如返回有序的key集合。  
> TreeMap 实现了Cloneable接口，意味着**它能被克隆**。  
> TreeMap 实现了java.io.Serializable接口，意味着**它支持序列化**。
>
> TreeMap基于**红黑树（Red-Black tree）实现**。该映射根据**其键的自然顺序进行排序**，或者根据**创建映射时提供的 Comparator 进行排序**，具体取决于使用的构造方法。  
> TreeMap的基本操作 containsKey、get、put 和 remove 的时间复杂度是 log\(n\) 。  
> 另外，TreeMap是**非同步**的。 它的iterator 方法返回的**迭代器是fail-fastl**的。

### TreeMap的构造函数

```java
TreeMap()    // 默认构造函数。使用该构造函数，TreeMap中的元素按照自然排序进行排列

TreeMap(Map<? extends K, ? extends V> copyFrom)    // 创建的TreeMap包含Map

TreeMap(Comparator<? super K> comparator)    // 指定Tree的比较器

TreeMap(SortedMap<K, ? extends V> copyFrom)// 创建的TreeSet包含copyFrom
```

### **TreeMap的API**

```java
Entry<K, V>                ceilingEntry(K key)
K                          ceilingKey(K key)
void                       clear()
Object                     clone()
Comparator<? super K>      comparator()
boolean                    containsKey(Object key)
NavigableSet<K>            descendingKeySet()
NavigableMap<K, V>         descendingMap()
Set<Entry<K, V>>           entrySet()
Entry<K, V>                firstEntry()
K                          firstKey()
Entry<K, V>                floorEntry(K key)
K                          floorKey(K key)
V                          get(Object key)
NavigableMap<K, V>         headMap(K to, boolean inclusive)
SortedMap<K, V>            headMap(K toExclusive)
Entry<K, V>                higherEntry(K key)
K                          higherKey(K key)
boolean                    isEmpty()
Set<K>                     keySet()
Entry<K, V>                lastEntry()
K                          lastKey()
Entry<K, V>                lowerEntry(K key)
K                          lowerKey(K key)
NavigableSet<K>            navigableKeySet()
Entry<K, V>                pollFirstEntry()
Entry<K, V>                pollLastEntry()
V                          put(K key, V value)
V                          remove(Object key)
int                        size()
SortedMap<K, V>            subMap(K fromInclusive, K toExclusive)
NavigableMap<K, V>         subMap(K from, boolean fromInclusive, K to, boolean toInclusive)
NavigableMap<K, V>         tailMap(K from, boolean inclusive)
SortedMap<K, V>            tailMap(K fromInclusive)
```



