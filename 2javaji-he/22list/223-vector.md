### 1.Vector (线程安全的集合) 需要关注的点：

- 1.构造函数，初始容量以及扩容

```java
 // 自己决定初始容量和，扩容容量
 public Vector(int initialCapacity, int capacityIncrement) {}
 // 如果不做设置，默认扩容容量为0
 public Vector(int initialCapacity) {
   this(initialCapacity, 0);
 }
 // 默认容量为0 且扩容为0 
 public Vector() {
   this(10);
 }
```



