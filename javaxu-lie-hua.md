串行化\(Serialization\)是计算机科学中的一个概念，它是指将对象存储到介质（如文件、内在缓冲区等）中或是以二进制方式通过网络传输。之后可以通过反串行化从这些连续的位数据重新构建一个与原始对象状态相同的对象，因此在特定情况下也可以说是得到一个副本，但并不是所有情况都这样。

Java有Serialization API为开发者提供了一种标准的机制来串行化类。

特别地，串行化主要有三种用途：

##### 1）作为一种持久化机制

如果使用的是FileOutputStream流的方式，则数据将被自动地写入文件中，

##### 2）作为一种复制机制

如果使用的是ByteArrayOutputStream流的方式，数据将写入内存中的字节数组中。该字节数组可以用来创建初始对象的副本，

##### 3）作为一种通信机制

如果是使用套接字（Socket）流的方式，则数据自动地通过网络连接传输一另一个端点，并由这个端点上的程序来决定做什么。

```java
        Student stu = new Student(981036, "LiuMing", 18, "CSD");     
    
        FileOutputStream fo = new FileOutputStream("data.ser");     
    
        ObjectOutputStream so = new ObjectOutputStream(fo);     
    
        try {     
    
            so.writeObject(stu);     
    
            so.close();     
    
        } catch (IOException e) {     
            System.out.println(e);     
        }     
    
        stu = null;     
    
        FileInputStream fi = new FileInputStream("data.ser");     
    
        ObjectInputStream si = new ObjectInputStream(fi);     
    
        try {     
    
            stu = (Student) si.readObject();     
    
            si.close();     
    
        } catch (IOException e)     
    
        {     
            System.out.println(e);     
        }     
```



