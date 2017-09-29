大多数情况下，对象在新生代Eden区中分配。当Eden区没有足够空间进行分配时，虚拟机将发起一次Minor GC。

> 新生代GC（Minor GC）：发生在新生代的垃圾收集动作，因为java对象大多都具备朝生夕死的特性，所以Minor非常频繁，一般回收速度也比较快
>
> 老年代GC（Major GC/ Full GC）：发生在老年代的GC，出现了Major GC经常会伴随至少一次的Minor GC。速度一般比Minor慢10倍以上。



