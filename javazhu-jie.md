用[@Deprecated](http://java.sun.com/j2se/1.5.0/docs/guide/javadoc/deprecation/deprecation.html)注释的程序元素，不鼓励程序员使用这样的元素，通常是因为它很危险或存在更好的选择。在使用不被赞成的程序元素或在不被赞成的代码中执行重写时，编译器会发出警告。

其次，请注意标题，这两个标记有大小写之分，一个是\*\*D\*\*，一个是\*\*d\*\*。

源代码标记[@Deprecated](http://java.sun.com/j2se/1.5.0/docs/guide/javadoc/deprecation/deprecation.html)是在JDK1.5中作为内置的annotation引入的，用于表明类\(class\)、方法\(method\)、字段\(field\)已经不再推荐使用，并且在以后的JDK版本中可能将其删除，编译器在默认情况下检测到有此标记的时候会提示警告信息。

Java注释中的@deprecated用于在用[Javadoc](http://java.sun.com/j2se/javadoc/)工具生成文档的时候，标注此类/接口、方法、字段已经被废止。

不过后者还有一个功能就是和源代码标记[@Deprecated](http://java.sun.com/j2se/1.5.0/docs/guide/javadoc/deprecation/deprecation.html)同样的功能，在JDK1.4版本之后，该功能被[@Deprecated](http://java.sun.com/j2se/1.5.0/docs/guide/javadoc/deprecation/deprecation.html)所取代。

java.lang.Deprectated是J2SE 5.0中标准的Annotation型态之一，它对编译器说明某个方法已经不建议使用，如果有人试图使用或重新定义该方法，必须提出警示讯息。

举个例子来说，您可能定义一个CustomObject类别，并在当中定义有getSomething\(\)方法，而在一段时间之后，您不建议使用这个方法 了，并要将这个方法标示为deprectated，您可以这么作：

##### CustomObject.java

```
public class CustomObject {
    @Deprecated public String getSomething() {
        return "something";
    }
}
```

如果有人试图在继承这个类别后重新定义getSomething\(\)，或是在程序中呼叫使用getSomething\(\)方法，则进行编译时，就会出现这 个警讯：

```
Note: SubCustomObject.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
```

想要知道详细的警讯内容的话，可以在编译时加上-Xline:deprecation自变量，例如：

```
>
javac -Xlint:deprecation SubCustomObject.java
SubCustomObject.java:5: warning: [deprecation] getSomething() in CustomObject ha s been deprecated
object.getSomething();
^
1 warning
```

java.lang.Deprecated是个Marker annotation，简单的说就是用于标示，annotation名称本身即包括了要给工具程序的信息。

转自

[http://lijinwei-123.i.sohu.com/blog/view/161053895.htm](http://lijinwei-123.i.sohu.com/blog/view/161053895.htm)

