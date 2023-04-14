# day49
## t121[买卖股票的最佳时机](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock/)
### 初始思路
### 学习收获[学习资源](https://programmercarl.com/0121.%E4%B9%B0%E5%8D%96%E8%82%A1%E7%A5%A8%E7%9A%84%E6%9C%80%E4%BD%B3%E6%97%B6%E6%9C%BA.html#%E6%80%9D%E8%B7%AF)
  - 1.dp[i][j]：dp[i][0] 第i天持有股票所得最多现金,注意区分 **持有和买入**
  - 2.递推公式 dp[i][0] = max(dp[i - 1][0], -prices[i])
  - 3.初始化 dp[0][1] = 0
  - 4. 遍历顺序 从前向后
