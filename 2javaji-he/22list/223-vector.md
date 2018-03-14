### 1.Vector (线程安全的集合) 需要关注的点：

由于是安全的所以所有的具有事务性的代码都进行了加锁

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

 // 扩容的代码，如果我们不指定扩容的size，则依据默认的size进行扩容 
 private void grow(int minCapacity) {
   int oldCapacity = elementData.length;
   int newCapacity = oldCapacity + ((capacityIncrement > 0) ?
                                          capacityIncrement : oldCapacity);
 } 
```

如上方式我们要学会，为不同的需求提供不同的构造函数




