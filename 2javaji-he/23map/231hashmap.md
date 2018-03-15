### 1、HashMap源码的解释：

> This map usually acts as a binned (bucketed) hash table, but when bins get too large, they are transformed into bins of TreeNodes,

hashMap本质是一个hash桶，但当桶太过于大的时候就会转换成树TreeMap(TreeMap)

- ##### 1.1.初始化相关容量

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

static final int MIN_TREEIFY_CAPACITY = 64;
```

- ##### 1.2.核心方法解析：

- put

```java
 /**
 * @param hash hash for key
 * @param key the key
 * @param value the value to put
 * @param onlyIfAbsent if true, 则不修改已存在的值
 * @param evict if false, 则创建这个table
 * @return previous value, or null if none
 */
final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
               boolean evict) {
    Node<K,V>[] tab; Node<K,V> p; int n, i;
    if ((tab = table) == null || (n = tab.length) == 0)
        n = (tab = resize()).length;
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

