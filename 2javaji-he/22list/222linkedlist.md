### 1.LinkList

主要是使用的链表实现的。而是使用的是双向链表


### 2.精彩的代码部分：

```java
// 以前的确没有想到链表可以这样进行遍历，我记得以前c都是使用的while来进行遍历的
for (Node<E> x = first; x != null; x = x.next) {
  if (x.item == null)
      return index;
  index++;
}
```