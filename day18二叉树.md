# day18
## t513[找树左下角的值](https://leetcode.cn/problems/find-bottom-left-tree-value/)
### 初始思路
  - 一直向左查找，直到找到一个最左的节点
  - 问题：这样的方法是有问题的，因为这里对于最左下的值每理解到位
### 学习收获([学习资源](https://programmercarl.com/0513.%E6%89%BE%E6%A0%91%E5%B7%A6%E4%B8%8B%E8%A7%92%E7%9A%84%E5%80%BC.html#%E6%80%9D%E8%B7%AF))
  - 这里最左下角，其实是最后一行的左起第一个元素，那么一直向左找是找不到的，因为最左的不一定在最后一行
  - 既然提到了行，那么用层序遍历是最简洁的，每次都记录最左边的元素，当遍历到最后一行的时候，也记录下来，就可以得到最终的结果
  <code>
class Solution {
    public int findBottomLeftValue(TreeNode root) {
        Queue<TreeNode> que = new LinkedList<>();
        que.offer(root);
        int result = 0;
        while(!que.isEmpty()){
            int size = que.size();
            for(int i=0; i<size; i++){
                TreeNode node = que.poll();
                if(i==0){result = node.val;}
                if(node.left!=null){que.offer(node.left);}
                if(node.right!= null){que.offer(node.right);}
            }

        }
        return result;
    }
}
  </code>
  <code>
  class Solution {
    public int findBottomLeftValue(TreeNode root) {
        Queue<TreeNode> que = new LinkedList<>();
        que.offer(root);
        int result = 0;
        while(!que.isEmpty()){
          
            for(int i=0; i<que.size(); i++){
                TreeNode node = que.poll();
                if(i==0){result = node.val;}
                if(node.left!=null){que.offer(node.left);}
                if(node.right!= null){que.offer(node.right);}
            }

        }
        return result;
    }
}
  </code>
