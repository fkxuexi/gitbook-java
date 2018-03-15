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
// 当桶中节点转换成树是，table最小的容量
static final int MIN_TREEIFY_CAPACITY = 64;
// 阈值，当（capacity * load factor）大于这个阈值时进行扩容
int threshold;
```

- ##### 1.2 几个核心的函数：

- putVal

```java
final V putVal(int hash, K key, V value, boolean onlyIfAbsent,boolean evict) {
              
    Node<K,V>[] tab; Node<K,V> p; int n, i;
    // 如果table未初始化，则进行扩容
    if ((tab = table) == null || (n = tab.length) == 0)
        // 扩容
        n = (tab = resize()).length;
        // (n-1) & hash 是确定放在哪一个桶中，数组下标从0开始，所以这里是n-1，此时桶为空，则新建节点
    if ((p = tab[i = (n - 1) & hash]) == null)

        tab[i] = newNode(hash, key, value, null);
    else {
        Node<K,V> e; K k;
        if (p.hash == hash &&
            ((k = p.key) == key || (key != null && key.equals(k))))
            e = p;
        else if (p instanceof TreeNode)
            e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
        else {
            for (int binCount = 0; ; ++binCount) {
                if ((e = p.next) == null) {
                    p.next = newNode(hash, key, value, null);
                    if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                        treeifyBin(tab, hash);
                    break;
                }
                if (e.hash == hash &&
                    ((k = e.key) == key || (key != null && key.equals(k))))
                    break;
                p = e;
            }
        }
        if (e != null) { // existing mapping for key
            V oldValue = e.value;
            if (!onlyIfAbsent || oldValue == null)
                e.value = value;
            afterNodeAccess(e);
            return oldValue;
        }
    }
    ++modCount;
    if (++size > threshold)
        resize();
    afterNodeInsertion(evict);
    return null;
}
```
