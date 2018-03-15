### 1、HashMap源码的解释：

> This map usually acts as a binned (bucketed) hash table, but when bins get too large, they are transformed into bins of TreeNodes,

hashMap本质是一个hash桶，但当桶太过于大的时候就会转换成树TreeMap(TreeMap)

- ##### 1.1.初始化相关容量

```java
// 初始化容量，一定要是2的幂才可以
static final int DEFAULT_INITIAL_CAPACITY = 1 << 4; // aka 16
// 最大的容量 ，容量一定要是2的幂才可以
static final int MAXIMUM_CAPACITY = 1 << 30;
// 装在因子
static final float DEFAULT_LOAD_FACTOR = 0.75f;
// 桶中的节点数量超过8 则使用转换成树来存储
static final int TREEIFY_THRESHOLD = 8;
// 当进行resize()操作时，桶中节点小于这个值，则树转换为链表
static final int UNTREEIFY_THRESHOLD = 6;
```

