### 接口定义如下：

```java
public interface Map<K,V> {
    ...
    interface Entry<K,V> {
        K getKey();
        V getValue();
        ...
    } 
}
```

泛型&lt;K,V&gt;分别代表key和value的类型。这时候注意到还定义了一个内部接口Entry，其实每一个键值对都是一个Entry的实例关系对象，所以Map实际其实就是Entry的一个Collection，然后Entry里面包含key，value。再设定key不重复的规则，自然就演化成了Map。

### 三个遍历Map的方法

* ##### Set&lt;K&gt; keySet\(\)
会返回所有key的Set集合，因为key不可以重复，所以返回的是Set格式，而不是List格式。（之后会说明Set，List区别。这里先告诉一点Set集合内元素是不可以重复的，而List内是可以重复的） 获取到所有key的Set集合后，由于Set是Collection类型的，所以可以通过Iterator去遍历所有的key，然后再通过get方法获取value。如下

```java
Map<String,String> map = new HashMap<String,String>();
map.put("01", "zhangsan");
map.put("02", "lisi");
map.put("03", "wangwu");

Set<String> keySet = map.keySet();
//先获取map集合的所有键的Set集合
Iterator<String> it = keySet.iterator();
//有了Set集合，就可以获取其迭代器。
while
(it.hasNext()) {
     String key = it.next();
      String value = map.get(key);
//有了键可以通过map集合的get方法获取其对应的值。
     System.out.println("key: "+key+"-->value: "+value);//获得key和value值
}
```

* ##### Collection&lt;V&gt; values\(\)
直接获取values的集合，无法再获取到key。所以如果只需要value的场景可以用这个方法。获取到后使用Iterator去遍历所有的value。

```java
Map<String,String>map = new HashMap<String,String>();

map.put("01", "zhangsan");
map.put("02", "lisi");
map.put("03", "wangwu");

Collection<String> collection = map.values();
//返回值是个值的Collection集合
System.out.println(collection);
```

* ##### Set&lt; Map.Entry&lt; K, V&gt;&gt; entrySet\(\)
是将整个Entry对象作为元素返回所有的数据。然后遍历Entry，分别再通过getKey和getValue获取key和value。如下

```java
Map<String,String> map = new HashMap<String,String>();
map.put("01", "zhangsan");
map.put("02", "lisi");
map.put("03", "wangwu");

//通过entrySet()方法将map集合中的映射关系取出（这个关系就是Map.Entry类型）
Set<Map.Entry<String, String>> entrySet = map.entrySet();

//将关系集合entrySet进行迭代，存放到迭代器中                
Iterator<Map.Entry<String, String>> it = entrySet.iterator();

while(it.hasNext()) {
     Map.Entry<String, String> me = it.next();
      //获取Map.Entry关系对象me

      String key = me.getKey();
      //通过关系对象获取key
      String value = me.getValue();//通过关系对象获取value
}
```

通过以上3种遍历方式我们可以知道，如果你只想获取key，建议使用keySet。如果只想获取value，建议使用values。如果key value希望遍历，建议使用entrySet。（虽然通过keySet可以获得key再间接获得value，但是效率没entrySet高，不建议使用这种方法）

| Map实现 |
| :--- |


| Map实现 | 使用场景 | 数据结构 |
| :--- | :--- | :--- |
| HashMap | 哈希表存储键值对，key不重复，无序 | 哈希散列表 |
| LinkedHashMap | 是一个可以记录插入顺序和访问顺序的HashMap | 存储方式是哈希散列表，但是维护了头尾指针用来记录顺序 |
| TreeMap | 具有元素排序功能 | 红黑树 |
| WeakHashMap | 弱键映射，映射之外无引用的键，可以被垃圾回收 | 哈希散列表 |

> 一个保存键值映射的对象。 映射Map中不能包含重复的key，每一个key最多对应一个value。
>
> 这个接口替代了原来的一个抽象类Dictionary。
>
> Map集合提供3种遍历访问方法：
>
> 1.获得所有key的集合然后通过key访问value;
>
> 2.获得value的集合;
>
> .获得key-value键值对的集合（key-value键值对其实是一个对象，里面分别有key和value）;
>
>  Map的访问顺序取决于Map的遍历访问方法的遍历顺序。 有的Map，比如TreeMap可以保证访问顺序，但是有的比如HashMap，无法保证访问顺序。



