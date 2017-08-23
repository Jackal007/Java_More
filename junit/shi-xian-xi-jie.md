![](/assets/org.junit目录结构.png)

* runner:定义了Junit模型中的许多基本概念，只要是一些虚类和接口，是整个Junit工程的基石
* runners:提供了从注解中使用反射完成测试用例执行的实现
* interval:提供了在Runner中许多虚类的默认实现，包括各类RunnerBuilder如基于注解提供Builder、各类Matchers、各类Request如类测试Request、方法测试Request。
* rules:用于用户自定义扩展，规定对于不同statement的用户自定义行为
* validator:从类、方法和域多个方面检查测试样例
* experimental:一些测试特性



JUnit源码被分配到6个包中：junit.awtui、junit.swingui、junit.textui、junit.extensions、junit.framework、junit.runner。其中前三个包中包含了JUnit运行时的入口程序以及运行结果显示界面，它们对于JUnit使用者来说基本是透明的。junit.runner包中包含了支持单元测试运行的一些基础类以及自己的类加载器，它对于JUnit使用者来说是完全透明的。

剩下的两个包是和使用JUnit进行单元测试紧密联系在一起的。其中junit.framework包含有编写一般JUnit单元测试类必须是用到的JUnit类；而junit.extensions则是对framework包在功能上的一些必要扩展以及为更多的功能扩展留下的接口。

JUnit提倡单元测试的简单化和自动化。这就要求JUnit的使用要简单化，而且要很容易的实现自动化测试。整个JUnit的设计大概也是遵循这个前提吧。整个框架的骨干仅有三个类组成（下图所示）。

![](/assets/junitTestResult组成.png)

junit.framework中类之间的关系，下图是我根据源代码分析出来的，大部分关系都表示了出来。

![](/assets/junitframework类关系.png)

 先来看看各个类的职责。Assert类提供了JUnit使用的一整套的断言，这套断言都被TestCase继承下来，Assert也就变成了透明的。Test接口是为了统一TestCase和TestSuite的类型；而TestCase里面提供了运行单元测试类的方法；在TestSuite中则提供了加载单元测试类，检验测试类格式等等的方法。TestResult故名思意就是提供存放测试结果的地方，但是在JUnit中它还带有一点控制器的功能。TestListener接口抽象了所有测试监听者的行为，他包括两个添加错误和失败的方法，开始测试和结束测试的方法。在JUnit框架中有两个类实现了这个接口，一个负责结果打印的ResultPrinter类，一个是所有TestRunner的基础类BaseTestRunner类（这两个类都不在framework包中）。

