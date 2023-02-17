# 代码随想录刷题第一天 | 704 二分查找 27移除元素
[code1题目链接：704二分查找](https://leetcode.cn/problems/binary-search/)
[code2题目链接：27移除元素](https://leetcode.cn/problems/remove-element/)
## 初始思路
需要用到递归，要注意边界

## 所遇困难
递归的边界条件难以确定
## 学习收获
### code1.两个边界值
while（L < R） or while(L<= R)区间的定义，影响二分法循环的处理。因为while循环中查找的是一个区间，该区间

大型项目中【】【）这两种较为常见

左闭右闭区间
left = 0; right = size - 1;
left == right是满足左闭右闭区间的，要确保while循环在合法区间
判断是middle还是middle-1要看区间的定义，闭合区间中没有要找的值，Middle值在闭区间上，则要找的值是middle-1，对于左闭右开区间，如果选择middle-1则会漏掉情况
分成三种情况，target< mid target > mid target = mid
对于左闭右开区间，【1，1）是不合法的，不能出现相等的情况
### code2 移除元素
数组，删除中间元素其实是将后续元素逐一覆盖
如果用库函数一行代码解决，那先不要用库函数，还要知道其复杂度
该题目是实现erase过程
双指针思路，时间复杂度O(n),节省一层for循环
快指针：寻找新数组所需要的元素
慢指针：新数组的长度
核心：快慢指针的指向
* （left+right）/2要注意越界问题

* 最后返回的不是slow+1,而是slow，仍然是边界值，此时边界值已经自动+1

  [学习链接](https://programmercarl.com/0704.%E4%BA%8C%E5%88%86%E6%9F%A5%E6%89%BE.html)

## 心得

手感很重要，坚持才会容易得心应手，一直保持计算机的思维


# 代录刷题day2 | t977、t209、t59
## [t977 有序数组的平方](https://leetcode.cn/problems/squares-of-a-sorted-array/)
### 初始思路
  - 快慢指针，两边同步比较绝对值，将数值大的挪动至最左边，然后从头遍历以此平方
  - 空间复杂度为1，但是时间复杂度为O(n^2)，相当于排序+遍历一次
  - Math.abs()求取绝对值
### 学习收获 ([视频链接](https://www.bilibili.com/video/BV1QB4y1D7ep))
  - 为什么想到用双指针：在平方后，最大数在左右两边，越向中间越小，两边同步检索，便可以依次得到由大到小的数据。双指针减少了时间复杂度，那么就要增大空间复杂度。
  - for循环中的终止条件：left<=right 如果不取=，那么左右指针同时指向一个数时，循环不再进行，该数就会被落下
  - for 循环中不写i++：for循环不写i++也符合语法要求
    <code>for (statement 1; statement 2; statement 3) {
        // code block to be executed
      }</code>
      >statement1 在code block之前只执行一次（one time）
      >statement2 定义code block的执行条件
      >statement3 在code block每次之后执行（every time）
    这里面left和right移动的条件是谁更大，因为更大的数字会被写入结果数组中，已经写入的数字被删除，因此要移动
  - 题解使用了while循环，个人用了for循环
## t209[长度最小的子数组](https://leetcode.cn/problems/minimum-size-subarray-sum/)
### 初始思路
  - 使用快慢指针，分别指向最小数组的头和尾，当和小于target的时候，快指针向前，当和大于target的时候慢指针向前，但是结束的边界条件不知道如何确定，因为当right（慢指针）< nums.length 跳出循环时，可能仍然存在答案
### 学习收获（[视频链接](https://www.bilibili.com/video/BV1tZ4y1q7XE/?spm_id_from=333.788&vd_source=f0ddb4642249f19ba16b9ccf8ca6e632)）
  - 没认真读题，要求是>=target，而不是=target,
  - **滑动窗口**本质还是**双指针**
  - for循环中以快指针（也就是窗口的右指针）为结束是没有问题的，左侧指针的移动可以叠加新的情况
  - 左右指针分别实现了一个循环，以右指针为大循环for loop，不落下每一个窗尾，左指针为小循环while loop，不落下每一个窗头
  - 要取最小值，那么一开始就要赋值最大，**Integer.MAX_VALUE**（这是一个数，不是函数，所以没有()），再用函数 Math.min(a,b)
  - 最后返回结果，可以用 **statement ？A(true) ：B(false)**，当statement为true的时候返回A，为false的时候返回B
## t59[螺旋矩阵]()
### 初始思路
  - 通过找规律公式，将每一行按照公式进行书写，但是公式较为繁琐

### 学习收获
  - 不涉及任何算法，只是在模拟转圈，转圈所涉及的边界条件很多
  - 关键四个点：边界上四个点，当前边处理or下一条边处理 要做统一，**遵循  循环不变量 原则**，左闭右开将最后一个节点留给下一条边，自己写代码的时候因为循环的方向改变而没有统一左闭右开导致出错
  - 按照所给方式进行转圈，循环以圈数为界限，转的圈数为n/2(对于宽度来说，每次会处理两条宽)，对于奇数可以进行单独的判断单独赋值
  - 每个圈的起始和终止位置都不是固定的，用字母替代
  - 数组中，nums[i][j]，i一般表示横坐标，j一般表示纵坐标，哪个坐标在变动就用哪个字母来做变量，减少混淆
  - 参考代码写法
    <code>while(loop++<n/2>)</code>