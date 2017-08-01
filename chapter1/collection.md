> **JDK不直接提供对于这个接口的实现，但是提供继承与该接口的子接口比如 List Set。这个接口的设计目的是希望能最大程度抽象出元素的操作。**

### 接口定义：

```java
public interface Collection<E> extends Iterable<E>{
    ...
}
```

### 定义的几个重要的接口方法：

```java
add(E e) 
 Ensures that this collection contains the specified element

clear()
 Removes all of the elements from this collection (optional operation).

contains(Object o)
 Returns true if this collection contains the specified element.

isEmpty()
 Returns true if this collection contains no elements.

iterator()
 Returns an iterator over the elements in this collection.

remove(Object o)
 Removes a single instance of the specified element from this collection, if it is present (optional operation).

retainAll(Collection<?> c)
 Retains only the elements in this collection that are contained in the specified collection (optional operation).（**ps:这个平时倒是没注意，感觉挺好用的接口，保留指定的集合**）

size()
 Returns the number of elements in this collection.

toArray()
 Returns an array containing all of the elements in this collection.

toArray(T[] a)
 Returns an array containing all of the elements in this collection; the runtime type of the returned array is that of the specified array.（**ps:这个接口也可以mark下**）

 ...
```

上面定义的接口就代表了Collection这一类容器最基本的操作，包括了插入，移除，查询等，会发现都是对单个元素的操作，Collection这类集合即元素对象的存储。

