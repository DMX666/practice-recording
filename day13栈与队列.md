# day13 | t239 t347
## t239[滑动窗口最大值](https://leetcode.cn/problems/sliding-window-maximum/)
### 初始思路
  - 借助队列或者栈，减少比较的次数，滑动窗口大小为k，每次只改变一个元素，k-1个元素是不变的，只需要将新增加的元素和原先的最大值做比较，
  - 但是原先最大值如果为第一个元素，那么现在已经不存在了，这个时候要进行新的判断？如何借助数据结构减少判断
### 学习收获（[学习资源](https://programmercarl.com/0239.%E6%BB%91%E5%8A%A8%E7%AA%97%E5%8F%A3%E6%9C%80%E5%A4%A7%E5%80%BC.html)）
  - 优先级队列不可行
  - 单调队列，自己diy
  - 维护一个单调队列，使用双端队列，加入元素时，与队尾元素判断，如果大于队尾的元素，前面的元素全部poll，因为只要有这个元素在，就不可能让前面的元素成为最大值，但是如果小于队尾元素，就要加入
  - 另外如果元素被移除已不在滑动窗口内，那么元素就要被移除，为了判断当前的最大值是否还在滑动窗口范围内，存储在队列中的是元素的下标，而非元素本身
  - 这道题好迷
## t347[前K个高频元素]()
### 初始思路
### 学习收获（[学习资源]()）
