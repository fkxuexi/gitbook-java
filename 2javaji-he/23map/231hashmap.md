### 1、HashMap源码的解释：

> This map usually acts as a binned (bucketed) hash table, but when bins get too large, they are transformed into bins of TreeNodes,

hashMap本质是一个hash桶，但当桶太过于大的时候就会转换成树TreeMap()
