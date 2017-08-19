![](/assets/org.junit目录结构.png)

* runner:定义了Junit模型中的许多基本概念，只要是一些虚类和接口，是整个Junit工程的基石
* runners:提供了从注解中使用反射完成测试用例执行的实现
* interval:提供了在Runner中许多虚类的默认实现，包括各类RunnerBuilder如基于注解提供Builder、各类Matchers、各类Request如类测试Request、方法测试Request。
* rules:用于用户自定义扩展，规定对于不同statement的用户自定义行为
* validator:从类、方法和域多个方面检查测试样例
* experimental:一些测试特性



