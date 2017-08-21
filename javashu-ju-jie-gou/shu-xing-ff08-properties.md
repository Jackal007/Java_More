# Java Properties 类

> Properties属性文件在JAVA应用程序中是经常可以看得见的，也是特别重要的一类文件。它用来配置应用程序的一些信息，不过这些信息一般都是比较少的数据，没有必要使用数据库文件来保存，而使用一般的文本文件来保存，如果是通过File直接保存的话，可能在存储和读取上都不是很方便，但如果保存为Properties文件就不一样了，属性文件都有键值对应的，在JAVA的包中，有提供专门的操作属性文件的类。这个类就是 java.uitl.Properties类，由于Properties类是一个集合类，所以，Properties会将属性以集合的方式读写。
>
> Properties 继承于 Hashtable.表示一个持久的属性集.属性列表中每个键及其对应值都是一个字符串。
>
> Properties 类被许多Java类使用。例如，在获取环境变量时它就作为System.getProperties\(\)方法的返回值。

Properties 定义如下实例变量.这个变量持有一个Properties对象相关的默认属性列表。

```java
Properties defaults;
```

Properties类定义了两个构造方法. 第一个构造方法没有默认值。

```java
Properties()
```

第二个构造方法使用propDefault 作为默认值。两种情况下，属性列表都为空：

```java
Properties(Properties propDefault)
```

除了从Hashtable中所定义的方法，Properties定义了以下方法：

| **方法描述** |
| :--- |
| **String getProperty\(String key\)**  用指定的键在此属性列表中搜索属性。 |
| **String getProperty\(String key, String defaultProperty\)** 用指定的键在属性列表中搜索属性。 |
| **void list\(PrintStream streamOut\)**  将属性列表输出到指定的输出流。 |
| **void list\(PrintWriter streamOut\)** 将属性列表输出到指定的输出流。 |
| **void load\(InputStream streamIn\) throws IOException**  从输入流中读取属性列表（键和元素对）。 |
| **Enumeration propertyNames\( \)** 按简单的面向行的格式从输入字符流中读取属性列表（键和元素对）。 |
| **Object setProperty\(String key, String value\)**  调用 Hashtable 的方法 put。 |
| **void store\(OutputStream streamOut, String description\)**  以适合使用  load\(InputStream\)方法加载到 Properties 表中的格式，将此 Properties 表中的属性列表（键和元素对）写入输出流。 |

### 实例

下面的程序说明这个数据结构支持的几个方法：

```java
import java.util.*;

public class PropDemo {

   public static void main(String args[]) {
      Properties capitals = new Properties();
      Set states;
      String str;

      capitals.put("Illinois", "Springfield");
      capitals.put("Missouri", "Jefferson City");
      capitals.put("Washington", "Olympia");
      capitals.put("California", "Sacramento");
      capitals.put("Indiana", "Indianapolis");

      // Show all states and capitals in hashtable.
      states = capitals.keySet(); // get set-view of keys
      Iterator itr = states.iterator();
      while(itr.hasNext()) {
         str = (String) itr.next();
         System.out.println("The capital of " +
            str + " is " + capitals.getProperty(str) + ".");
      }
      System.out.println();

      // look for state not in list -- specify default
      str = capitals.getProperty("Florida", "Not Found");
      System.out.println("The capital of Florida is "
          + str + ".");
   }
}
```

以上实例编译运行结果如下：

```java
The capital of Missouri is Jefferson City.
The capital of Illinois is Springfield.
The capital of Indiana is Indianapolis.
The capital of California is Sacramento.
The capital of Washington is Olympia.

The capital of Florida is Not Found.
```



