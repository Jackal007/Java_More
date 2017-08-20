| 方法 | class：类；object：对象 |
| :--- | :--- |
| obj.getClass\(\) | String str = "abc";    Class c1 = str.getClass\(\); |
| obj.getSuperClass\(\) |  |
| 静态方法 Class.forName\(\) | Class c = Class.forName \("Java.lang.String"\); |

> 在你想检查一个类的信息之前，你首先需要获取类的 Class 对象。Java 中的所有类型包括基本类型\(int, long, float等等\)，即使是数组都有与之关联的 Class 类的对象。如果你在编译期知道一个类的名字的话，那么你可以使用如下的方式获取一个类的 Class 对象。
>
> ```java
> String className = ... ;//在运行期获取的类名字符串
> Class class = Class.forName(className);
> ```



## 获取Class对象的一些基本信息

| Java class 内部模块 | 说明 | 相应之Reflection API，多半为Class methods。 | 返回值类型\(return type\) |
| :--- | :--- | :--- | :--- |
| package | class隶属的package | getPackage\(\) | Package |
| import | class导入哪些classes | 间接获取 |  |
| modifier | class（或methods, fields）的属性 |  int getModifiers\(\)                Modifier.toString\(int\)         Modifier.isInterface\(int\) | int   String    bool |
| class name or interface name | class/interface | getName\(\) | String |
| type parameters | 参数化类型的名称 | getTypeParameters\(\) | TypeVariable &lt;Class&gt;\[\] |
| base class | base class（只可能一个） | getSuperClass\(\) | Class |
| implemented interfaces | 实现有哪些interfaces | getInterfaces\(\) | Class\[\] |
| inner classes | 内部classes | getDeclaredClasses\(\) | Class\[\] |
| outer class | 如果我们观察的class 本身是inner classes，那么相对它就会有个outer class。 | getDeclaringClass\(\) | Class |

上表中，列出了一些Java class内部信息的获取方式。所采用的方法几乎都是调用Class对象的成员方法（由此你就可以了解到Class类的用处了吧）。

