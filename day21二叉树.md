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
  - TreeNode pre = new TreeNode();这本身会建立一个节点，只是节点的值为空，因此后面在查询pre是否为空时就会出现问题，空节点是 TreeNode pre;
## t501[二叉树搜索树中的众数](https://leetcode.cn/problems/find-mode-in-binary-search-tree/)
### 初始思路
  - 构建一个map，利用中序遍历，统计重复的次数
  - 根据次数进行排序
### 学习收获([学习资源](https://programmercarl.com/0501.%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E4%B8%AD%E7%9A%84%E4%BC%97%E6%95%B0.html#%E9%80%92%E5%BD%92%E6%B3%95))
  - 初始思路适合普通二叉树，前中后序都可以，层序也可以
  - 利用二叉搜索树的特性，中序遍历是有序的，因此只要相同的数一定是相邻的
  - 众数可能不止一个，这里就可以用到maxcount来进行判断，如果发现等于maxcount就也加入结果
  - 但是在一开始并不知道真正的maxcount，所以一旦遇到大于maxcount的时候就修改，然后清空结果
  - 因为在中序中相同的一定会相邻，这里也省去了很多操作
  - steam是一个接口，提供对数据集合使用流的方式进行操作，流中元素不可变，只能被消费一次
  - ```
         if(pre != null){
            if(root.val == pre.val){
                count++;
                if(count == maxcount){
                    res.add(root.val);
                }
                if(count>maxcount){
                    res.clear();
                    maxcount = count;
                    res.add(root.val);
                }
            }else{
                count = 1;
            }
        }
        pre = root;
    ```
    ```
    int rootValue = root.val;
        // 计数
        if (pre == null || rootValue != pre.val) {
            count = 1;
        } else {
            count++;
        }
        // 更新结果以及maxCount
        if (count > maxCount) {
            resList.clear();
            resList.add(rootValue);
            maxCount = count;
        } else if (count == maxCount) {
            resList.add(rootValue);
        }
        pre = root;
    ```
    - 第一种写法，一部分不被允许进入res处理相关的函数，所以会报错
## t236[二叉树的最近公共祖先](https://leetcode.cn/problems/lowest-common-ancestor-of-a-binary-tree/)
  - 
