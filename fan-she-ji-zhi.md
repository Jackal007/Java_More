Java反射机制可以让我们在编译期（Compile Time）之外的运行期（Runtime）获得任何一个类的字节码。包括接口、变量、方法等信息。还可以让我们在运行期实例化对象，通过调用get/set方法获取变量的值。

 下面是一个小例子，让大家感受下Java反射的魔力

```java
Method[] methods = MyObject.class.getMethods();
for(Method method : methods){
    System.out.println("method = " + method.getName());
}
```

这个例子通过调用类的class属性获取对应的class对象，通过这个 Class 类的对象获取 MyObject 类中的方法集合

```java
Class myObjectClass = MyObject.class;
```

使用 Java 反射机制可以在运行时期检查 Java 类的信息，检查 Java 类的信息往往是你在使用 Java 反射机制的时候所做的第一件事情，通过获取类的信息你可以获取以下相关的内容：

## 1.Class 对象

在你想检查一个类的信息之前，你首先需要获取类的 Class 对象。Java 中的所有类型包括基本类型\(int, long, float等等\)，即使是数组都有与之关联的 Class 类的对象。如果你在编译期知道一个类的名字的话，那么你可以使用如下的方式获取一个类的 Class 对象。

```
String
 className = ... ;
//在运行期获取的类名字符串
Class
class
 = 
Class
.forName(className);
```

## 2.类名

如果你在编译期不知道类的名字，但是你可以在运行期获得到类名的字符串,那么你则可以这么做来获取 Class 对象:  
你可以从 Class 对象中获取两个版本的类名。

通过 getName\(\) 方法返回类的全限定类名（包含包名）：

```
Class
 aClass = ... //获取
Class
对象，具体方式可见
Class
对象小节
String className = aClass.getName();
```

如果你仅仅只是想获取类的名字\(不包含包名\)，那么你可以使用 getSimpleName\(\)方法:

```
Class
 aClass = ... //获取
Class
对象，具体方式可见
Class
对象小节
String simpleClassName = aClass.getSimpleName();
```

这个方法对读别人（庞大复杂的app）的代码特别有用，就拿安卓来说吧，你可以在Activity 或者是自己定义的BaseActivity中打印该className or simpleClassName

```
Log
.
i
(simpleClassName,
"Someting"
);

//这样你就知道自己每次打开的是具体哪个activity了，对阅读捋清App功能逻辑很有帮助
```

## 3.修饰符

可以通过 Class 对象来访问一个类的修饰符， 即public,private,static 等等的关键字，你可以使用如下方法来获取类的修饰符：

```
Class
  aClass = ... //获取
Class
对象，具体方式可见
Class
对象小节

int
 modifiers = aClass.getModifiers();
```

修饰符都被包装成一个int类型的数字，这样每个修饰符都是一个位标识\(flag bit\)，这个位标识可以设置和清除修饰符的类型。 可以使用 java.lang.reflect.Modifier 类中的方法来检查修饰符的类型：

```
Modifier.isAbstract(int modifiers)
;

Modifier.isFinal(int modifiers)
;

Modifier.isInterface(int modifiers)
;

Modifier.isNative(int modifiers)
;

Modifier.isPrivate(int modifiers)
;

Modifier.isProtected(int modifiers)
;

Modifier.isPublic(int modifiers)
;

Modifier.isStatic(int modifiers)
;

Modifier.isStrict(int modifiers)
;

Modifier.isSynchronized(int modifiers)
;

Modifier.isTransient(int modifiers)
;

Modifier.isVolatile(int modifiers)
;
```

## 4.包信息

可以使用 Class 对象通过如下的方式获取包信息：

```
Class
  aClass = ... 
//获取Class对象，具体方式可见Class对象小节
Package
package
 = aClass.getPackage();
```

通过 Package 对象你可以获取包的相关信息，比如包名，你也可以通过 Manifest 文件访问位于编译路径下 jar 包的指定信息，比如你可以在 Manifest 文件中指定包的版本编号。更多的 Package 类信息可以阅读 java.lang.Package。

## 5.父类

通过 Class 对象你可以访问类的父类，如下例：

```
Class superclass
 = aClass.getSuperclass();
```

可以看到 superclass 对象其实就是一个 Class 类的实例，所以你可以继续在这个对象上进行反射操作。

## 6.实现的接口

可以通过如下方式获取指定类所实现的接口集合：

```
Class
  aClass = ... //获取
Class
对象，具体方式可见
Class
对象小节

Class
[] interfaces = aClass.getInterfaces();
```

