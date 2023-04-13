# day36
## t435[无重叠区间](https://leetcode.cn/problems/non-overlapping-intervals/)
### 初始思路
  - 重写arrays.sort根据每个子区间的start大小进行排序，如果子区间start相同，就比较end，end越大越放后面
### 学习收获（[学习资源](https://programmercarl.com/0435.%E6%97%A0%E9%87%8D%E5%8F%A0%E5%8C%BA%E9%97%B4.html#%E6%80%9D%E8%B7%AF)）
  - 这里按照右边界排序，从左向右记录非交叉区间个数，区间总数-非交叉区间个数，得到的是需要移除的区间个数
  - 当确定两个区间重合后，再来一个可能重叠的区间，用这两个区间右边界的最小值去做比较；因为该最小值前面都是重合度部分，如果新来的区间也重叠到了这部分，那么这三个区间都重叠
