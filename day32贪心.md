# day32
## t122[买卖股票的最佳时机2](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-ii/)
### 初始思路
  - 好像做过，还是没思路
### 学习收获[学习资源](https://programmercarl.com/0122.%E4%B9%B0%E5%8D%96%E8%82%A1%E7%A5%A8%E7%9A%84%E6%9C%80%E4%BD%B3%E6%97%B6%E6%9C%BAII.html#%E6%80%9D%E8%B7%AF)
  - 这道题要点：只能持有一只股票，当前只有买股票或卖股票操作。--》想要获利必须至少两天为一个交易单元
  - 如果第一天买第三天卖，那么利润为price[3]-price[0],看起来很复杂，但是可以拆解为(prices[3] - prices[2]) + (prices[2] - prices[1]) + (prices[1] - prices[0])
  - 也就是要去拆解利润
  - 那么每天的利润就得到了，只选择利润为正的地方，就可以得到最大利润了
  - 利润序列 会比 天数 少一天，因为第一天是没有利润的
  - 小技巧 使用 Math.max(price[i]-price[i-1], 0),无痛筛选
