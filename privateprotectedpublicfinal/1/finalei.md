### 不可变类

不可变类是指创建该类的实例后，该实例的Field是不可改变的。

被final修饰过的类不能被继承

如果创建自定义的不可变类，应该遵循如下规则

（1）使用private和final修饰符来修饰该类的Field。

（2）提供带参数的构造器，用于传入参数来初始化类里的Field。

（3）仅为该类的Field提供getter方法，不要为该类的Field提供setter方法。

（4）如果有必要，重写Object类的hashCode和equals方法。

