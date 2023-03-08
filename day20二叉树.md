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
  
