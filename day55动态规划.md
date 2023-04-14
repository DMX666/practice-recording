# day55
## t392[判断子序列](https://leetcode.cn/problems/is-subsequence/)
### 初始思路
  - 或许可以双指针？
### 学习收获[学习资源](https://programmercarl.com/0392.%E5%88%A4%E6%96%AD%E5%AD%90%E5%BA%8F%E5%88%97.html#%E6%80%9D%E8%B7%AF)
  - 编辑距离的入门题目
  - 1.dp数组含义  以下标i-1为结尾的字符串s，和以下标j-1为结尾的字符串t，相同子序列的长度为dp[i][j]；这个完全想不到
  - 2.递推公式的两种情况 s[i - 1] == t[j - 1]   s[i - 1] != t[j - 1]
  - 3.初始化  
  - 4.遍历顺序 从上到下，从左到右
