# day7
## [t454 四数相加Ⅱ](https://leetcode.cn/problems/4sum-ii/description/)
### 初始思路
  - 用两个hashmap，但是如何进行运用，不太能想清楚
### 学习收获([学习资源](https://programmercarl.com/0454.%E5%9B%9B%E6%95%B0%E7%9B%B8%E5%8A%A0II.html))
  - getOrDefault这一函数，可以帮助省去判断，default设置为0，就可以实现自动置零并添加
  - 这道题每个数据都要遍历一遍，通过先求出一半，用相反数判断另一半，用两个双层循环解决
  - 该题对于到底是何种组合并没有要求打印，因此一个存放数据，一个存放数量就可以很好的解决该题
## [t383赎金信](https://leetcode.cn/problems/ransom-note/description/)
### 初始思路
  - 该题与t242十分相似，都是快速找到一个数据，这里可以用hashmap也可以用数组
  - 遍历字符串的两种方式
  <code>
  String slist = "1233444asdfgasdgasdg"
  for(int i=0;i<slist.length();i++){
    char cc = slist.charAt(i);
  }
  String slist2 = "1233444asdfgasdgasdg"
  char[] clist = slist2.**toCharArray()**;
  </code>
### 学习收获([学习资源](https://programmercarl.com/0383.%E8%B5%8E%E9%87%91%E4%BF%A1.html#%E5%93%88%E5%B8%8C%E8%A7%A3%E6%B3%95))
  - 用hashmap所消耗的资源更多，因为该数据结构更为复杂，所以用数组是最为便捷、经济的方式
## [t15三数之和](https://leetcode.cn/problems/3sum/)
### 初始思路
  - 对于多重排列组合不知道如何下手，而且该题要保留排列组合的结果
### 学习收获([学习资源](https://programmercarl.com/0015.%E4%B8%89%E6%95%B0%E4%B9%8B%E5%92%8C.html#%E5%85%B6%E4%BB%96%E8%AF%AD%E8%A8%80%E7%89%88%E6%9C%AC))
  - 三个数要有三重循环，在遍历的同时要注意去重的操作
  - 用一个循环作为一个大的循环，该循环主要是遍历a的取值，这个循环从第一位遍历到最后一位
  - 再用双指针作为其他两重循环，分别代表b 和 c
  - 该题目要求和为0，那么可以先对数组进行排序，另外本题未要求返回原始下标，因此下标可以更改
  - 排序后，一旦a的值大于0，那么该组合必不可能为0
  - 这里要考虑去重的问题，分别针对abc三个，对于a每次与上一次做对比，也就是left和left-1(不能取left 和left+1，会影响left的取值判断)
  - left和right相等的时候指向同一个数字，不符合要求，因此while循环中边界条件不取等号
  - 由于已经将数组进行排序，那么对于求和的结果，如果大于0， 最右边的指针向左移动，如果小于0，left向右移动，等于0则计入结果
  - 计入结果后，不应当直接移动左右指针，而应该进行b c的去重，left = left+1的就left++，right=right-1的就right--
  - 对于Left<right这一条件中间也要进行控制，如果没有二次判断，很容易在中间出现超出界限的情况
  - <code>
  **Arrays.sort(nums)**;
  List<List<Integer>> result = new **ArrayList<>()**;
  result.add(**Arrays.asList(nums[i],nums[left],nums[right])**);
  </code>
 ## [t18 四数之和](https://leetcode.cn/problems/4sum/) 
 ### 初始思路
  - 感觉可能会需要用到两个哈希数组，但是哈希难以记录下元素
 ### 学习收获([学习资源](https://programmercarl.com/0018.%E5%9B%9B%E6%95%B0%E4%B9%8B%E5%92%8C.html))
  - 四数之和与三数之和，相差一个数，那么就要多一层循环
  - 对于需要遍历的题目，不要想着可以节省遍历的总次数，所谓“节省”可以通过控制边界条件，指针等帮助减少，但是大体上是没办法回避的
  - 这里的target不一定是0，如果小于0，那么即便nums[i]>target就continue是不成立的，因为负数相加会更小
  - 多一层循环，就用for添加，已经没办法再增加指针了
  - 每一层都要做去重工作
  
  
  
