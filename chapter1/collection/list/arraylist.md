> **ArrayList 是一个数组队列，相当于动态数组。与Java中的数组相比，它的容量能动态增长。它继承于AbstractList，实现了List, RandomAccess, Cloneable, java.io.Serializable这些接口。**
>
> **ArrayList**_**继承了AbstractList，实现了List**_**。它是一个数组队列，提供了相关的添加、删除、修改、遍历等功能。  
> ArrayList**_**实现了RandmoAccess接口，即提供了随机访问功能。**_**RandmoAccess是java中用来被List实现，为List提供快速访问功能的。在ArrayList中，我们即可以通过元素的序号快速获取元素对象；这就是快速随机访问。**
>
> **ArrayList 实现了Cloneable接口，即覆盖了函数clone\(\)，能被克隆。**
>
> **ArrayList 实现java.io.Serializable接口，这意味着ArrayList支持序列化，能通过序列化去传输。**
>
> **和Vector不同，ArrayList中的操作不是线程安全的！所以，建议在单线程中才使用ArrayList，而在多线程中可以选择Vector或者CopyOnWriteArrayList。**

![](/assets/ArrayList与Collection关系.png)

add实现机制：每次add时会判断数据长度，如果不够的话会调用Arrays.copyOf，复制一份更长的数组，并把前面的数据放进去。

remove实现机制：直接使用System.arraycopy把需要删除index后面的都往前移一位然后再把最后一个去掉。

### **ArrayList构造函数**

```java
// 默认构造函数
ArrayList()

// capacity是ArrayList的默认容量大小。当由于增加数据导致容量不足时，容量会添加上一次容量大小的一半。
ArrayList(int capacity)

// 创建一个包含collection的ArrayList
ArrayList(Collection<? extends E> collection)
```

### **ArrayList的API**

```java
// Collection中定义的API
boolean             add(E object)
boolean             addAll(Collection<? extends E> collection)
void                clear()
boolean             contains(Object object)
boolean             containsAll(Collection<?> collection)
boolean             equals(Object object)
int                 hashCode()
boolean             isEmpty()
Iterator<E>         iterator()
boolean             remove(Object object)
boolean             removeAll(Collection<?> collection)
boolean             retainAll(Collection<?> collection)
int                 size()
<T> T[]             toArray(T[] array)
Object[]            toArray()
// AbstractCollection中定义的API
void                add(int location, E object)
boolean             addAll(int location, Collection<? extends E> collection)
E                   get(int location)
int                 indexOf(Object object)
int                 lastIndexOf(Object object)
ListIterator<E>     listIterator(int location)
ListIterator<E>     listIterator()
E                   remove(int location)
E                   set(int location, E object)
List<E>             subList(int start, int end)
// ArrayList新增的API
Object               clone()
void                 ensureCapacity(int minimumCapacity)
void                 trimToSize()
void                 removeRange(int fromIndex, int toIndex)
```

### **ArrayList遍历方式**

**第一种，通过迭代器遍历。**即通过Iterator去遍历。

```java
Integer value = null;
Iterator iter = list.iterator();
while
 (iter.hasNext()) {
    value = (Integer)iter.next();
}
```

**第二种，随机访问，通过索引值去遍历。**  
由于ArrayList实现了RandomAccess接口，它支持通过索引值去随机访问元素。

```java
Integer value = null;
int size = list.size();
for (int i=0; i<size; i++) {
    value = (Integer)list.get(i);        
}
```

**第三种，for循环遍历**。如下：

```java
Integer value = null;
for (Integer integ:list) {
    value = integ;
}
```

**遍历ArrayList时，使用随机访问\(即，通过索引序号访问\)效率最高，而使用迭代器的效率最低！**

