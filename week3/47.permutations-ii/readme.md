# 47. 全排列2
[lc link](https://leetcode-cn.com/problems/permutations-ii/)

这题目是在46的基础上加上了list中可能有重复元素的限制。这样的话如果遇到了重复元素，继续下去进行的排列组合就有可能会是完全重复的，需要进一步剪枝。看了几种方法可以考虑使用额外的list来记录元素/数字的使用情况，遇到相同的数字可以直接剪掉那个可能性（因为得到的排列必定会重复）。
在这个方法中，我们用转换为set的方式防止了剩下的数组内部有重复元素的情况，然后再尝试remove以防止剩下的数组和之前当前循环数字重复。
* 8.23第一遍

```python3
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        n = len(nums)
        res = []
        def dfs(nums, l):
            if l == n-1:
                res.append(list(nums))
                return 
            for i in set(nums[l:]):
                remaining = nums[l:]
                remaining.remove(i)
                dfs(nums[:l] + [i] + remaining, l+1)
        dfs(nums, 0)
        return res
```