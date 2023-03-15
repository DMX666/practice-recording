# day27
## t39[组合总和](https://leetcode.cn/problems/combination-sum/)
### 初始思路
  - 开始对于无限重复不知道怎么入手解决--》突然想到Index是为了去重，那么这里不需要index就可以了
  - 其他基本上和之前的很相似
### 学习收获[学习资源](https://www.bilibili.com/video/BV1KT4y1M7HJ/?spm_id_from=333.788)
  - 重复选取--考虑0，因此题目中给了数的上限，也知道了没有重复元素
  - index依然是需要的否则会出现顺序不同组合相同的情况，横向中需要Index，递归的时候仍然需要把当前的加进来
  - 用break剪枝，那么就一定要对candidates中的元素从小到大进行排序,sort，这样才不会漏掉结果
## t40[组合总和Ⅱ](https://leetcode.cn/problems/combination-sum-ii/description/)
### 初始思路
  - 与之前的十分相似
  - 但是没有注意到这里是需要去重的
### 学习收获[学习资源](https://programmercarl.com/0040.%E7%BB%84%E5%90%88%E6%80%BB%E5%92%8CII.html)
  - 主要是去重，用了一个Boolean数组，Arrays.sort(used,false)，一开始所有的都是没用过的，这里不仅要区分同层的没用过，还要区分同枝
  - ```
                if(i>0 && candidates[i]==candidates[i-1] && !used[i-1]){continue;}
            //有重复并且上一个节点已经被访问过了
            used[i] = true;//已经用过了
            path.add(candidates[i]);
            sum += candidates[i];
            combination(candidates, target, i+1);
            used[i]= false;
            sum -= candidates[i];
            path.remove(path.size()-1);
    ```
## t131[分割回文串](https://leetcode.cn/problems/palindrome-partitioning/)
### 初始思路
  - 要多重循环，n×n-1，从第0个到第n-1个开始的从1一个到n-1个，逐一分割每次分割出的都进行判断是回文就记录，不是就下一个
  - ```
        class Solution {
        List<List<String>> res = new ArrayList<>();
        List<String> temp = new LinkedList<>();
        public List<List<String>> partition(String s) {
            for(int i=0; i<s.length(); i++){
                for(int j=i;j<s.length();j++){
                    temp.add(Character.toString(s.charAt(j)));
                    if(isPalindrome(temp)){
                        res.add(new ArrayList(temp));
                    }

                }
                temp = null;
            }
            return res;

        }

        public boolean isPalindrome(List<String> list){
            List<String> temp = list;
            Collections.reverse(list);
            if(temp.equals(list)){
                return true;
            }
            return false;
        }
    }
    ```
