**一、File的构造方法**

```java
public File(String pathname)//传入一个表示路径的字符串，可以是绝对路径也可以是相对路径
public File(String parent, String child)//果parent为空的话，自然是以child为路径初始化参数，这就等于第一种方式了
public File(File parent, String child)//传入File类的对象作为parent，其实内部是将parent.path的路径值拿来执行第二种构造方法
```



**二、文件名和文件路径操作**  
     我们知道，File对象既可以存文件也可以存路径，那么对他们的相关操作有如下几种：

```java
public String getName()
public String getPath()
public boolean isAbsolute()

public String getParent()
public File getParentFile()

public String getAbsolutePath()
public File getAbsoluteFile()

public String getCanonicalPath()
public File getCanonicalFile()
```

```
 主要有上述几种对文件名和文件路径的操作。getName很简单，就是获取该文件对象的文件名，内部是怎么实现的呢？我们看看代码：
```

```java
public
 String getName() {

int
index
 = path.lastIndexOf(separatorChar);

if
 (
index
<
 prefixLength) 
return
 path.substring(prefixLength);

return
 path.substring(
index
 + 
1
);
    }
```

```
 separatorChar 表示路径分隔符，在windows中，一般默认使用“\”，作为文件分隔符，Linux系统中使用“/”。prefixLength表示文件前缀名长度。（也就是最后一个路径分隔符前面的所有字符串的长度），此处index拿到最后一个路径分隔符的索引，截取此位置后面的字符串作为结果返回。这样无论File对象中存放的是什么，都可以拿到它的name。
```

```
public
class
Test_InputOrOutput
 {

public
static
void
main
(
String[] args
) throws IOException
{

        File f = 
new
 File(
"C://Users/directory"
);
        System.
out
.println(f.getName());

    }
}

//即使File对象中存放的是路径，依然返回路径名directory
```

```
 接下来看看getPath这个方法。getPath就一条语句，返回该对象的私有成员path，这是当初调用构造方法传入的pathName。isAbsolute方法调用文件系统类的方法判断当前pathName是否是绝对路径，getAbsolutePath获取当前File对象的绝对路径，相对于当前项目根目录的位置来指定的。  
 getParent方法返回当前文件对象的父目录路径。内部是这样实现的：
```

```
public
 String getParent() {

int
index
 = path.lastIndexOf(separatorChar);

if
 (
index
<
 prefixLength) {

if
 ((prefixLength 
>
0
) 
&
&
 (path.length() 
>
 prefixLength))

return
 path.substring(
0
, prefixLength);

return
 null;
        }

return
 path.substring(
0
, 
index
);
    }
```

```
 和getName方法类似，都是首先找到默认路径分隔符的最后一次出现的位置，然后通过一系列判断处理了各种意外的情况，例如：
```

```
File f = 
new
 File(
"directory"
);
System.
out
.println(f.getParent());  
//输出：null


File f = 
new
 File(
"directory/"
);
System.
out
.println(f.getParent());  
//输出：null


File f = 
new
 File(
"a/directory"
);
System.
out
.println(f.getParent());  
//输出：a
```

```
 只有路径正常的时候才会执行：return path.substring\(0, prefixLength\);，返回对应的父目录的路径。getParentFile方法返回父目录对应的File对象。
```

```
public
 File 
getParentFile
(
) 
{
        String p = 
this
.getParent();

if
 (p == 
null
) 
return
null
;

return
new
 File(p, 
this
.prefixLength);
    }
```

```
 从getParentFile的源代码中，我们可以看到，它调用了getParent方法获取父目录路径，但是如果该路径是空的的话就返回null，否则根据此路径构建一个新的File对象并返回。像下面这种情况就不能正确获取getParentFile：
```

```
File f = 
new
 File(
"directory"
);
File 
parent
 = f.getParentFile();
System.out.println(
parent
.getPath());

//抛出空指针异常，说明parent为null
```

```
 对于这种情况难道就没有办法了吗？其实可以组合getAbsoluteFile方法和getParentFile方法，来获取父目录的File对象。
```

```
File
 f = new 
File
(
"directory"
);

File
 parent = f.getAbsoluteFile().getParentFile();
System.
out
.println(parent.getPath());
```

