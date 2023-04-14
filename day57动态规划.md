# day57
## t647[回文子串](https://leetcode.cn/problems/palindromic-substrings/)
### 初始思路
  - 可以暴力求解
### 学习收获[学习资源](https://programmercarl.com/0647.%E5%9B%9E%E6%96%87%E5%AD%90%E4%B8%B2.html#%E6%9A%B4%E5%8A%9B%E8%A7%A3%E6%B3%95)
  - dp数组含义 要注意回文串含义 区间范围[i,j] （左闭右闭）的子串是否是回文子串，如果是为true，否则为false
  - 递推公式
    - 情况一：i 与 j相同，如a
    - 情况二：i 与 j相差为1，如aa
    - 情况三：i 与 j相差大于1的时候，如cabac，s[i]与s[j]已经相同了，看i到j区间是不是回文子串就看aba是不是回文就可以了，那么aba的区间就是 i+1 与 j-1区间，这个区间是不是回文就看dp[i + 1][j - 1]是否为true。
  - 初始化 dp[i][j]=false
  - 遍历顺序 一定要从下到上，从左到右遍历，这样保证dp[i + 1][j - 1]都是经过计算的
