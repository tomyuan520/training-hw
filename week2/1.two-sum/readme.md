# 1. 两数之和

[lc地址](https://leetcode-cn.com/problems/two-sum/)

这题很好理解，暴力想法也很简单，但是timeout有无可能要看运气。还是用hashmap或者类似的map解决会更快。
也知道了 python3 dict的底层就是hashmap类似的实现。

* 于8.4日第一次，使用求差再索引成dict的方法。
* 于8.10日做了第三次，dict的索引第一遍塞错了！！！
* 要注意是为了找到 list里存在的 target-a，所以将当前的a作为索引值。
* 8.15第四次，也是塞错了索引，debug后发现了问题。
```python3
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        ht = dict()
        for i in range(len(nums)):
            # 找到数列里的值 = target - nums[i]
            # 所以将nums[i]作为字典索引
            if target - nums[i] not in ht:
                ht[nums[i]] = i
            else:
                return [ht[target - nums[i]], i]
        return []
```
