有如下两个变量定义，这两种定义有什么区别呢？

　　1. int\[\] zero = new int\[0\];  
　　2. int\[\] nil = null;

　　zero是一个长度为0的数组，我们称之为“空数组”，空数组也是一个对象，只是包含元素个数为0。nil是一个数组类型的空引用。

　　假设一个方法返回一个数组，如果它返回null，则调用方法必须先判断是否返回null，才能对放回数组进一步处理，而如果返回空数组，则无须null引用检查。鉴于此，返回数组的方法在没有结果时我们通常返回空数组，而不是null，这样做对于函数调用者的处理比较方便。

