# day42
## 01背包（基础）
  - 二维dp
    - 01背包：n种物品，每种物品只有一个
    - 完全背包： n种物品，每种物品不限
    - 多维背包：n种物品，每种物品个数不同
    - 暴力解法，每个物品只有两种状态取和不取，用回溯暴力搜索
    - dp[i][j] 下标为0-i之前的物品任取放进容量为j的背包 的最大价值
    - 不放物品i dp[i-1][j],放物品i dp[i-1][j-weight[j]]+value[i]; dp[i][j] = max(dp[i-1][j], dp[i-1][j-weight[j]]+value[i])
    - 一层遍历物品，一层遍历背包。对于二维实现01背包两层循环可以颠倒的，因为当前表格由左上方和正上方决定
  - 一维dp
    - 用一维dp数组解决01背包，说明状态可以压缩，滚动数组，当前层由上一层决定，那么将上一层数据拷贝到当前层
    - dp[i] = max (dp[j], dp[j-weight[j]]+valie[i])
    - 这里面的遍历顺序很有考究，倒序遍历为了确定每个物品只被添加过一次，
## 完全背包



## t416[分割等和子集](https://leetcode.cn/problems/partition-equal-subset-sum/)
### 初始思路
  - 没懂为什么是背包
### 学习收获
  - 先将集合元素相加所得到的值除以2就是一个集合的和，每个元素只能用一次，就是0 1背包
  - dp[j] 重量和价值相同
