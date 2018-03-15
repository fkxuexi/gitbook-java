### 1、HashMap源码的解释：

> This map usually acts as a binned (bucketed) hash table, but when bins get too large, they are transformed into bins of TreeNodes,

hashMap本质是一个hash桶，但当桶太过于大的时候就会转换成树TreeMap(TreeMap)

- 1.1.初始化相关容量

```java
/**
* The default initial capacity - MUST be a power of two.
* 初始容量为16，且容量必须2的倍数
*/
static final int DEFAULT_INITIAL_CAPACITY = 1 << 4; // aka 16
// 最大容量
static final int MAXIMUM_CAPACITY = 1 << 30;
/**
 * The load factor used when none specified in constructor.
 * 加载因子，这是一个非常重要的衡量HashMap在扩容时候的一个指标
*/
static final float DEFAULT_LOAD_FACTOR = 0.75f;
// hash桶中存储的是链表，但当链表的层数达到8，则使用树来代替链表
static final int TREEIFY_THRESHOLD = 8;
// 当进行resize()操作的时候如果树的层数小于6，则使用链表
static final int UNTREEIFY_THRESHOLD = 6;
```
