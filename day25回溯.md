# day25
## t216[组合总和Ⅲ](https://leetcode.cn/problems/combination-sum-iii/)
### 初始思路
  - 不会，好难啊。没思路
### 学习收获[学习资源](https://programmercarl.com/0216.%E7%BB%84%E5%90%88%E6%80%BB%E5%92%8CIII.html)
  - 题目关键还是要先想象成一棵树
  - 除了求和的判断，跟上题十分类似，唯一增加的是剪枝需要多考虑一些，另外剪枝位置和回溯的位置要多注意
## t17[电话号码的字母组合](https://leetcode.cn/problems/letter-combinations-of-a-phone-number/)
### 初始思路
  - 对于每个传进来的string，遍历其中的每个char并转为数字，将数字对应的字母罗列出来，对于每个字母串进行for循环
  - 不知道如何使用递归，因为有多个字母串
### 学习收获[学习资源](https://www.bilibili.com/video/BV1yV4y1V7Ug/?spm_id_from=pageDriver&vd_source=f0ddb4642249f19ba16b9ccf8ca6e632)
  - 对于数字和字符串的对应， 直接建造一个字符串数组做对应
  - 除了传入字符串，还传入字符串的index，这个Index来控制当前递归的字符串
  - 这里的index与之前的不同，之前是为了去重，这里是不同的集合中取字母，是不需要去重的
  - ```
    class Solution {
    //直接创造对应，比找到对应更方便
    String[] letterList = {" "," ","abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};
    List<String> res = new ArrayList<>();
    StringBuilder path = new StringBuilder(); 

    public List<String> letterCombinations(String digits) {
        if(digits==null || digits.length()==0){return res;}
        letterCom(digits,0);
        return res;

    }
    public void letterCom (String digits, int index){//index是针对digits的下标，每次传递digit，不同递归用Index来区分
        if(index == digits.length()){
            res.add(path.toString());//index的下标刚超出digit，表明遍历完了，已经有结果了
            return;
        }
        String letter = letterList[digits.charAt(index)-'0'];
        for(int i=0; i<letter.length(); i++){
            path.append(letter.charAt(i));
            letterCom(digits, index+1);
            path.deleteCharAt(path.length()-1);
        }
        //return;
    }
}
  ```
