# 24.两两交换链表中的节点

![lc link](https://leetcode-cn.com/problems/swap-nodes-in-pairs/)

这题一样是个有关linkedList的题目，和先前做过的21题一样。
暴力方法就是用个计数器（因为无从得知list的长度）每隔两个换一下，迭代的方式和这个有些许类似。
我所学到/使用的也是机遇递归的方法，在交换前创建原有的节点备份，然后递归到最后两个node，先交换最后两个再往前建立link，最后再由缓存的node建立link来创建一整个linkedList。
有关创建的中间缓存，上述为个人理解，不知道是否有锅（

* 于8.7日做了第一遍。

```python3
class Solution:
    def swapPairs(self, head: ListNode) -> ListNode:
        if not head or not head.next:
            return head
        
        # 注意：这里需要一个缓存，防止被修改后找不到原来的节点
        # 因为此时的完结条件下 原来的head.next会变成空
        n = head.next
        head.next = self.swapPairs(head.next.next) 
        # 而这里是针对原来实际的head.next，故这里不能使用缓存的head.next

        n.next = head # 最后再通过缓存保证linked，此时list会从缓存开始往后走
        return n
```