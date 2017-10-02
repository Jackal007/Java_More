准备阶段是正式为类变量分配内存并设置变量初始值的阶段，这些变量所使用的内存都将在方法区中进行分配。这个时候进行内存分配的仅包括类变量（static修饰的变量），而不包括实例变量（实例变量将会在对象实例化时随着对象一起分配到java堆中）。这里说的初始值时数据类型的零值，而不是赋的值（这个操作在初始化阶段进行）

| 数据类型 | 零值 |
| :--- | :--- |
| int | 0 |
| long | 0L |
| short | \(short\)0 |
| char | '\u0000' |
| byte | \(byte\)0 |
| boolean | false |
| float | 0.0f |
| double | 0.0d |
| reference | null |

在通常情况下初始值时零值，一些其他的情况：

类字段的字段属性中存在ConstantValue属性，那在准备阶段变量的value就会被初始化为ConstantValue属性所指定的值：

`public static`**`final`**`int value = 1`

