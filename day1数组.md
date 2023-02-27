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


