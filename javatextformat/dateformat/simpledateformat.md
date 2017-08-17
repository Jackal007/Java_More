`SimpleDateFormat`是`DateFormat`的一个具体类，它允许我们指定格式模式从而获取我们理想的格式化日期和时间。  
通过`SimpleDateFormat`的构造方法你可以传入一个格式模式字符串或者通过`applyPattern(String pattern)`方法添加一个格式模式字符串。  
对于格式模式字符串，API为我们提供了丰富的模式元素，下面列出几个常用的模式元素

| 字母 | 日期或时间元素 | 示例 |
| :--- | :--- | :--- |
| y | 年 | 2015 |
| M | 年中的月份 | 12 |
| w | 年中的周数 | 50 |
| W | 月份中的周数 | 02 |
| D | 年中的天数 | 344 |
| d | 月份中的天数 | 10 |
| F | 月份中的星期 | 02 |
| E | 星期中的天数 | 星期四、Thu |
| a | AM/PM标记 | 下午、PM |
| H | 一天中的小时数\(0~23\) | 21 |
| k | 一天中的小时数\(1~24\) | 21 |
| K | am/pm中的小时数\(0~11\) | 09 |
| h | am/pm中的小时数\(1~12\) | 09 |
| m | 小时中的分钟数 | 31 |
| s | 分钟中的秒数 | 08 |
| S | 毫秒数 | 716 |

如果你设置Locale的话，会有不同的显示格式，比如如果设置Locale.**ENGLISH**，E会显示为英文格式，a显示为AM或PM  


```java
Date date = new Date();
SimpleDateFormat format = new SimpleDateFormat("今天是yyyy-MM-dd E hh:mm:ss，是yyyy年的第DD天，在该月是第dd天");
System.out.println(format.format(date));
将会输出：今天是2015-12-10 星期四 09:38:16，是2015年的第344天，在该月是第10天
```



> 作者：Jadyn
>
> 链接：http://www.jianshu.com/p/c8f16cab35e1
>
> 來源：简书
>
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



