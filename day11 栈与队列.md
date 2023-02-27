# day11栈与队列
## t20 有效的括号
### 初始思路
  - 虽然写过一次，印象模糊，但是代码还是有问题
  <code>
  class Solution {
    public boolean isValid(String s) {
        Stack<Character> charStack = new Stack<Character>();
        for(int i=0; i<s.length(); i++){
            char cur = s.charAt(i);
            if(cur == '(' || cur=='{' || cur=='['){
                charStack.push(cur);
            }else if(cur == ')'){
                if(charStack.peek()==null){
                    return false;
                }
                if(charStack.peek()=='('){
                    charStack.pop();
                    continue;
                }else{
                    return false;
                }
            }else if(cur=='}'){
                if(charStack.peek()==null){
                    return false;
                }
                if(charStack.peek()=='{'){
                    charStack.pop();
                    continue;
                }else{
                    return false;
                }
            }else if(cur==']'){
                if(charStack.peek()==null){
                    return false;
                }
                if(charStack.peek()=='['){
                    charStack.pop();
                    continue;
                }else{
                    return false;
                }
            }
        }

        return charStack.isEmpty();
    }
}
  </code>
### 学习收获（[学习资源](https://programmercarl.com/0020.%E6%9C%89%E6%95%88%E7%9A%84%E6%8B%AC%E5%8F%B7.html#%E9%A2%98%E5%A4%96%E8%AF%9D)）
  - 因为栈结构的特殊性，非常适合做**匹配**
  - 分析有哪几种匹配错误的情况：左方向括号多余，右方向括号多余，没有多余的括号但是不匹配
  - 将没种情况都代入入栈过程，可以发现其中的规律
  - 栈不为空，但是字符已经遍历完毕； 栈没空字符也没完但是不匹配；栈空了，字符还没有遍历完
  - 对于如何使用栈去做匹配并没有想清楚，遍历到左括号，就push匹配的右括号，这样遍历到右括号的时候相同就pop出来，不相同就说明右问题，返回false
 ## t1047[删除字符串中的所有相邻重复项](https://leetcode.cn/problems/remove-all-adjacent-duplicates-in-string/)
 ### 初始思路
  - 这道题相较于上题目就显得简单很多
  <code>
  class Solution {
    public String removeDuplicates(String s) {
        Stack<Character> charStack = new Stack<Character>();
        for(int i=0; i<s.length(); i++){
            char ch = s.charAt(i);
            if(charStack.isEmpty()){
                charStack.push(ch);
            }else if(charStack.peek()==ch){
                charStack.pop();
            }else {
                charStack.push(ch);
            }
        }
        StringBuilder result = new StringBuilder();
        while(!charStack.isEmpty()){
            result = result.insert(0,charStack.pop());
        }
        return result.toString();
    }
}
  </code>
  - 本题目用了stringbuilder，为了方便从栈中取了字符然后组成字符串
  - toString()不要忘记
  - 另外还有一个易错点，就是栈因为是先进后出，所以栈中元素依次pop出来与最后要求的顺序是相反的，所以可以用insert(0,char ch)
### 学习收获（[学习资源]()）
  - 可以精简代码，在开头做三个If判断时，可以合并其中两个
  - 可以使用String str = ""; str = str+stackChar.pop()更为简单
## t150[逆波兰表达式求值](https://leetcode.cn/problems/evaluate-reverse-polish-notation/)
### 初始思路
  - 充分理解波兰表达式如何求值，就可以写出该题
  - 遇见符号就取数字做运算，并将运算结果写入栈中
  - 遇见数字就写入栈中
  - 入栈，要将字符串转为int
### 学习收获([学习资源](https://programmercarl.com/0150.%E9%80%86%E6%B3%A2%E5%85%B0%E8%A1%A8%E8%BE%BE%E5%BC%8F%E6%B1%82%E5%80%BC.html#%E9%A2%98%E5%A4%96%E8%AF%9D))
  - 字符串因为是 **对象类型**，不能用==进行判断，要用str.equals(str1)
  - equals比较的是对象的内容（区分大小写），==比较的是内存地址（即便内容相同，对象的内存地址也是不同的）
  - string 转 int    Integer.valueOf(str)      Integer.parseInt(str)
  - int 转 string      Integer.toString(num)    String s = ""+num   String.valueOf(num)
  
