# day50
## t123[买卖股票的最佳时机III](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-iii/description/)
### 学习收获[学习资源](https://programmercarl.com/0123.%E4%B9%B0%E5%8D%96%E8%82%A1%E7%A5%A8%E7%9A%84%E6%9C%80%E4%BD%B3%E6%97%B6%E6%9C%BAIII.html#%E6%80%9D%E8%B7%AF)
  - dp[i][1]，表示的是第i天，买入股票的状态，**并不是第i天一定要买入股票**
  - 2. 递推公式 dp[i][1]有两个操作 dp[i][1] = max(dp[i-1][0] - prices[i], dp[i - 1][1])；dp[i][2]也是由两个影响 dp[i][2] = max(dp[i - 1][1] + prices[i], dp[i - 1][2])
  - 3.初始化 dp[0][0] = 0 dp[0][1] = -prices[0]  dp[0][2] = 0 dp[0][3] = -prices[0] dp[0][4] = 0
  - 4.遍历顺序：从前向后
