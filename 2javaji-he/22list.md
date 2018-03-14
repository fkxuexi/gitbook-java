### 1.List 的体系结构
- list
 
 - ArrayList
 
 - LinkedList
 
 - Vector
 
### 2.几者之间的比较

 对象|本质|特点
 ---|---|--- 
 ArrayList|数据实现的|查询速度快，但增删效率低，非线程安全的
 LinkedList|链表实现的|查询速断慢，但增删效率高，非线程安全
 Vector|数组实现的|查询快，增删效率低，线程安全
 
 
 ### 3.需要去关注的点：
 
 - ArrayList 初始化容量以及扩容
   
   初始化容量：```  private static final int DEFAULT_CAPACITY = 10;```
 
 - ArrayList 遍历
 