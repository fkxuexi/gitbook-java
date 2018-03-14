### 1.需要关注的点

有些代码还是比较简单的，但是我们需要关注里面比较核心的点

- 1.ArrayList 初始化的几种方式
  
  ```java
  public ArrayList(int initialCapacity) {}
  // 这种方式貌似是我们没有指定 容量，其实在添加第一个元素的时候，便初始化了容量了
  public ArrayList() {}
  // 用一个集合来初始化
  public ArrayList(Collection<? extends E> c) {}
  ```   

- 2.ArrayList 扩容的以及复制方式
  
```java
// 初始化容量
 private static final int DEFAULT_CAPACITY = 10;
 
 
```



- ArrayList 遍历