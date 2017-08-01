### 循环读，直到文件末尾

```java
import java.io.*;

public class CopyFile {
   public static void main(String args[]) throws IOException
   {
      FileReader in = null;
      FileWriter out = null;

      try {
         in = new FileReader("input.txt");
         out = new FileWriter("output.txt");

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

import java.io.DataInputStream;
import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
  
public class DataOutputStreamDemo{
   public static void main(String[] args) throws IOException{
       File file = new File("d:" + File.separator +"hello.txt");
       DataInputStream input = new DataInputStream(new FileInputStream(file));
       char[] ch = new char[10];
       int count = 0;
       char temp;
       while((temp = input.readChar()) != 'C'){
           ch[count++] = temp;
       }
       System.out.println(ch);
    }
}

```

### 

### 一次性读入



