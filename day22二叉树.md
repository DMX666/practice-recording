# day22
## t235[二叉搜索树的最近公共祖先](https://leetcode.cn/problems/lowest-common-ancestor-of-a-binary-search-tree/description/)
### 初始思路
  - 要利用搜索二叉树的特性，但是不知道如何利用
### 学习收获([学习资源](https://programmercarl.com/0235.%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E7%9A%84%E6%9C%80%E8%BF%91%E5%85%AC%E5%85%B1%E7%A5%96%E5%85%88.html#%E8%BF%AD%E4%BB%A3%E6%B3%95))
  - 首先二叉搜索树中的数值是有序的，小的在左，大的在右，根据这个特点就可以更快速的判断到底是在左子树还是右子树
  - 如果root.val比p q都大，那么说明p q都在root.left上，如果比p q都小，说明p q都在root.right上
  - 如果p.val<root.val<q.val那么说明中间节点就是最近的公共祖先，可以这么想
    - 如果向左，那么就没有了q，向右，就没有了p，这些再往下都不可能是公共祖先
  - 本题的代码十分简洁
  - ```
    class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root.val >p.val && root.val > q.val){return lowestCommonAncestor(root.left,p,q);}
        if(root.val < p.val && root.val<q.val){return lowestCommonAncestor(root.right,p,q);}
        return root;        
        }
    }
    ```
## t701（[二叉搜索树中的插入操作](https://leetcode.cn/problems/insert-into-a-binary-search-tree/)）
### 初始思路
  - 与当前节点进行比较，如果小就向左子树，如果大就向右子树，那么插入操作怎么合适呢
### 学习收获（[学习资源](https://programmercarl.com/0701.%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E4%B8%AD%E7%9A%84%E6%8F%92%E5%85%A5%E6%93%8D%E4%BD%9C.html#%E9%80%92%E5%BD%92)）
  - 虽然插入同一个节点会有不同种的方式，但是这里并不需要去顾及，还是一样的逻辑
  - 找到空节点，也就是合适的位置，进行插入操作就可以，这里就是创建节点，并返回
  - 还没弄明白，为什么返回节点就可以---明白了：因为上一层要用root.left 或 root.right接住，这样就能够层层接触到
## t450[删除二叉搜索树中的节点](https://leetcode.cn/problems/delete-node-in-a-bst/)
### 初始思路
  - 删除要比添加更为复杂，因为删除要顾及剩下的节点，还满足二叉树
### 学习收获（[学习资源](https://programmercarl.com/0450.%E5%88%A0%E9%99%A4%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E4%B8%AD%E7%9A%84%E8%8A%82%E7%82%B9.html#%E9%80%92%E5%BD%92)）
  - 首先要总结出类型，这里一共五种类型
    - 没有找到该结点，不需要删除，直接返回null
    - 找到了该节点
      - 该节点无左右子节点，直接删除后，返回Null，说明这里没有节点了
      - 节点无左节点，有右节点，删除后，返回右节点
      - 无右节点，有左节点，删除后，返回左节点
      - 左右节点都有，删除后，左节点为右节点的左节点，返回右节点
      - 以上中，返回谁，谁就是替代原来的节点
  - 还有一点要注意，左右子树都可能不止有一个节点
  - 如果是普通二叉树（待完善）
