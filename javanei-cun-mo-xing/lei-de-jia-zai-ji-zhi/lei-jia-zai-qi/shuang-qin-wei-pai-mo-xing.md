从java虚拟机的角度来讲，只存在两种不同的类加载器：

* 启动类加载器（使用C++实现），它是虚拟机自身的一部分
* 所有其他的类加载器，处于虚拟机外部，这些类加载器都是由java实现的，都继承自抽线类java.lang.ClassLoader



从java开发人员的角度来看，类加载器还可以划分得更细致一些绝大部分java会使用到一下3种系统提供的类加载器

* 启动类加载器\(Bootstrap ClassLoader\)
* 扩展加载器\(Extension ClassLoader\)
* 应用程序类加载器\(Application ClassLoader\)

我们的应用程序都是由这3种类加载器互相配合进行加载的，如果由必要，还可以加入自定义的类加载器。![](/assets/双亲委派模型.png)

