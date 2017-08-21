#### public &lt;U&gt; Class&lt;? extends U&gt; asSubclass\(Class&lt;U&gt; clazz\)

这是Java.lang.Class中的一个方法，作用是将调用这个方法的class对象转换成由clazz参数所表示的class对象的某个子类。举例来说，

List&lt;String&gt; strList = new ArrayList&lt;String&gt;\(\);

Class&lt;? extends List&gt; strList\_cast = strList.getClass\(\).asSubclass\(List.class\);

上面的代码将strList.getClass\(\)获取的class对象转换成Class&lt;? extends List&gt;

#### isAssignableFrom

用来判断一个类Class1和另一个类Class2是否相同或是另一个类的超类或接口



