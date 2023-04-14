# day56
## t583[两个字符串的删除操作](https://leetcode.cn/problems/delete-operation-for-two-strings/)
### 初始思路
### 学习收获[学习资源](https://programmercarl.com/0583.%E4%B8%A4%E4%B8%AA%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E5%88%A0%E9%99%A4%E6%93%8D%E4%BD%9C.html#%E6%80%9D%E8%B7%AF)
  - 1.dp数组的含义 以i-1为结尾的字符串word1，以j-1位结尾的字符串word2，想要达到相等，所需要删除元素的**最少次数**
  - 2.递推公式 
    - 情况一：删word1[i - 1]，最少操作次数为dp[i - 1][j] + 1
    - 情况二：删word2[j - 1]，最少操作次数为dp[i][j - 1] + 1
    - 情况三：同时删word1[i - 1]和word2[j - 1]，操作的最少次数为dp[i - 1][j - 1] + 2
 - 3.初始化
 - 4.遍历顺序，从上到下，从左到右
