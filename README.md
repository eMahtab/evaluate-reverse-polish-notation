# Evaluate Reverse Polish Notation 
## https://leetcode.com/problems/evaluate-reverse-polish-notation

Evaluate the value of an arithmetic expression in Reverse Polish Notation.

Valid operators are +, -, *, /. Each operand may be an integer or another expression.

Note:
1. Division between two integers should truncate toward zero.
2. The given RPN expression is always valid. That means the expression would always evaluate to a result and there won't be any divide by zero operation.

```
Example 1:

Input: ["2", "1", "+", "3", "*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9

Example 2:

Input: ["4", "13", "5", "/", "+"]
Output: 6
Explanation: (4 + (13 / 5)) = 6

Example 3:

Input: ["10", "6", "9", "3", "+", "-11", "*", "/", "*", "17", "+", "5", "+"]
Output: 22
Explanation: 
  ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
```
## Implementation :

```java
  public static int evalRPN(String[] tokens) {
      Stack<Integer> st = new  Stack<>();
      for(String s : tokens){
        if(isOperator(s)){
         int rightOperand = st.pop();
         int leftOperand = st.pop();
         st.push(evaluate(leftOperand, rightOperand, s));
        } else{
          st.push(Integer.parseInt(s));
        }
      }
      return st.pop();
  }

  private static boolean isOperator(String token) {
    if (token.equals("+") || token.equals("-") || token.equals("*") 
        || token.equals("/")) {
      return true;
    }
    return false;
  }

  private static int evaluate(int left, int right , String operator){
    int result = 0;
    switch(operator){
        case "+" : result = left + right; break;
        case "-" : result = left - right; break;
        case "*" : result = left * right; break;
        case "/" : result = left / right; break;
    }
    return result;
  }
```
Above implementation have runtime complexity of O(n) and space complexity of O(n), where n is the number of elements in the input `tokens` array.
```
Runtime Complexity = O(n)
Space Complexity   = O(n)
```

