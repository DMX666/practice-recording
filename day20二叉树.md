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
### 学习收获
  