由于一个类可以实现多个接口，因此 getInterfaces\(\); 方法返回一个 Class 数组，在 Java 中接口同样有对应的 Class 对象。 注意：getInterfaces\(\) 方法仅仅只返回当前类所实现的接口。当前类的父类如果实现了接口，这些接口是不会在返回的 Class 集合中的，尽管实际上当前类其实已经实现了父类接口。

## 7.构造器

我们可以通 过 Class 对象来获取 Constructor 类的实例：

```
Class
 aClass = ...
//获取Class对象
Constructor
[] 
constructors
 = 
aClass
.
getConstructors
()
;
```

返回的 Constructor 数组包含每一个声明为公有的（Public）构造方法。 如果你知道你要访问的构造方法的方法参数类型，你可以用下面的方法获取指定的构造方法，这例子返回的构造方法的方法参数为 String 类型：

```
Class
 aClass = ...
//获取Class对象
Constructor
constructor
 =

aClass
.
getConstructor
(
new
Class
[]{String.
class
})
;
```

如果没有指定的构造方法能满足匹配的方法参数则会抛出：NoSuchMethodException。

构造方法参数  
你可以通过如下方式获取指定构造方法的方法参数信息：

```
Constructor
constructor
 = ... 
//获取Constructor对象
Class
[] 
parameterTypes
 = 
constructor
.
getParameterTypes
()
;
```

利用 Constructor 对象实例化一个类  
你可以通过如下方法实例化一个类：

```
Constructor
constructor
 = 
MyObject
.
class
.
getConstructor
(
String
.
class
)
;

MyObject myObject = (MyObject)
 
constructor
.
newInstance
("
constructor
-arg1")
;
```

constructor.newInstance\(\)方法的方法参数是一个可变参数列表，但是当你调用构造方法的时候你必须提供精确的参数，即形参与实参必须一一对应。在这个例子中构造方法需要一个 String 类型的参数，那我们在调用 newInstance 方法的时候就必须传入一个 String 类型的参数。

## 8.方法

可以通过 Class 对象获取 Method 对象，如下例：

```
Class
 aClass = ...
//获取Class对象
Method
[] 
methods
 = 
aClass
.
getMethods
()
;
```

返回的 Method 对象数组包含了指定类中声明为公有的\(public\)的所有变量集合。

如果你知道你要调用方法的具体参数类型，你就可以直接通过参数类型来获取指定的方法，下面这个例子中返回方法对象名称是“doSomething”，他的方法参数是 String 类型：

```
Class
  aClass = ...
//获取Class对象
Method
method
 = 
aClass
.
getMethod
("doSomething", 
new
Class
[]{String.
class
})
;
```

如果根据给定的方法名称以及参数类型无法匹配到相应的方法，则会抛出 NoSuchMethodException。 如果你想要获取的方法没有参数，那么在调用 getMethod\(\)方法时第二个参数传入 null 即可，就像这样：

```
Class
  aClass = ...
//获取Class对象
Method
method
 = 
aClass
.
getMethod
("doSomething", null)
;
```

方法参数以及返回类型  
你可以获取指定方法的方法参数是哪些：

```
Method
method
 = ... //获取
Class
对象

Class
[] 
parameterTypes
 = 
method
.
getParameterTypes
()
;
```

你可以获取指定方法的返回类型：

```
Method
method
 = ... //获取
Class
对象

Class
returnType
 = 
method
.
getReturnType
()
;
```

通过 Method 对象调用方法  
你可以通过如下方式来调用一个方法：

```
//获取一个方法名为doSomesthing，参数类型为String的方法
Method
method
 = 
MyObject
.
class
.
getMethod
("doSomething", String.
class
)
;

Object returnValue = 
method
.
invoke
(null, "parameter-value1")
;
```

传入的 null 参数是你要调用方法的对象，如果是一个静态方法调用的话则可以用 null 代替指定对象作为 invoke\(\)的参数，在上面这个例子中，如果 doSomething 不是静态方法的话，你就要传入有效的 MyObject 实例而不是 null。 Method.invoke\(Object target, Object … parameters\)方法的第二个参数是一个可变参数列表，但是你必须要传入与你要调用方法的形参一一对应的实参。就像上个例子那样，方法需要 String 类型的参数，那我们必须要传入一个字符串。

## 9.变量

你可以通过如下方式访问一个类的成员变量：

```
Field[] 
method
 = 
aClass
.
getFields
()
;
```

