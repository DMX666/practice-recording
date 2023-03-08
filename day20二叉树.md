# day20
## t654[最大二叉树](https://leetcode.cn/problems/maximum-binary-tree/)
### 初始思路
  - 这道题和前序中序构建二叉树很相似，感觉可以做出来
  - 首先通过最大值确定中间节点，空列表的返回null
  - 然后左边递归为左子树，右边为右子树
  - ```  class Solution {
    public TreeNode constructMaximumBinaryTree(int[] nums) {
        if(nums.length == 0){return null;}
        return consTree(nums);}
    public TreeNode consTree(int[] nums){
        if(nums.length == 0){return null;}//空节点
        int maxnum = Integer.MIN_VALUE;
        int maxIndex = -1;
        for(int i=0; i<nums.length;i++){
            if(nums[i]>maxnum){
                maxnum=nums[i];
                maxIndex = i;
            }else{
                continue;
            }

        }//找出最大值作为中间节点
        TreeNode root = new TreeNode(maxnum);
        int[] left = Arrays.copyOfRange(nums,0,maxIndex);
        int[] right = Arrays.copyOfRange(nums,maxIndex+1,nums.length);
        root.left = consTree(left);
        root.right = consTree(right);
        return root; }} 
      ```
 - 运行通过，可喜可贺
### 学习收获（[学习资源](https://programmercarl.com/0654.%E6%9C%80%E5%A4%A7%E4%BA%8C%E5%8F%89%E6%A0%91.html)）
  - 细化判断条件，对于只剩一个的数组，无需再切割，直接生成新节点，返回就可以
  - 每次切割数组，创建新的数组，浪费空间，直接复用原先的数组，每次传入起止点的Index就可以，与上一题很类似
  - 对于是否判断为空，主要是看代码是否允许空节点进入递归循环，如果允许就不需要判断，不允许则需要
  - 进入条件的改变，也会带来终止条件的改变，如果不允许空节点进入递归，遇到叶子结点就返回（当数组长度为1）。允许空节点进入那么数组长度为0时返回
## t98[验证二叉搜索树](https://leetcode.cn/problems/validate-binary-search-tree/)
### 初始思路
  - 要再写一个函数
  - 终止条件，遇到了叶节点，但是遇到后不知道如何处理
  - 返回值用boolean，因为不一定要检索完整个树
  - ```java
  class Solution {
    public boolean isValidBST(TreeNode root) {
        return isBST(root);

    }
    public boolean isBST(TreeNode root){
        if(root.left==null && root.right==null){
            return false;
        }

        if(root.left!=null){
            if(root.left.val > root.val){
                return false;
            }
        }
        if(root.right != null){
            if(root.right.val < root.val){
                return false;
            }
        }
        return isBST(root.left)&&isBST(root.right);

    }
}
    ```
### 学习收获（[学习资源](https://programmercarl.com/0098.%E9%AA%8C%E8%AF%81%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91.html#%E9%80%92%E5%BD%92%E6%B3%95)）
  - 两种思路，一是按照中序遍历，将所有的数值加入到一个数组中，看数组是否单调递增，如果是那么这个就是二叉搜索树，这里要求二叉搜索树中不能有重复值
  - 另一种是正常的递归思想，
    - 递归的返回值：boolean，不必须将所有的节点遍历完；递归的传参：当前节点
    - 递归的终止条件，空节点是二叉搜索树，二叉搜索树可以为空
    - 递归单层逻辑中序遍历，先找出一个最小值，中序遍历中不断替换该值，如果一路在替换，那么就返回true，否则返回false
    - 二叉搜索树中，必须右边全部大于左边，所以初步思路中的代码逻辑是有问题的，这版代码仅仅能够右子树大于左子树，但是整体不能顾及
    - 在测试代码中，最小值会取到integer的min，所以要先取long的最小值
