## 链表

参考：
[时间极客-数据结构与算法之美](https://time.geekbang.org/column/intro/100017301)

### 链表的特性
__1. 不支持随机访问__
- 不同与数组，不需要连续的内存空间
- 通过指针将离散的内存「连接」起来
- 因此，低效的查找访问: O(n)

__2. 高效的插入和删除__
- 不考虑查找时间，仅考虑插入和删除的操作时间: O(1)

### 常见的链表结构
__1. 单链表__
- 每个结点通过后继指针`next`指向下一个结点
- 尾结点指向空地址`null`

__2. 循环链表__
- 相比单链表，尾结点指向头节点，尾首相连
- 适合具有环型结构的数据

__3. 双向链表__
- 相比单链表，每个结点同时拥有后继指针`next`和前驱指针`prev`
- 删除指定结点或在指定结点前插入新结点时，相比单链表更有优势
  单链表需要O(n)遍历找到前驱结点，再进行删除操作，而双向链表只需要O(1)时间
- 缺点是会占用更多的内存空间

### 数组与链表比较
- 数组优于随机访问；链表优于插入删除
- 数组使用连续的内存空间，可以利用CPU缓存机制预读数组中的数据，缺点是系统可能没有足够的连续空间；链表并不使用连续内存，因此无法借助CPU缓存预读
- 数组的大小固定，扩容需要拷贝；链表无大小限制，天然支持动态扩容
- 链表使用额外的内存，且频繁的插入删除，会导致频繁的内存申请释放，容易造成内存碎片(频繁的GC)

### 链表的技巧
__1. 哑结点__(dummy node)
对链表进行操作时，特别是循环型操作，首结点常常会需要特殊的操作逻辑，可以借助哑结点简化代码
```java
ListNode dummy = new ListNode();
dummy->next = head;
```

__2. 注意边界条件__(corner case)
- 如果链表为空？
- 如果链表只包含1个或2个(根据具体问题)结点？
- 代码逻辑对于头尾结点是否适用？