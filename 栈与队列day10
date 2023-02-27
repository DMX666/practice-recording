# day10
## 232 [用栈实现队列](https://leetcode.cn/problems/implement-queue-using-stacks/)
### 初始思路 没啥思路直接看解析
### 学习收获（[学习资源](https://programmercarl.com/0232.%E7%94%A8%E6%A0%88%E5%AE%9E%E7%8E%B0%E9%98%9F%E5%88%97.html#%E6%80%9D%E8%B7%AF)）
  - 首先实现队列，是一定需要两个栈的，在刚看到题目的时候心里并没有这个概念，下次对于这类型，可以先思考需要什么，每个用于做什么
  - 对于队列是否为空的判断十分重要，也很容易出错，目前对于边界条件，还没有很好的把握，希望能够越来越熟练
  - 一些更为简洁的写法
  <code>
  stackOut.push(stackIn.pop());
  return stackOut.isEmpty() && stackIn.isEmpty();
  </code>
  - 当输出栈为空的时候，再将输入栈里的元素放进来，判断为空很重要
  - peek和Pop可以复用
## t225 [用队列实现栈](https://leetcode.cn/problems/implement-stack-using-queues/description/)
### 初始思路
  - 粗心的以为这题跟上题一样，后来看了解析才明白其实不太一样，因为栈和队列的输入输出就完全不一样
### 学习收获([学习资源](https://programmercarl.com/0225.%E7%94%A8%E9%98%9F%E5%88%97%E5%AE%9E%E7%8E%B0%E6%A0%88.html))
  - 该题目十分关键的一点，从一个元素变两个元素来思考，如何让新来的结点加入到队列的头部，如果只使用队列，会直接加到队尾
  - 那么就使用一个辅助的队列，让新元素先加入，再将老元素加入，就成功实现在头部插入元素，实现了栈的特点
  - 插入成功后，要将两个队列调换，要以一个队列为主
  - 注意 <code>stack0  和  stackO  的区别</code>
