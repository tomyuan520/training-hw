# 122. 买卖股票的最佳时机ii

[lc link] (https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii/)

* "Is this problem a joke?"
* 最简单，但是不是很好理解的算法就是贪心，每一步都取得当前的最优解，在此题目下因为可以进行无数此交易所以可以每次见到后一天的大于前一天就开始卖出。只是这个想法的正确性需要一些额外的证明。
* 因为是一套题目，所以最通用的解法是dp。代码不好写但是相对我各人而言容易理解。

* 8.29第一遍，两种方式都可以相对借鉴。

```python3
# 1. "this problem is a joke" 进行一个类似(事实证明就是贪心)贪心的处理，当后一天的价格高于前一天的价格，则直接进行一个卖出。（但这种方式为什么依然能保证总利润最大还需要进一步推敲，结果上是没有问题。)
# 2. 进行一个dp的记录。 
# 每一天的行为其实分析简化变成一个抉择：我到底是卖还是不卖，进而得到两个状态，手里有无股票。
# 到最后一天时，手中没有股票所拥有的钱必然大于手中依然持有股票所拥有的钱。故直接输出。
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        '''res = 0
        for i in range(len(prices) - 1):
            if prices[i+1] > prices[i]:
                res += prices[i+1] - prices[i]
        return res'''
        if len(prices) < 2:
            return 0
        
        dp_no = 0
        dp_yes = -prices[0] # 第一天买了股票，此时手中的钱等于买了股票所消耗的钱。

        for i in range(1, len(prices)):
            # dp_no: 手中没有股票，则更新时需要清空股票库存。
            # 用最后一次有股票的价格起步，卖掉所有的股票来算最终。
            dp_no = max(dp_no, dp_yes + prices[i])
            # dp_yes: 手中有股票，则更新时需要全部买入。更新方式和没股票时候相反。
            dp_yes = max(dp_yes, dp_no - prices[i])
        return dp_no

```
