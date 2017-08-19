随着开发规模的深入和扩大，项目或越来越大，相应的我们的测试类也会越来越多；那么就带来一个问题，假如测试类很多，就需要多次运行，造成测试的成本增加；此时就可以使用junit批量运行测试类的功能，junit test suite，测试套件；每次运行测试类，只需要执行一次测试套件类就可以运行所有的测试类；

```java
@RunWith(Suite.class)
@Suite.SuiteClasses({TaskTest1.class, TaskTest2.class, TaskTest3.class})
public class SuiteTest {


}
```

写一个作为测试套件的入口类，这个类中不能包含任何方法

