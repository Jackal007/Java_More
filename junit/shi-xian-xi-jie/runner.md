* Runner:以Notifier为参数允许测试样例，运行过程中的Notifier负责监视测试过程

* Request:负责记录测试样例的Description信息，同事负责提供对应的Runner。可以通过Computer结合指定或默认的RunnerBuilder来直接为一系列测试类统一提供Runner

* Description:描述测试样例，使用Composite模式，组合多个样例

* Result:记录异常和失败，内置一个Listener来实现与测试过程的同步，测试完成时count自增，有样例失败则加入Failure列表

* Failure:将断言失败和抛出异常综合在同一个框架下，同时提供了Description的信息

* Listener:监视测试过程,典型的观察者模式

* Notifier:管理一系列Listener，保证线程安全

* Filter:指定条件，只运行符合条件的测试样例，可以动态添加，为每次测试增加了灵活性



