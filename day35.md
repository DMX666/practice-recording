# day35
## t406[根据身高重建队列](https://leetcode.cn/problems/queue-reconstruction-by-height/)
### 初始思路
  - 感觉要维护两个变量，很难用贪心（局部最优）
### 学习收获([学习资源](https://programmercarl.com/0406.%E6%A0%B9%E6%8D%AE%E8%BA%AB%E9%AB%98%E9%87%8D%E5%BB%BA%E9%98%9F%E5%88%97.html#%E6%80%9D%E8%B7%AF))
  - 有两个维度，就要 先确定一个维度，再确定另外一个维度
  - 如果先按照身高排序，那么前面的一定比自己高，只需要针对k的数量做局部调整即可，因为在调整的时候知道前面的一定更高，可以很方便的就进行插入
  - Arrays.sort()重写模板
    ```
    Arrays.sort(T[], new Comparator<T>() {
	    public int compare(T a, T b){
		    return fa - fb;
	    }
    });
    
    Arrays.sort(people,(a,b)->{
       if(a[0] == b[0]) return a[1] - b[1];//在两个身高相等的情况下，让k更小的排在前面
            return b[0] - a[0];
    });
    ```
