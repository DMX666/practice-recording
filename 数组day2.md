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
