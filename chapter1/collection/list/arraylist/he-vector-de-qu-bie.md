

**Vector & ArrayList的主要区别    
**

1）同步性:Vector是线程安全的，也就是说是同步的，而ArrayList是线程序不安全的，不是同步的 数2。

2）数据增长:当需要增长时,Vector默认增长为原来一倍，而ArrayList却是原来的50%，这样,ArrayList就有利于节约内存空间。

如果涉及到堆栈，队列等操作，应该考虑用Vector，如果需要快速随机访问元素，应该使用ArrayList。

