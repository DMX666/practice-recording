# day60
## 84[柱状图中最大的矩形](https://leetcode.cn/problems/largest-rectangle-in-histogram/)
### 初始思路
### 学习收获[学习资源](https://programmercarl.com/0084.%E6%9F%B1%E7%8A%B6%E5%9B%BE%E4%B8%AD%E6%9C%80%E5%A4%A7%E7%9A%84%E7%9F%A9%E5%BD%A2.html#%E6%9A%B4%E5%8A%9B%E8%A7%A3%E6%B3%95)
  - 这道题与接雨水很相似，但是难度更大；接雨水是找每个柱子左右两边第一个大于该柱子高度的柱子，这道题是找每个柱子左右两边第一个小于该柱子的柱子；那么这道题从栈头到栈底，应该是从大到小
  - 加元素0的原因：当栈里没有元素的时候，为了避免空栈取值，直接跳过计算结果的逻辑
