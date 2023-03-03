# day16
## t104[二叉树的最大深度](https://leetcode.cn/problems/maximum-depth-of-binary-tree/solutions/)
### 初始思路
  - 这道题要遍历到树的最深的地方，之前在做树的遍历的时候，似曾相识
### 学习收获（[学习资源](https://www.bilibili.com/video/BV1Gd4y1V75u/?spm_id_from=333.788&vd_source=f0ddb4642249f19ba16b9ccf8ca6e632)）
  - 树的深度和高度是两个概念
  - 树深度：任一节点到根节点的距离；树高度：任意节点到叶子节点的距离
  - 深度从下往上算的，所以应该是后序遍历（左右中）；高度从上往下算用到的是前序遍历（中左右）
  - 这里虽然是求深度，其实用到的是后序遍历，因为二叉树的最大深度等于根节点的高度
  - 代码十分简单，但是很容易不明白为什么这么写
  - 代码用递归写后序遍历，后序遍历
  - 左：int leftHeight = maxDepth(root.left);
  - 右：int rightHeight = maxDepth(root.right);
  - 中：进行操作，int deepth = Math.max(leftHeight,rightHeight)+1;
  - 在递归的时候不断将这个deepth向上传递，没传递一次增加1
  - 对于根节点为Null的情况，那么deepth=0，直接return 0
  - 这个递归仍然是思考，传参treenode，返回值deepth，终止条件：node == null，单层逻辑：左右中
## t111[二叉树的最小深度](https://leetcode.cn/problems/minimum-depth-of-binary-tree/)
### 学习收获（[学习资源](https://www.bilibili.com/video/BV1QD4y1B7e2/?spm_id_from=333.788&vd_source=f0ddb4642249f19ba16b9ccf8ca6e632)）
  - 弄清楚最小深度是什么，根节点到最近叶子节点的最短路径上的节点数量
  - 那么这里求取最小的深度，就是将上一题中的max换成min，上一题求取的是最大深度
  - 这里从下往上遍历，仍然通过后序遍历实现
  - 值得注意的是，这里仅将max换成Min是不行的，因为这样会使得空节点被算进来，那么便不符合要求
  - 于是对于左节点为空，右节点不为空的情况下，直接返回右节点的高度，反之亦然，这样才能够满足题目的要求（到叶子节点）
## t222[完全二叉树的节点个数](https://leetcode.cn/problems/count-complete-tree-nodes/)
### 初始思
  - 在层序遍历的时候有用到队列，这里应该可以用类似的方法进行计算
### 学习收获（[学习资源](https://www.bilibili.com/video/BV1eW4y1B7pD/?spm_id_from=333.788&vd_source=f0ddb4642249f19ba16b9ccf8ca6e632)）
  - 普通二叉树用递归（前中后序，其中后序最为简单）、层序遍历都可以实现节点个数的统计，因为会遍历到每一个节点
  - 左 int left = getNum(node.left) 右 int right = getNum(node.right) 中 num = left+right+1
  - 但是对于完全二叉树来说，可以借用完全二叉树的特点进行一些简化，完全二叉树中，除了最下面一层之外都是满二叉树
  - 满二叉树的节点个数   2^深度-1
  - 利用这一特点可以想到，如果将树拆分，左子树为满二叉树，右子树为满二叉树，那么总的节点数是左+右+1，左右子树的节点数直接用满二叉树的计算方式计算
  - 如果一个节点一直向左遍历到最深==向右遍历到最深，那么可以确定这个子树是满二叉树
  - 这样的方法省去了中间节点的遍历
