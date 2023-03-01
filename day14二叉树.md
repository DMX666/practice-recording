# day14
## 二叉树理论（[学习资源]([https://programmercarl.com/%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E9%80%92%E5%BD%92%E9%81%8D%E5%8E%86.html](https://programmercarl.com/%E4%BA%8C%E5%8F%89%E6%A0%91%E7%90%86%E8%AE%BA%E5%9F%BA%E7%A1%80.html))）
  - 二叉树种类  满二叉树，完全二叉树，二叉搜索树，平衡二叉搜索树（AVL）
  - 二叉树的存储方式，链式存储、顺序存储
  - 二叉树遍历方式 前序，中序，后序（前中后指的是中间节点的顺序） （深度优先）和 层序遍历（广度优先）
  - 二叉树定义
  <code>
  public class BinTreeNode{
    private int data;
    private BinTreeNode leftChild;
    private BinTreeNode rightChild;
    
    BinTreeNode (){}
    BinTreeNode(int data){this.data = data;}
    BinTreeNode(int data, BinTreeNode leftChild, BinTreeNode rightChild){
      this.data = data;
      this.leftChild = leftChild;
      this.rightChild = rightChild;
  }
  </code>
## 二叉树的递归遍历
#### 递归三要素
  - 递归函数的 **参数和返回值**
  - **终止条件**
  - **单层递归**的逻辑
  - 如在前序遍历中
    - 参数：当前节点，存储节点数值的数组，无返回值
    - 终止条件：遍历的节点为空，那么遍历需要终止
    - 单层逻辑：对于前序遍历，先中间节点，再左节点，再右节点
    
### [二叉树的前序遍历](https://leetcode.cn/problems/binary-tree-preorder-traversal/description/)
### [二叉树的中序遍历](https://leetcode.cn/problems/binary-tree-inorder-traversal/)
### [二叉树的后序遍历](https://leetcode.cn/problems/binary-tree-postorder-traversal/)
### 学习收获
  - 对于迭代，自己调用自己，使用的不够熟练
  - 对于终止条件刚开始理解的不够
