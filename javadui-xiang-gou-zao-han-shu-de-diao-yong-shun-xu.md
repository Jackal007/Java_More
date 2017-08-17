> * 使用super调用父类构造器的语句必须是子类构造器的第一条语句
> * 如果子类构造器没有显式地调用父类的构造器，则将自动调用父类的默认（没有参数）的构造器
> * 如果父类没有不带参数的构造器，并且在子类的构造器中又没有显式地调用父类的构造器，则Java编译器将报告错误

总结继承关系中，当new一个对象时，调用顺序如下（此时不讨论静态代码块static修饰的代码块）：

1. 首先初始化父类的成员变量，如果后面跟有代码块那么执行该块

2. 调用父类的无参构造函数

3. 初始化子类的成员变量，如果后面跟有代码块那么执行该块

4. 调用子类的构造函数



### 例子：

```java
class A {
	public A() {
		System.out.println("A");
		t();
	}

	public void t() {
		System.out.println("At");
	}
}

class B extends A {
	public B() {
		System.out.println("B");
	}

	public void t() {
		System.out.println("Bt");
	}
}

B b=new B();
```

结果：

```java
A
Bt
B
```

子类重写的方法会覆盖掉父类的方法



但是如果方法加了private（这时子类写一个名字一样的方法相当于一个新的方法，不是重写）：

```java
class A {
	public A() {
		System.out.println("A");
		t();
	}

	private void t() {
		System.out.println("At");
	}
}

class B extends A {
	public B() {
		System.out.println("B");
	}

	public void t() {
		System.out.println("Bt");
	}
}
```

结果

```java
A
At
B
```



