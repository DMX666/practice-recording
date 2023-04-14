# day51
## t309[最佳买卖股票时机含冷冻期](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-with-cooldown/)
### 学习收获[学习资源](https://programmercarl.com/0309.%E6%9C%80%E4%BD%B3%E4%B9%B0%E5%8D%96%E8%82%A1%E7%A5%A8%E6%97%B6%E6%9C%BA%E5%90%AB%E5%86%B7%E5%86%BB%E6%9C%9F.html#%E6%80%9D%E8%B7%AF)
  - dp[i][j]，第i天状态为j，所剩的最多现金为dp[i][j]
  - 共计有四种状态
    - 状态一：持有股票状态（今天买入股票，或者是之前就买入了股票然后没有操作，一直持有）
    - 不持有股票状态，两种卖出股票状态
      - 状态二：保持卖出股票的状态（两天前就卖出了股票，度过一天冷冻期，或前一天已经是卖出股票状态，一直没操作）
      - 状态三：今天卖出股票
    - 状态四：冷冻期状态，但冷冻期状态只有一天
  - 递推公式 
    ```
    dp[i][0] = max(dp[i - 1][0], max(dp[i - 1][3], dp[i - 1][1]) - prices[i]);
    dp[i][1] = max(dp[i - 1][1], dp[i - 1][3]);
    dp[i][2] = dp[i - 1][0] + prices[i];
    dp[i][3] = dp[i - 1][2];
    ```
  - 初始化 dp[0][0] = -prices[0] = 0；dp[0][2] = 0； dp[0][3] = 0；
  - 遍历顺序，从前向后