在通常的观点中从对象的外部访问私有变量以及方法是不允许的，但是 Java 反射机制可以做到这一点。使用这个功能并不困难，在进行单元测试时这个功能非常有效。本节会向你展示如何使用这个功能。

注意：这个功能只有在代码运行在单机 Java 应用\(standalone Java application\)中才会有效,就像你做单元测试或者一些常规的应用程序一样。如果你在 Java Applet 中使用这个功能，那么你就要想办法去应付 SecurityManager 对你限制了。但是一般情况下我们是不会这么做的，所以在本节里面我们不会探讨这个问题。

访问私有变量  
要想获取私有变量你可以调用 Class.getDeclaredField\(String name\)方法或者 Class.getDeclaredFields\(\)方法。

Class.getField\(String name\)和 Class.getFields\(\)只会返回公有的变量，无法获取私有变量。下面例子定义了一个包含私有变量的类，在它下面是如何通过反射获取私有变量的例子：

```
public
class
PrivateObject
{

  
private
String
 privateString = 
null
;

  
public
 PrivateObject(
String
 privateString) {
    
this
.privateString = privateString;
  }
}
PrivateObject privateObject = 
new
PrivateObject
(
"The Private Value"
);

Field privateStringField = PrivateObject.class.
            getDeclaredField(
"privateString"
);

privateStringField.setAccessible(
true
);


String
 fieldValue = (
String
) privateStringField.
get
(privateObject);
System.out.println(
"fieldValue = "
 + fieldValue);
```

这个例子会输出”fieldValue = The Private Value”，The Private Value 是 PrivateObject 实例的 privateString 私有变量的值，注意调用 PrivateObject.class.getDeclaredField\(“privateString”\)方法会返回一个私有变量，这个方法返回的变量是定义在 PrivateObject 类中的而不是在它的父类中定义的变量。 注意 privateStringField.setAccessible\(true\)这行代码，通过调用 setAccessible\(\)方法会关闭指定类 Field 实例的反射访问检查，这行代码执行之后不论是私有的、受保护的以及包访问的作用域，你都可以在任何地方访问，即使你不在他的访问权限作用域之内。但是你如果你用一般代码来访问这些不在你权限作用域之内的代码依然是不可以的，在编译的时候就会报错。

访问私有方法  
访问一个私有方法你需要调用 Class.getDeclaredMethod\(String name, Class\[\] parameterTypes\)或者 Class.getDeclaredMethods\(\) 方法。 Class.getMethod\(String name, Class\[\] parameterTypes\)和 Class.getMethods\(\)方法，只会返回公有的方法，无法获取私有方法。下面例子定义了一个包含私有方法的类，在它下面是如何通过反射获取私有方法的例子：

```
public
class
PrivateObject
{

  
private
String
 privateString = 
null
;

  
public
 PrivateObject(
String
 privateString) {
    
this
.privateString = privateString;
  }

  
private
String
 getPrivateString(){
    
return
this
.privateString;
  }
}
PrivateObject privateObject = 
new
PrivateObject
(
"The Private Value"
);

Method privateStringMethod = PrivateObject.class.
        getDeclaredMethod(
"getPrivateString"
, 
null
);

privateStringMethod.setAccessible(
true
);


String
 returnValue = (
String
)
        privateStringMethod.invoke(privateObject, 
null
);

System.out.println(
"returnValue = "
 + returnValue);
```

这个例子会输出”returnValue = The Private Value”，The Private Value 是 PrivateObject 实例的 getPrivateString\(\)方法的返回值。 PrivateObject.class.getDeclaredMethod\(“privateString”\)方法会返回一个私有方法，这个方法是定义在 PrivateObject 类中的而不是在它的父类中定义的。 同样的，注意 Method.setAcessible\(true\)这行代码，通过调用 setAccessible\(\)方法会关闭指定类的 Method 实例的反射访问检查，这行代码执行之后不论是私有的、受保护的以及包访问的作用域，你都可以在任何地方访问，即使你不在他的访问权限作用域之内。但是你如果你用一般代码来访问这些不在你权限作用域之内的代码依然是不可以的，在编译的时候就会报错。

## 10.泛型

运用泛型反射的经验法则

下面是两个典型的使用泛型的场景：  
1、声明一个需要被参数化（parameterizable）的类/接口。  
2、使用一个参数化类。

