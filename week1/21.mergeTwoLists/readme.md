# 21. 合并两个有序列表
![lc地址](https://leetcode-cn.com/problems/merge-two-sorted-lists/)

这题暴力方法可以从l1取得一个，遍历l2来确定位置，也可以通过递归的思路。因为两个数列都是已经排好顺序的，可以让后面的先排好顺序，然后再以此一个个叠上去。
由此题目，同理可得类似的链表相关（24.两两交换链表节点）
* 于8.7进行了第一遍。
```python3
class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        # 如果有其中任意一个已经空了，则说明完成。
        if not l1: return l2
        if not l2: return l1
        if l1.val <= l2.val:
            l1.next = self.mergeTwoLists(l1.next, l2)
            return l1 # 头部linkedlist会从l1开始，接到l2的后半段
        else:
            l2.next = self.mergeTwoLists(l1, l2.next)
            return l2 # 同理
```