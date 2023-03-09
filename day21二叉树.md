# day21
## t530[二叉搜索树的最小绝对差](https://leetcode.cn/problems/minimum-absolute-difference-in-bst/)
### 初始思路
  - 遍历每一个节点，找最小值，最大值，最后求取差值 
  - ```
      class Solution {
    public int getMinimumDifference(TreeNode root) {
        search(root);
        int res = Integer.parseInt(String.valueOf(max-min));
        return Math.abs(res);}
    private long min = Long.MIN_VALUE;
    private long max = Long.MAX_VALUE;
    public void search(TreeNode root){
        if(root==null){return;}
        search(root.left);
        if(root.val >= max){
            max = root.val;
        }
        if(root.val <= min){
            min = root.val;
        }
        search(root.right);
        return;
    }}
    ```
### 学习收获（[学习资源](https://programmercarl.com/0530.%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E7%9A%84%E6%9C%80%E5%B0%8F%E7%BB%9D%E5%AF%B9%E5%B7%AE.html#%E9%80%92%E5%BD%92)）
  - 这道题是二叉搜索树，可以转成有序数组，这样遍历数组后，就可以求出最小值
  - 采用中序遍历，在遍历的时候不断获取前后两个节点之差，因为在升序数组中，两数最小差只可能出现在相邻数字中
  - 在遍历的时候要注意空节点直接返回0，单层中，遇到空节点就退出这层逻辑return了
  - 找一个pre记录上一个节点
  - 当下节点和上一节点之差，不断调用Math.min()
## t
