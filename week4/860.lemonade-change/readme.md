# 860. 柠檬水找零
[lc link] (https://leetcode-cn.com/problems/lemonade-change/)

* 相当经典的找零问题。这题的贪心倒是容易想到。不过一开始去想着遍历所有可能情况了。
* 后来发现可以直接维护一个与5块钱之间的差距，每次用掉了找零就减掉相对应的纸币的数量。

```python3
# 1. 罗列所有可能出现的情况，然后针对性找零，那样代码量太大且不好维
# 当然核心思想依然是贪心，想办法用最大的钱找零
# 2. 统一维护一个找零量总和，然后依然是贪心，不过这下可以统一维护比饺简洁。

class Solution:
    def lemonadeChange(self, bills: List[int]) -> bool:
        change = defaultdict(int)
        for i in bills:
            change[i] += 1
            diff = i - 5
            while diff:
                if diff >= 10 and change[10]:
                    change[10] -= 1
                    diff -= 10
                elif diff >= 5 and change[5]:
                    change[5] -= 1
                    diff -= 5
                else: return False
        # 小心写错缩进导致意义的变化（
        return True
```
