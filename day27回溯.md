# day27
## t39[组合总和](https://leetcode.cn/problems/combination-sum/)
### 初始思路
  - 开始对于无限重复不知道怎么入手解决--》突然想到Index是为了去重，那么这里不需要index就可以了
  - 其他基本上和之前的很相似
### 学习收获[学习资源](https://www.bilibili.com/video/BV1KT4y1M7HJ/?spm_id_from=333.788)
  - 重复选取--考虑0，因此题目中给了数的上限，也知道了没有重复元素
  - index依然是需要的否则会出现顺序不同组合相同的情况，横向中需要Index，递归的时候仍然需要把当前的加进来
