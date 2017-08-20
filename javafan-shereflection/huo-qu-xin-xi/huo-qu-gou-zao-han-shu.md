#### Constructor getConstructor\(Class\[\] params\)

#### Constructor\[\] getConstructors\(\)

#### Constructor getDeclaredConstructor\(Class\[\] params\)

#### Constructor\[\] getDeclaredConstructors\(\)



Class\[\] params为目标类的构造函数参数类型数组，具体见以下的举例

不带Declared关键字的函数（如：getConstructor）只能获取到公有的构造函数，

带Declared关键字的函数（如：getDeclaredConstructor）能获取到非公有的构造函数，即所有访问保护机制的构造函数。

