![](/assets/InputStream.png)

1. InputStream 是所有的输入字节流的父类，它是一个抽象类。

2. ByteArrayInputStream、StringBufferInputStream、FileInputStream 是三种基本的介质流，它们分别从Byte 数组、StringBuffer、和本地文件中读取数据。PipedInputStream 是从与其它线程共用的管道中读取数据

3. ObjectInputStream 和所有FilterInputStream 的子类都是装饰流（装饰器模式的主角）。



