# 46.全排列
[lc-link](https://leetcode-cn.com/problems/permutations/)

这题目的逻辑结构的确有点像树，通过不同的枝叶来添加组合。此处bfs和dfs均可。
在国际站上见到了一套相当干净的解释，[原文]（https://leetcode.com/problems/permutations-ii/discuss/189116/summarization-of-permutations-I-and-II-(Python)）
其实最简单的方法是裸递归，但是也因为是裸的所以递归过程中没有剪枝。此题目中回溯方法会带有缓存和记录，所以会快。我认为其中有剪枝操作但是可能需要进一步debug才能确认。

* 于8.23日写了第一遍，这题目估计还要多多思考。

```python3
# 1. 暴力法，其实还不太好想，本身在这里的dfs就有一些尝试所有解决方案的样子。
# 2. dfs，做一个循环格子，每次往里面塞单个数字来尝试排列，然后再来来回回。
# 3. 回溯，交换塞入，然后换回去来开始新的回合。
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        res = []
        n = len(nums)
        def dfs(place):
            if place == n - 1:
                # we reach the final number of nums
                res.append(list(nums))
                return
            for i in range(place, n):
                # start process in range starting place to end
                # we try to swap the nearest two numbers, then add
                nums[place], nums[i] = nums[i], nums[place]
                dfs(place + 1)
                # then swap back for another round.
                nums[place], nums[i] = nums[i], nums[place]
        dfs(0)
        return res
```