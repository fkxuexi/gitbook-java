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
// 最大的容量为21亿左右即为int的取值返回的正数的部分
public static final int   MAX_VALUE = 0x7fffffff;
 
public boolean add(E e) {
    ensureCapacityInternal(size + 1);  
    elementData[size++] = e;
    return true;
} 
 
private void ensureCapacityInternal(int minCapacity) {
  // 如果是空数组的话，则采用默认的容量 
  if (elementData == DEFAULTCAPACITY_EMPTY_ELEMENTDATA) {
     minCapacity = Math.max(DEFAULT_CAPACITY, minCapacity);
  }
  // 否则则进行扩容
    ensureExplicitCapacity(minCapacity);
}
 
private void ensureExplicitCapacity(int minCapacity) {
  // 这个变量表示修改list被修改的次数，用于遍历中，会引发 ConcurrentModificationException异常的出现
  modCount++;
  /**
   * size 是list实际含有的元素的个数，而不是数据的容量
   * 这个判断是，如果size 大于数组的容量则进行扩容，否则则不用管
  **/
  if (minCapacity - elementData.length > 0){
      grow(minCapacity);
  }
} 

// 核心的扩容代码：
private void grow(int minCapacity) {
    // oldCapacity  则代表 的是数据的容量
    int oldCapacity = elementData.length;
    int newCapacity = oldCapacity + (oldCapacity >> 1);
    if (newCapacity - minCapacity < 0)
        newCapacity = minCapacity;
    if (newCapacity - MAX_ARRAY_SIZE > 0)
        newCapacity = hugeCapacity(minCapacity);
    // minCapacity is usually close to size, so this is a win:
    elementData = Arrays.copyOf(elementData, newCapacity);
}

```



- ArrayList 遍历