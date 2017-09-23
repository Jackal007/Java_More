![](/assets/ArrayList与Collection关系.png)

### **ArrayList构造函数**

```java
ArrayList()    // 默认构造函数

ArrayList(int capacity)    // capacity是ArrayList的默认容量大小。当由于增加数据导致容量不足时，容量会添加上一次容量大小的一半。

ArrayList(Collection<? extends E> collection)    // 创建一个包含collection的ArrayList
```

### **ArrayList的API**

```java
// Collection中定义的API
boolean             add(E object)
//add实现机制：每次add时会判断数据长度，如果不够的话会调用Arrays.copyOf，复制一份更长的数组，并把前面的数据放进去。
boolean             addAll(Collection<? extends E> collection)
void                clear()
boolean             contains(Object object)
boolean             containsAll(Collection<?> collection)
boolean             equals(Object object)
int                 hashCode()
boolean             isEmpty()
Iterator<E>         iterator()
boolean             remove(Object object)
//remove实现机制：直接使用System.arraycopy把需要删除index后面的都往前移一位然后再把最后一个去掉。
boolean             removeAll(Collection<?> collection)
boolean             retainAll(Collection<?> collection)    //取得两个List的交集
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

* **通过迭代器遍历**

  ```java
  Integer value = null;
  Iterator iter = list.iterator();
  while
  (iter.hasNext()) {
    value = (Integer)iter.next();
  }
  ```

* **随机访问，通过索引值去遍历。** 由于ArrayList实现了RandomAccess接口，它支持通过索引值去随机访问元素。

  ```java
  Integer value = null;
  int size = list.size();
  for (int i=0; i<size; i++) {
    value = (Integer)list.get(i);        
  }
  ```

* **for循环遍历**

  ```java
  Integer value = null;
  for (Integer integ:list) {
    value = integ;
  }
  ```

**遍历ArrayList时，使用随机访问\(通过索引序号访问\)效率最高，而使用迭代器的效率最低！**

### 线程同步

**IsSynchronized属性和ArrayList.Synchronized方法**

**IsSynchronized属性指示当前的ArrayList实例是否支持线程同步，而ArrayList.Synchronized静态方法则会返回一个ArrayList的线程同步的封装。**

**如果使用非线程同步的实例，那么在多线程访问的时候，需要自己手动调用lock来保持线程同步，例如：**

> 1. ArrayListlist = 
>    new
>     ArrayList\(\);  
> 2. //...
> 3. lock\(list.SyncRoot \)
>    //当ArrayList为非线程包装的时候，SyncRoot属性其实就是它自己，但是为了满足ICollection的SyncRoot定义，这里还 是使用SyncRoot来保持源代码的规范性
> 4. {  
> 5. list.Add\(“Add a Item” \);  
> 6. }

**                  
**

**如果使用ArrayList.Synchronized方法返回的实例，那么就不用考虑线程同步的问题，这个实例本身就是线程安全的，实际上ArrayList内部实现了一个保证线程同步的内部类，ArrayList.Synchronized返回的就是这个类的实例，它里面的每个属性都是用了lock关键字来保证线程同步。**

**\*\*\*\***

**但是，使用这个方法（ArrayList.Synchronized）并不能保证枚举的同步，例如，一个线程正在删除或添加集合项，而另一个线程同时进行枚举，这时枚举将会抛出异常。所以，在枚举的时候，你必须明确使用SyncRoot 锁定这个集合。**

**Hashtable与ArrayList关于线程安全性的使用方法类似。**

ArrayList 是一个数组队列，相当于动态数组。与Java中的数组相比，它的容量能动态增长。它继承于AbstractList，实现了List, RandomAccess, Cloneable, java.io.Serializable这些接口。

> ArrayList继承了AbstractList，实现了List。它是一个数组队列，提供了相关的添加、删除、修改、遍历等功能。  
> ArrayList实现了RandmoAccess接口，即提供了随机访问功能。RandmoAccess是java中用来被List实现，为List提供快速访问功能的。在ArrayList中，我们即可以通过元素的序号快速获取元素对象；这就是快速随机访问。
>
> ArrayList 实现了Cloneable接口，即覆盖了函数clone\(\)，能被克隆。
>
> ArrayList 实现java.io.Serializable接口，这意味着ArrayList支持序列化，能通过序列化去传输。
>
> 和Vector不同，ArrayList中的操作不是线程安全的！所以，建议在单线程中才使用ArrayList，而在多线程中可以选择Vector或者CopyOnWriteArrayList。



