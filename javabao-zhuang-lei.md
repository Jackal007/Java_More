Java语言是一个面向对象的语言，但是Java中的基本数据类型却是不面向对象的，这在实际使用时存在很多的不便，为了解决这个不足，在设计类时为每个基本数据类型设计了一个对应的类进行代表，这样八个和基本数据类型对应的类统称为包装类\(Wrapper Class\)，有些地方也翻译为外覆类或数据类型类，如下表所示：

| 基本类型 | 大小 | 包装器类型 |
| :--- | :--- | :--- |
| boolean | / | Boolean |
| char | 16bit | Character |
| byte | 8bit | Byte |
| short | 16bit | Short |
| int | 32bit | Integer |
| long | 64bit | Long |
| float | 32bit | Float |
| double | 64bit | Double |
| void | / | Void |

### Java中的包装器类有两个主要的目的：

1. 提供一种机制，将基本值“包装”到对象中，从而使基本值能够包含在为对象而保留的操作中，比如添加到Collections 中，或者从带对象返回值的方法中返回。注意，java5增加了自动装箱和拆箱，程序员过去需手工执行的许多包装操作，现在可以由java自动处理了。
2. 为基本值提供分类功能。这些功能大多数于各种转换有关：在基本值和String对象间相互转换，在基本值和String对象之间按不同基数转换，如二进制、八进制和十六进制。

### 包装类共同的方法 {#包装类共同的方法}

* 带有
  `基本值参数`
  并创建包装类对象的构造函数。如利用Integer包装类创建对象，Integer obj=new Integer\(145\);
* 带有
  `字符串参数`
  并创建包装类对象的构造函数.如：new Integer\(“-45.36”\);
* 可生成对象基本值的
  `typeValue`
  方法，如：obj.intValue\(\);
* 将字符串转换为基本值的
  `parseType`
  方法，如：Integer.parseInt\(args\[0\]\);
* 生成哈稀表代码的
  `hashCode`
  方法，如：obj.hasCode\(\);
* 对同一个类的两个对象进行比较的
  `equals()`
  方法，如：obj1.eauqls\(obj2\);
* 生成字符串表示法的
  `toString()`
  方法，如：obj.toString\(\).

---

### 引用自：[http://alexyyek.github.io/2014/12/29/wrapperClass/](#) {#装箱和拆箱}



