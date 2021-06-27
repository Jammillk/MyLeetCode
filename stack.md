#### [20. 有效的括号](https://leetcode-cn.com/problems/valid-parentheses/)





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

