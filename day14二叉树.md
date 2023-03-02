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
## 二叉树的迭代遍历
  - 可以用迭代实现的原因，递归的实现用到的是栈，将函数的局部变量、参数值、返回函数压入栈中，递归返回的时候就从栈中弹出上一次递归的各项参数。那么也可以用栈实现前后中序遍历
  - 本质上还是模拟递归
### 二叉树前序迭代遍历
  - 该过程是模仿栈弹出元素，可以想象，最先弹出来的是中间节点，然后是中间节点的左节点，然后是中间节点的右节点
  - 如果要达到这样的效果，那就先将中间节点Push，然后弹出，弹出后检查中间节点的右节点是否为空，不为空就入栈，再检查左节点，不为空也入栈，然后下一轮再弹出
  - 这个过程有些抽象，拿出一个单独的小三角来思考可以帮助理解
  - 对于root==null的情况可以单独拿出来，作为特殊情况
  - 每次要对左右子节点进行判断，以防止空节点
### 二叉树的中序迭代遍历
  - 前序遍历不能修改后直接拿来使用，这里的原因是，在前序遍历中，当前访问的元素就是要被找的，从中间节点，向左节点，向右节点
  - 迭代要进行两个操作： 处理（将数值加入result数组中）访问（遍历到节点），要处理和要访问的节点在前序遍历中是相同的，但是在这里是不同的
  - 中序遍历看不明白
### 二叉树的后序迭代遍历
  - 前序是   中左右，如果在入栈时调换左右子节点顺序得到的是   中右左， 将这个reverse一下   左右中    就是后序遍历的结果
  <code>Collections.reverse(res);</code>
## 二叉树的统一迭代遍历
  - 解决了访问和操作不在同一个节点的问题，解决方法便是 **做标记**，用空指针对要操作的节点后放一个空指针。要操作和要访问的节点都入栈
