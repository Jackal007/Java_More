## 类名

如果你在编译期不知道类的名字，但是你可以在运行期获得到类名的字符串,那么你则可以这么做来获取 Class 对象:  
你可以从 Class 对象中获取两个版本的类名。

通过 getName\(\) 方法返回类的全限定类名（包含包名）：

```
Class aClass = ... //获取Class对象，具体方式可见Class对象小节
String className = aClass.getName();
```

如果你仅仅只是想获取类的名字\(不包含包名\)，那么你可以使用 getSimpleName\(\)方法:

```
Class aClass = ... //获取Class对象，具体方式可见Class对象小节
String simpleClassName = aClass.getSimpleName();
```

这个方法对读别人（庞大复杂的app）的代码特别有用，就拿安卓来说吧，你可以在Activity 或者是自己定义的BaseActivity中打印该className or simpleClassName

```
Log.i(simpleClassName,"Someting");
//这样你就知道自己每次打开的是具体哪个activity了，对阅读捋清App功能逻辑很有帮助
```



