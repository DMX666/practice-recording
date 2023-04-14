# day53
## t1143[最长公共子序列](https://leetcode.cn/problems/longest-common-subsequence/)
### 学习收获[学习资源](https://programmercarl.com/1143.%E6%9C%80%E9%95%BF%E5%85%AC%E5%85%B1%E5%AD%90%E5%BA%8F%E5%88%97.html#%E6%80%9D%E8%B7%AF)
  - 1.dp数组含义  长度为[0, i - 1]的字符串text1与长度为[0, j - 1]的字符串text2的最长公共子序列为dp[i][j]；定义长度为[0, i - 1]的字符串text1为了代码实现的方便
  - 2.递推公式  两大情况： text1[i - 1] 与 text2[j - 1]相同，text1[i - 1] 与 text2[j - 1]不相同
  - 3.初始化 dp[i][0] = 0
  - 4. 遍历顺序 从前向后
