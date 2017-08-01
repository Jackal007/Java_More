> **LinkedList 是一个继承于AbstractSequentialList的双向链表。它也可以被当作堆栈、队列或双端队列进行操作。  
> **
>
> **LinkedList 实现 List 接口，能对它进行队列操作。  
> **
>
> **LinkedList 实现 Deque 接口，即能将LinkedList当作双端队列使用。  
> **
>
> **LinkedList 实现了Cloneable接口，即覆盖了函数clone\(\)，能克隆。  
> **
>
> **LinkedList 实现java.io.Serializable接口，这意味着LinkedList支持序列化，能通过序列化去传输。  
> **
>
> **LinkedList 是非同步的。**
>
> **数组和链表的对比：**
>
> 1.**查找方面。数组的效率更高，可以直接索引出查找，而链表必须从头查找。**
>
> 2.**插入删除方面。特别是在中间进行插入删除，这时候链表体现出了极大的便利性，只需要在插入或者删除的地方断掉链然后插入或者移除元素，然后再将前后链重新组装，但是数组必须重新复制一份将所有数据后移或者前移。**
>
> 3.**在内存申请方面，当数组达到初始的申请长度后，需要重新申请一个更大的数组然后把数据迁移过去才行。而链表只需要动态创建即可。**
>
> **如上LinkedList和ArrayList的区别也就在此。根据使用场景选择更加适合的List。**
>
> **LinkedList适合做增删操作，ArrayList适合做查找操作**

![](/assets/LinkedList与Collection关系.png)

### **LinkedList构造函数**

```java
// 默认构造函数
LinkedList()

// 创建一个LinkedList，保护Collection中的全部元素。
LinkedList(Collection<? extends E> collection)
```

### LinkedList的API

```java
LinkedList的API
boolean       add(E object)
void          add(int location, E object)
boolean       addAll(Collection<? extends E> collection)
boolean       addAll(int location, Collection<? extends E> collection)
void          addFirst(E object)
void          addLast(E object)
void          clear()
Object        clone()
boolean       contains(Object object)
Iterator<E>   descendingIterator()
E             element()
E             get(int location)
E             getFirst()
E             getLast()
int           indexOf(Object object)
int           lastIndexOf(Object object)
ListIterator<E>     listIterator(int location)
boolean       offer(E o)
boolean       offerFirst(E e)
boolean       offerLast(E e)
E             peek()
E             peekFirst()
E             peekLast()
E             poll()
E             pollFirst()
E             pollLast()
E             pop()
void          push(E e)
E             remove()
E             remove(int location)
boolean       remove(Object object)
E             removeFirst()
boolean       removeFirstOccurrence(Object o)
E             removeLast()
boolean       removeLastOccurrence(Object o)
E             set(int location, E object)
int           size()
<T> T[]       toArray(T[] contents)
Object[]     toArray()
```

### **LinkedList遍历方式**

\(01\) 第一种，通过**迭代器**遍历。即通过Iterator去遍历。

```
for(Iterator iter = list.iterator(); iter.hasNext();)
    iter.next();
```

\(02\) 通过**快速随机**访问遍历LinkedList

```
int size = list.size();
for (int i=0; i<size; i++) {
    list.get(i);        
}
```

\(03\) 通过**另外一种for循环**来遍历LinkedList

```
for (Integer integ:list);
```

\(04\) 通过**pollFirst\(\)**来遍历LinkedList

```
while(list.pollFirst() != null);
```

\(05\) 通过**pollLast\(\)**来遍历LinkedList

```
while(list.pollLast() != null);
```

\(06\) 通过**removeFirst\(\)**来遍历LinkedList

```
try {
    
while(list.removeFirst() != null);
} 
catch(NoSuchElementException e) {
}
```

\(07\) 通过**removeLast\(\)**来遍历LinkedList

```
try {
    
while(list.removeLast() != null);
} 
catch
 (NoSuchElementException e) {
}
```

遍历LinkedList时，使用removeFist\(\)或removeLast\(\)效率最高。但用它们遍历时，会删除原始数据；若单纯只读取，而不删除，应该使用第3种遍历方式。

**无论如何，千万不要通过随机访问去遍历LinkedList！**

