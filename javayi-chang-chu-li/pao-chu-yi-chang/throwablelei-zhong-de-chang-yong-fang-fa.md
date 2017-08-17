注意：catch关键字后面括号中的Exception类型的参数e。Exception就是try代码块传递给catch代码块的变量类型，e就是变量名。catch代码块中语句"e.getMessage\(\);"用于输出错误性质。通常异常处理常用3个函数来获取异常的有关信息:

     getCause\(\)：返回抛出异常的原因。如果 cause 不存在或未知，则返回 null。

　 getMeage\(\)：返回异常的消息信息。

　 printStackTrace\(\)：对象的堆栈跟踪输出至错误输出流，作为字段 System.err 的值。

     有时为了简单会忽略掉catch语句后的代码，这样try-catch语句就成了一种摆设，一旦程序在运行过程中出现了异常，就会忽略处理异常，而错误发生的原因很难查找。

