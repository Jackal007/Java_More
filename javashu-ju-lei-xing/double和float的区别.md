### Java 中 float 与 double 的区别

1.float是单精度浮点数，内存分配4个字节，占32位，有效小数位6-7位

double是双精度浮点数，内存分配8个字节，占64位，有效小数位15位



2.java中默认声明的小数是double类型的，如double d=4.0

如果声明： float x = 4.0则会报错，需要如下写法：float x = 4.0f或者float x = \(float\)4.0

其中4.0f后面的f只是为了区别double，并不代表任何数字上的意义              



3.对编程人员而言，double 和 float 的区别是double精度高，但double消耗内存是float的两倍，且double的运算速度较float稍慢。

> http://www.imooc.com/wiki/detail/id/111



