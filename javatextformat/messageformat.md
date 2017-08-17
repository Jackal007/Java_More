`MessageFormat`提供了以语言环境无关的生成连接消息的方式。  
常用`MessageFormat`的静态方法`format`，该方法接收一个字符串的模式和一组对象\(对象数组\)，按照模式形式将格式化的对象插入到模式中，然后返回字符串结果。  
`MessageFormat`的格式模式元素（FormatElement）形式如下:  
{ArgumentIndex}  
{ArgumentIndex,FormatType}  
{ArgumentIndex,FormatType,FormatStyle}  
其中ArgumentIndex对象数组中的索引，从0开始，  
FormatType包括number、date、 time、choice，  
FormatStyle包括short、medium、long、full、integer、currency、percent、SubformatPattern\(子模式\)，  
在MessageFormat类的内部，FormatType和FormatStyle实际上是创建格式元素的Format示例  
number对应了NumberFormat，其子格式对应了DecimalFormat  
date和time对应了DateFormat，其资格是对应了SimpleDateFormat  
choice对应了ChoiceFormat  
敢说没有意思，来多举几个栗子：  
你可以直接使用`MessageFormat`类中的静态方法format，像这样：

```java
/**这是源码注释中的一个例子
* 在这个例子中静态方法format第一个参数是字符串类型的，
* 即模式字符串，第二个参数是个可变参数，实际上就是一个Object类型的数组。
* 在模式字符串中使用"{}"标识一个FormatElement。"{}"中的ArgumentIndex对应Object数组中响应索引处的值。
*/
int planet = 7;
String event = "a disturbance in the Force";
String result = MessageFormat.format("At {1,time} on {1,date}, there was {2} on planet {0,number,integer}.",
                  planet, new Date(), event);
System.out.println(result);
//输出：At 20:39:15 on 2015-12-11, there was a disturbance in the Force on planet 7.
```

你也可以使用`MessageFormat`的构造方法传入pattern string（模式字符串），然后调用普通的`format`方法，在这里就不举栗子了。  
我们不仅被允许使用`MessageFormat`类中提供默认的FormatElement去format这些对象，还可以设置自己的`Forma`t对象format这些Object。

```java
/**在这个例子中，MessageFormat和ChoiceFormat被结合使用
* MessageFormat类中有3个方法值的我们关注
* 1.setFormatByArgumentIndex(int argumentIndex, Format newFormat)//
* 2.setFormats(Format[] newFormats)
* 3.setFormat(int formatElementIndex, Format newFormat)
* 在这个例子当中，在MessageFormat的模式字符串的FormatElement（即{}中的内容）中
* 索引为0的地方将使用ChoiceFormat的格式去格式化。
* 如果在set的Format中仍具有FormatElement，则会递归调用MessageFormat的format方法。
*/
MessageFormat form = new MessageFormat("The disk \"{1}\" contains {0}.");
double[] filelimits = { 0, 1, 2 };
String[] filepart = { "no files", "one file", "{0,number} files" };
ChoiceFormat fileform = new ChoiceFormat(filelimits, filepart);
form.setFormatByArgumentIndex(0, fileform);
int fileCount = 1273;
String diskName = "MyDisk";
Object[] testArgs = { new Long(fileCount), diskName };
System.out.println(form.format(testArgs));
//输出：The disk "MyDisk" contains 1,273 files.
```



> 作者：Jadyn

> 链接：[http://www.jianshu.com/p/c8f16cab35e1](http://www.jianshu.com/p/c8f16cab35e1)
>
> 來源：简书
>
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



