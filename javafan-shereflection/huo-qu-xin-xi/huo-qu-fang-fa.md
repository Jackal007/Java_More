#### Method getMethod\(String name,Class...parameterTypes\)

参数解释：

```
       name： method的名称

       parameterTypes：method的参数类型的列表（参数顺序需按声明method时的参数列表排列）
```

返回：符合method名称和参数的method对象

抛出错误：

```java
         NoSuchMethodException   //没有找到所要查询的Method对象  或  Method名称为“<init>”或“<clinit>”
```

```java
           NullPointerException    //所要查询的Method对象的名称为null
```

```java
            SecurityException    //原因：调用的类或其父类没有调用权限
```

例：

```java
Method m1 = Employee.class.getMethod("getName");
Method m2 = Employee.class.getMethod("raiseSalary",double.class);
```

上面例子分别获得了Employee类的getName方法和raiseSalary方法的方法指针m1,m2。



#### Method\[\] getMethods\(\)

#### Method getDeclaredMethod\(String name, Class\[\] params\)

#### Method\[\] getDeclaredMethods\(\)  //获取所有的methods对象



