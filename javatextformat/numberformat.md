`NumberFormat`根据当前语言环境格式化数字  
`NumberFormat`同样是一个抽象基类，可以使用API中的工厂方法获取实例对象  
1.`getCurrencyInstance()`方法，根据当前语言环境获取货币数值格式。传递Locale对象可以获取指定语言环境下的货币数值格式，比如

```java
NumberFormat format = NumberFormat.getCurrencyInstance(Locale.CANADA);
System.out.println(format.format(439.6));
将会输出：$439.60
```

2.`getInstance()`和`getNumberInstance()`方法都会获取到常规数值格式  
3.`getIntegerInstance()`方法获取常规整数值格式，如果需要格式化的数值为小数，则会将数值四舍五入为最接近的整数  
4.`getPercentInstance()`方法获取百分比的数值格式  
`NumberFormat`有两个具体实现子类`DecimalFormat`和`ChoiceFormat`

###### DecimalFormat

`DecimalFormat`同SimpleDateFormat类似，允许我们指定格式模式获取我们想要的格式化数值  
DecimalFormat类对于数值的小数部分，默认显示3位小数，在去掉超出小数点后面3位的部分时，会将数值四舍五入为最接近的数值格式化输出。淡然我们可以对这个默认进行设置  
`setMaximumFractionDigits(int newValue)`方法，设置小数部分中允许的最大数字位数  
`setMinimumFractionDigits(int newValue)`方法，设置小数部分中允许的最小数字位数，如果原数小数位数不够的话，会补零。  
对于数值的整数部分，默认3个数字为一组进行显示，同样对此我们也可以自定义，使用`setGroupingSize(int i)`方法，设置分组中一组的位数。  
`setGroupingUsed(boolean value)`方法设置是否使用分组，true表示使用，false表示取消分组  
`setMaximumIntegerDigits(int newValue)`方法设置整数部分允许的最大数字位数  
`setMinimumIntegerDigits(int newValue)`方法设置整数部分允许的最小数字位数  
在\`\`\`\`的构造方法中，允许我们传入格式模式字符串输出我们想要的格式化数值，格式模式元素包含如下

|  |  |
| :--- | :--- |
| 0 | 表示一个数字，被格式化数值不够的位数会补0 |
| \# | 表示一个数字，被格式化数值不够的位数会忽略 |
| . | 小数点分隔符的占位符 |
| , | 分组分隔符的占位符 |
| - | 缺省负数前缀 |
| % | 将数值乘以100并显示为百分数 |
| \u2030 | 将数值乘以1000并显示为千分数 |

再次

```java
DecimalFormat format1 = new DecimalFormat("#\u2030");
System.out.println(format1.format(0.3345));//输出334‰

DecimalFormat format2 = new DecimalFormat("##.##");
System.out.println(format2.format(12.345));//输出12.35

DecimalFormat format3 = new DecimalFormat("0000.00");
System.out.println(format3.format(12.345));//输出0012.35

DecimalFormat format4 = new DecimalFormat("#.##%");
System.out.println(format4.format(12.345));//输出1234.5%
```

###### ChoiceFormat

`ChoiceFormat`允许将格式化运用到某个范围的数，通常与`MessageFormat`一同使用。`ChoiceFormat`在构造方法中接收一个format数组和一个limits数组，这两个数组的长度必须相等，例如：

```java
limits = {1,2,3,4,5,6,7}
formats = {"Sun","Mon","Tue","Wed","Thur","Fri","Sat"}
```

limits数组实际上是个区间，可开可闭，并且必须按升序排列，如果不按升序排列，格式化结果将会不正确，还可以使用\u221E\(表示无穷大\)。  
`ChoiceFormat`的匹配公式

> limit\[j\] &lt;= X &lt;limit\[j+1\]

其中X表示使用format方法传入的值，j表示limit数组中的索引。当且仅当上述公式成立时，X匹配j，如果不能匹配，则会根据X是太小还是太大，匹配limits数组的第一个索引或最后一个索引，然后使用匹配的limits数组中的索引，去formats数组中寻找相同索引的值。例子：

```java
double[] limits = { 3, 4, 5, 6, 7, 8, 9 };
String[] formats = { "星期一", "星期二", "星期三", "星期四", "星期五", "星期六", "星期日" };
ChoiceFormat format = new ChoiceFormat(limits, formats);
System.out.println(format.format(2.5));//将会输出"星期一"
/**3.6介于3和4之间，所以会匹配3，又由于3在limits数组中的索引是0，所以会在formats数组徐照索引0的值，即输出"星期一"
*/
System.out.println(format.format(3.6));
```

下面看一下`ChoiceFormat`类中的几个常用方法  
1.`nextDouble(double d)`静态方法查找大于d的最小double值，用在limits数组中，从而使limits数组形成一个右开区间数组，例如  
`limits = {0,1,ChoiceFormat.nextDouble(1)}`  
2.`nextDouble(double d, boolean positive)`静态方法，如果positive参数为true，表示查找大于d的最小double值；如果positive参数为false，表示查找小于d的最大double值，这样就可以使limits形成一个左开区间数组。  
3.`previousDouble(double d)`静态方法，查找小于d的最大double值  
`ChoiceFormat`类的构造方法也允许我们传入一个模式字符串，format方法会根据这个模式字符串执行格式化操作。一个模式元素的格式如下：

> doubleNum \[占位符\] formatStr

占位符可以使用\#、&lt; 、\u2264\(&lt;=\)

```java
ChoiceFormat cf = new ChoiceFormat("1#is 1 | 1<is more than 1");
System.out.println(cf.format(1));//输出"is 1"
System.out.println(cf.format(2));//输出"is more than 1"
System.out.println(cf.format(0));//输出"is 1"
```

由上面的例子可以看出，模式字符串中的每个模式元素之间使用"\|"分割，"\|"前后可以添加空格以美化代码，而且必须按照升序进行书写，否则会出现java.lang.IllegalArgumentException的运行时异常。  
观看`ChoiceFormat`类的源码我们得知，实际上在内部，模式字符串还是被转换为limits和formats两个数组。在源码中

```java
public ChoiceFormat(String newPattern)  {
     applyPattern(newPattern);
}
/** applyPattern(newPattern)方法的部分源码
*/
public void applyPattern(String newPattern) {
...
choiceLimits = new double[count];
System.arraycopy(newChoiceLimits, 0, choiceLimits, 0, count);
choiceFormats = new String[count];
System.arraycopy(newChoiceFormats, 0, choiceFormats, 0, count);
...
}
```

可以看出`ChoiceFormat(String newPattern)`调用了`applyPattern(String newPattern)`方法，在`applyPattern`方法中对`newPattern`字符串进行解析，然后将解析后的数据放置到`ChoiceFormat`类的两个私有属性`double[] choiceLimits`和`String[] choiceFormats`中，然后使用格式化方法即可。



> 作者：Jadyn
>
> 链接：[http://www.jianshu.com/p/c8f16cab35e1](http://www.jianshu.com/p/c8f16cab35e1)
>
> 來源：简书
>
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



