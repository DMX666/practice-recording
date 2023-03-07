# day20
## t654[最大二叉树](https://leetcode.cn/problems/maximum-binary-tree/)
### 初始思路
  - 这道题和前序中序构建二叉树很相似，感觉可以做出来
  - 首先通过最大值确定中间节点，空列表的返回null
  - 然后左边递归为左子树，右边为右子树
