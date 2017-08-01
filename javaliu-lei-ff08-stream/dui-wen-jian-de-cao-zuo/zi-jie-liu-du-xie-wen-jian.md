### 循环读，直到文件末尾

```java
import java.io.*;

public class CopyFile {
   public static void main(String args[]) throws IOException
   {
      FileInputStream in = null;
      FileOutputStream out = null;

      try {
         in = new FileInputStream("input.txt");
         out = new FileOutputStream("output.txt");

         int c;
         while ((c = in.read()) != -1) {
            out.write(c);
         }
      }finally {
         if (in != null) {
            in.close();
         }
         if (out != null) {
            out.close();
         }
      }
   }
}

import java.io.*;
class hello{
   public static void main(String[] args) throws IOException {
       String fileName="D:"+File.separator+"hello.txt";
       File f=new File(fileName);
       InputStream in=new FileInputStream(f);
       byte[] b=new byte[1024];
       int len=in.read(b);
       in.close();
       System.out.println("读入长度为："+len);
       System.out.println(new String(b,0,len));
    }
}

```

### 一次性读入

```java
import java.io.*;
class hello{
   public static void main(String[] args) throws IOException {
       String fileName="D:"+File.separator+"hello.txt";
       File f=new File(fileName);
       InputStream in=new FileInputStream(f);
       byte[] b=new byte[1024];
       in.read(b);
       in.close();
       System.out.println(new String(b));
    }
}
```

```java
import java.io.*;
class hello{
   public static void main(String[] args) throws IOException {
       String fileName="D:"+File.separator+"hello.txt";
       File f=new File(fileName);
       InputStream in=new FileInputStream(f);
       byte[] b=new byte[(int)f.length()];
       in.read(b);
       System.out.println("文件长度为："+f.length());
       in.close();
       System.out.println(new String(b));
    }
}
```



