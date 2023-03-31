# day39
## t62[不同路径](https://leetcode.cn/problems/unique-paths/)
### 初始思路
  - 暂无思路，感觉是二维的dp
### 学习收获[学习资源](https://programmercarl.com/0062.%E4%B8%8D%E5%90%8C%E8%B7%AF%E5%BE%84.html)
  - 首先要先找出状态推导的公式，在一个格子中，当前状态应该是由上一个或者左一个得到的（因为只能向下或者向右移动），也就是dp[i][j]由dp[i-1][j]或dp[i][j-1]得到
  - 也就是 dp[i][j]=dp[i-1][j]+dp[i][j-1]
  - 左边与上边的值都要初始化，纵方向初始化dp[0][j]=1（一直向右走只有一种走法），横方向初始化dp[i][0]=1（一直向下走也只有一种走法）
  - 遍历顺序，从左往右从上往下，因为每一个都是由上或者左推导得到的
  - 打印dp，方便debug
  - ```
      class Solution {
      public int uniquePaths(int m, int n) {
          int[][] dp = new int[m][n];
          for(int i=0; i<m; i++){
              dp[i][0]=1;
          }
          for(int j=0; j<n; j++){
              dp[0][j]=1;
          }
          for(int i=1; i<m; i++){
              for(int j=1; j<n; j++){
                  dp[i][j] = dp[i-1][j]+dp[i][j-1];
              }
          }
          return dp[m-1][n-1];
          }
      }
    ```
## t63[不同路径2](https://leetcode.cn/problems/unique-paths-ii/)
### 初始思路
  - 基本思路应该与第一题差不多，但是遇到障碍物要进行单独的处理，在障碍物的左边和上边的时候就只剩一个方向的路，在障碍物左边就只能向下走，在障碍物上边就只能向右走
  - 困难：障碍物如何知晓
### 学习收获[学习资源](https://programmercarl.com/0063.%E4%B8%8D%E5%90%8C%E8%B7%AF%E5%BE%84II.html)
  - 对于障碍物不需要单独弄一个数组，直接访问已有的就可以，而且已有的可以对应dp[][]十分方便
  - 初始化也是非常容易忽略掉的一个地方，横向中，障碍物往右的都是0，因为根本不可能到达，纵向中，障碍物向下的也都是0，因为也不可能到达
  - 起始位置或终止位置有障碍的话，是没办法走的，路径数为0
  - ```
      class Solution {
      public int uniquePathsWithObstacles(int[][] obstacleGrid) {
          int m = obstacleGrid.length;
          int n = obstacleGrid[0].length;
          int[][] dp = new int[m][n];
          if(obstacleGrid[0][0]==1 || obstacleGrid[m-1][n-1]==1){
              return 0;//初始或终止位置有障碍物是不可能到达的
          }
          for(int i=0; i<m && obstacleGrid[i][0]==0; i++){
              dp[i][0] = 1;//限制条件除了边界，还有没有障碍物，一旦有了障碍物，后面都是0，    无需再赋值
          }
          for(int j=0; j<n && obstacleGrid[0][j]==0; j++){
              dp[0][j] = 1;//同理
          }
          for(int i=1; i<m; i++){
              for(int j=1; j<n; j++){
                  dp[i][j] = (obstacleGrid[i][j]==1)  ? 0 : dp[i-1][j]+dp[i][j-1]; 
              }
          }//如果obstacleGrid[i][j]==1为真 那么dp[i][j]=0，否则为dp[i-1][j]+dp[i][j-1]
          //也就是如果有障碍物，那么路径为0，没有障碍物就和之前一样
          return dp[m-1][n-1];
            }
        }
    ```
