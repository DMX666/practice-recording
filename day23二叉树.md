# day23
## t669[修剪二叉搜索树](https://leetcode.cn/problems/trim-a-binary-search-tree/)
### 初始思路
  - 没啥思路，感觉变化很多，要重新建一个二叉树
### 学习收获（[学习资源](https://programmercarl.com/0669.%E4%BF%AE%E5%89%AA%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91.html#%E9%80%92%E5%BD%92%E6%B3%95)）
  - 这道题看起来很复杂，其实并不需要重构唯一需要注意的是如果一个节点不在范围内，不能简单的删除返回null，因为该节点的左右子节点可能会满足区间
  - 所以如果root.val < low，那么就递归root.right，root.val > high就递归root.left
  - 上述操作处理完毕，就递归root.left root.right
## t108[将有序数组转换为二叉搜索树]()
### 学习收获[学习资源]()
  - 数组中间的作为中间节点，这样才能保证平衡
  - 复用数组，减少空间浪费
  - 传入left right 求取mid，注意区间开闭一致
## t538[把二叉搜索树转换为累加树](https://leetcode.cn/problems/convert-bst-to-greater-tree/description/)
### 初始思路
  - 看不懂题
### 学习收获[学习资源](https://programmercarl.com/0538.%E6%8A%8A%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E8%BD%AC%E6%8D%A2%E4%B8%BA%E7%B4%AF%E5%8A%A0%E6%A0%91.html#%E9%80%92%E5%BD%92)
  - 首先题目是从大到小逐步累加，形成一个新的树，这个过程在树的结构中看起来十分复杂，但是如果放在一个从小到大的数组中倒序遍历，就看起来十分直白
  - 二叉搜索树是有序的，后序二叉搜索树即可实现这样的效果，右中左遍历，不断增加后替换root.val的值
