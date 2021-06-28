#### [20. 有效的括号](https://leetcode-cn.com/problems/valid-parentheses/)



#### [32. 最长有效括号](https://leetcode-cn.com/problems/longest-valid-parentheses/)



####  20. 有效的括号 

一道典型的使用栈的题目。

如果是左半边符号，就往里面加。

如果是右半边的符号，就弹出，并判断是否匹配。

```java
class Solution {
    public boolean isValid(String s) {
        if(s == null || s.length() == 0){
            return true;
        }
        Deque<Character> stack = new ArrayDeque<>();
        for(int i = 0;i < s.length();i++){
            char c = s.charAt(i);
            if(c == '(' || c == '[' || c == '{'){
                stack.push(c);
            }else if(c == ')'){
                if(stack.isEmpty() || stack.pop() != '('){
                    return false;
                }
            }else if(c == ']'){
                if(stack.isEmpty() || stack.pop() != '['){
                    return false;
                }
            }else if(c == '}'){
                if(stack.isEmpty() || stack.pop() != '{'){
                    return false;
                }
            }
        }
        return stack.isEmpty();
    }
}
```







#### 32. 最长有效括号 



> 给你一个只包含 '(' 和 ')' 的字符串，找出最长有效（格式正确且连续）括号子串的长度。
>
>  
>
> 示例 1：
>
> 输入：s = "(()"
> 输出：2
> 解释：最长有效括号子串是 "()"
> 示例 2：
>
> 输入：s = ")()())"
> 输出：4
> 解释：最长有效括号子串是 "()()"
> 示例 3：
>
> 输入：s = ""
> 输出：0 

这个题使用栈做，就是利用栈存下标，当左右括号配对的时候就出栈，然后计算它的长度。

```java
class Solution {
    public int longestValidParentheses(String s) {
        int maxVal = 0;
        Deque<Integer> stack = new ArrayDeque<>();
        stack.push(-1);
        for(int i = 0;i < s.length();i++){
            if(s.charAt(i) == '('){
                stack.push(i);
            }else{
                stack.pop();
                if(stack.isEmpty()){
                    stack.push(i);
                }else{
                    maxVal = Math.max(maxVal, i - stack.peek());
                }
            }
        }
        return maxVal;
    }
}
```

