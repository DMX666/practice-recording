# 代录day3 | 链表基础、t203移除链表元素、t707、t206
## 链表理论基础
    - 链表是一种用 **指针** 串联在一起的 **线性结构**
    - 每个结点两部分组成，数据域，指针域
    - 链表的类型： 单链表，双链表，循环链表
    - 链表的存储：分布不连续，分布机制取决于操作系统的内存管理
    - 链表方便插入删除，但是不方便查询，数组与之相反；链表适合 数据量不固定，删减频繁，较少查询
    - 链表的定义
       里面应该有 指针域（int）数据域（ListNode） 三个构造函数（无参数，一个参数，两个参数）
       <code>
       public class ListNode{
         int val;
         ListNode next;
         public ListNode(){
         }
         public ListNode(int val){
            this.val = val;
        }
        public ListNode(int val, ListNode next){
            this.val = val;
            this.next = next;
        }
       }
       </code>
## t203 移除链表元素
### 初始思路
    - 之前做过该题，已经不算初始思路
    - 核心在于通过删除这一基本操作，分析删除的情况，删除涉及到上一个节点和下一个节点（上一个节点的指针指向下一个节点），共两种，一种是删除头节点，一种是删除中间节点（包括尾节点），这两种删除操作不一样的原因在于头节点没有上一个节点的指针，尾节点虽然没有下一个节点，但是删除操作不会涉及到
    - 创建一个新的虚拟节点作为头节点，这样所有的删除操作方法便统一了
    - <code>/**
              * Definition for singly-linked list.
              * public class ListNode {
              *     int val;
              *     ListNode next;
              *     ListNode() {}
              *     ListNode(int val) { this.val = val; } 
              *     ListNode(int val, ListNode next) { this.val = val; this.next = next; } 
              * }
              */
                class Solution {
                    public ListNode removeElements(ListNode head, int val) {
                        ListNode newNode = new ListNode(0,head);//创建一个新的虚拟头节点，为了统一删除的操作
                        ListNode pre = newNode;//遍历每个节点的指针，从虚拟头节点开始，
                        while(pre.next != null){ //用pre.next做判断，能够确保遍历到每一个节点
                            if(pre.next.val == val){
                                pre.next = pre.next.next;                                
                            }else{
                                pre = pre.next; //对于满足if条件的节点来说，下一个节点已经被删除，因此不需要这一步骤，这点容易忘记，移动的本质是改变，在if操作中，删除已经帮助改变了
                            }                            
                        }
                        return newNode.next;//返回虚拟头节点的下一个，就是所要的结果
                    }
                }</code>
### t707设计链表
# 代录day4 t24
## [t24两两交换链表中的节点](https://leetcode.cn/problems/swap-nodes-in-pairs/)
### 初始思路
    - 知道要用虚拟头节点，但是不知道为什么
    - 在交换头结点的时候有些混乱，不知道如何有条理的去分析
    - 对于结束循环的条件不太清楚
### 学习收获（[视频资源](https://www.bilibili.com/video/BV1YT411g7br/?spm_id_from=333.788&vd_source=f0ddb4642249f19ba16b9ccf8ca6e632)）
    - 为什么需要**虚拟头节点**：（1）为了方便头节点自身的交换，（2）交换两节点的时候需要依赖这两节点的前一个结点，所以用虚拟头节点做第一个cur
    - 在遍历的时候要找好**cur**(也就是光标)，这里的cur就是两个待交换结点前的一个结点
    - 对于循环的中止条件，分奇数和偶数，奇数情况下cur.next.next为0，偶数情况下cur.next为0，那么写条件的时候要用&&，并且cur.next在前，否则会出现**空指针**的情况
    - 对于交换的过程中，改变一条，划去一条，改变的同时可以观察该条线是否还需要，如果需要就要**备份**
    - 每一个**指针**其实就代表了一个**结点**
