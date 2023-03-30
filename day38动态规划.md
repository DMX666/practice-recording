# day38
## 动态规划基础理论
  - dynamic programming，DP,如果某一问题有很多重叠子问题，使用动态规划是最有效的
  - 与贪心算法的区别是，贪心算法没有状态推导，动态规划每一个状态依赖于上一个状态推导
### t509[斐波那契数列]()
### 初始思路
  - 第一反应需要递归
### 学习收获[学习资源](https://programmercarl.com/0509.%E6%96%90%E6%B3%A2%E9%82%A3%E5%A5%91%E6%95%B0.html#%E6%80%9D%E8%B7%AF)
  - 1.dp[i]含义，第i个斐波那契数的数值为dp[i]
  - 2.递推公式，dp[i]=dp[i-1]+dp[i-2]。这里直接给出来，因为改题非常简单
  - 3.dp数组初始化，dp[0]=0,dp[1]=1。在实际代码中需要先初始化，再列公式，这里思考的过程中，要通过公式来思考初始化
  - 4.确定遍历顺序，这里每个状态需要前面的，所以从前向后遍历。有时候需要从后向前遍历
  - 5.打印dp数组，方便debug
  - 这里每次仅仅依赖前面两个数值，因此没有必要存储所有的数组，可以通过不断赋值更新来记录
## t70[爬楼梯](https://leetcode.cn/problems/climbing-stairs/)
### 初始思路
  - 没有看到与 斐波那契数的相似之处
### 学习收获[学习资源](https://programmercarl.com/0070.%E7%88%AC%E6%A5%BC%E6%A2%AF.html#%E6%80%9D%E8%B7%AF)
  - 相似之处在于，爬到n层楼的方法是爬到n-1层楼+爬到n-2层楼方法数量的加和
## t746[使用最小花费爬楼梯](https://leetcode.cn/problems/min-cost-climbing-stairs/description/)
### 初始思路
  - 看不懂题目
### 学习收获[学习资源](https://programmercarl.com/0746.%E4%BD%BF%E7%94%A8%E6%9C%80%E5%B0%8F%E8%8A%B1%E8%B4%B9%E7%88%AC%E6%A5%BC%E6%A2%AF.html#%E6%80%9D%E8%B7%AF)
  - 爬到i层楼的花费是dp[i]，dp[i]=dp[i-1]+cost[i-1]=dp[i-2]+cost[i-2]
  - 将两者的大小进行比较，就可以得到最小花费
