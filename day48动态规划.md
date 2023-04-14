# day48
## t198[打家劫舍](https://leetcode.cn/problems/house-robber/)
### 初始思路
  - 为啥开头是 “专业的小偷”笑cry
  - 感觉计算奇数位还是偶数位的总和更大
### 学习收获[学习资源](https://programmercarl.com/0198.%E6%89%93%E5%AE%B6%E5%8A%AB%E8%88%8D.html)
  - 初始思路思考简单了
  - 这里还是要进行递推
  - 1.dp[i]表示  偷盗下标i（包括i）以内的房屋，最多的金额dp[i]
  - 2.递推公式：**dp[i] = dp[i - 2] + nums[i]**
  - 3.初始化 dp[1] = max(nums[0], nums[1])
  - 4.遍历顺序 从前向后
