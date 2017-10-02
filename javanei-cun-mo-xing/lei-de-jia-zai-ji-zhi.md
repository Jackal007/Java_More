类从被加载到虚拟机内存开始，到卸载出内存为止，它的整个生命周期包括：

* 加载 Loading
* 验证 Verification
* 准备 Preoaration
* 解析 Resolution
* 初始化 Initialization
* 使用 Using
* 卸载 Unloading![](/assets/类的生命周期.png)

解析阶段在某些情况下可以在初始化阶段之后再开始，这是为了支持Java语言的运行时绑定（也称动态绑定或晚期绑定）

这些阶段通常都是互相交叉地混合进行地，通常会在一个阶段执行的过程中调用、激活另外一个阶段。



