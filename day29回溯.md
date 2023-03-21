# day29
## t12[递增子序列](https://leetcode.cn/problems/non-decreasing-subsequences/)
### 初始思路
  - 可以通过排序更为方便
### 学习收获[学习资源](https://www.bilibili.com/video/BV1EG4y1h78v/?spm_id_from=333.788&vd_source=f0ddb4642249f19ba16b9ccf8ca6e632)
  - 这道题也是深度搜索
  - 同一树枝上可以重复，但是同一数层上不能重复，树枝上是一个子集中的元素，数层是不同子集
  - 一定要学会怎么画数图
  - 判断条件，树层上不重复，数枝上数值在递增
  - 子集类问题是没有必要写终止条件的，因为当index足够大的时候会自动跳出循环
  - 并不一定需要排序后再找，因为并不会减少工作量
  - 没有回溯，每层都重新定义了一个uset，只记录当前层，这也是一种去重方式
  - ```
            class Solution {
          private List<Integer> path = new ArrayList<>();
          private List<List<Integer>> res = new ArrayList<>();
          public List<List<Integer>> findSubsequences(int[] nums) {
              backtracking(nums,0);
              return res;

          }

          private void backtracking (int[] nums, int start) {
              if(path.size()>1){res.add(new ArrayList<>(path));}//元素数大于等于2，就是一种结果
              int[] used = new int[201];//题目中给的数字范围-100 到 100

              for(int i=start; i<nums.length; i++){
                  if(!path.isEmpty() && nums[i]<path.get(path.size()-1) || (used[nums[i]+100]==1)){
                      continue;
                      //判断该数是不是更大（保持递增），如果为空会报错，另外如果与之前的重复，就也要剪枝
                  }
                  used[nums[i]+100] = 1;//标记
                  path.add(nums[i]);
                  backtracking(nums,i+1);
                  path.remove(path.size()-1);//回溯

              }

          }
      }
  - ```
## t46[排列](https://leetcode.cn/problems/permutations/)
### 初始思路
  - 不知道如何使用回溯
### 学习收获[学习资源](https://www.bilibili.com/video/BV19v4y1S79W/?spm_id_from=333.788&vd_source=f0ddb4642249f19ba16b9ccf8ca6e632)
  - 不需要考虑去重问题
  - 排列与组合不同，排列强调顺序，组合强调元素内容
  - 排列中相同元素不能重复使用，用use来进行标记
  - 求排列的时候for循环从0开始，因为可以重复使用
## t47[全排列Ⅱ](https://leetcode.cn/problems/permutations-ii/)
### 初始思路
  - 同上一题相同，在添加res的时候判断一下是否有，如果有就不添加
### 学习收获[学习资源](https://www.bilibili.com/video/BV1R84y1i7Tm/?spm_id_from=333.788&vd_source=f0ddb4642249f19ba16b9ccf8ca6e632)
  - 数层不能重复，树枝可以
  
  
