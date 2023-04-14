# day45
## t322[零钱兑换](https://leetcode.cn/problems/coin-change/)
### 初始思路
  - 这道题与之前的题目很相似，只是返回的不是组合的个数，而是硬币最少的个数，那么每次取Min就可以了
### 学习收获（[学习资源](https://programmercarl.com/0322.%E9%9B%B6%E9%92%B1%E5%85%91%E6%8D%A2.html)）
  - 1.dp数组的含义： dp[i]凑足总额为i所需钱币的最小个数
  - 2.确定递推公式，凑到面额为i-coins[j]的最小个数为dp[i-coins[j]],那么再加上coins[j]这一种方案，就是凑到dp[i]的方案。**dp[i] = min(dp[i-coins[j]]+1, dp[i])**
    - 这里容易想不清楚为什么要加一，因为这里表示的是数量，不是种类
  - 3.dp数组初始化：dp[0] = 0
  - 4.历顺序，本题目不强掉组合还是排序，for循环的顺序都可以