**三、文件的信息**  
     在我们的文件操作中，File对象中既可以存放文件有可以存放路径信息，那我们怎么区分他们呢？其实在File中还封装了一些判断文件信息的方法。

```
public
boolean
 canRead()

public
boolean
 canWrite()

public
boolean
 exists()

public
boolean
 isDirectory()

public
boolean
 isFile()

public
boolean
 isHidden()

public
long
 lastModified()  
//最后一次修改的时间
```

```
 从方法的命名大家就可以看出来每个方法所代表的含义。（世界上最好的注释就是没有注释，单命名就已经让人理解其作用）
```

**四、操作文件**  
     最后是文件的操作，真正意义上的对文件在磁盘上的存储方式进行操作。java中的File对象被创建出来之后，并不意味着在磁盘上已经创建了对应的文件，真正想要在磁盘上创建文件需要调用createNewFile方法。不用看实现代码，这么底层的操作肯定调用的是文件系统类中的方法。  
     使用createNewFile创建文件成功返回true，失败返回false。如果文件已经存在则不会去创建他，但是返回false。  
     文件的删除主要有两个方法。delete和deleteOnExit，前者会删除文件或者目录返回boolean，后者标记一下，等到虚拟机退出时候进行实际删除操作。需要注意的是如果将要删除的文件目录不为空就不能完成删除操作。

```
File f = 
new
 File(
"a"
);
f.mkdir();

File d = 
new
 File(
"a/a.txt"
);
d.createNewFile();

System.out.
println
(f.
delete
());

//输出结果：false
```

```
 所以在我们将要删除一个目录的时候就需要清空其中的所有内容。
```

**五、目录操作**  
     最后说说目录操作，其实在我们上面的代码中也已经稍有涉及了。创建一个目录有两种方法：

```
public
boolean
 mkdir()

public
boolean
 mkdirs()
```

```
 这两个操作有一定的区别，比如我要在c盘根目录下创建一个名为a的文件夹，new File\("C://a"\).mkdir\(\);或者new File\("C://a"\).mkdirs\(\);。浪着的效果是一样的。但是如果我要在c盘的b文件夹中创建一个d目录，其中b文件夹不存在。mkdir方法就无法完成任务了，因为中间有个文件夹b没有被创建。而mkdirs会将b文件夹也一起创建了。这就是它俩的区别。  
 关于目录操作的最后一个就是目录的遍历。File中也提供了很多方法。
```

```
public
String
[] list()

public
File
[] listFiles()


public
String
[] list(FilenameFilter filter)

public
File
[] listFiles(FilenameFilter filter)

public
File
[] listFiles(FileFilter filter)
```

```
 调用list返回目录下的所有文件的name：
```

```
File f = 
new
 File(
"f:/360"
);
String[] 
list
 = f.
list
();

for
 (String s : 
list
){
    System.out.println(s);
}

//这是在我的f盘下的360文件夹中的所有文件名

输出结果：

360
defender

360
sdSetup.exe

360
zip
```

```
 毋庸置疑，listFiles返回的是这些文件名构成的File对象数组。我们重点看剩下的几个方法，他们都传入了一个参数，这个参数其实就是过滤器，用来对目录下的文件进行进一步的筛选。他们两个都是函数式接口，只有一个方法。该方法返回true表示遍历中的当前的目录或者文件可以作为结果返回到结果集中。
```

```
public
interface
FileFiter
{

boolean
accept
(File pathName)
;
}


public
interface
FilenameFiter
{

boolean
accept
(File dir,String name)
;
}
```

```
 针对上述介绍，演示一个实例，使用的还是我的f盘下的360文件夹。
```

```
public
static
void
main
(String[] args)
throws
 IOException
{

        File f = 
new
 File(
"f:/360"
);

        File[] s = f.listFiles(
new
 FileFilter() {


@Override
public
boolean
accept
(File pathname)
{

return
 pathname.isDirectory() ? 
true
 : 
false
;
            }
        });



for
 (File name : s){
            System.out.println(name.getName());
        }
    }
```

```
 上述代码过滤筛选出，360文件夹中所有目录的文件，输出他们的名字。
```



