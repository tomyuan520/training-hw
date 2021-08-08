# 283. 移动零

![lc link] (https://leetcode-cn.com/problems/move-zeroes/)

这题目的暴力解法比较容易想到，移除数组里遇见的0之后记录下次数，然后向数组的最后塞0，但是比较慢。
双指针的方式比较快，不过我后来选择的是二次遍历，移动非0元素，最后遍历剩下的位置赋值为0。不过在写的过程中因为fast和slow指针的变化顺序错误有可能会导致无限while而OT。
暂时还没想到无限while的原因，看起来前后的变化顺序应该不会影响到实际指针数字的变化（？

```python3
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        # count = 0
        # while 0 in nums:
        #    nums.remove(0)
        #    count += 1
        # for i in range(count):
        #    nums.append(0)

        slow = fast = 0
        while fast < len(nums):
            if nums[fast] != 0:
                nums[slow] = nums[fast]
                # 先移动slow然后fast，否则会出现无限循环
                # 当遇到一个nums[fast]=0时，因为无法满足if，fast会一直不动无法更新。
                slow += 1
            fast += 1
        
        # 保留完成后变更应有的0值
        for i in range(slow, len(nums)):
            nums[i] = 0
```