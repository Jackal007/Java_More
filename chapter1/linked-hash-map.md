> **LinkedHashMap相对于HashMap来说区别是，LinkedHashMap遍历的时候具有顺序，可以保存插入的顺序，（还可以设置最近访问的元素也放在前面，即LRU）**
>
> **其实LinkedHashMap的存储还是跟HashMap一样，采用哈希表方法存储，只不过LinkedHashMap多维护了一份head，tail链表。**
>
> **即在创建新Node的时候将新Node放到最后，这样遍历的时候不再像HashMap一样，从数组开始判断第一个非空元素，而是直接从表头进行遍历。这样即满足有序遍历。**



