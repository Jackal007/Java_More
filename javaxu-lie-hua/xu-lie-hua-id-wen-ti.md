1. 串行化**只能保存对象的非静态成员变量**，不能保存任何的成员方法和静态的成员变量，而且串行化保存的只是变量的值，对于变量的任何修饰符都不能保存。

2. 串行化可能涉及将对象存放到磁盘上或在网络上**发送**数据，这时候就会产生安全问题。因为数据位于Java运行环境之外，不在Java安全机制的控制之中。对于这些需要保密的字段，不应保存在永久介质中 ，或者不应简单地不加处理地保存下来 ，为了保证安全性。应该在这些字段前加上**transient**关键字。`private transient String pwd`

3. **序列化 ID 问题，**发送和接收方的对象应该有一样的ID，否则转换将不成功

4. 自定义**对象类里的 writeObject 和 readObject 方法，**否则默认调用是 ObjectOutputStream 的 defaultWriteObject 方法以及 ObjectInputStream 的 defaultReadObject 方法。自定义那两个方法可以实现很多功能，比如密码的加密





