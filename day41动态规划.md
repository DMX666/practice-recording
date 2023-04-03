# day41
## t343[整数拆分](https://leetcode.cn/problems/integer-break/)
### 初始思路
  - 不知道状态如何推导，感觉有很多种状态，因为n虽然可以由n-1推导，但是也可以由n-2,n-3等等进行推导
### 学习收获[学习资源](https://programmercarl.com/0343.%E6%95%B4%E6%95%B0%E6%8B%86%E5%88%86.html)
  -  尽可能拆成相同的数，想办法拆成m个数，其值相近
  -  10 拆成2-8，8拆成2-6， 6拆成2-4，这是依赖关系
  -  dp[i] i拆分后的最大乘积
  -  拆分i为两个数 j * i-j
  -  拆分成三个数 j * dp[i-j],固定j后，i-j能包含所有情况
  -  初始化dp[0]=0,dp[1]=1,dp[2]=2
  -  遍历顺序，i=3,i<=n,i++     j=1;j<i;j++      dp[i] = math.max(j*(i-j),j*dp[i-j],dp[i])
  -  因为拆成近似的，所以，j<n/2就可以
## t96[不同的二叉搜索树](https://leetcode.cn/problems/unique-binary-search-trees/)
### 初始思路
  - 没思路
### 学习收获[学习资源](https://programmercarl.com/0096.%E4%B8%8D%E5%90%8C%E7%9A%84%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91.html)
  - 这里数值是没有影响的，主要是布局，找布局上的规律
  - dp[3] = dp[0]*dp[2] + dp[1]*dp[1] + dp[2]*dp[2]