当你声明一个类或者接口的时候你可以指明这个类或接口可以被参数化， java.util.List 接口就是典型的例子。你可以运用泛型机制创建一个标明存储的是 String 类型 list，这样比你创建一个 Object 的l ist 要更好。  
当你想在运行期参数化类型本身，比如你想检查 java.util.List 类的参数化类型，你是没有办法能知道他具体的参数化类型是什么。这样一来这个类型就可以是一个应用中所有的类型。但是，当你检查一个使用了被参数化的类型的变量或者方法，你可以获得这个被参数化类型的具体参数。  
总之：  
你不能在运行期获知一个被参数化的类型的具体参数类型是什么，但是你可以在用到这个被参数化类型的方法以及变量中找到他们，换句话说就是获知他们具体的参数化类型。 在下面的段落中会向你演示这类情况。  
泛型方法返回类型  
如果你获得了 java.lang.reflect.Method 对象，那么你就可以获取到这个方法的泛型返回类型信息。如果方法是在一个被参数化类型之中（译者注：如 T fun\(\)）那么你无法获取他的具体类型，但是如果方法返回一个泛型类（译者注：如 List fun\(\)）那么你就可以获得这个泛型类的具体参数化类型。你可以在“[Java Reflection: Methods](http://tutorials.jenkov.com/java-reflection/generics.html)”中阅读到有关如何获取Method对象的相关内容。下面这个例子定义了一个类这个类中的方法返回类型是一个泛型类型：

```
public
class
MyClass
{

  
protected
 List
<
String
>
 stringList = ...;

  
public
 List
<
String
>
 getStringList(){
    
return
this
.stringList;
  }
}
```

我们可以获取 getStringList\(\)方法的泛型返回类型，换句话说，我们可以检测到 getStringList\(\)方法返回的是 List 而不仅仅只是一个 List。如下例：

```
Method
method
 = 
MyClass
.
class
.
getMethod
("getStringList", null)
;
Type
 returnType = 
method
.
getGenericReturnType
()
;
if
(returnType instanceof ParameterizedType)
{
    ParameterizedType type = (ParameterizedType) returnType;
    Type[] typeArguments = type.getActualTypeArguments();
    for(Type typeArgument : typeArguments){
        Class typeArgClass = (Class) typeArgument;
        System.out.println("typeArgClass = " + typeArgClass);
    }

}
```

这段代码会打印出 “typeArgClass = java.lang.String”，Type\[\]数组typeArguments 只有一个结果 – 一个代表 java.lang.String 的 Class 类的实例。Class 类实现了 Type 接口。

泛型方法参数类型

你同样可以通过反射来获取方法参数的泛型类型，下面这个例子定义了一个类，这个类中的方法的参数是一个被参数化的 List：

```
public
 class MyClass {
  
protected
List
<
String
>
 stringList = 
...
;

  
public
void
 setStringList(
List
<
String
>
list
){
    this.stringList = 
list
;
  }
}
```

你可以像这样来获取方法的泛型参数：

```
method
 = 
Myclass
.
class
.
getMethod
("setStringList", List.
class
)
;
Type
[] genericParameterTypes = 
method
.
getGenericParameterTypes
()
;
for
(
Type
 genericParameterType : genericParameterTypes)
{
    if(genericParameterType instanceof ParameterizedType){
        ParameterizedType aType = (ParameterizedType) genericParameterType;
        Type[] parameterArgTypes = aType.getActualTypeArguments();
        for(Type parameterArgType : parameterArgTypes){
            Class parameterArgClass = (Class) parameterArgType;
            System.out.println("parameterArgClass = " + parameterArgClass);
        }

    }
}
```

这段代码会打印出”parameterArgType = java.lang.String”。Type\[\]数组 parameterArgTypes 只有一个结果 – 一个代表 java.lang.String 的 Class 类的实例。Class 类实现了Type接口。  
泛型变量类型  
同样可以通过反射来访问公有（Public）变量的泛型类型，无论这个变量是一个类的静态成员变量或是实例成员变量。你可以在“[Java Reflection: Fields](http://tutorials.jenkov.com/java-reflection/fields.html)”中阅读到有关如何获取 Field 对象的相关内容。这是之前的一个例子，一个定义了一个名为 stringList 的成员变量的类。

```
method
 = 
Myclass
.
class
.
getMethod
("setStringList", List.
class
)
;
Type
[] genericParameterTypes = 
method
.
getGenericParameterTypes
()
;
for
(
Type
 genericParameterType : genericParameterTypes)
{
    if(genericParameterType instanceof ParameterizedType){
        ParameterizedType aType = (ParameterizedType) genericParameterType;
        Type[] parameterArgTypes = aType.getActualTypeArguments();
        for(Type parameterArgType : parameterArgTypes){
            Class parameterArgClass = (Class) parameterArgType;
            System.out.println("parameterArgClass = " + parameterArgClass);
        }

    }
}
```

这段代码会打印出”fieldArgClass = java.lang.String”。Type\[\]数组 fieldArgClass 只有一个结果 – 一个代表 java.lang.String 的 Class 类的实例。Class 类实现了 Type 接口。

  


  


作者：总是擦破皮

链接：http://www.jianshu.com/p/2315dda64ad2

來源：简书

著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



[**Java**](http://lib.csdn.net/base/java)**反射机制的适用场景及其利与弊**

**一、反射的适用场景是什么？**

**1）**.Java的反射机制在做基础框架的时候非常有用，有一句话这么说来着：**反射机制是很多Java框架的基石**。而一般应用层面很少用，不过这种东西，现在很多开源框架基本都已经给你封装好了，自己基本用不着写。典型的除了[hibernate](http://lib.csdn.net/base/javaee)之外，还有[spring](http://lib.csdn.net/base/javaee)也用到很多反射机制。经典的就是在xml文件或者properties里面写好了配置，然后在Java类里面解析xml或properties里面的内容，得到一个字符串，然后用反射机制，根据这个字符串获得某个类的Class实例，这样就可以动态配置一些东西，不用每一次都要在代码里面去new或者做其他的事情，以后要改的话直接改配置文件，代码维护起来就很方便了，同时有时候要适应某些需求，Java类里面不一定能直接调用另外的方法，这时候也可以通过反射机制来实现。  
总的来说，自己写的很少，具体什么时候要用那要看需求，反射机制无非就是根据一个String来得到你要的实体对象，然后调用它原来的东西。**但是如果是要自己写框架的话，那就会用得比较多了。**

**2）**当你做一个软件可以安装插件的功能，你连插件的类型名称都不知道，你怎么实例化这个对象呢？因为程序是支持插件的（第三方的），在开发的时候并不知道 。所以无法在代码中 New出来 ，但反射可以，通过反射，动态加载程序集，然后读出类，检查标记之后再实例化对象，就可以获得正确的类实例。

**3）**在编码阶段不知道那个类名,要在运行期从配置文件读取类名, 这时候就没有办法硬编码new ClassName\(\),而必须用到反射才能创建这个对象.反射的目的就是为了扩展未知的应用。比如你写了一个程序，这个程序定义了一些接口，只要实现了这些接口的dll都可以作为插件来插入到这个程序中。那么怎么实现呢？就可以通过反射来实现。就是把dll加载进内存，然后通过反射的方式来调用dll中的方法。很多工厂模式就是使用的反射。 

**二、程序员在自己的业务开发中应该尽量的远离反射**

**反射：**在流行的库如Spring和Hibernate中，反射自然有其用武之地。不过内省业务代码在很多时候都不是一件好事，**原因有很多，一般情况下我总是建议大家不要使用反射。**

首先是代码可读性与工具支持。打开熟悉的IDE，寻找你的Java代码的内部依赖，很容易吧。现在，使用反射来替换掉你的代码然后再试一下，结果如何呢？如果通过反射来修改已经封装好的对象状态，那么结果将会变得更加不可控。请看看如下示例代码：

![](http://img.blog.csdn.net/20140608160935296)  


如果这样做就无法得到编译期的安全保证。就像上面这个示例一样，你会发现如果getDeclaredField\(\)方法调用的参数输错了，那么只有在运行期才能发现。要知道的是，寻找运行期Bug的难度要远远超过编译期的Bug。

最后还要谈谈代价问题。JIT对反射的优化程度是不同的，有些优化时间会更长一些，而有些甚至是无法应用优化。因此，有时反射的性能损失可以达到几个数量级的差别。不过在典型的业务应用中，你可能不会注意到这个代价。

总结一下，我觉得在业务代码中唯一合理\(直接\)使用反射的场景是通过AOP。除此之外，你最好远离反射这一特性。

**三、性能分析**

反射机制是一种程序自我分析的能力。用于获取一个类的类变量，构造函数，方法，修饰符。

**优点：**运行期类型的判断，动态类加载，动态代理使用反射。

**缺点：**性能是一个问题，反射相当于一系列解释操作，通知jvm要做的事情，性能比直接的java代码要慢很多。



http://blog.csdn.net/zolalad/article/details/29370565

