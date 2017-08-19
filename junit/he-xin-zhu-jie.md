| @Before | 初始化方法 |
| :--- | :--- |
| @After | 释放资源 |
| @Test | 测试方法，在这里可以测试期望异常和超时时间 |
| @Ignore | 忽略的测试方法 |
| @BeforeClass | 针对所有测试，只执行一次，且必须为static void |
| @AfterClass | 针对所有测试，只执行一次，且必须为static void |
| @RunWith | 指定测试类使用某个运行器 |
| @Parameters | 指定测试类的测试数据集合 |
| @Rule | 允许灵活添加或重新定义测试类中的每个测试方法的行为 |
| @FixMethodOrder | 指定测试方法的执行顺序 |

#### 执行顺序

一个测试类单元测试的执行顺序为：

@BeforeClass –&gt; @Before –&gt; @Test –&gt; @After –&gt; @AfterClass

每一个测试方法的调用顺序为：

@Before –&gt; @Test –&gt; @After



