> 存在使i + 1 &lt; i的数吗（）
>
> 答案：存在
>
> 解析：如果i为int型，那么当i为int能表示的最大整数时，i+1就溢出变成负数了，此时不就&lt;i了吗。



> 扩展：存在使i &gt; j \|\| i &lt;= j不成立的数吗（）
>
> 答案：存在
>
> 解析：比如Double.NaN或Float.NaN



> 0.6332的数据类型是（）
> A float     B double     C Float      D Double
>
> 答案：B
>
> 解析：默认为double型，如果为float型需要加上f显示说明，即0.6332f



> **short s1 = 1; s1 = s1 + 1;有错吗?short s1 = 1; s1 += 1;有错吗**
>
> 答：对于short s1 = 1; s1 = s1 + 1;由于1是int类型，因此s1+1运算结果也是int 型，需要强制转换类型才能赋值给short型。而short s1 = 1; s1 += 1;可以正确编译，因为s1+= 1;相当于s1 = \(short\)\(s1 + 1\);其中有隐含的强制类型转换。



>



