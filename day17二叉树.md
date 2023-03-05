# day16
## t110平衡二叉树
### 初始思路
  - 需要用到递归，因为最本质的是要从两个最小的子树进行比较
### 学习收获([学习资源](https://www.bilibili.com/video/BV1Ug411S7my/?spm_id_from=333.788&vd_source=f0ddb4642249f19ba16b9ccf8ca6e632))
  - 对于一个更底层的节点，如果左右高度相差超过一，那么这个树一定不是平衡二叉树，可以直接不再进行新的判断
  - 这题还是要从下向上，因此要采用后序遍历
  - 递归三步骤
  - 【1】参数（节点）返回值（传入节点为根节点的树的高度）。 如果左右子树差值大于1不是平衡树，返回高度没有意义，直接返回-1，用于标记非平衡二叉树
  - 【2】终止条件： 节点为空节点，返回0
  - 【3】单层逻辑：如何判断以当前节点为根节点的是否为平衡树-->通过左右子树的高度差，求出左子树高度，求出右子树高度，根据差值，如果是平衡树就返回当前子树高度，否则就返回-1
  - 左：判断左子树高度，如果不是平衡二叉树，那么就返回-1
  - 右：同上
  - 中间的处理：  到这里，说明左右子树的高度已经求解完毕，求差值，是平衡二叉树就返回高度
  - 注意！ 父节点的高度，应该是子结点高度最大值+1，注意这里要求取最大值
## [t257二叉树的所有路径](https://leetcode.cn/problems/binary-tree-paths/)
### 初始思路
### 学习收获（[学习资源](https://www.bilibili.com/video/BV1ZG411G7Dh/?spm_id_from=333.788&vd_source=f0ddb4642249f19ba16b9ccf8ca6e632)）
  - **回溯**在这道题中是一个很重要的思想，因为要不断返回父节点，其实就是回溯
  - 通过模拟回溯的路径发现，很多路径是可以复用一部分的（删除叶子节点后）
  - 在这里用父节点找到子结点的思路，考虑用到前序遍历，仍然是递归三要素
  - 返回值：无，参数：当前传入节点，存放路径的List，存放结果的数组
  - 终止条件，这里不再是简单的当前节点为零，遍历一条路径直到找到叶节点，那么条件应该是当前节点不为null，左右子节点为null。遇到终止条件后，就讲这一路所遇到的节点遍历出来（不要忽略当前的叶子节点），组合成string字符串，同时加入到结果中
  - 单层逻辑：中，左，右。
  - 中：这里中间是对路径的添加，注意，该步骤应当在终止条件之前，如果在终止条件之后，那么遇到终止条件以后，就不会再将叶子节点进行添加了
  - 左：将左节点放入递归中（注意判断为null）
  - 右：将右节点放入递归中（注意判断为Null）
  - **注意**在左右节点递归的同时，要进行回溯，也就是将最后一个节点去掉，这样能够复用所需要的部分
  <code>
class Solution {
    public List<String> binaryTreePaths(TreeNode root) {
        List<Integer> path = new ArrayList<Integer>();
        List<String> res = new ArrayList<String>();
        if(root==null){return res;}
        traversal(root, path, res);
        return res;

    }
    public void traversal(TreeNode root, List<Integer> path, List<String> res){
        path.add(root.val);//前序遍历，中
        if(root!= null && root.left==null && root.right==null){//终止条件，遇到叶子节点
         StringBuilder sb = new StringBuilder();
            for(int i=0;i<path.size()-1;i++){//只剩下一个，为了方便->的添加
                sb.append(path.get(i)).append("->");//先append数值，再append->
            }
            sb.append(path.get(path.size()-1));//还剩最后一个，不要忘记添加
            res.add(sb.toString());
            return ;//返回值不要忘记
        }
        if(root.left != null){
            traversal(root.left, path, res);//空节点要判断，前序遍历的左节点
            path.remove(path.size()-1);//返回父节点，复用路径
        }
        if(root.right != null){//前序遍历，右节点
            traversal(root.right, path, res);
            path.remove(path.size()-1);
        }
        return ;
    }
}  
</code>
## t[404左叶子之和](https://leetcode.cn/problems/sum-of-left-leaves/)
### 初始思路
  - 模仿写递归的思路，写了一部分，很多边界条件没有想清楚
  <code>
  class Solution {
    public int sumOfLeftLeaves(TreeNode root) {

    }

    public int sum(TreeNode root){
        int sum = 0;
        if(root != null && root.left == null && root.right == null){
            return sum;
        }
        sum = sum + root.left;
        if(root.left != null){
            sum(root.left);
        }
        if(root.right != null){
            sum(root.right);
        }

    }
}</code>
### 学习收获（[学习资源](https://programmercarl.com/0404.%E5%B7%A6%E5%8F%B6%E5%AD%90%E4%B9%8B%E5%92%8C.html#%E8%A7%86%E9%A2%91%E8%AE%B2%E8%A7%A3)）
  - 首先对于左叶子节点的定义没有搞清楚
  - 这里参与求和的只有左叶子节点，也就是A的左孩子不为空,但是左孩子的左右孩子都为空,那么A的左孩子可以称为 左叶子节点
  - 如果当前节点为空，那么左叶子节点和为0
  - 当前节点是不是左叶子节点，必须通过父节点来判断是左孩子还是右孩子
  - 找到左节点的逻辑，node.left != null && node.left.left == null && node.left.right == null
  - 递归三要素
  - 返回值：左叶子节点之和； 参数：当前传入的根节点
  - 终止条件：便利到左叶子节点，或者空节点
  - 单层逻辑：遇到左叶子节点，记录数值，递归求取左子树左叶子之和，递归右子树左叶子之和，相加
