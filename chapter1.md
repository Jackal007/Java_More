Java容器类![](/assets/import.png)Collection接口是集合类的跟接口，java中没有提供这个接口的直接的实现类。但是却让其被继承产生了两个接口，就是Set和List。Set中不能包含重复的元素。List是一个有序的集合，可以包含重复的元素，提供了按索引访问的方式。

Map是java.util包中的另一个接口，它和Collection接口没有关系，是相互独立的，但是都属于集合类的一部分。Map包含了key-value对。Map不能包含重复的key，但是可以包含相同的value。

Iterator，所有的集合类都实现了Iterator接口，这是一个用于遍历集合中元素的接口，主要包含以下三种方法：1.hasNext\(\)是否还有下一个元素；2.next\(\)返回下一个元素；3.remove\(\)删除当前元素。

# **Collection和Map**

> **在Java容器中一共定义了2种集合, 顶层接口分别是Collection和Map。但是这2个接口都不能直接被实现使用，分别代表两种不同类型的容器。**
>
> **简单来看，Collection代表的是单个元素对象的序列，（可以有序/无序，可重复/不可重复 等，具体依据具体的子接口Set，List，Queue等）；Map代表的是“键值对”对象的集合（同样可以有序/无序 等依据具体实现）**

![](/assets/ksdalfk.png)**存放的是对象的引用**



> 链接：[http://www.jianshu.com/p/50e19038e361](http://www.jianshu.com/p/50e19038e361)

> 本章大部分内容转载自\(链接：[http://www.jianshu.com/p/047e33fdefd2\](http://www.jianshu.com/p/047e33fdefd2%29\) & [http://www.cnblogs.com/skywang12345](http://www.cnblogs.com/skywang12345)



