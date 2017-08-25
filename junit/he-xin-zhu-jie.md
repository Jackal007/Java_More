| 注解 | 解释 |
| :--- | :--- |
| @Before | 一个类中的每个@Test执行前都会执行一遍，常用于所有测试都会做的事情 |
| @After | 一个类中的所有@Test执行后都会执行一遍 |
| @Test | 一个@Test方法就是一个测试，函数名最好是testXXX               @Test\(timeout=xx\)可以设置超时时间 |
| @Ignore | 忽略该测试 |
| @BeforeClass | 在所有有测试前执行一次，且必须为static void，常用于初始化资源 |
| @AfterClass | 在所有有测试前执行一次，且必须为static void，常用于回收资源 |
| @RunWith | 指定测试类使用某个运行器，参数化测试，有几对参数，下面的每个测试就会跑几遍 |
| @Parameters | 指定测试类的测试数据集合 |
| @Rule | 允许灵活添加或重新定义测试类中的每个测试方法的行为 |
| @FixMethodOrder | 指定测试方法的执行顺序 |



```java
@RunWith(Parameterized.class)
public class PrimeNumberCheckerTest {
   private Integer inputNumber;
   private Boolean expectedResult;
   private PrimeNumberChecker primeNumberChecker;

   @Before
   public void initialize() {
      primeNumberChecker = new PrimeNumberChecker();
   }

   // Each parameter should be placed as an argument here
   // Every time runner triggers, it will pass the arguments
   // from parameters we defined in primeNumbers() method
   public PrimeNumberCheckerTest(Integer inputNumber, 
      Boolean expectedResult) {
      this.inputNumber = inputNumber;
      this.expectedResult = expectedResult;
   }

   @Parameterized.Parameters
   public static Collection primeNumbers() {
      return Arrays.asList(new Object[][] {
         { 2, true },
         { 6, false },
         { 19, true },
         { 22, false },
         { 23, true }
      });
   }

   // This test will run 4 times since we have 5 parameters defined
   @Test
   public void testPrimeNumberChecker() {
      System.out.println("Parameterized Number is : " + inputNumber);
      assertEquals(expectedResult, 
      primeNumberChecker.validate(inputNumber));
   }
}
```

#### 执行顺序

一个测试类单元测试的执行顺序为：

@BeforeClass –&gt; @Before –&gt; @Test –&gt; @After –&gt; @AfterClass

每一个测试方法的调用顺序为：

@Before –&gt; @Test –&gt; @After

