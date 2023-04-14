# day52
## t300[最长递增子序列](https://leetcode.cn/problems/longest-increasing-subsequence/)
### 学习收获[学习资料](https://programmercarl.com/0674.%E6%9C%80%E9%95%BF%E8%BF%9E%E7%BB%AD%E9%80%92%E5%A2%9E%E5%BA%8F%E5%88%97.html#%E6%80%9D%E8%B7%AF)
  - 1.dp数组的含义 以下标i为结尾的连续递增的子序列长度为dp[i]
  - 2.递推公式 dp[i] = dp[i - 1] + 1
  - 3.dp[i] =1
  - 4.遍历顺序，从前向后
  - 改题目并不复杂，套用这几个步骤，基本可以得出
