# day37
## t738[单调递增的数字](https://leetcode.cn/problems/monotone-increasing-digits/)
### 初始思路
  - 感觉很有趣，但是不知道怎么下手
### 学习收获（[学习资源](https://programmercarl.com/0738.%E5%8D%95%E8%B0%83%E9%80%92%E5%A2%9E%E7%9A%84%E6%95%B0%E5%AD%97.html#%E6%9A%B4%E5%8A%9B%E8%A7%A3%E6%B3%95)）
  - 如果出现非单调递增了，就先让高位--，低位为9
  - 从前向后还是从后向前： 看到299--》从后向前（从地位向高位遍历）
  - 这道题的核心是先找简单的两位找规律，先不要急着考虑多位的
  - ```
      integer.parseint("5")是将整型数据Integer转换为基本数据类型int
    ```
