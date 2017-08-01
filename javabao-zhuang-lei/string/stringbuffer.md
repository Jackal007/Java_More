## StringBuffer 方法

以下是 StringBuffer 类支持的主要方法：

| 方法 | 描述 |
| :--- | :--- |
| public StringBuffer append\(String s\)  | 将指定的字符串追加到此字符序列。 |
| public StringBuffer reverse\(\)   | 将此字符序列用其反转形式取代。 |
| public delete\(int start, int end\)  | 移除此序列的子字符串中的字符。 |
| public insert\(int offset, int i\) |  将`int`参数的字符串表示形式插入此序列中。 |
| replace\(int start, int end, String str\)  | 使用给定`String`中的字符替换此序列的子字符串中的字符。 |

| int capacity\(\) | 返回当前容量。 |
| :--- | :--- |
| char charAt\(int index\) | 返回此序列中指定索引处的`char`值。 |
| void ensureCapacity\(int minimumCapacity\) | 确保容量至少等于指定的最小值。 |
| void getChars\(int begin, int end, char\[\] dst, int dstBegin\) | 将字符从此序列复制到目标字符数组`dst`。 |
| int indexOf\(String str\) | 返回第一次出现的指定子字符串在该字符串中的索引。 |
| int indexOf\(String str, int fromIndex\) | 从指定的索引处开始，返回第一次出现的指定子字符串在该字符串中的索引。 |
| int lastIndexOf\(String str\) | 返回最右边出现的指定子字符串在此字符串中的索引。 |
| int lastIndexOf\(String str, int fromIndex\) | 返回最后一次出现的指定子字符串在此字符串中的索引。 |
| int length\(\) |  返回长度（字符数）。 |
| void setCharAt\(int index, char ch\) | 将给定索引处的字符设置为`ch` |
| void setLength\(int newLength\) | 设置字符序列的长度。 |
| CharSequence subSequence\(int start, int end\) | 返回一个新的字符序列，该字符序列是此序列的子序列。 |
| String substring\(int start\) | 返回一个新的`String`，它包含此字符序列当前所包含的字符子序列。 |
| String substring\(int start, int end\) | 返回一个新的`String`，它包含此序列当前所包含的字符子序列。 |
| String toString\(\) | 返回此序列中数据的字符串表示形式。 |



