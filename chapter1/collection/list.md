## List

是存储的元素容器是有个有序的可以索引到元素的容器，元素可重复。

* ##### List提供了一种特殊的iterator遍历器，叫做ListIterator

  这种遍历器允许遍历时插入，替换，删除，双向访问。 并且还有一个重载方法允许从一个指定位置开始遍历。

  然后我们再看下List接口新增的接口，会发现add，get这些都多了index参数，说明在原来Collection的基础上，List是一个可以指定索引，有序的容器。在这注意以下添加的2个新Iteractor方法。

  ```java
  ListIterator<E>listIterator();

  ListIterator<E>listIterator(int index);
  ```

  一个集合在遍历过程中进行插入删除操作很容易造成错误，特别是无序队列，是无法在遍历过程中进行这些操作的。但是List是一个有序集合，所以在这实现了一个ListIteractor，可以在遍历过程中进行元素操作，并且可以双向访问。

  > ### Iterator和ListIterator的区别是什么？
  >
  > * Iterator可用来遍历Set和List集合，但是ListIterator只能用来遍历List。
  > * Iterator对集合只能是前向遍历，ListIterator既可以前向也可以后向。
  > * ListIterator实现了Iterator接口，并包含其他的功能，比如：增加元素，替换元素，获取前一个和后一个元素的索引

* ##### 各个实现类：

  而List接口一共有三个实现类，分别是ArrayList、Vector和LinkedList。3个具体实现类的相关区别如下：

  1. ArrayList是最常用的List实现类，内部是通过数组实现的，它允许对元素进行快速随机访问。数组的缺点是每个元素之间不能有间隔，当数组大小不满足时需要增加存储能力，就要讲已经有数组的数据复制到新的存储空间中。当从ArrayList的中间位置插入或者删除元素时，需要对数组进行复制、移动、代价比较高。因此，它适合随机查找和遍历，不适合插入和删除。

  2. Vector与ArrayList一样，也是通过数组实现的，不同的是它支持线程的同步，即某一时刻只有一个线程能够写Vector，避免多线程同时写而引起的不一致性，但实现同步需要很高的花费，因此，访问它比访问ArrayList慢。
  
  3. LinkedList是用链表结构存储数据的，很适合数据的动态插入和删除，随机访问和遍历速度比较慢。另外，他还提供了List接口中没有定义的方法，专门用于操作表头和表尾元素，可以当作堆栈、队列和双向队列使用。



