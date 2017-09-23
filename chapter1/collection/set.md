Set的核心概念就是集合内所有元素不重复。在Set这个子接口中没有在Collection特别实现什么额外的方法，应该只是定义了一个Set概念。

Set的实现类都是基于Map来实现的\(如，HashSet是通过HashMap实现的，TreeSet是通过TreeMap实现的\)。

| Set实现 | 使用场景 | 数据结构 |
| :--- | :--- | :--- |
| HashSet | 无序的、无重复的数据集合 | 基于HashMap |
| LinkedSet | 维护次序的HashSet | 基于LinkedHashMap |
| TreeSet | 保持元素大小次序的集合，元素需要实现Comparable接口 | 基于TreeMap |

| **常用方法** |
| :--- |


| Method |  Description |
| :--- | :--- |
| **add\(\)** | **add\( \)**Adds an object to the collection. |
| **clear\(\)** | **clear\( \)**Removes all objects from the collection. |
| **contain\(\)** | **contains\( \)**Returns true if a specified object is an element within the collection. |
| **isEmpty\(\)** | **isEmpty\( \)**Returns true if the collection has no elements. |
| **iterator\(\)** | **iterator\( \)**Returns an Iterator object for the collection, which may be used to retrieve an object. |
| **remove\(\)** | **remove\( \)**Removes a specified object from the collection. |
| **size\(\)** | **size\( \)**Returns the number of elements in the collection. |



